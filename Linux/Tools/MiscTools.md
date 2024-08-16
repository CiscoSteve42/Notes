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


Tmux Commands that I might Forget
---------------------------------

* Reattach to a Session:  

```bash
tmux ls
tmux attach-session -t 0
```

* Kill window with Prefix + the `&` key
