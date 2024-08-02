Gentoo Installation Mini Guide/Tips & Tricks
============================================
* Because when you're compiling this much, you have the time.  
* Gentoo is great for running in a VM in the background while doing literally anything else. 

NEW NOTES
=========
* After multiple failed and successful Gentoo installs and a good amount of research, I've decided to start these notes from scrach but still leave my old notes at the bottom. 




OLDNOTES
========

Creating a user and not locking yourself out of root during Install 
-------------------------------------------------------------------
### As far as I know, there is no default root password so you do this

* `sudo passwd` to change default root password

* `sudo useradd -m -G users dad` create user, and

* `sudo passwd dad` to set your password, THEN

* `sudo usermod -aG wheel dad` (very important)

* `visudo` or `nano /etc/sudoers` (even more important)

* `su - dad` enjoy your not locked out user 


Setting generic EFI filesystem with fdisk
-----------------------------------------
### (ask explained in the Documentation)

* `lsblk` to confirm your drive (we'll assume sda for simplicity's sake)

* `sudo fdisk /dev/sda` to start partitioning the drive

### IN FDISK:

* `g` wipes the existing disk and assigns a new disk label

* `p` prints out the current partitioning of the disk

* `n` create a new partition, `t` to change it's type

* `+1G` makes the partition size 1Gb, 

* Pressing Enter fills the rest of the disk space with that partition

* `w` writes changes to the disk (don't forget!)


### Useful partition type aliases to remember

* 1 = EFI System

* 19 = Linux swap

* 23 = Linux root (x86-64)


Applying Filesystems to Your Partitions
---------------------------------------
### This is based on the partitions that we just created using recommended filesystems in the Documentation.

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

* `sudo rm -rf *.tar.xz` to clean up.


Installing Base System
----------------------

* `sudo cp --dereference /etc/resolv.conf /mnt/gentoo/etc/` passes DNS info to the new environment so that you still have intarwebz.



### Mount the necessary filesystems

* If using installation disk, just `sudo arch-chroot /mnt/gentoo`

* If not, mount each of these separately:

```sh
sudo mount --types proc /proc /mnt/gentoo/proc
sudo mount --rbind /sys /mnt/gentoo/sys
sudo mount --make-rslave /mnt/gentoo/sys
sudo mount --rbind /dev /mnt/gentoo/dev
sudo mount --make-rslave /mnt/gentoo/dev
sudo mount --bind /run /mnt/gentoo/run
sudo mount --make-slave /mnt/gentoo/run
```

* THEN you can `sudo chroot /mnt/gentoo /bin/bash`

* `source /etc/profile`

* `export PS1="(chroot) ${PS1}`

* `mkdir /efi` and `mount /dev/sda1 /efi` to prepare bootloader

* `emerge-webrsync` installs latest mirrors to System

* `emerge --sync` updates packages

* `eselect news list` lists news items

* `eselect news read` reads items

* These commands will recommend that you update @World `emerge -avuND @world` then `emerge --depclean`

* `eselect profile list` list profiles (may wanna `> plist.txt`)

* `eselect profile set 29` sets up minimal 64-bit environment with no 32 bit support
