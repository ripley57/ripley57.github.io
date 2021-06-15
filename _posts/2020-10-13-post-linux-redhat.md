---
layout: post
title: Red Hat Linux
categories:
  - Linux
---
* [Configurre Red Hat EL 8 on Windows Hyper-V](https://developers.redhat.com/rhel8/install-rhel8-hyperv/)
* [Firewall management using firewalld](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/security_guide/sec-viewing_current_status_and_settings_of_firewalld)
* [ksmtuned can hog CPU](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/virtualization_tuning_and_optimization_guide/chap-ksm)
* Network configuration GUI: `nmtui`  (see also [nmcli](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html-single/networking_guide/index#sec-Adding_and_Configuring_a_Static_Ethernet_Connection_with_nmcli))  
  * If you edit the details of an interface (E.g. the search domains for ens192), then it will update a file such as: `sysconfig/network-scripts/ifcfg-ens192`  
  * To re-generate `/etc/resolv.conf` after updating the search domains, you can run this: `asroot systemctl restart NetworkManager`
  * If `ifup ...` fails, you can try `asroot nmcli device connnect ens192`
* Version: `cat /etc/os-release`
* Check network status: `asroot systemctl -l status network.service`  
