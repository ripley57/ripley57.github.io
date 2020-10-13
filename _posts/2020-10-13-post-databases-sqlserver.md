---
layout: post
title: MS SQL Server
categories:
  - Databases
---
* Client errors:  
  * `[Microsoft][SQL Server Native Client 11.0]Named Pipes Provider: Could not open a connection to SQL Server [5].`  
  `[Microsoft][SQL Server Native Client 11.0]Login timeout expired`  
  **Solution:** Use SQL Server Configuration Manager (an mmc dialog). Expand the network connectivity section on the left. Enable TCP/IP (or named pipes, if that's what you want).  
* [MS SQL Server "mixed mode" authenticaton](https://docs.microsoft.com/en-us/sql/relational-databases/security/choose-an-authentication-mode?view=sql-server-ver15)
