# 使用MySQL

#### 创建数据库

```shell
# 创建数据库
# CREATE DATABASE IF NOT EXISTS <数据库名>
# DEFAULT CHARACTER SET <字符集名> 
# DEFAULT COLLATE <校对规则名>
CREATE DATABASE test_db;
# SHOW CREATE DATABASE 查看数据库的定义声明
SHOW CREATE DATABASE test_db;
```

#### 选择数据库

```shell
#USE dbname;
USE carshcourse;

Database changed
```

USE 语句并不返回任何结果。依赖于使用的客户机，显示某种形式的通知。**Database changed**为mysql命令行实用程序在数据库选择成功后显示的。必须先使用**USE**打开数据库，才能读取其中的数据。

数据库、表、列、用户、权限等的信息被存储在数据库和表中。可以用MySQL的**SHOW**命令来显示这些信息。

```shell
# SHOW DATABASE 查看数据库列表
SHOW DATABASE;
+--------------------+ 
| Database           | 
+--------------------+ 
| information_schema | 
| carshcourse        | 
| mysql              | 
| performance_schema | 
| sys                | 
+--------------------+ 
5 rows in set (0.01 sec)
```

**SHOW DATABASE;**返回可用数据库的一个列表。

#### 创建表

```shell
# CREATE TABLE <表名>
 CREATE TABLE customers
 -> (
 -> id INT(11),
 -> name VARCHAR(25),
 -> deptld INT(11),
 -> salary FLOAT
 -> );
 
 Query OK, 0 rows affected (0.11 sec)
```

为了获得一个数据库内的表的列表，使用**SHOW TABLES;**该语句返回当前萱蕚的数据库内可用的表的列表。

```shell
SHOW TABLES;
+-----------------------+
| Tables_in_carshcourse |
+-----------------------+
| customers             |
+-----------------------+
1 row in set (0.00 sec)
```

**SHOW**可以用来显示表列：

```shell
SHOW COLUMNS FROM customers;
+--------+-------------+------+-----+---------+-------+
| Field  | Type        | Null | Key | Default | Extra |
+--------+-------------+------+-----+---------+-------+
| id     | int(11)     | YES  |     | NULL    |       |
| name   | varchar(25) | YES  |     | NULL    |       |
| deptld | int(11)     | YES  |     | NULL    |       |
| salary | float       | YES  |     | NULL    |       |
+--------+-------------+------+-----+---------+-------+
4 rows in set (0.01 sec)
```

