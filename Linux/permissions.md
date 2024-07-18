User Permissions in Linux/Unix
------------------------------
Because I still haven't learned them, its kinda sad.

Basic Info:
----------
WHAT: 

r: read  
w: write  
x: execute  
-: no write  


WHERE: 

d: directory  
-: file (not a directory)  
b: block device (additional drives or partitions)  
c: character device (mouse, keyboard, all peripherals)  
l: symbolic link  


OTHER: 

t: sticky bit, users can only modify or delete files that THEY own, even if they technically have permissions.

USAGE:
-----
these are written out like this:  
```drwxrw-r--```

which looks like gibberish at first but lets break it down, logically section it off as so: 

```-|---|---|---```
d is the directory  
  rwx: the OWNER of the folder has read, write, and execute  
      rw-: people part of the associated GROUP can read and write to the folder but not run things  
          --r: Anybody else can look, but thats it  


For example, when you add yourself to the docker group, you're allowing your user to the docker group, which has access to the docker.sock file, lets take a look at it's permissions:

```
-rw--rw---
```
The owner (root) will be the only person in this group upon it's creation, since using sudo gives root permission to do whatever command you put in, and nobody outside of that group can access it. So if you don't have root access, no Docker for you. You literally don't have permission. 

Directories
-----------
/ directory (owner is ROOT):

root and lost+found: drwx------ 
tmp: drwxrwxrwx 
All other folders in dir: drwxr-xr-x 


YOUR home directory (owner is YOU):

drwx------


Files:
------
ssh private key: -rw-------   
ssh public key: -rw-r--r--

helloworld.c: -rw-r--r--  
after compiling: rwxr-xr-x  

this is the same logic as chmod +x with non-compiled languages.  


Chmod beyond +x:
---------------
Based on what we just learned about permissions, we can use chmod to:

+: add permissions   
-: remove permissions  
=: give permissions  
X: people already with permissions keep them  

to any or all of the following groups:

u: user  
g: group    
a: all  

so when I make a folder called foo in my home directory (for the sake of example), it has the following permissions: rwxr-xr-x 

lets say that I don't want anybody in this folder except for me and a few people on my team, lets go ahead and make a group for our team called coolpeople:

```sudo groupadd datausers```

then we can use the same usermod -aG command that we use to add ourselves to groups such as sudo and wireshark (owned by the root account) to add new users to our group since we made it and all.
```
sudo usermod -aG coolpeople bob
sudo usermod -aG coolpeople alice
```
Now let's change some permissions up, I want myself and my team have to full access this folder, and nobody else, so we can:

```
chmod u=rwx,g=rwx,a=
```

which gives myself and my trusted associates full access and everybody else unable to interact with the contents.


Additionally, the -R flag sets permissions recursively to all files/folders in the chosen directory 

Chmod with Numbers:
------------------
r = 4  
w = 2  
x = 1  

so a random file has -rw-r--r--,  
it would read out as 644 numerically since it the variable values make it 4+2, 4, 4  


Here's a small list of examples in no particular order:  

Numbers           Letters         
```
chmod 777         chmod u=rwx,g=rwx,a=rwx
chmod 000         chmod u=,g=,a=
chmod 644         chmod u=rwx,g=r-x,a=r-x
chmod 755         chmod u=rw-,g=r--,a=r--
chmod 700         chmod u=rwx
chmod 600         chmod u=rw
chmod 666         chmod u=rw-,g=rw-,a=rw-
```

