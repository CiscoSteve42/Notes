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
    - `$#` The number of passed positional arguments
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

# MY EXERCISE 1 SCRIPT:

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


# Example of an **if** condition in Bash:

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

# An Example of **while** Loops in Bash

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


# Example of an **until** Loop 

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


# **For** loop examples

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

DIR=$(ls .)
for file in ${DIR}; do 
  mv ${DIR} "Not Porn"
done
  
```
