Change Cisco Switch IP:
----------------------
en  
conf t   
int vlan1  
ip addr 192.168.1.1 192.168.2.1  
exit  
copy running-config startup-config
