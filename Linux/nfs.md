Adding a device to NFS server:
------------------------------

ON SERVER:
---------
sudo vim /etc/exports

add desired IP to the server(rw,sync,no_subtree_check)

sudo exportfs -ra  
sudo systemctl restart nfs-kernel-server


ON CLIENT:
---------
sudo apt install nfs-common

sudo mkdir mnt/nfs 

sudo mount -t nfs 192.168.whateverthe.NFS_IPis:/path/to/shared/folder /mnt/nfs

