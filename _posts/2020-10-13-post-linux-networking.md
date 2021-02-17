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
* SSH:  
  * [Configure password-less login (sshkeygen)](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-on-centos7):  
  Create public/private keypair: `ssh-keygen` (Note: Press Return for all questions, including passphrase. Not the most secure, but hey).  
  Copy the public key to the machine(s) you want to log into: `ssh-copy-id nwb-jcdccentos2`  
  You can now login with using a password: (as user ansible): `ssh nwb-jcdccentos2`
