---
layout: post
title: Linux Services
categories:
  - Linux
---
* **systemd**:  
  * Debug service startup faiure: `journalctl -xe -u redis`
  * List all services: `systemctl list-unit-files | grep -i postgres`    
  * Example config file path: `/usr/lib/systemd/system/MFSafeNet.service`
