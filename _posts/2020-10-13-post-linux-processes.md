---
layout: post
title: Linux Processes
categories:
  - Linux
---
* **environment variables in a process**:  
  `[rhel7tpcc-hub]cat /proc/29640/environ | tr '\0' '\n' | grep COBPATH`  
  `COBPATH=/home/hub/pkg_260324_es/lib/es`  
* **pstree**:  
  * See child processes: `pstree -pa` (see also `/proc/<parent-pid>/task/`)
* **shared memory**:  
  * [ipcs command](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/5/html/tuning_and_optimizing_red_hat_enterprise_linux_for_oracle_9i_and_10g_databases/sect-oracle_9i_and_10g_tuning_guide-setting_shared_memory-removing_shared_memory)
* **signals**:
  * https://www-uxsup.csx.cam.ac.uk/courses/moved.Building/signals.pdf
  * SIGABRT (6): The program called the abort() function. This is an emergency stop.
  * SIGSEGV (11): An attempt was made to access memory not allocated to the process. This is often caused by reading off the end of arrays etc.
* **strace**:  
  * Follow child processes (-ff), capture child process output in separate files (-o), and don't truncate the strings (-v -s 1024):      
  `strace -v -s 1024 -o test -ff casstart /rTPCCDBFH /uSYSAD /pSYSAD`  
* **sysctl** (configure kernel parameters at runtime):    
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
  * [Nice examples (from Oracle install)](https://docs.oracle.com/en/database/oracle/oracle-database/19/ladbi/checking-resource-limits-for-oracle-software-installation-users.html#GUID-293874BD-8069-470F-BEBF-A77C06618D5A)   
  * General procedure: edit `/etc/security/limits.conf` (and/or files in `/etc/security/limits.d`) and then run `sysctl -p`    
  * [Names of common items to change](https://www.thegeekdiary.com/understanding-etc-security-limits-conf-file-to-set-ulimit/)  
 
