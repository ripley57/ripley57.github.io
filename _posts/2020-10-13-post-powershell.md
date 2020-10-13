---
layout: post
title: Powershell
categories:
  - Programming
---
* One-liners:  
`powershell -command "Get-Help .\pac_tpcc.ps1 -examples"`  
* Managing Windows scheduled tasks:  
`Start|Enable|Disable-ScheduledTask -TaskName Execute`  							 
* Remoting - from execute_Test.ps1:  
`Enable-PSRemoting -force`  
`Set-Item WSMan:\localhost\Client\TrustedHosts $pair_IP -Force`  
`Restart-Service WinRm`  
* See all the properties of an object:  
`$date | Select-Object -Property *`
* Get a property/member value (i.e. excluding the key "FullName"):  
`$dir = [string](Get-ChildItem -Directory -Path "C:\TPCC5_1\LOAD Ramped*" | Sort CreationTime -Descending | Select-Object -First 1 FullName).FullName`  
* See the CLR (.NET) version being used by PS ([this can be changed with a .config file](http://viziblr.com/news/2012/5/16/the-easy-way-to-run-powershell-20-using-net-framework-40.html)): `$PSVersionTable`
* [Creating in-built help usage](http://kevinpelgrims.com/blog/2010/05/10/add-help-to-your-own-powershell-scripts/)
* Running command-line: `powershell.exe -file Stop-Region.ps1 -Region VREG01 -Server localhost`  
* [Preventing default parameter values from being overwritten with non-named parameter arguments](https://stackoverflow.com/questions/25156729/param-in-powershell-can-i-enforce-a-name-pass-only):  
Declare the last parameter like this to catch-all the non-named parameters args...  
`[Parameter(Mandatory=$False, Position=0)][Array]$RemainingNonNamedArgs`
* [Creating a function library file](https://dennisspan.com/powershell-function-library/)
    
