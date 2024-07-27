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

* `sudo fdisk /dev/sda` to start partitioning the drive

# IN FDISK:

* `g` wipes the existing disk and assigns a new disk label

* `p` prints out the current partitioning of the disk

* `n` create a new partition, `t` to change it's type

* `+1G` makes the partition size 1Gb, 

* Pressing Enter fills the rest of the disk space with that partition

* `w` writes changes to the disk (don't forget!)


# Useful partition type aliases to remember

* 1 = EFI System

* 19 = Linux swap

* 23 = Linux root (x86-64)


Applying Filesystems to Your Partitions
---------------------------------------
# This is based on the partitions that we just created using recommended filesystems in the Documentation.

* `sudo mkfs.xfs /dev/sda3` makes root partition xfs (recommended by Documentation)

* `sudo mkfs.vfat -F 32 /dev/sda1` EFI partition must be FAT32

* `sudo mkswap /dev/sda2` and `sudo swapon /dev/sda2` activate Swap


Mounting Root and Installing the Stage File 
-------------------------------------------

* `mkdir --parents /mnt/gentoo` prepare the mount point

* `sudo mount /dev/sda3 /mnt/gentoo` to mount your root partition

* `date` to confirm the right time. `date 072707172024` is how I would update for the right timezone right now since NTP traffic isn't authenticated yet. 

* Find the tar.xz for your desired stage 3 and `sudo wget` the URL

* `sudo tar xpvf stage3-*.tar.xz --xattrs-include='*.*' --numeric-owner` make sh!t happen. `stage3-*.tar.xz` should cover all versions via wildcard but adjust if needed I suppose.



