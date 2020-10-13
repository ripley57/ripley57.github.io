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
* Version:  
`C:\>psql --version`  
`psql (PostgreSQL) 10.11`
* Locate main config file:  
`psql -U postgres`  
`postgres=# show config_file;`  
`config_file`  
`----------------------------------------`    
`/var/lib/pgsql/12/data/postgresql.conf`  
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
* Drop database example:  
`postgres=# drop database "MicroFocus$SEE$Files$VSAM2";`  
* [pgpass.conf](https://www.postgresql.org/docs/9.1/libpq-pgpass.html):  
Note: pgpass.conf simply provides the password for you.  
`C:\>type %APPDATA%\postgresql\pgpass.conf`  
`localhost:5432:*:postgres:Passport1!`
* [dump database](https://www.linode.com/docs/databases/postgresql/how-to-back-up-your-postgresql-database/):  
`set PGUSER=postgres`  
`pg_dump "MicroFocus$CAS$CrossRegion" > crossregion.bak`  
* [Restore database dump](https://www.linode.com/docs/databases/postgresql/how-to-back-up-your-postgresql-database/):  
`postgres=# create database "MicroFocus$CAS$CrossRegion";`  
`set PGUSER=postgres`  
`psql "MicroFocus$CAS$CrossRegion" < crossregion.bak`  
* [Add a user](https://stackoverflow.com/questions/5189026/how-to-add-a-user-to-postgresql-in-windows)
    