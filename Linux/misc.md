Misc Stuff
==========
Various commands that I might use a few flags on but I'm not 100% with yet. 

Figlet
------
```bash
figlet -o 'figlet -o'
  __ _       _      _
 / _(_) __ _| | ___| |_        ___
| |_| |/ _` | |/ _ | __|_____ / _ \
|  _| | (_| | |  __| |_|_____| (_) |
|_| |_|\__, |_|\___|\__|      \___/
       |___/

```

Wget to Avoid Clicking Image Links
----------------------------------
* Works with Startpage, SearX instances, and DuckDuckGo  
* Does **NOT** work with Google, Bing, or Yahoo  

If you're on a search engine, and you find an image link, you can copy the link and paste it in your terminal with:


```bash
wget <your copied URL here>
```

and the image should download into the directory that you ran the command in.


Tricks with Grep
----------------
* You can use `grep -B x foo` with x being the number of lines **BELOW** the output that you want printed with the grep'd line, as seen below:

```bash
cat foo.txt | grep -B 5 






```

* You can use `grep -A x foo` to the same effect but above the grep'd line:

```bash
cat foo.txt | grep -A 5



```
