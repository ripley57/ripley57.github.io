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
* [netcat, netc, nc](https://www.varonis.com/blog/netcat-commands/):  
  server: `nc -l -p <port>`
* [tcpdump](https://danielmiessler.com/study/tcpdump/):   
  `tcpdump dst port 6742`  
