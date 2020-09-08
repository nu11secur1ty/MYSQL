# MySQL : Identify Locked Tables

- - - Basic

In MySQL, locked tables are identified using the SHOW OPEN TABLES command.

```mysql
SHOW OPEN TABLES [{FROM | IN} db_name] [LIKE 'pattern' | WHERE expr]
```
- In its simplest form is displays all locked tables.

```mysql
mysql> show open tables;
+--------------------+----------------------------------------------------+--------+-------------+
| Database           | Table                                              | In_use | Name_locked |
+--------------------+----------------------------------------------------+--------+-------------+
| test1              | tab1                                               |      1 |           0 |
| test1              | tab2                                               |      1 |           0 |
| test2              | tab3                                               |      1 |           0 |
+--------------------+----------------------------------------------------+--------+-------------+
3 rows in set (0.00 sec)

mysql>
```

All open tables in the table cache are listed, but the IN_USE column indicates of the table is locked. When the first lock is taken, the value increments to 1. Subsequent lock requests will be blocked until the initial lock is released. Each blocked lock request increments the counter further, such that a count of 5 represents the initial lock and 4 blocked locks.

The NAME_LOCKED columns indicates whether the table name is locked, due to a drop or rename request.
Filtered

The output can be restricted to a single databases as follows.

```mysql
mysql> show open tables in test2;
+--------------------+----------------------------------------------------+--------+-------------+
| Database           | Table                                              | In_use | Name_locked |
+--------------------+----------------------------------------------------+--------+-------------+
| test2              | tab3                                               |      1 |           0 |
+--------------------+----------------------------------------------------+--------+-------------+
1 row in set (0.00 sec)

mysql>
```
The LIKE and WHERE clauses can be used to filter the output further.

```mysql
mysql> show open tables where in_use > 1;
Empty set (0.00 sec)

mysql>


mysql> show open tables like 'tab3';
+--------------------+--------------+--------+-------------+
| Database           | Table        | In_use | Name_locked |
+--------------------+--------------+--------+-------------+
| test2              | tab3         |      1 |           0 |
+--------------------+--------------+--------+-------------+
1 row in set (0.00 sec)

mysql>
```
# BR 
 @nu11secur1ty
