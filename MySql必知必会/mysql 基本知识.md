### 基本操作

#### 创建数据库

```mysql
CREATE DATABASE runoob;
```

#### 删除数据库

```mysql
DROP DATABASE runoob;
```

#### 选择数据库

```mysql
use runoob;
```

#### 创建数据表

```mysql
CREATE TABLE IF NOT EXISTS `runoob_tbl`(
   `runoob_id` INT UNSIGNED AUTO_INCREMENT,
   `runoob_title` VARCHAR(100) NOT NULL,
   `runoob_author` VARCHAR(40) NOT NULL,
   `submission_date` DATE,
   PRIMARY KEY ( `runoob_id` )
)ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

#### 删除数据表

```mysql
DROP TABLE runoob_tbl;
```

#### 查询数据表

```mysql
show tables;
```

#### 展示某个表

```mysql
desc table_name;
```

### 数据操作

#### 插入数据

```mysql
INSERT INTO table_name(field1, field2, ...file)

INSERT INTO runoob_tbl 
    -> (runoob_title, runoob_author, submission_date)
    -> VALUES
    -> ("学习 PHP", "菜鸟教程", NOW());
INSERT INTO runoob_tbl
    -> (runoob_title, runoob_author, submission_date)
    -> VALUES
    -> ("学习 MySQL", "菜鸟教程", NOW());
INSERT INTO runoob_tbl
    -> (runoob_title, runoob_author, submission_date)
    -> VALUES
    -> ("JAVA 教程", "RUNOOB.COM", '2016-05-06');
```

#### 查询数据

```mysql
SELECT column_name,column_name
FROM table_name
[WHERE Clause]
[LIMIT N][ OFFSET M]
```

##### 检索不同的行

```mysql
# DISTINCT 只返回不同的值
SELECT DISTINCT vend_id FROM products;
```

##### 限制结果

```mysql
#LIMIT 限制返回的数据量
SELECT prod_name FROM products LIMIT 5;
#分页查找 从行5开始，返回5条
SELECT prod_name FROM products LIMIT 5,5
```

#### 更新数据

```mysql
UPDATE table_name SET field1=new-value1, field2=new-value2
[WHERE Clause]
```

#### 删除数据

```mysql
DELETE FROM table_name [WHERE Clasuse];
```

> 不指定where语句，会清空表



> - 查询语句中你可以使用一个或者多个表，表之间使用逗号(,)分割，并使用WHERE语句来设定查询条件。
> - SELECT 命令可以读取一条或者多条记录。
> - 你可以使用星号（*）来代替其他字段，SELECT语句会返回表的所有字段数据
> - 你可以使用 WHERE 语句来包含任何条件。
> - 你可以使用 LIMIT 属性来设定返回的记录数。
> - 你可以通过OFFSET指定SELECT语句开始查询的数据偏移量。默认情况下偏移量为0。

#### WHERE 子句

```mysql
SELECT field1, field2,...fieldN FROM table_name1, table_name2...
[WHERE condition1 [AND [OR]] condition2.....
```

```mysql
SELECT * from runoob_tbl WHERE runoob_title='xuexi';
```

> - 查询语句中你可以使用一个或者多个表，表之间使用逗号**,** 分割，并使用WHERE语句来设定查询条件。
> - 你可以在 WHERE 子句中指定任何条件。
> - 你可以使用 AND 或者 OR 指定一个或多个条件。
> - WHERE 子句也可以运用于 SQL 的 DELETE 或者 UPDATE 命令。
> - WHERE 子句类似于程序语言中的 if 条件，根据 MySQL 表中的字段值来读取指定的数据。

| 操作符 | 描述                                                         | **实例**             |
| ------ | ------------------------------------------------------------ | -------------------- |
| =      | 等号，检测两个值是否相等，如果相等返回true                   | (A = B) 返回false。  |
| <>, != | 不等于，检测两个值是否相等，如果不相等返回true               | (A != B) 返回 true。 |
| >      | 大于号，检测左边的值是否大于右边的值, 如果左边的值大于右边的值返回true | (A > B) 返回false。  |
| <      | 小于号，检测左边的值是否小于右边的值, 如果左边的值小于右边的值返回true | (A < B) 返回 true。  |
| >=     | 大于等于号，检测左边的值是否大于或等于右边的值, 如果左边的值大于或等于右边的值返回true | (A >= B) 返回false。 |
| <=     | 小于等于号，检测左边的值是否小于或等于右边的值, 如果左边的值小于或等于右边的值返回true | (A <= B) 返回 true。 |



### 数据类型

#### 数值类型

| 类型         | 大小                                     | 范围（有符号）                                               | 范围（无符号）                                               | 用途            |
| ------------ | ---------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | --------------- |
| TINYINT      | 1 byte                                   | (-128，127)                                                  | (0，255)                                                     | 小整数值        |
| SMALLINT     | 2 bytes                                  | (-32 768，32 767)                                            | (0，65 535)                                                  | 大整数值        |
| MEDIUMINT    | 3 bytes                                  | (-8 388 608，8 388 607)                                      | (0，16 777 215)                                              | 大整数值        |
| INT或INTEGER | 4 bytes                                  | (-2 147 483 648，2 147 483 647)                              | (0，4 294 967 295)                                           | 大整数值        |
| BIGINT       | 8 bytes                                  | (-9,223,372,036,854,775,808，9 223 372 036 854 775 807)      | (0，18 446 744 073 709 551 615)                              | 极大整数值      |
| FLOAT        | 4 bytes                                  | (-3.402 823 466 E+38，-1.175 494 351 E-38)，0，(1.175 494 351 E-38，3.402 823 466 351 E+38) | 0，(1.175 494 351 E-38，3.402 823 466 E+38)                  | 单精度 浮点数值 |
| DOUBLE       | 8 bytes                                  | (-1.797 693 134 862 315 7 E+308，-2.225 073 858 507 201 4 E-308)，0，(2.225 073 858 507 201 4 E-308，1.797 693 134 862 315 7 E+308) | 0，(2.225 073 858 507 201 4 E-308，1.797 693 134 862 315 7 E+308) | 双精度 浮点数值 |
| DECIMAL      | 对DECIMAL(M,D) ，如果M>D，为M+2否则为D+2 | 依赖于M和D的值                                               | 依赖于M和D的值                                               | 小数值          |
