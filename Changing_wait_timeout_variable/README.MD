# Changing MySQL wait_timeout variable

- We can set the wait_timeout variable, for a session or globally.
- If we set the wait_timeout variable for a session, it will valid only for a particular session. But when we set the wait_timeout variable globally it will valid for all the sessions.


To run these commands, first we need to login to MySql server.
We can check the current values of the wait_timeout variable using below commands.

```mysql
SHOW SESSION VARIABLES LIKE "%wait_timeout%"; or SHOW SESSION VARIABLES LIKE "wait_timeout";
```

- Default wait_timeout value is 28800 seconds.

- - - If we need to set this timeout for a session we can use below command.

```mysql
SET session wait_timeout=300;
```

If we need to change the wait_timeout global value we should follow below steps.


1. Open the my.cnf file which resides in /etc/mysql directory.
2. Add below value with the mysqld blog to my.cnf file.

```mysql
[mysqld]
wait_timeout=300
interactive_timeout = 300
```

3. Restart the MySQL server using command below


```bash
service mysql restart # Debian
systemct restart mysql.service
rcmysql restart       # RHEL-opensuse
```

4. Then we can see the wait_timeout variable has changed globally.

```mysql
SHOW SESSION VARIABLES LIKE "wait_timeout";
```




