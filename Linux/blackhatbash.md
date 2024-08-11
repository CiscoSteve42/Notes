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





