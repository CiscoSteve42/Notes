Cisco CLI Notes
===============
Cisco Command Line Interface notes in no particular order


Setting Up SSH in the Cisco CLI
-------------------------------

* Enable Telnet temporarily 

```
#conf t 
(config)#line vty 0 15
(config-if)#transport input telnet
```


* Set up hostname, DNS, and generate keys 

```
Switch1(config)#hostname Switch1
Switch1(config)#ip domain-name 192.168.1.1 
Switch1(config)#crypto key generate rsa modulus 2048
```


* Set up user and SSH:  

```
 Switch1(config)#ip ssh version 2
 Switch1(config)#username CiscoSteve privilege 15 secret dog123
 Switch1(config)#line vty 0 15
 Switch1(config-if)#transport input SSH
 Switch1(config-if)#login local
 Switch1(config-if)#exit
 Switch1(config)#exit
 Switch1#copy running-config startup-config
```


* Verify configuration with: `Switch1#show ip ssh`


Change Cisco Switch IP:
----------------------
```
Switch1#en  
Switch1#conf t   
Switch1(config)#int vlan1  
Switch1(config-if)#ip addr 192.168.2.1 255.255.255.0
Switch1(config-if)#no shutdown
Switch1(config-if)#exit  
Switch1(config)#exit
Switch1#copy running-config startup-config
```


Activating PoE in the Cisco Cli (for PoE devices)
------------------------------------------------
Obviously only available for PoE-capable equipment

* Do the thing:

```
Switch1#en
Switch1#conf t 
Switch1(config)#interface GigabitEthernet0/9
Switch1(config-if)#power inline auto
```

* Then save and verify: 

```
Switch1(config-if)#exit 
Switch1(config)#exit
Switch1#show power inline interface GigabitEthernet0/9
Switch1#copy running-config startup-config
```
