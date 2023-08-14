## Transactional Support in MySQL

MySQL is virtually unique in modern relational databases in that transactions are not mandatory. Under certain circumstances, they are not even possible. In fact, with MySQL, transactional support is a property not of the MySQL server itself, but of the underlying storage engine employed. Currently, the two most popular storage engines used with MySQL are MyISAM and InnoDB, although a small number of users use BerkeleyDB:

## MyISAM

MyISAM does not support transactions. Using a nontransactional storage engine is fine for certain applications—in particular those that are overwhelmingly read-only. Certainly, if you do not need to manage transactions, you can improve the performance of some applications by avoiding the overhead associated with transaction management. If, on the other hand, you are building an application with a significant amount of updates and concurrent updates to the database, you will probably want to avoid MyISAM and instead rely on a transactional engine.

## InnoDB

InnoDB is the most popular transaction-safe MySQL storage engine. It supports ACID transactions as well as row-level locking and multiversion concurrency.

## Berkeley DB
This storage engine also supports transactions but is currently less widely used than InnoDB.

In a survey conducted by MySQL AB (http://dev.mysql.com/tech-resources/quickpolls/storage-engines.html), about 60% of respondents reported using MyISAM as their primary storage engine, while 37% used InnoDB and about 1% used
