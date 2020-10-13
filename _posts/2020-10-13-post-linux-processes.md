---
layout: post
title: Linux Processes
categories:
  - Linux
---
* **pstree**:  
  * See child processes: `pstree -pa` (see also `/proc/<parent-pid>/task/`)
* **shared memory**:  
  * [ipcs command](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/5/html/tuning_and_optimizing_red_hat_enterprise_linux_for_oracle_9i_and_10g_databases/sect-oracle_9i_and_10g_tuning_guide-setting_shared_memory-removing_shared_memory)
* **strace**:  
  * Follow child processes (-ff), capture child process output in separate files (-o), and don't truncate the strings (-v -s 1024):      
  `strace -v -s 1024 -o test -ff casstart /rTPCCDBFH /uSYSAD /pSYSAD`  
* **sysctl**:  
  * [Updating /etc/sysctl.conf](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/kernel_administration_guide/working_with_sysctl_and_kernel_tunables):  
  1. Use `sysctl -a` to get the full name.  
  2. Add the new value to `/etc/sysctl.d/99-custom.conf` (Note: On my system, this is a symbolic link to `/etc/sysctl.conf`).  
  3. Reboot (alternatively, to avoid the reboot for now, run: `sysctl -p /etc/sysctl.d/99-custom.conf`).  
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
  
