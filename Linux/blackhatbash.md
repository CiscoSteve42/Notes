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

* Example of using Input Prompting with the `read` command:

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

* MY EXERCISE 1 SCRIPT:

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


