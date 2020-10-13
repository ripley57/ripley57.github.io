---
layout: post
title: Linux Processes
categories:
  - Linux
---
* **child processes**:  
  * See child processes: `pstree -pa` (see also `/proc/<parent-pid>/task/`)
* **strace**:  
  * Follow child processes (-ff), capture child process output in separate files (-o), and don't truncate the strings (-v -s 1024):      
  `strace -v -s 1024 -o test -ff casstart /rTPCCDBFH /uSYSAD /pSYSAD`  
      
