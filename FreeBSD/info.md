It's JUST different enough from Linux
=====================================
Updating regularly throughout my FreeBSD journey in both a desktop and server environment. 


The Config File
---------------
* Is located at /etc/rc.conf

* Contains a list of default values that you can alter such as hostname, ssh, ntpd, nfs, and mountd 

* There aren't a lot of default values listed, but if you go back to /etc/default/rc.conf you'll find a 700 line behemoth of options for you to configure away on

**NOTE** Alot of these are things that you accomplish via packages from your package manager in Linux, unless you're a Nix user of course, then you might feel more at home here.

A quick visual of options:

```sh
nfs_client_enabled="YES"
rcpbind_enable="YES"
mountd_enable="YES"
```

Install packages on FreeBSD
---------------------------

```sh
pkg install navidrome  
```


Search for packages
-------------------

```sh
pkg search neofetch
```


Upgrade Packages
----------------

```sh
pkg update && pkg upgrade
```


Start Services on FreeBSD
-------------------------

```sh
service navidrome onestart  

service navidrome onestatus  
```


Fixing DNS Issues
-----------------
The following sets default DNS to Google:  

```sh
echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf
echo "nameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
```


Restart Network Service
-----------------------

```sh
service netif restart
```


Usermod -aG Equivalent
----------------------

```sh
sudo pw usermod yourmom -G mypants
```


Troubleshooting NTP Issues
--------------------------
* You should really do this in the config file but I'm gonna keep it here for now

Start by setting the wrong date:  
```sh
date 04201984
```

Then connect to the ntp server to get the right date:  


```sh
ntpdate -v -b in.pool.ntp.org
```
I just wrote these 2 commands into a shell script until I figure it out better


Grabbing Patches and Drivers
----------------------------

```sh
freebsd-update fetch
freebsd-update install
```


Using Ports:
-----------
Fetching ports repo:

```sh
portsnap fetch && portsnap extract
```

Find and install packages:

```sh
cd /usr/ports/editors/neovim
make install clean
```


Delete EVERY pkg except pkg
---------------------------
I've clearly been having some fun here.

```sh
sudo pkg info -a | awk '{print $1}' | xargs sudo pkg delete -y
```



