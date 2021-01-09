---
layout: post
title: Linux Sysadmin
categories:
  - Linux
---
* User accounts:  
  * [Add user to sudoers](https://linuxize.com/post/how-to-add-user-to-sudoers-in-centos/)  
  Add user to wheel group: (run this as root) `usermod -aG wheel username`. Now log in again as `username` and run `groups` command.  
  * Create group: `sudo groupadd ansible`
  * [Create user (also add user to sudoers via `wheel` group membership)](https://linuxize.com/post/how-to-create-users-in-linux-using-the-useradd-command/):  
  `sudo useradd -g ansible -G wheel ansible`  
  * Set password
* [Cron](https://opensource.com/article/17/11/how-use-cron-linux)
* [LD_LIBRARY_PATH - how to update for a system service](https://unix.stackexchange.com/questions/46614/how-to-export-ld-library-path-to-all-users-and-system-services):
Add the directory to /etc/ld.so.conf or a new file in /etc/ld.so.conf.d/, depending on distro. After that, you must run (at least on Redhat) ldconfig as root.
* **rpm**:  
  * List installed packages: `rpm -qa`
  * List files in an **uninstalled** rpm: `rpm -qpl ./BaseOS/Packages/yum-utils-4.0.8-3.el8.noarch.rpm`  
  * List files in an **installed** rpm: `rpm -ql postgresql12-server.x86_64 | grep conf`
  * Idenitfy the package a file came from: `rpm -qf /usr/bin/svn`
  * Install an rpm, and automatically install any dependencies (via yum): `yum --nogpgcheck localinstall VirtualBox-6.1-6.1.12_139181_el8-1.x86_64.rpm` 
* **systemd**:  
  * Debug service startup faiure: `journalctl -xe -u redis`
  * List all services: `systemctl list-unit-files | grep -i postgres` or `sudo systemctl list-units --type=service`
  * Example config file path: `/usr/lib/systemd/system/MFSafeNet.service`
* **yum**:
  * [Yum cheatsheet](https://access.redhat.com/sites/default/files/attachments/rh_yum_cheatsheet_1214_jcs_print-1.pdf)
  * List files in an uninstalled package:  
  `yum repoquery --list postgresql12-contrib.x86_64`  
  * List all available versions of each package, rather than the most recent version:  
  `yum --showduplicates --disablerepo="*" --enablerepo="pgdg10" list available`
  * Install a package version that is not the most recent:  
  `yum --showduplicates --disablerepo="*" --enablerepo="pgdg10" install postgresql10-server-10.12`  
  Another example:  
  `yum --showduplicates --disablerepo="*" --enablerepo="pgdg10" install postgresql10-odbc-10.03.0000-1PGDG.rhel7`  
  **Note:** Take the package base name (e.g. "postgresql10-server") and then add the version (e.g. "10.12"). See also [here](https://unix.stackexchange.com/questions/151689/how-can-i-instruct-yum-to-install-a-specific-version-of-package-x).
  
