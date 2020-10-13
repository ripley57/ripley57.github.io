---
layout: post
title: Linux Sysadmin
categories:
  - Linux
---
* [Cron](https://opensource.com/article/17/11/how-use-cron-linux)
* rpm:  
  * List installed packages: `rpm -qa`
  * List files in an **uninstalled** rpm: `rpm -qpl ./BaseOS/Packages/yum-utils-4.0.8-3.el8.noarch.rpm`  
  * List files in an **installed** rpm: `rpm -ql postgresql12-server.x86_64 | grep conf`
  * Idenitfy the package a file came from: `rpm -qf /usr/bin/svn`
  * Install an rpm, and automatically install any dependencies (via yum): `yum --nogpgcheck localinstall VirtualBox-6.1-6.1.12_139181_el8-1.x86_64.rpm` 
