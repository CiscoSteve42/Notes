Gentoo Installation Mini Guide/Tips & Tricks
============================================

Creating a user and not locking yourself out of root during Install 
-------------------------------------------------------------------
# As far as I know, there is no default root password so you do this

* `sudo passwd` to change default root password

* `sudo useradd -m -G users dad` create user, and

* `sudo passwd dad` to set your password, THEN

* `sudo usermod -aG wheel dad` (very important)

* `visudo` or `nano /etc/sudoers` (even more important)

* `su - dad` enjoy your not locked out user 


Setting generic EFI filesystem with fdisk
-----------------------------------------
## (ask explained in the Documentation)

* `lsblk` to confirm your drive (we'll assume sda for simplicity's sake)

* `sudo /dev/sda` to start partitioning the drive
