Install packages on FreeBSD:
---------------------------
```
pkg install navidrome  
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
