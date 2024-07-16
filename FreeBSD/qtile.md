Installing Qtile in FreeBSD
---------------------------
I was unable to install qtile via
```
pkg install qtile
```
but was able to get results with:   

```
portsnap fetch update
cd /usr/ports/x11-wm/qtile
make install clean
```

EXTRA PACKAGES WILL BE REQUIRED:  
your terminal will tell you what they are, install them  
(might update later with my bash history when Qtile finishes installing)
