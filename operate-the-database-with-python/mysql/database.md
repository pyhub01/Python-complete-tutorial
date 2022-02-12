---
coverY: 0
---

# database

## query database

```sql
show databases;
```

This command can query all databases in MySQL.

```sql
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| naive              |
| performance_schema |
| sys                |
| world              |
+--------------------+
6 rows in set (0.00 sec)
```

Above we can see all the databases we already have. The **world** database is the database that comes with MySQL for our practice, **naive** is the database I created, and the other four databases are MySQL system databases. We should not delete them or modify them.

## create database

```sql
create database naive;
```

I used the above command to create a database. If the database does not exist, the database will be created. If the database exists, **ERROR 1007 (HY000): Can't create database 'naive'; database exists** will be returned.

## Modify the database

If we want to modify a database, then we should enter this database:

```sql
use naive;
```

After you have selected the database, you can modify the contents of this database.

## delete database

```sql
drop database sakila;
```

The above command will delete the sakila database, please be very careful, because the authority of this command is very high, if you accidentally delete the database without backup, it will be very difficult to restore, so you should not generally operate the database using root privileges (in a company you don't normally have root privileges)

sakila is a database that comes with MySQL. If you execute this command and delete the sakila database, don't worry, because you can easily restore this database:

{% embed url="https://dev.mysql.com/doc/world-setup/en/world-setup-installation.html" %}
install world database
{% endembed %}

{% embed url="https://dev.mysql.com/doc/sakila/en/sakila-installation.html" %}
install sakila database
{% endembed %}

If you use the windows platform, you just need to double-click the sql file, it will automatically start the MySQL GUI interface, you just need to run the query code, and then the database will be installed in your MySQL.

## Statistics

Start time of this page: February 10, 2022

Completion time of this page: February 10, 2022
