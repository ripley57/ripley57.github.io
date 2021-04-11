---
layout: post
title: Linux Networking
categories:
  - Networking
---
* Curl:
  * [download](https://curl.haxx.se/download.html)
  * CICSWS example (see URIMAP etc and "CICWS Repro steps.txt"):  
  `C:\curl\curl\bin\curl.exe -v -X POST localhost:9233/tpccws/NewOrder -H "Content-Type: text/xml;charset=UTF-8" --data-binary "@C:/curl/New_Order_request.txt"`  
* [netcat, netc, nc](https://www.digitalocean.com/community/tutorials/how-to-use-netcat-to-establish-and-test-tcp-and-udp-connections-on-a-vps):  
  server: `nc -l -p <port>`
* [tcpdump](https://danielmiessler.com/study/tcpdump/):   
  `tcpdump dst port 6742`  
* Alternative to netstat: "ss" command, and also the "ip" command.
* Red Hat networking interface setup:
  * https://www.redhat.com/sysadmin/start-nic-boot
  * https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/deployment_guide/s1-networkscripts-interfaces
* SSH:  
  * Important files:  
    * `$HOME/.ssh/known_hosts`
    * `$HOME/.ssh/authorized_keys`  (On a remote machine, add your public key to this file).
    * `$HOME/.ssh/config`  (Define an alias here for your ssh connection, to simplify connection, e.g. specify ssh port and username)
  * [Configure password-less login (sshkeygen)](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-on-centos7):  
  Create public/private keypair: `ssh-keygen` (e.g. `ssh-keygen -b 1024 -t rsa`) (Note: Press Return for all questions, including passphrase. Not the most secure, but hey).  
  Copy the public key to the machine(s) you want to log into: `ssh-copy-id nwb-jcdccentos2`  
  You can now login without using a password: (as user ansible): `ssh nwb-jcdccentos2`
