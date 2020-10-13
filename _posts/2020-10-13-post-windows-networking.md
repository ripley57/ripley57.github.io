---
layout: post
title: Windows Networking
categories:
  - Networking
---
* IIS
  * Restart: `iisrestart /noforce` (see also [here](https://learning.oreilly.com/library/view/windows-server-cookbook/0596006330/ch12s03.html))
  * Windows Server 2016: The IIS service long name in services.msc is "World Wide Web Publishing Service" (the command-line short name is "W3SVC").
  * vbscript to log something to the IIS response log file under C:\inetpub\log\ (NOTE: the client connection has to work):   
  `Response.AppendToLog "Database Being Accessed"` 
* SSH:
  * Using pscp.exe (from PuttyGen) to copy from Linux to Windows:  
  `pscp -pw mypssword hub@nwb-tpccrhes1:/var/mfcobol/es/TPCCVSAM/ESmonitor1.log .` 
