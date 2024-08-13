Brief Notes on ChromeOS/Chromebooks
===================================
I don't use them a lot, but when I do I have no idea wtf I'm doing so these need to exist to some extent.

Installing Google's version of 'Linux'
--------------------------------------

* Click on the bottom-right panel that contains the time and your battery

* Click on the Android-esqe Settings gear

* Advanced, Developers, Linux development environment

* Finshed product should give you a terminal to your new "Linux" instance! The default OS is Debian 11 

* **ALSO** You cannot access root the usual way with commands such as `su -`, which threw me off. The default root account for the system does not have a password (I guess Google meant for this to be a 'feature' to be more user-friendly to normies) and you'll get prompted for a password that doesn't exist. You have `sudo` and therefore `visudo` obviously, so you can just run visudo as sudo to actually give the sudo group root permissions.

* Or you can be like me and not think of that until immediately after the fact, so to get root access in ChromeOS, you use `sudo su root`



