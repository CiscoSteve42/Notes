Adding a device to NFS server:
=============================

ON SERVER:
---------

* `sudo vim /etc/exports`

* add desired IP and permissions to the folder, as so `/mnt/share 192.168.1.69(rw,sync,no_subtree_check)`

    * If adding a BSD machine, you may have to add `no_root_squash` to the permissions for proper functionality

* then run `sudo exportfs -ra`  

* and reset the service `sudo systemctl restart nfs-kernel-server`


ON CLIENT:
---------

* `sudo apt install nfs-common` adjust based on package manager/distro

* make a directory to be the designated folder if you haven't already `sudo mkdir mnt/nfs`  

* mount that baby up`sudo mount -t nfs 192.168.X.X:/path/to/shared/folder /mnt/nfs`

    * On BSDs, the you also have to declare the nfs version (probably v4) `sudo mount -t nfs -o nfsv4 192.168...`


Fixing Stale File Handle
------------------------
This happens a lot to people like me that always forget to dismount the shared drive before a reboot, so pretty much every time that I run updates. This can be solved by more rebooting, or you can make sure to dismount the drive or add the line to do so to a relevant script:

```bash
#!/usr/bin/env bash

sudo apt update && sudo apt upgrade -y 
sudo umount mnt/nfs
echo "NFS drive unmounted successfully, rebooting now..."
sudo reboot
```
