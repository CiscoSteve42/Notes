Change Cisco Switch IP:
----------------------
en  
conf t   
int vlan1  
ip addr 192.168.2.1 255.255.255.0
no shutdown
exit  
copy running-config startup-config
