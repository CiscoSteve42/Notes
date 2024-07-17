Setting Up SSH in the Cisco CLI
-------------------------------
Enable Telnet temporarily  
```
conf t 
line vty 0 15
transport input telnet
password dog123
```

Set up hostname, DNS, and generate keys  
```
hostname Switch1
ip domain-name 192.168.1.1 
crypto key generate rsa modulus 2048
```

Set up user and SSH  
```
ip ssh version 2
username CiscoSteve privilege 15 secret cat456
line vty 0 15
transport input SSH
login local
copy running-config startup-config
```

Verify configuration with:
```
show ip ssh
```
