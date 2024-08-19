Android 13 w/ Termux Notes
==========================

* Documenting me cloning my Notes repo and setting up Git and my Github stuff in Termux on my Android 13 phone. I am not rooted this is just stock Android but Termux still has some cool stuff to offer besides being able to read manpages on your phone and telling people that you're running Tmux in Termux.

* I'm planning to only work on this file from my phone (which is painfully slower than my regular pace) and setting up a workable environment on my phone, which I imagine will be pretty alias heavy. I definitely plan on covering proot-distro at some point, not sure what else yet just a fun little side project for those rare moments that I don't have my laptop.


Some Basics
-----------

* I won't be giving any initial setup tips, as I've had this install for a while but it comes pretty bareboned package-wise, which makes sense considering what it is. The default package manager is pkg, which is a wrapper for apt but Termux doesn't use any other repos and they strongly suggest against trying it. You CAN use apt instead of pkg but it is also not recommended via the [wiki](https://wiki.termux.com/wiki/Package_Management). You can install packages with `pkg in` which will run an `apt update` before it installs the package if necessary. For the most part it functions like apt.  


Tips and tricks
---------------

* You can not only use the touch screen to scroll through manpages and other docs, but when using Tmux you can TAP on the individual sessions instead of having to use the prefix key at all!

* Having [KDE Connect](https://f-droid.org/packages/org.kde.kdeconnect_tp/) can really help out with moving over things like a keepass file for [KeePassDX](https://f-droid.org/packages/com.kunzisoft.keepass.libre/) or the shared clipboard so you don't have ALL of your passwords in your mobile .kdbx file, which I recommend since this is Android.

* Besides setting up a custom .rc file and aliasing everything, the asterisk `*a` wildcard is going to be your best friend for typing commands.


Proot and Proot-distro
----------------------

* 





