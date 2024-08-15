Linux Privilege Escalation Notes (HtB)
=====================================

Enumeration
-----------

### Environment Enumeration

* `sudo -l` check user's root permissions

* `cat /etc/os-release` show OS/version

* `echo $PATH` check user's PATH

* `env` check user's environmental variables

* `uname -a` or `cat /proc/version` show kernel version

* `lscpu` show CPU information

* `lpstat` shows printer info if CUPS is installed on host

* `cat /etc/fstab` shows drive information

* `route` or `netstat -rn` display routing table

* `getent group wheel sudo` list members of sudo groups

* `df -h` check mounted filesystems

* `find / -type f -name ".*" -exec ls -l {} \; 2>/dev/null | grep YOURUSERNAME > hidden.txt` makes a txt file of all hidden files on the system

* `find / -type d -name ".*" -ls 2>/dev/null > hdir.txt` makes a txt file of hidden directories on the system

* `ls -a /tmp /var/tmp /dev/shm` displays temporary files


### Linux Services & Internals Enumeration

* `lastlog` to check last login time of all users

* `w` displays currently logged in users

* `ls -l /bin /usr/bin/ /usr/sbin/` check permissions in bin folders


