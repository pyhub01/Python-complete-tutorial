---
coverY: 0
---

# First try MySQL

```sql
mysql -u root -p
```

Use the above command to log in to your MySQL. After entering the above command, you need to enter a password. You need to enter your initial password.

```sql
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 9
Server version: 8.0.28 MySQL Community Server - GPL

Copyright (c) 2000, 2022, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>
```

If the above content appears, it means that your MySQL login is successful.



```sql
show databases;
```

The above code can display the database you already have.

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

### mysql syntax and return results

There is a semicolon (;) at the end of each statement in MySQL, otherwise the MySQL statement cannot be executed normally and will wait for you to enter a semicolon. MySQL has multiple lines of statements. If your statement is not completed, it may jump to the next line.

MySQL will return the results of each query statement and operation statement, including the output content, the number of records modified, and the operation time.

## Statistics

Start time of this page: February 2, 2022

Completion time of this page: February 10, 2022
