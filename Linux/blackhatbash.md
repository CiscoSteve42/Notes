Notes while reading Black Hat Bash
==================================
These are the notes that I'm taking while reading Black Hat Bash

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

* Notable Exit Codes:
    - 0 means success
    - 1 means failure
    - 126 means command found but not executable
    - 127 command not found
