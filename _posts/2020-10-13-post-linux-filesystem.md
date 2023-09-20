---
layout: post
title: Linux Filesystem
categories:
  - Linux
---
* find command and follow symlinks: `find -L`
* List symlinks: `find -type l`
* Mount cdrom using /etc/fstab: `/home/hub/Downloads/rhel-8.1-x86_64-dvd.iso     /media/cdrom/   iso9660 loop,ro 0 0`
* List symbols of binary: 
```
# nm -D /usr/pgsql-10/lib/libpq.so.5.10 | grep PQconninfo
0000000000010150 T PQconninfo
0000000000010220 T PQconninfoFree
00000000000118b0 T PQconninfoParse
```
* rsync
  * Exclude directory: `rsync -avz --exclude VirtualBox_VMs /home/jcdc .` (See [here](https://www.thegeekstuff.com/2011/01/rsync-exclude-files-and-folders/))
* Determine file creation time (see also [here](https://kodekloud.com/blog/file-creation-time-linux/#:~:text=to%20our%20terminal.-,Find%20File%20Creation%20Date%2FTime%20Using%20ls%20Command,creation%20time%20of%20a%20file.)
  * Method 1: "stat filename":
  Even on an ext4 filesystem (RH Linux), the "Birth" value was blank (apparently, it is down to the kernel if the "Birth" value is populated):
```
[wibble]stat myfile.txt
  File: '/home/fred/myfile.txt'
  Size: 329066          Blocks: 648        IO Block: 4096   regular file
Device: 802h/2050d      Inode: 2229605     Links: 1
Access: (0644/-rw-r--r--)  Uid: ( 1000/     hub)   Gid: ( 1000/     hub)
Access: 2023-09-20 09:58:38.000000000 +0100
Modify: 2023-09-20 09:58:38.000000000 +0100
Change: 2023-09-20 10:06:05.316755558 +0100
 Birth: -
```
  * Method 2: "debugfs" (Note this must be run as root) - looks for the "crtime" value (not "ctime"!):  
```
[wibble]asroot debugfs -R 'stat myfile.txt' /dev/sda2
debugfs 1.42.9 (28-Dec-2013)
Inode: 2229605   Type: regular    Mode:  0644   Flags: 0x80000
Generation: 2201300265    Version: 0x00000000:00000001
User:  1000   Group:  1000   Size: 329066
File ACL: 0    Directory ACL: 0
Links: 1   Blockcount: 648
Fragment:  Address: 0    Number: 0    Size: 0
 ctime: 0x650ab5fd:4b853998 -- Wed Sep 20 10:06:05 2023
 atime: 0x650ab43e:00000000 -- Wed Sep 20 09:58:38 2023
 mtime: 0x650ab43e:00000000 -- Wed Sep 20 09:58:38 2023
crtime: 0x650ab5fd:4b0b269c -- Wed Sep 20 10:06:05 2023
```  

