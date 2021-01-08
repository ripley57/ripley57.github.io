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
