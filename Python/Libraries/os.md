os
==

* Provides functions for interacting with the operating system (sweet)

* `os.system()` allows you to use shell commands in your program, which opens up a whole world of possibilities, for example:

```python
import os

cmd = 'cat /etc/passwd'
os.system(cmd)
```

* You can also use it like this to get a shell on a system: 

`python -c 'import os; os.system("/bin/sh")'`








