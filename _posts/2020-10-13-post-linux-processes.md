---
layout: post
title: Linux Processes
categories:
  - Linux
---
* **pstree**:  
  * See child processes: `pstree -pa` (see also `/proc/<parent-pid>/task/`)
* **strace**:  
  * Follow child processes (-ff), capture child process output in separate files (-o), and don't truncate the strings (-v -s 1024):      
  `strace -v -s 1024 -o test -ff casstart /rTPCCDBFH /uSYSAD /pSYSAD`  
* [UID/GID of running process](https://unix.stackexchange.com/questions/333598/how-could-one-determine-uid-gid-of-running-process):  
  `cat /proc/<PID>/status (the first two values are real and then effective id)`  
  `Uid: 0 0 0 0`  
  `Gid: 1 1 1 1`       
* **ulimit**:  
  * Soft and Hard limits:  
  `# ulimit -u -S`  
  `# ulimit -u -H`  
  * Increase open files limit (for the current shell): `ulimit -n 4096`  
  * Using prlimit to check the limit (e.g. useful in a script): `prlimit -n -p $$ --noheadings -o SOFT`  
  
