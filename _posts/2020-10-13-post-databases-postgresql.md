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
* Drop database example:  
`postgres=# drop database "MicroFocus$SEE$Files$VSAM2";`  
* [pgpass.conf](https://www.postgresql.org/docs/9.1/libpq-pgpass.html):  
Note: pgpass.conf simply provides the password for you.  
`C:\>type %APPDATA%\postgresql\pgpass.conf`  
`localhost:5432:*:postgres:Passport1!`
* [dump database](https://www.linode.com/docs/databases/postgresql/how-to-back-up-your-postgresql-database/):  
`set PGUSER=postgres`  
`pg_dump "MicroFocus$CAS$CrossRegion" > crossregion.bak`  
  Another example:  
 `/usr/pgsql-10/bin/pg_dump -U escc -W -F t 'MicroFocus$SEE$Files$MLVSAM' > MLVSAM.tar`  
* [Restore database dump](https://www.linode.com/docs/databases/postgresql/how-to-back-up-your-postgresql-database/):  
`postgres=# create database "MicroFocus$CAS$CrossRegion";`  
`set PGUSER=postgres`  
`psql "MicroFocus$CAS$CrossRegion" < crossregion.bak`  
See [here](https://www.postgresqltutorial.com/postgresql-backup-database/)  
* [Add a user](https://stackoverflow.com/questions/5189026/how-to-add-a-user-to-postgresql-in-windows)
    
