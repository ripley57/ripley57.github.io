---
layout: post
title: PostgreSQL
categories:
  - Databases
---
* [General PG admin (including creating new users, aka "roles")](https://www.postgresqltutorial.com/postgresql-administration/)
* [Adding specific access (least privilege model)](https://aws.amazon.com/blogs/database/managing-postgresql-users-and-roles/)
* [Optimization and Tuning](https://wiki.postgresql.org/wiki/Performance_Optimization)
* [Downloads](https://www.enterprisedb.com/downloads/postgres-postgresql-downloads)
* [PG transactions (xact_commit and xact_rollback)](https://www.tutorialspoint.com/postgresql/postgresql_transactions.htm)
* See config values:  
`psql -U postgres postgres -c "show all;" | grep cost`  
* Version:  
`C:\>psql --version`  
`psql (PostgreSQL) 10.11`
* Locate main config file:    
`PGPASSWORD=fred psql -U escc postgres -c "show config_file;"`  
`config_file`  
`----------------------------------------`    
`/var/lib/pgsql/10/data/postgresql.conf`  
* Locate hba (host-based-authentication) file:  
`psql -U postgres`  
`postgres=# show hba_file`  
* List connections to a database:  
Colin: "To see what the connections to the database are, can you run the following query against the cross-region database":  
`psql -U postgres "MicroFocus\$CAS\$CrossRegion" -c "SELECT * FROM pg_stat_activity"`
* List databases - one-liner:  
` psql -U postgres -c "select datname from pg_database"`  
* List databases, then quit:  
`psql -U postgres`  
`\list`  
`\q`  
* List databaases from pg_database:
```
postgres=# select datname from pg_database;
           datname
------------------------------
 postgres
 template1
 template0
 MicroFocus$CAS$CrossRegion
 MicroFocus$CAS$Region$MYPAC
 MicroFocus$SEE$Files$VSAM
 MicroFocus$CAS$Region$MYPAC2
(7 rows)
```
* [pgpass.conf](https://www.postgresql.org/docs/9.1/libpq-pgpass.html):  
Note: pgpass.conf simply provides the password for you.  
`C:\>type %APPDATA%\postgresql\pgpass.conf`  
`localhost:5432:*:postgres:Passport1!`
* [dump single database](https://www.postgresqltutorial.com/postgresql-backup-database/):  
`/usr/pgsql-10/bin/pg_dump -U escc -W -F t 'MicroFocus$SEE$Files$MLVSAM' > MLVSAM.tar`  
* [Restore single database dump](https://www.postgresqltutorial.com/postgresql-restore-database/):  
NOTE: The pg_restore command is very confusing!!! If you are importing the backup archive into the same database, then you need to use "--dbname=postgres". This is because the name of the database being restored is actually in  the archive file. But, if you want to import the backup archive into a differently-named database, then you use "--dbname==<newdbname>", but you will have to create the database first yourself!  
See my script `pg_backup.sh`    
* [Add a user](https://stackoverflow.com/questions/5189026/how-to-add-a-user-to-postgresql-in-windows)
  * [Create a user with postgres privileges](https://chartio.com/resources/tutorials/how-to-change-a-user-to-superuser-in-postgresql/):  
  ```
  psql -U postgres postgres
  # \du
  # create user escc with encrypted password 'CC1adm1n';
  # alter user escc with SUPERUSER CREATEDB REPLICATION;
  ```
* [PG Replication status](https://stackoverflow.com/questions/43388243/check-postgres-replication-status)    
* [Vacuum and analyze (includes query to show last of both)](https://www.lob.com/blog/supercharge-your-postgresql-performance)
