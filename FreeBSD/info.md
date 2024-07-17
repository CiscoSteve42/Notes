It's JUST different enough from Linux
-------------------------------------
Updating regularly throughout my BSD journey.  

The sad part is how many times I've tried to !! just to sigh and ctrl+A  


Install packages on FreeBSD:
---------------------------
```
pkg install navidrome  
```

Search for packages:
-------------------
```
pkg search neofetch
```

Upgrade Packages:
----------------
```
pkg update && pkg upgrade
```

Start Services on FreeBSD:
-------------------------
```
service navidrome onestart  

service navidrome onestatus  
```

Fixing DNS Issues:
-----------------
The following sets default DNS to Google:  
```
echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf
echo "nameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
```

Restart Network Service:
-----------------------
```
service netif restart
```

Usermod -aG Equivalent:
----------------------
```
sudo pw usermod yourmom -G mypants
```

Troubleshooting NTP Issues:
--------------------------
This is just what worked for me as a noob.  
Start by setting the wrong date:  
```
date 04201984
```
Then connect to the ntp server to get the right date:  
```
ntpdate -v -b in.pool.ntp.org
```
I just wrote these 2 commands into a shell script until I figure it out better

Grabbing Patches and Drivers:
----------------------------
```
freebsd-update fetch
freebsd-update install
```


