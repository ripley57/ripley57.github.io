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
* Robocopy
  * [robocopy syntax](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc733145(v=ws.11)?redirectedfrom=MSDN)  
  * Mirror directories (and preserve timestamps, for files and dirs):  
  `robocopy \\source_dir \\dest_dir /MIR /COPY:DT /DCOPY:DT /E`  
  * Copy specific files from the top-level folder (not subdirs):  
  `robocopy \\nwb-xtest\public\ D:\public\ /COPY:DT /DCOPY:DT /E /LEV:1 OpenJDK*`  
  * Non-mirror normal copy, with sub-dir and file not overwritten:  
  `robocopy \\nwb-xtest\c$\Inetpub\wwwroot\ C:\Inetpub\wwwroot\ /COPY:DT /DCOPY:DT /E /XD "aspnet_client" /XF "iisstart.htm"`  
  * Mirroring svn files (exclude ".svn" dirs, creation "C:\automation" dir, don't list folder names:  
  `robocopy \\nwb-xtest\c$\automation\ C:\automation /MIR /COPY:DAT /DCOPY:DAT /E /XD ".svn" /NDL`
  * My MF directory clone, but minus the .git folder:  
  `robocopy C:\Users\jclough\git\MF D:\MF /MIR /COPY:DT /DCOPY:DT /E /XD C:\Users\jclough\git\MF\.git`  
* SMB:  
  * [SMB1 decprecated by Windows (Note: Windows Server 2003 only supports SMB1)](https://blogs.technet.microsoft.com/josebda/2015/04/21/the-deprecation-of-smb1-you-should-be-planning-to-get-rid-of-this-old-smb-dialect/)  
Note: If you need to add support for the SMBv1 protocol client-side, use appwiz.cpl and add/remove features.
* Windows symbolic links
  * A "junction" is a link to a target folder.
  Example (using the sysinternals tool "junction.exe"):
  `junction.exe c:\users\jclough\My_Files "c:\users\jclough\OneDrive - Rocket Software, Inc\My_Files"  
  And to later verify that this is a junction:  
  `junction.exe c:\users\jclough\My_Files`  
  `...`  
  `c:\users\jclough\My_Files: JUNCTION`  
  `   Substitute Name: c:\users\jclough\OneDrive - Rocket Software, Inc\My_Files`  
