It's JUST different enough from Linux
-------------------------------------
Updating regularly throughout my BSD journey  


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
date 0420131627
```
Then connect to the ntp server to get the right date:  
```
ntpdate -v -b in.pool.ntp.org
```

