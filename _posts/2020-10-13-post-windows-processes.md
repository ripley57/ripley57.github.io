---
layout: post
title: Windows Processes
categories:
  - Windows
---
* [psexec.exe examples (of running remote commands)](https://gist.github.com/mpslanker/50469045fbf2a08e40ac)
* List processes including command-line:  
`WMIC path win32_process get Caption,Processid,Commandline`  
`WMIC /OUTPUT:C:\Process.txt path win32_process get Caption,Processid,Commandline`  
* List handles being used by all processes (Note: This matches the Threads and Handles counts in Task Manager): `handle -s [-p processsname]`   
