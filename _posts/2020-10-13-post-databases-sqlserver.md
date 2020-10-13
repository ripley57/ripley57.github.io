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
* [Switch SQL Server authentication mode](https://docs.microsoft.com/en-us/sql/database-engine/configure-windows/change-server-authentication-mode?view=sql-server-ver15)
* [Check basic connectivity to instance name](https://www.manageengine.com/products/active-directory-audit/kb/how-to/how-to-test-sql-server-connection.html)
* [Determine instance name and version](https://www.manageengine.com/products/active-directory-audit/kb/how-to/how-to-check-sql-server-version-name-using-command-prompt.html)
* List databases: `sqlcmd -S localhost -U sa -P Passport1 -Q "select name from sys.databases"` 
* Table: Describe table:  
  `exec sp_help '$DISTRICT_@4_RecordLocks$'`  
* ["who" has SQL Server sessions running?](https://docs.microsoft.com/en-us/sql/relational-databases/system-stored-procedures/sp-who-transact-sql?redirectedfrom=MSDN&view=sql-server-ver15)  
    (Be careful using the query feature in the SQL Server Management UI. This is a session, and also prevents you from deleting the database, until you kill that query session). 
* Indexes:  
  * [View indexes](https://www.mytecbits.com/microsoft/sql-server/find-indexes-on-a-table):  
  `EXEC sp_helpindex 'Customer'`  
  `GO`  
   **Note:** It looks like a restore of a db backup with indexes with restore/create the indexes again.  
  * Dropping indexes:  
  This doesn't look very easy to automate/script, so I will use the SQL Server UI for now (expand each table to see the indexes, but don't delete the primary key indexes).
* Example Queries:
  * To run an adhoc query, right-click on the **database** name and select "New Query". 
  * How to specify the table: `select finalresult from [tpccresults].[dbo].[tpcc_data] Where finalresult IS NOT NULL group by finalresult order by Max(RIGHT(REPLICATE(N' ', 500) + package, 500)) DESC`
  * Show table schema: `select * from INFORMATION_SCHEMA.COLUMNS where TABLE_NAME='tpcc_data'`
  * SQL Server has no "LIMIT" query clause! You need to use "TOP", e.g.:  
  `select top 5 test_id,test_params,test_luid32,test_luid64 from [tpccresults].[dbo].[tpcc_data] order by test_id desc`  
  * SQL Server update example:  
  `update [tpccresults].[dbo].[tpcc_data] set test_type = 'SILK_PAC' where test_id = 3597 and test_type = 'SILK_ZIP'`
* [odbcconf.exe (soon to be deprecated by PowerShell)](https://docs.microsoft.com/en-us/sql/odbc/odbcconf-exe?redirectedfrom=MSDN&view=sql-server-ver15)
* [ODBC Driver "SQL Server" vs "SQL Server Native Client"](https://stackoverflow.com/questions/39440008/differences-between-drivers-for-odbc-drivers)
* [SQL Server Log](https://docs.microsoft.com/en-us/sql/relational-databases/performance/view-the-sql-server-error-log-sql-server-management-studio?view=sql-server-ver15)
* [Forcibly close all connections to database](https://dba.stackexchange.com/questions/6031/how-do-you-kick-users-out-of-a-sql-server-2008-database/6041)
* [SQL Server Single User mode](https://docs.microsoft.com/en-us/sql/relational-databases/databases/set-a-database-to-single-user-mode?view=sql-server-ver15)
    
