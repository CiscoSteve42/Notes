Activating PoE in the Cisco Cli (for PoE devices)
------------------------------------------------

```
en
conf t 
interface GigabitEthernet0/9
power inline auto
```
Save and verify:  
```
exit 
show power inline interface GigabitEthernet0/9
exit
copy running-config startup-config
```
