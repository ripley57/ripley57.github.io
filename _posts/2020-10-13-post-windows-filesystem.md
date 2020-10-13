---
layout: post
title: Windows Filesystem
categories:
  - Windows
---
* Event Log: Search System event log for Windows low disk space warning "disk is at or near capacity":   
  `psloglist -s system | findstr c/:"capacity"`   
  (I've been unable to confirm this, but "capacity" is 200Mb free, or possibly when free space is less than 10% of the disk size).
* Size of a folder:  
  `PS C:\> Get-ChildItem -recurse "C:\temp\" | Measure-Object -Property Length -sum | Format-Table @{Label="Size MB"; Expression={[math]::Round($_.Sum / 1MB,2)}}`  
  `Size MB`  
  `-------`  
  `1882.14`  
* Free disk space on each drive:  
  `PS C:\> gwmi  win32_logicaldisk | Format-Table DeviceId,Size,@{Label="Freespace MB"; Expression={[math]::Round($_.FreeSpace/1MB)}}`  
  `DeviceId          Size Freespace MB`  
  `--------          ---- ------------`  
  `C:        506333229056       181282`  
  `D:       2000263573504      1722109`  
  
