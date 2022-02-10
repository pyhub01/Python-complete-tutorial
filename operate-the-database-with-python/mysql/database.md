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

## Modify the database

If we want to modify a database, then we should enter this database:

```sql
use naive;
```





## Statistics

Start time of this page: February 10, 2022

Completion time of this page: February 10, 2022
