awk nawk, gawk, and mawk
========================

* This is a rabbithole that I fell down earlier when I noted that `man awk` did not pull up anything on Arch Linux. After a bit of research, I discovered that `man gawk` pulls up the awk man page, and that's where our journey begins today...

* Now lets start off with **gawk** since its what led us here. Gawk is GNU awk, basically the awk that the GNU team made when they made their core utils that all we know and love. GNU awk is full of useful features that greatly extend upon the capabilities and features of it's predecessor, awk.

    * Let it be noted that when I was ran a test on Gentoo, it was also gawk, but `man awk` still worked like normal. Although I tried it in Termux on Android and it had the same issue as Arch.

* **awk**, which was created in the 70s at Bell Labs by Alfred **A**ho, Peter **W**einberger, and Brian **K**ernighan (think Crosby, Stills, and Nash) as a tool to process and analyze text data, meant to fill in the gap between basic Unix utilities and more complex programming languages. It kinda revolutionized text processing, and by extension shell scripting, at the time. And its actually a whole scripting language! Here's Hello World in Awk:

   ``` 
    BEGIN {
        print "Hello, world!"
        exit
    }
    ```


    * When I `man awk` on my FreeBSD and OpenBSD machines, I get the manpage for awk. I saw it referred to a few times as **nawk**, or new awk which came out in the 80s,

    * But if you'll G down to the bottom of your awk manpage on FreeBSD or OpenBSD, you'll find the name that they fancy for themselves, the **"One True Awk"** and some interesting lore referring to the fabled *Script Compatibility Wars*. 

* But wait, there's more! Next is **mawk**, which is the default awk for Debian-based OSs, as suspected when the manpages for awk in both Debian and Armbian pulled up mawk. Mawk, like myself, was born in 1991 and was designed to be fast and efficient, although it doesn't have as many features a gawk.  

* Other members of the awk multiverse include tawk, jawk, CLAWK, awka, libmauk, xgawk, and goawk...I could keep going, but it might get **awk**-ward...I'll show myself out.

* So there you are, all of the different forms of awk a little background on them and just 1 example of the difference between Linux and Unix core utils. 

