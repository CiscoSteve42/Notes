Notes while reading Black Hat Bash
==================================
These are the notes that I'm taking while reading Black Hat Bash (award winning thesis statement right here)

Chapter 1: Bash Basics 
----------------------

* `df --human-readable` checks available disk space

* `bash -r script.sh` runs the script in restricted mode

* `bash -n script.sh` doesn't run program but displays errors for debugging

* `>` overwrites and `>>` appends

* `foo >& bar` redirects stdout and stderr to a file

* Assigning variables in bash:

```bash
#!/usr/bin/env bash

let x="23 * 3"
echo ${x}
```

* You can use the following script with a domain or IP as an argument to ping the host:

```bash
#!/usr/bin/env bash

IP="${1}"
ping "${IP}"
```

* The argument would look like this after the chmod `./iping.sh gentoo.org`


* Variables Related to Positional Arguments:
    - `$0` The name of the file
    - `$1, $69, $420` Positional arguments
    - `$###` The number of passed positional arguments
    - `$*` All positional arguments (in a single string)
    - `$@` All positional arguments, but individually quoted (separate strings)

* Example of `$@` and `$*` Differences:

    - `./args.sh "f*ck" "yeah"` with a `$*` will print a single string with each argument, but with `$@` each string will print separately

* use `read` to read the input as a variables

* use `read -r` to do the same, but interpret backslashes literally and not as escape characters

* Example of using **Input** **Prompting** with the `read` command:

```bash
#!/bin/bash

echo "What is your first name?"
read -r firstname

echo "What is your last name?"
read -r lastname

echo "Your name is ${firstname} ${lastname}"
```

* Notable Exit Codes:
    - `0` means success
    - `1` means failure
    - `126` means command found but not executable
    - `127` command not found

* `echo "$?"` returns the exit code used

* redirect output into the abyss: `ls -l > /dev/null`

* the `exit` command can be used to set the exit code:

```bash
#!/bin/bash

exit 69
```

* Then you can `echo $?` to get the valid exit number

* `echo $?` will also let you check the exit codes of other programs

### MY EXERCISE 1 SCRIPT:

```bash
#!/usr/bin/env bash

echo "What is your first name?"
read -r firstname
echo "What is your last name?"
read -r lastname

date +"%m-%d-%Y" > output.txt
echo "${firstname} ${lastname}" >> output.txt
cp output.txt backup.txt

cat output.txt
```

Chapter 2: Flow Control and Text Processing 
-------------------------------------------

* File test operators let us perform tests against files in the system, some examples include:

    * `-d` checks whether the file is a directory
    * `-r` checks whether the file is readable 
    * `-x` checks where the file is executable
    * `-w` checks whether its writable
    * `-f` checks if its a regular file
    * `-s` checks if the file size is greater than zero


* String comparision operators test strings, these are:

    * `=` checks if one string is equal to another
    * `==` same as `=` in double brackets `[[]]`
    * `!=` checks if the string isn't equal
    * `<` BEFORE `>` AFTER, checks whether a string comes before or after another alphabetically
    * `-z` checks if the string is null
    * `-n` checks if it isn't null

* Integer comparison operators are exactly what you think that they are, the different ones:

    * `-eq` checks if 2 numbers are equal
    * `-ne` checks if they're not equal
    * `-ge` checks if a number is greater than OR equal to a number
    * `-gt` checks if a number is greater than another
    * `-lt` checks if it's less
    * `-le` less than or equal to


### Example of an **if** condition in Bash:

```bash
#!/bin/bash

echo "what is x?"
read -r x
if [[ ${x} == 69 ]]; then
  echo "nice"
else
  echo "x is ${x}"
fi
```

* You don't need to use an else statement if it isn't necessary

* `;` needs to separate if and then, `fi` closes the if statement

* `&&` (and) and `||` (or) can be used in statements like you would in the shell. For example, we can append a previous line in our last script to be more specific after adding a new variable:

```bash
y=$(date +"%m-%d")

if [[ ${x} == 420 ]] && [[ ${y} == "04-20" ]] || [[ ${x} == 69 ]]; then
```

### An Example of **while** Loops in Bash

* Performs function while condition is true

* The following script will run forever:

```bash
#!/bin/bash

while true; do 
  echo "Buffering..."
  sleep 2
done
```

* If we wanted to make the loop end on a certain condition, such as the creation of a certain file, we could append the previous script as so:

```bash
#!/bin/bash
SIGNAL = 'stahp'

while [[ ! -f "${SIGNAL}" ]]; do 
  echo "Buffering..."
  sleep 2
done

echo "Video failed to load, aborting"
```


### Example of an **until** Loop 

* The loop runs until a condition is met, for example:

```bash
#!/bin/bash

FILE="your_mom"

touch "${FILE}"
until [[ -s ${FILE} ]]; do 
  echo "${FILE} is still empty"
  echo "Shes blowing up my phone!"
  sleep 2 
done

THING=$(cat your_mom)
echo "${FILE} feels so much better after being filled with ${THING}!"
```

* The previous script will run forever until the file has been filled, so we can enter `echo my_dick > your_mom` into our terminal and the script can finish.


### **For** loop examples

* Interates over a designated sequence, where we define the commands that are ran against each value.

* A common example is interating over series of numbers listed with `seq` (see `man seq` for more details)

```bash
#!/bin/bash

for index in $(seq 69 420); do
  echo "${index}"
done
```

* It can be used for many more relevant tasks as well, such as renaming every file in a folder

```bash
#!/bin/bash

FILES=$(ls .)
COUNT=1

for file in ${FILE}; do 
  if [ -f "$file" ]; then
    mv $"file" "Not_Porn_${COUNT}"
done
```

* Or a creating all of the folders for the previous example to rename

```bash
#!/bin/bash

for the_Horde in $(seq 1 25); do 
  touch "${the_Horde}" # Thrall like
done
```

### Case Statements 

* keyword case followed by an expression, for example:

```bash
#!/bin/bash

FOOD="${1}"

case ${FOOD} in
  "Hot Do"*)
    echo "Is a Hot Dog"
  ;;
  *)
    echo "Is Not a Hot Dog"
  ;;
esac  
```

* Now if you chmod the script, we can run it with 1 argument, which will be passed as a variable to `"${1}`. So we can run it with various arguments for our desired results:

```bash 
$ chmod +x seefood.sh 
$ ./seefood.sh Hot\ Dog 
Is a Hot Dog

$ ./seefood.sh Pizza
Is Not a Hot Dog
```

* Note that the astrisk `*` (not the one from the Bleach OST) acts like a regular Bash wildcard and does it's thing.


###### Text Processing and Parsing

* This section covers the `grep`, `awk`, and `sed` commands. [Distrotube](https://www.youtube.com/@DistroTube) actually has an amazing [video](https://www.youtube.com/watch?v=0AfPcxOoY4w) that covers ALL 3 of these commands specifically, which I highly recommend along with all of his other content. 


### Grep

* The first part of this section goes over the `grep` command. For references to the wonders of grep, check out my [Grep Notes](https://github.com/CiscoSteve42/Notes/blob/main/Linux/Tools/Grep.md) here on Github!


### Awk 
 
* First off, if you're on Arch Linux (btw) you might've noticed that there's no entry when you `man awk`, which is because Arch uses Gnu awk, or gawk, which is a standard GNU util, which is different from mawk, which is the default on Debian. For a full trip down this rabbithole, check out my [Github repo]() covering the history and different forms of awk.

* You can use `awk` to indentify and return specific fields from a file, for example we can take a text file and return just the first field of each line:

```
$ cat foo.txt
You may be
Lost in
The
Game of life

$ awk '{print $1}' foo.txt
```


* You can use this same logic to print multiple fields in any desired order:

```
$ cat footwo.txt
T O M M A R V O L O R I D D L E

$ awk '{print $12,$5,$3,$9,$10,$6,$13,$7,$2,$15,$14,$16,$4,$8,$11,$1}' foo.txt
I A M L O R D V O L D E M O R T
```


* Printing `$NF` will display the last field: 

```
$ cat foodra.txt
You aren't that bad at the game, those guys just suck

$ awk '{print $1,$NF}'
You suck
```


* we can use the `-F` flag to change the separaters (*default delimiters*) for each word, like changing commas to spaces in a CSV as so `awk -F',' '{print $1}' users.csv`


* You can also use awk to emulate tools like `head`, with `NR` being the total amount of records `awk 'NR < 10' example.sh`


* Combining grep and awk can be useful `grep "alias" .zshrc | awk '{print $2}`


### Sed

* That thing that I use in Vim all the time, I now know what its called. 


* `s/Kirk/Picard/g captain.txt > TNGcaptain.txt` will output the replaced version and send it to the new file while the original txt file retains all of it's original values.


* You can remove all whitespace with `sed 's/ //g' foo.txt`


* You can delete lines by giving them the `d` command, you can use it as so `sed '999d' /etc/sudoers`, or you can use `$d` to only delete the last line of the file or `sed 6,9d' bar.txt`  


* You can print specific lines using `p` like so `sed -n '1 p' info.txt`  


* You can make any of these arguments with the `-i` flag, the changes are made to the file itself of as output.


### Job Control 


* You can send a command to the background by using the `&` character as so `htop &`

* You can check to see what job is running in the background with `jobs` then bring that process back to the foreground with `fg %1` assuming that the job ID is 1.


### Keeping Jobs Running After Logout

* Keep a script running in the background after logout or closing the terminal window with the `nohup` command and `&` to send it into the background as so `nohup ./script.sh &`


Bash Customizations for PenTesters 
---------------------------------- 

* placing a script in your `$PATH` allows you to call it like any other program


### Shortening Commands with Aliases

* You can use the `alias` command to set temporary aliases.


### Customizing the .bashrc Profile

* you can set aliases in your .bash/zsh/etc.rc file, for example:

```bash
~ » cat .zshrc | grep alias                    
        aliases
alias neo=neofetch
alias vim=nvim
alias vi=nvim
alias v=nvim
alias t=tmux
alias iv=sxiv
alias ..='cd ..'
alias ...='cd ../..'
alias cl=clear
alias Syu='sudo pacman -Syu'
alias mix=pacmixer
alias blue=blueman-manager
alias wifi='nmcli dev wifi list'
alias news=newsboat
alias disk='sudo fdisk -l'
```

* Then add the changes with `source ~/.bashrc` if you're using bash or `source ~/.zshrc` if you're using zsh. Adjust command according to your preferred shell. 


### Importing Custom Scripts 

* You can also source your .rc file for specific purposes and source it when needed `source ~./samesmailbsgnowplz.sh`


### Capturing Terminal Session Activity

* Example listed to create a sessions directory named sessions (if it doesn't already exist) and saves the session capture in a separate file based on the time of the log creation, which happens when you close the terminal window

```bash
#!/bin/bash
FILENAME=$(date +%m_%d_%Y_%H:%M:%S).log
if [[ ! -­
d ~/sessions ]]; then
  mkdir ~/sessions
fi
# Starting a script session
if [[ -­
z $SCRIPT ]]; then
  export SCRIPT="/home/dad/sessions/${FILENAME}"
  script -­
q -­
f "${SCRIPT}"
fi
```


### My Exercise 2 Script

```bash
#!/usr/bin/env bash

NAME="${1}"
DOMAIN="${2}"
OUTPUT_FILE="results.csv"

if [ -z "${NAME}" || -z "${DOMAIN}" ; then
  echo "This script requires 2 positional arguments: a name, and a target domain"
  exit 1 
fi
  
echo "name,target,result,date" > ${OUTPUT_FILE}

if ping -c 1 "${DOMAIN}" &> /dev/null; then
  echo "${NAME},${DOMAIN},success,$(date)" >> ${OUTPUT_FILE}
else
  echo "${NAME},${DOMAIN},failure,$(date)" >> "${OUTPUT_FILE}"
fi
```


Chapter 3: Setting up a Hacking Lab
-----------------------------------

* Sorry for the delay on this chapter, I didn't have a recent Kali ISO as I try to shy away from the distro in particular and I don't have internet currently so I had to install it at my mom's place.


