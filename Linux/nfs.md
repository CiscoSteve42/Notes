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

# writing this one down for anyone reading my Github, I usually make it into a script on my servers and my autocomplete plugin for zsh on my other devices makes it easy to mount
sudo mount -t nfs 192.168.whateverthe.NFS_IPis:/path/to/shared/folder /mnt/nfs

