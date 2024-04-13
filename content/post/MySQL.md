## 连接 MySQL 数据库
`mysql -u root -p`

## Mysql基础
## EXISTS 语法
在 MySQL 中，EXISTS 操作符用来判断一个子查询是否返回数据行。如果一个子查询返回了至少一个数据行，则 EXISTS 的计算结果为 TRUE，否则计算结果为 FALSE。

## LIKE
% 匹配零或多个任意字符。
_ 匹配单个任意字符。
如果需要匹配通配符，则需要使用 \ 转义字符，如 \% 和 \_。
使用通配符匹配文本时，不区分字母大小写。

## 按自定义顺序排序
## 使用 CASE 实现自定义排序
## 使用 FIELD() 函数实现自定义排序
在 MySQL 中的升序排序中， NULL 值出现在非 NULL 值之前
当我们使用 ORDER BY 子句降序 DESC 排序时， NULL 值排在非 NULL 值的后面

## MySQL LIMIT 
在 MySQL 中，我们使用 LIMIT 子句来限定 SELECT 语句返回的行的数量

当 DISTINCT 遇到 NULL 值时，只保留一个 NULL 值。因为 DISTINCT 认为所有的 NULL 值都是相同的，这与字段的类型无关。

## MySQL 连接类型
MySQL 支持以下类型的连接：

内部联接 (INNER JOIN)
左连接 (LEFT JOIN)
右连接 (RIGHT JOIN)
交叉连接 (CROSS JOIN)
MySQL 目前不支持全连接 FULL OUTER JOIN 。

交叉连接返回两个集合的笛卡尔积。也就是两个表中的所有的行的所有可能的组合。这相当于内连接没有连接条件或者连接条件永远为真

内连接基于连接条件组合两个表中的数据。内连接相当于加了过滤条件的交叉连接。

内连接将第一个表的每一行与第二个表的每一行进行比较，如果满足给定的连接条件，则将两个表的行组合在一起作为结果集中的一行

由于两个表都使用相同的字段进行等值匹配，因此您可以使用 USING 以下查询

左连接是左外连接的简称，左连接需要连接条件。

两个表左连接时，第一个表称为左表，第二表称为右表。例如 A LEFT JOIN B，A 是左表，B 是右表。

左连接以左表的数据行为基础，根据连接匹配右表的每一行，如果匹配成功则将左表和右表的行组合成新的数据行返回；如果匹配不成功则将左表的行和 NULL 值组合成新的数据行返回

右连接是右外连接的简称，右连接需要连接条件。

右连接与左连接处理逻辑相反，右连接以右表的数据行为基础，根据条件匹配左表中的数据。如果匹配不到左表中的数据，则左表中的列为 NULL 值

*右连接其实是左右表交换位置的左连接，即 A RIGHT JOIN B 就是 B LEFT JOIN A，因此右连接很少使用。*

右连接可以转换为下面的左连接

## GROUP BY
HAVING 子句用来过滤 GROUP BY 分组的数据，需要使用逻辑表达式作为条件，其中逻辑表达式中的字段或表达式只能使用分组使用的字段和聚合函数

GROUP BY 子句用于将结果集根据指定的字段或者表达式进行分组。
GROUP BY 子句的分组字段或表达式至少一个，可以多个。
HAVING 子句是可选的，用来过滤分组数据。
GROUP BY 子句经常用于数据统计汇总，通常使用聚合函数。

## UNION
在 MySQL 中，UNION 操作符是一个集合操作符，它用于合并 2 个结果集中的所有的行。

SQL 标准中定义了 3 个集合操作符： UNION, INTERSECT 和 MINUS。目前 MySQL 只支持 UNION

UNION 运算删除了结果集中的重复项，返回一个唯一记录值的结果集。

UNION 是 UNION DISTINCT 的简写

## UNION ALL 运算
UNION ALL 保留了两个结果集中的所有行

## UNION 排序
当需要对 UNION 运算的结果进行排序时，最需要在 SQL 语句的最后添加 ORDER BY 子句。

## UNION 列数
当对两个结果集进行 UNION 运算的时候，要保证每个结果集具有相同的列数。否则就会产生错误。

参与 UNION 运算的结果集和字段的名称没有关系，只要列数一样就可以

## UNION 列名
参与 UNION 运算的结果集只要列数一样就可以。返回结果集的列名采用第一个结果集的列名

## 别名
列别名
表别名
派生表别名
使用派生表必须指定别名。因为，FROM 子句中的所有表都必须有一个名字

可以通过 AS 关键字指定别名，但是 AS 关键字是可选的。
当别名中包含空格时，必须使用 反引号 将别名引起来。
除了为字段指定别名，表达式也可以指定别名。
当 SQL 中涉及多个表时，使用表别名很重要。
派生表必须指定别名。

## 子查询
## 派生表
当一个子查询位于 FORM 子句中时，这个子查询被称为派生表。

子查询是一个嵌套在语句中的查询。
子查询经常做为比较运算的一个操作数被用在 WHERE 子句中。
位于 FORM 子句中的子查询被称为派生表。派生表必须具有别名。

## insert修饰符
在 MySQL 中， INSERT 语句支持 4 个修饰符:
LOW_PRIORITY: 如果你指定了 LOW_PRIORITY 修饰符，MySQL 服务器将延迟执行 INSERT 操作直到没有客户端对表进行读操作。

LOW_PRIORITY 修饰符影响那些只支持表级锁的存储引擎，比如： MyISAM, MEMORY, 和 MERGE。

HIGH_PRIORITY: 如果你指定了 HIGH_PRIORITY 修饰符，它会覆盖掉服务器启动时的 --low-priority-updates 选项。

HIGH_PRIORITY 修饰符影响那些只支持表级锁的存储引擎，比如： MyISAM, MEMORY, 和 MERGE。

IGNORE: 如果你指定了 IGNORE 修饰符，MySQL 服务器会在执行 INSERT 操作期间忽略那些可忽略的错误。这些错误最终会作为 WARNING 返回。

DELAYED: 这个修饰符已经在 MySQL 5.6 版本中弃用，将来会被删除。在 MySQL 8.0 中，这个修饰符可用但会被忽略。

## DELETE 多表删除
只要是 SELECT 语句中允许使用的 JOIN 类型，多表删除语句都可以使用。

多表删除语句中不能使用 LIMIT 子句和 ORDER BY 子句。

## DELETE 修饰符
LOW_PRIORITY: 如果你指定了 LOW_PRIORITY 修饰符，MySQL 服务器将延迟执行 DELETE 操作直到没有客户端对表进行读操作。这个修饰符影响那些只支持表级锁的存储引擎，比如： MyISAM, MEMORY, 和 MERGE。

QUICK: 如果你指定了 QUICK 修饰符，MyISAM 存储引擎不会在 DELETE 操作期间合并索引。这在某种程度上会加快 DELETE 操作。

IGNORE: 如果你指定了 IGNORE 修饰符，MySQL 服务器会在执行 DELETE 操作期间忽略那些可忽略的错误。这些错误最终会作为 WARNING 返回。

## UPDATE 修饰符
LOW_PRIORITY: 如果你指定了 LOW_PRIORITY 修饰符，MySQL 服务器将延迟执行 UPDATE 操作直到没有客户端对表进行读操作。

LOW_PRIORITY 修饰符影响那些只支持表级锁的存储引擎，比如： MyISAM, MEMORY, 和 MERGE。

IGNORE: 如果你指定了 IGNORE 修饰符，MySQL 服务器会在执行 UPDATE 操作期间忽略那些可忽略的错误。这些错误最终会作为 WARNING 返回

REPLACE 语句和 INSERT 语句很像，它们的不同之处在于，当插入过程中出现了重复的主键或者重复的唯一索引的时候，INSERT 语句会产生一个错误，而 REPLACE 语句则先删除旧的行，再插入新的行。

REPLACE 语句还可以使用 SET 关键词，这只适用于操作单行

## MySQL数据库和表
数据库是存储数据的容器。一个数据库中可以包含多个表。要想创建表，必须首先创建数据库。

在 MySQL 中，CREATE DATABASE 和 CREATE SCHEMA 语句用来创建数据库
CREATE DATABASE 和 CREATE SCHEMA 的是一样的
DROP DATABASE 语句将永久删除数据库和数据库中的所有表，请谨慎操作。
DROP DATABASE 和 DROP SCHEMA 是一样的。

## 登陆时指定数据库
mysql -u root -p -D testdb

## 查看当前数据库
使用 SELECT DATABASE()
使用 STATUS
使用 SHOW TABLES
`
CREATE TABLE `testdb`.`user_hobby` (
  `hobby_id` INT NOT NULL AUTO_INCREMENT,
  `user_id` INT NOT NULL,
  `hobby` VARCHAR(45) NOT NULL,
  `created_at` DATETIME NOT NULL,
  INDEX `fk_user_idx` (`user_id` ASC) VISIBLE,
  PRIMARY KEY (`hobby_id`),
  CONSTRAINT `fk_user`
    FOREIGN KEY (`user_id`)
    REFERENCES `testdb`.`user` (`user_id`)
    ON DELETE CASCADE
    ON UPDATE RESTRICT);
`
这里创建的 user_hobby 表有 4 个字段：

hobby_id 列的数据类型是 INT，它不能为 NULL，并且它是一个自增列。
user_id 列的数据类型是 INT。它不能为 NULL。它通过外键指向了 user 表的 user_id 列。
hobby 列的数据类型是 VARCHAR，它最多为 45 个字符。 它不能为 NULL。
created_at 列的数据类型是 DATETIME。它不能为 NULL。
user_hobby 表的约束有：

PRIMARY KEY (`hobby_id`) 子句表明 hobby_id 列是主键。
INDEX `fk_user_idx` 设定了在 user_id 列上建立索引。
CONSTRAINT `fk_user` 设定了一个外键。这个外键将 user_id 列引用了 user 表的 user_id 列

## CREATE TABLE … LIKE
语句可以用来克隆另一个表的定义。它以另一个表的定义为基础创建一个新的空表，包含了原表中定义的列属性和索引

## CREATE TABLE … SELECT
你可以使用 CREATE TABLE ... SELECT 语句从另一个表创建一个新表。该语句会一句 SELECT 子句中的列创建新表，并将 SELECT 的结果集插入到新表中

## ALTER TABLE 语法
其中 alter_action 是一个修改动作，包括：

ADD 关键字可用来添加列、索引、约束等，包括：

ADD [COLUMN]: 添加列
ADD INDEX: 添加索引
ADD PRIMARY KEY: 添加主键
ADD FOREIGN KEY: 添加外键
ADD UNIQUE INDEX: 添加唯一索引
ADD CHECK: 添加检查约束
DROP 关键字可用来删除列、索引、约束等，包括：

DROP [COLUMN] col_name: 删除列
ADD INDEX index_name: 删除索引
DROP PRIMARY KEY: 删除主键
DROP FOREIGN KEY fk_symbol: 删除外键
DROP CHECK symbol: 删除检查约束
MODIFY 关键字用来修改列的定义。与 CHANGE 关键字不同，它不能重命名列。例如: MODIFY [COLUMN] col_name column_definition。

CHANGE 关键字用来修改列的定义。与 MODIFY 关键字不同，它可以重命名列。例如: CHANGE [COLUMN] old_col_name new_col_name column_definition。

RENAME 关键字可以重命名列、索引和表。包括：

RENAME COLUMN old_col_name TO new_col_name: 重命名列。
RENAME INDEX old_index_name TO new_index_name: 重命名索引。
RENAME new_tbl_name: 重命名表。

ALTER TABLE 关键字后面跟要修改的表名。
ADD 关键字可用来添加列、索引、约束等。
DROP 关键字可用来删除列、索引、约束等。
RENAME 关键字可以重命名列、索引和表。
MODIFY 关键字用来修改列的定义。
CHANGE 关键字用来修改列的定义和列名。
RENAME TABLE ... TO ... 用来重命名表。

您可以在一个 RENAME TABLE 语句中同时重命名多个表。
RENAME TABLE 语句不可以用来重命名临时表，而 ALTER TABLE 语句可以用来重命名临时表。

MySQL 提供了 RENAME TABLE 和 ALTER TABLE 语句重命名表。

请记住，在重命名一个表的时候，此表中不能有未完成的事务，并且此表不能是锁定状态。

## TRUNCATE TABLE 语法

如果想要清空一个表， TRUNCATE TABLE 语句比 DELETE 语句更加有效。

TRUNCATE TABLE 语句相当于先将此表删除掉，再创建一个新表。TRUNCATE TABLE 语句需要对操作的表具有 DROP 权限。

TRUNCATE 被归类为 DDL 语句，而 DELETE 被归类为 DML 语句。
TRUNCATE 操作无法被回滚，而 DELETE 可以被回滚。
TRUNCATE 操作删除和重建表，它的速度比 DELETE 快得多。
TRUNCATE 操作会重置表的自增值，而 DELETE 不会。
TRUNCATE 操作不会激活删除触发器，而 DELETE 会。
TRUNCATE 操作不返回代表删除行的数量的值，它通常返回 0 rows affected。DELETE 返回删除的行数。
如果一个表被其他表的外键引用，对此表的 TRUNCATE 操作会失败。

主键可以包含一个列或者多个列。

## 添加主键
ALTER TABLE user
ADD PRIMARY KEY(id);

## 删除主键
ALTER TABLE user
DROP PRIMARY KEY;

## 如何产生主键值
通常在业务系统中，我们不使用业务字段作为主键，虽然它们也是唯一的。我们一般使用单独的字段作为主键，这主要是出于以下两方面的原因：

保密业务数据
方便这些业务字段的修改
为了生成唯一的主键值，我们通常采用以下方法：

将主键字段设置为 AUTO_INCREMENT。

声明为 AUTO_INCREMENT 的字段会自动生成连续的整数值。

使用 UUID() 函数。

UUID() 函数产生一个长度为 36 个字符的字符串，并且永不重复。

UUID() 适合用在集群环境下。这样即使一个表被分区在多个服务器上，也不会产生相同的主键的记录

使用 UUID_SHORT() 函数。

UUID_SHORT() 函数返回一个 64 位无符号整数并全局唯一

## 主键 vs 唯一索引
主键和唯一索引都要求值是唯一的，但它们之间存在一些不同：

一个表中只能定义一个主键，但是能定义多个唯一索引。
主键中的值不能为 NULL，而索引中的值可以为 NULL

## 什么是外键
外键相对于主键而言，用来引用其他表。外键通过子表的一个或多个列对应到父表的主键或唯一键值，将子表的行和父表行建立起关联关系

这里定义了一个外键：

位于 CONSTRAINT 关键字之后的 fk_city_country 是外键的名字。它是可选的。

位于 FOREIGN KEY 关键字之后的是作为外键的列名。

位于 REFERENCES 关键字之后的是被引用的表和列。

ON DELETE 和 ON UPDATE 指定了删除或更新被引用的表中的数据时要采取的约束策略。你可以使用以下 3 个策略中的一个：

CASCADE：如果被引用的表中的一行被删除或更新，该表中匹配行的值会自动删除或更新。
SET NULL：如果被引用的表中的一行被删除或更新，该表中匹配行的值设置为 NULL。
RESTRICT: 如果被引用的表中的一行在该表中有匹配的行，试图删除或更新被引用的表中行时会引发 MySQL 错误。这是默认的策略。
通常，外键所属的表被称作子表，被外键引用的表被称作父表。

DROP FOREIGN KEY 后面指定外键名，也就是约束名。
DROP CONSTRAINT 后面指定约束名。它可以通过名字删除任何约束，并不仅仅是外键

## CASCADE 策略
如果外键的 ON DELETE 和 ON UPDATE 使用了 CASCADE 策略：

当父表的行被删除的时候，子表中匹配的行也会被删除。
当父表的行的键值更新的时候，子表中匹配的行的字段也会被更新

## RESTRICT 策略
MySQL 禁止删除父表中与子表匹配的行。
MySQL 禁止删除父表中与子表匹配的行的键的值

## SET NULL 策略
当父表的行被删除的时候，子表中匹配的行的列的值被设置为 NULL。
当父表的行的键值被更新的时候，子表中匹配的行的列的值被设置为 NULL

## 自引用外键
有时，子表和父表可能是同一个表。这种表中的外键被称为自引用外键。

通常，自引用外键定义在表示树形数据结构的表中。比如一个代表分类的表

## 启用或禁用外键约束
要禁用外键约束
SET foreign_key_checks = 0;

要启用外键约束
SET foreign_key_checks = 1;

*禁用外键约束在批量导入数据的时候很有用*

## 确定列是否存在
在向表中添加一个列之前，您可以需要首先确定此表中是否存在同名的列。

要查看一个表中的所有列的信息，您可以使用 DESC 或者 SHOW COLUMNS 两个语句中的一个。这两个语句都可以显示一个表中的所有的列，但是 SHOW COLUMNS 语句更灵活和方便，因为它可以根据您的要求过滤结果集。

*MySQL 为非空的 VARCHAR 列使用空字符串作为默认值*

另外，删除列还可能带来一些隐藏的问题：

如果要删除的列被外键引用，您需要同步删除外键后才能进行。这可能会破坏数据的完整性。
删除列后，您需要同步修改应用程序中依赖此列的代码。这包括独立的应用程序和触发器、视图、存储过程和函数中的引用。
对于一个大表来说，删除列是一个很耗时的过程。
重要：删除之前请一定要备份表和表中的数据

## MySQL AUTO_INCREMENT 自增列

在 MySQL 中，如果需要一个列的值为一个有序的整数序列，请使用自增列。

自增列是 MySQL 中的一个特殊的列，该列的值可由 MySQL 服务器自动生成，并且是一个按升序增长的正整数序列。自增列能够被用来为表的新行产生唯一的标识

*当修改了表的 AUTO_INCREMENT 值之后， INFORMATION_SCHEMA.TABLES 表中的 AUTO_INCREMENT 列并不会立刻更新。你可以使用 SHOW CREATE TABLE 语句查看。*

一个表中只能有一个自增列。
自增列的数据类型只能使用整数和浮点数。
自增列的初始值是 1。你可以在创建表的时候设置自增列的初始值，也可以修改自增列的值。
删除一些行后，删除的自增列的值不能重用。
你可以使用 SHOW CREATE TABLE 语句查看自增列的值。

## 什么是生成列
在 MySQL 中，生成列（GENERATED COLUMN）是一个特殊的列，它的值会根据列定义中的表达式自动计算得出。并且，你不能直接写入或更新生成列的值。

生成列有 2 种类型：

虚拟生成列：列值不会被存储下来。当读取该列时，MySQL 自动计算该列的值。
存储生成列：当插入或修改数据时，MySQL 自动计算该列的值并存储在磁盘上

MySQL 生成列可以简化我们的工作，让你不用写这么复杂的 SELECT 语句。现在我们要通过以下语句添加一个生成列
ALTER TABLE order_item
ADD COLUMN total_amount DECIMAL
GENERATED ALWAYS AS (price * quantity) STORED;

生成列有两种类型： VIRTUAL 和 STORED。他们之间有些不同：

虚拟生成列不需要存储空间；存储生成列需要存储空间。
虚拟生成列的值在每次读操作的时候都会被重新计算；存储生成列的值在插入行或者修改行的时候被计算。
如果数据经常发生变动，请考虑使用虚拟生成列；如果数据在创建后不经常变动，请考虑使用存储生成列。

像上面的例子中，一个订单被创建后一般不会再改动，这里很适合使用存储生成列

## MySQL UNIQUE KEY 唯一键
主键列不能包含 NULL 值，而唯一键列可以包含 NULL 值。

在 MySQL 中，KEY 是 INDEX 的同义词。一个唯一键对应了一个唯一索引

不像主键，唯一键允许其中的列接受 NULL 值。但是，NULL 值会破坏唯一键约束。也就是唯一键对 NULL 值无效。

*NOT NULL 也是一种特殊的约束*

假设在一个银行系统中有这样的逻辑：

当用户 A 从自己的银行账户取出 500 元时，用户 A 的余额为 原余额 减去 500。当另一个用户 B 给用户转入 500 元时，用户 A 的余额为 原余额 加上 500。

如果这两个操作同时发生，则可能导致用户 A 的余额是错误的。

MySQL 的锁就是为了解决这种并发问题的。MySQL 支持三种类型的锁：表级锁、行级锁和页面所。

MySQL 允许您在会话中显式地获取表锁，以防止其他会话在您需要独占访问表的期间修改表。

锁的操作是在当前会话中进行的。一个会话只能为自己获取锁，并只能释放自己的锁。

MySQL 提供了 LOCK TABLES 和 UNLOCK TABLES 语句用于显式地的获取表锁和释放表锁

## 锁类型
表锁支持 READ 和 WRITE 两种类型的锁。 READ 锁用于共享读取表， WRITE 锁用于排斥的读写表，他们的特点如下：

READ 锁
持有表锁的会话只能读取表，但不能写入表。

多个会话可以同时获取一个表的 READ 锁。

其他会话无需显式获取 READ 锁即可读取该表，但是不能写入表。其他会话的写操作会一直等待知道读锁被释放。

WRITE 锁
持有锁的会话可以读写表。

只有持有锁的会话才能访问该表。在释放锁之前，没有其他会话可以访问它。

持有 WRITE 锁时，其他会话对表的锁请求会阻塞。

如果您没有显式地的释放表锁，当会话结束后，无论是 READ 锁还是 WRITE 锁，都会被 MySQL 释放掉。

## 设置服务器字符集和排序规则
在配置文件中设置 MySQL 服务器的字符集和排序规则
这是推荐的设置方式，它是永久的。在修改配置文件后，请记得重启 MySQL 服务器。

启动 MySQL 服务器时指定字符集和排序规则

在命令行修改字符集和排序规则

## 要查看数据库的字符集和排序规则
要查看当前数据库的字符集和排序规则，请使用如下语句：
SELECT @@character_set_database, @@collation_database;

## 要查看指定数据库的字符集和排序规则
SHOW CREATE DATABASE testdb;

MySQL 提供了各种字符集以有效地存储各种字符。您可以为服务器、数据库、表、和列设置不同的字符级和排序规则。

如果您需要在不同的字符集之间转换字符串，请使用 MySQL 提供的两个函数： CONVERT 和 CAST

一个 ENUM 是一个字符串的列表，它定义了一个列中允许的值，列的值只能是创建列时定义的允许值列表中的的一个

ENUM ('v1', 'v2', ..., 'vn')

现在，我们已经创建好了 orders 表，其中 state 列为 ENUM 数据类型，并且它将只接受四个值: Unpaid, Paid, Shipped 和 Completed。同时，按照列定义时的顺序，Unpaid, Paid, Shipped 和 Completed 的索引分别为 1, 2, 3, 4

## MySQL 创建索引
索引是一种数据结构，例如 B-Tree，它提高了从表中检索数据行的速度，但需要额外的写入和存储来维护它。

查询优化器可以使用索引来快速定位数据，而不必针对给定查询扫描表中的每一行。

当您使用主键 或唯一键创建表时，MySQL 会自动创建一个名为 PRIMARY 的索引。 该索引称为聚集索引。

PRIMARY 索引是特殊的，因为索引本身与数据一起存储在同一个表中。聚集索引强制执行表中行的顺序。

PRIMARY 索引以外的其他索引称为二级索引或非聚集索引。

*如果您不指定索引类型，MySQL 将创建 B-Tree 索引。下面显示了基于表的存储引擎允许的索引类型*

让我们使用以下 CREATE INDEX 语句为该列 first_name 创建索引 
CREATE INDEX first_name ON actor(first_name);

## MySQL 删除主键索引
DROP INDEX `PRIMARY` ON t;

**MySQL 唯一索引是一种特殊的索引，它不但可以加快从表中检索数据的速度，还能防止在指定的一个或多个列中出现重复值。**


## MySQL 索引提示：USE INDEX
MySQL 查询优化器是 MySQL 数据库服务器的一个组件，它为 SQL 语句制定最佳执行计划。 MySQL 优化器通常根据索引基数进行决策。 有时候，虽然你创建了索引，但是你的 SQL 语句却不一定使用索引。 这是因为 MySQL 查询优化器的做出了它认为的更优的选择。

MySQL 允许您使用 USE INDEX 语句建议查询优化器去使用指定的命名索引。

但是， MySQL 查询优化器依然有可能不适用您建议的索引。 如果您想 MySQL 必须使用您指定的索引，请使用 FORCE INDEX 子句。

在 EXPLAIN 显示查询优化器使用错误索引的情况下， USE INDEX 很有用

从输出可以发现， MySQL 查询优化器选择使用 idx_last_name 索引。

如果您认为使用 idx_last_name_first_name 更好，则使用 USE INDEX 指定它

USE INDEX 告诉 MySQL 用列表中的其中一个索引去做本次查询，但是 MySQL 不一定会用。
FORCE INDEX 强制 MySQL 使用一个特定的索引。

有时候，虽然你创建了索引，但是你的 SQL 语句却不一定使用索引。 这是因为 MySQL 查询优化器的做出了它认为的更优的选择。

MySQL 查询优化器是 MySQL 数据库服务器的一个组件，它为 SQL 语句制定最佳执行计划。

但是，您可以是使用 FORCE INDEX 子句告诉 MySQL 查询优化器必须使用指定的索引。

要查看该语句的执行计划，请使用 EXPLAIN 语句：

EXPLAIN
SELECT *
FROM film
WHERE language_id = 1;

**当您定义多列索引时，您应该始终考虑业务上下文以确定哪些列经常用于查找，并在定义索引时将这些列放在列列表的开头**

## MySQL 聚集索引
聚集索引是一种特殊的索引，此索引中的键值的顺序决定了表中相应行的物理顺序。作为类比，聚集索引类似于一个词典，词典中的目录相当于聚集索引，目录和词语都是按照字母顺序排序的。

由于表中的数据只能按照一种顺序进行存储，因此一个表中最多只能有一个聚集索引

## MySQL 索引基数
一个索引的基数是指这个索引的列中的唯一值的数量。它是根据统计信息生成的一个估计值，不一定是准确的。

索引的基数是 MySQL 查询优化器决定是否使用索引的一个重要依据。索引基数越高，使用索引越有效。

如果索引的基数很低，全表扫描可能比使用索引更有效。

## MySQL 隐藏索引
MySQL 8 引入了隐藏索引（invisible index）。隐藏索引是实际存在的，但是对 MySQL 查询优化器不可见的索引。即使使用 FORCE INDEX，优化器也不会使用隐藏索引。

在删除一个索引前，您可以先将索引隐藏。如果这不影响性能，您再去真正的删除索引。

隐藏索引对 MySQL 查询优化器是不可见的，但是它是真实存在的，并且对写入操作保持最新

MySQL 允许您使用 VISIBLE 和 INVISIBLE 标识索引是否可见

## MySQL 隐藏索引开关
MySQL 查询优化器默认不使用隐藏索引，但是您可以通过系统变量 optimizer_switch 中的 use_invisible_indexes 修改这一行为

## MySQL 字符串前缀索引
在 MySQL 中，您可以为字符串列的指定长度的前缀创建前缀索引。

相比于为整个字符串列创建索引，前缀索引能减少磁盘的使用量，并提高索引的写入速度

## MySQL 索引顺序
在 MySQL 中，您可以在创建索引的时候指定索引的顺序。默认情况下，索引按照升序存储。

## Linux 启动/停止 MySQL
启动 MySQL 服务器
sudo systemd start mysqld

停止 MySQL 服务器
sudo service stop mysqld

重启 MySQL 服务器
sudo service restart mysqld

*在一些 Linux 发行版中，请使用 mysql 替代上面命令中的 mysqld。*

创建一个名为 sqliz 的新用户
CREATE user 'sqliz'@'%' IDENTIFIED by 'SqLiZ9879123!';

使用以下 DROP USER 语句删除用户 sqliz@localhost：
DROP USER sqliz@localhost;

## 杀掉已删除用户的会话
如果删除的用户在删除之前已经登录了一个会话，删除后并不会影响此会话，直到会话结束。这也会会带来危险。

你可以使用以下 SHOW PROCESSLIST 语句查看会话列表，并使用 KILL 语句结束已删除的用户的会话。

如您所见，用户帐户 sqliz@localhost 会话的 ID 是 26 。

您可以使用使用 KILL 语句终止会话 26
KILL 26;

您不能使用一个已有的用户账户作为新的用户账户，否则您将收到错误消息。

RENAME USER 将旧用户的所有权限转移给新用户。但是，它不会删除或使依赖于旧用户的数据库对象无效。

选择 mysql 数据库：
USE mysql;

更新密码
UPDATE user
SET password = PASSWORD('Db123654')
WHERE user = 'dbadmin' AND
      host = 'localhost';

刷新权限
FLUSH PRIVILEGES;

请注意，从 MySQL 5.7.6 开始，用户表使用列 authentication_string 来存储密码。并且，它删除了 password 列。

因此，如果您使用 MySQL 5.7.6+，则必须修改 UPDATE 语句中的 authentication_string 列
UPDATE user
SET authentication_string = PASSWORD('Db123654')
WHERE user = 'dbadmin' AND
      host = 'localhost';

*通过使用该 SET PASSWORD 语句，您无需执行该 FLUSH PRIVILEGES 语句即可从授权表重新加载权限*
以下语句使用 SET PASSWORD 语句更改用户帐户 dbadmin 的密码
SET PASSWORD FOR 'dbadmin'@'localhost' = PASSWORD('Db123654');

请注意，从 5.7.6 版开始，您不需要在 SET PASSWORD 语句中使用 PASSWORD()，而是直接使用明文密码。
SET PASSWORD FOR 'dbadmin'@'localhost' = 'Db123654';

第三种更改用户帐户密码的方法是使用 ALTER USER 带有 IDENTIFIED BY 子句的语句
ALTER USER dbadmin@localhost IDENTIFIED BY 'Db123654';

## 如何在 MySQL 中锁定用户帐户

某些特定的场景下，您可能想要锁定一个用户账户，比如：

创建一个锁定的用户，等授权完成后再解锁
此用户账户已经不被使用
此用户账户已经被泄露
此用户只是临时使用，使用完成后将用户锁定
要锁定一个已经存在的用户，请使用 ALTER USER .. ACCOUNT LOCK 语句。

要直接创建一个锁定的用户，请使用 CREATE USER .. ACCOUNT LOCK 语句。


## 查询用户的锁定状态
SELECT user, host, account_locked
FROM mysql.user;

## 在 MySQL 中使用 GRANT 语句给用户授权
作为一个数据库管理员或者维护人员，为了数据库的安全性，您需要更精确的权限控制。您可以给不同的用户赋予不同的权限。

当您创建了一个新用户之后，这个新的用户可以登录 MySQL 数据库服务器，但是他可能没有任何权限。只有在赋予他数据库和相关表的权限之后，他才可以进行选择数据库和查询等操作。

在 MySQL 中， GRANT 语句用于给用户赋予权限。
分配全局权限
GRANT ALL ON *.* TO sqliz@localhost;
这里将全部数据库全部对象的全部权限分配给了用户 sqliz@localhost

分配数据库全部对象的全部权限
GRANT ALL ON sqliz.* TO sqliz@localhost;
这里将 sqliz 数据库全部对象的全部权限分配给了用户 sqliz@localhost

分配数据库中某个表的的查询和插入权限
GRANT SELECT, INSERT ON sqliz.test_table TO sqliz@localhost;
这里将 sqliz 数据库中的 test_table 表的 SELECT 和 INSERT 权限分配给了用户 sqliz@localhost

## MySQL REVOKE 语句介绍
MySQL REVOKE 语句用于撤销用户帐户的一项或多项权限。

MySQL REVOKE 语句有几种形式。

## 撤销代理
要撤销代理用户，请使用以下 REVOKE PROXY 命令

代理用户是 MySQL 中可以模拟另一个用户的有效用户，因此，代理用户拥有它模拟的用户的所有权限。

在撤销用户的权限之前，使用以下 SHOW GRANTS 语句显示用户帐户的权限是一个好习惯

## MySQL REVOKE 生效时机
REVOKE 语句的生效时机取决于权限级别：

全局: 当用户帐户在后续会话中连接到 MySQL 服务器时，更改生效。更改不会应用于所有当前连接的用户。

数据库级别: 更改在下 USE 一条语句后生效。

表和列级别: 更改对所有后续查询生效。

在 MySQL 中，您可以使用 REVOKE 语句撤销授予用户的一个或者多个权限。

## 显示授予当前用户的权限
SHOW GRANTS;

*GRANT USAGE 是没有权限的代名词。默认情况下，当新用户创建时，它没有权限。*

在 MySQL 中，您可以使用 SHOW GRANTS 语句显示授予用户或角色的权限。

## 在 MySQL 中使用角色来简化权限管理
## MySQL 角色语法
如果要将同一组权限授予多个用户，请执行以下步骤：

首先，创建一个新角色。
其次，为角色授予权限。
第三，将角色授予用户。

角色名称类似于用户帐户，由两部分组成：名称和主机。如果省略主机部分，则默认为 %，表示任何主机。

如果需要在一个语句中创建多个角色，请使用逗号分隔不同的角色名。

## 设置活跃角色
用户帐户可以通过指定哪个授予的角色处于活动状态来修改当前用户在当前会话中的有效权限。

以下语句将活动角色设置为 NONE，表示没有活动角色
SET ROLE NONE;

要将活动角色设置为所有授予的角色，请使用
SET ROLE ALL;

要将活动角色设置为 SET DEFAULT ROLE 语句设置的默认角色，请使用
SET ROLE DEFAULT;

SHOW SCHEMAS 是 SHOW DATABASES 的同义词，他们具有相同的返回结果。

如果运行此命令的用户不是超级用户，则只返回用户具有权限的数据库列表。

您还可以使用 LIKE 对结果进行过滤

## MySQL 中的几个维护数据库表的语句
定期的维护数据表是一个很好的习惯。对提高数据库的性能很有帮助。

MySQL 提供了几个维护数据库表的语句：

ANALYZE TABLE: 分析表
在一个表中进行了大量数据插入，更新或者删除操作后，键分布可能是不准确的。如果键分布不准确，查询优化器可能会选择错误的查询执行计划，这可能会导致严重的性能问题。

如果你感觉实际执行计划并不是预期的执行计划，执行一次分析表可能会解决问题

OPTIMIZE TABLE: 优化表
典型的，在一个表中进行了大量数据更新或者删除操作后，表的物理存储可能变得碎片化。最总导致数据库服务器的性能下降

CHECK TABLE: 检查表
数据库服务器可能发生一些错误，例如服务器意外关闭、向硬盘写入数据时出错等。这些情况可能导致数据库运行不正确，最坏的情况可能是崩溃。

MySQL 允许您使用 CHECK TABLE 语句检查数据库表的完整性

REPAIR TABLE: 修复表
REPAIR TABLE 语句允许您修复数据库表中发生的一些错误。MySQL 不保证 REPAIR TABLE 语句可以修复表可能存在的所有错误

## 使用 mysqldump 工具备份数据库
mysqldump 是一个用于备份 MySQL 数据库的工具，它能将 MySQL 数据库导出为一个 sql 文件。

作为一个数据库管理员或者运维人员，定期备份线上的 MySQL 数据库是一个很有必要的工作。它可能帮你在数据库遭到损坏的时候保留数据或者恢复备份。

MySQL 提供了 mysqldump 工具用于从 MySQL 数据库服务器中导出数据库结构和数据

**mysqldump 是一个用于备份 MySQL 数据库的工具。它提供了很多选项以应对不同的备份需求**

## 使用 MySQL SOURCE 命令恢复数据库

## 使用 mysql 命令恢复

在 MySQL 中， SOURCE 命令可以帮您将数据库备份文件恢复到数据库中。除此之外，您还可以直接使用 mysql 命令恢复数据库

## 在 MySQL 中使用 SHOW PROCESSLIST 语句显示连接列表
MySQL 提供了 SHOW PROCESSLIST 命令用来返回当前数据库服务器的所有的连接的信息，包括连接的 ID，用户，主机，数据库，时间和状态等。

MySQL 将当前服务器的所有的连接信息保存在 information_schema.processlist 表中，您还可以从此表查询所有的连接的信息。

实际上， SHOW PROCESSLIST 命令只是查询 information_schema.processlist 表的简写形式。

有时，您可能会收到 MySQL 服务器返回的“连接过多”错误。要找出原因，您可以使用 SHOW PROCESSLIST 命令获取当前所有的连接，并使用 KILL 语句终止空闲线程

## MySQL 创建视图
MySQL 是一种常用的关系型数据库管理系统，提供了 CREATE VIEW 语法，用于创建视图（View）。视图是一种虚拟的表，实际上并不存储数据，而是从一个或多个表中派生出来的查询结果集，具有与表相似的结构。通过创建视图，可以将复杂的查询操作封装成一个简单的视图，方便用户进行查询和数据访问

**CREATE VIEW 是 MySQL 中用于创建视图的语法，通过创建视图，可以将复杂的查询操作封装成一个简单的视图，方便用户进行查询和数据访问。在使用 CREATE VIEW 时，需要指定视图的名称、包含的列名、基表和查询条件等。视图可以在数据权限管理、应用程序开发等场景中起到很大的作用，提高数据库的灵活性和安全性。**

可以使用 SHOW 命令来列出数据库中的所有视图
SHOW FULL TABLES IN database_name WHERE TABLE_TYPE LIKE 'VIEW';

SHOW FULL TABLES IN mydb WHERE TABLE_TYPE LIKE 'VIEW';

## MySQL 可更新视图
WITH CHECK OPTION 是 MySQL 中 CREATE VIEW 的一个有用的子句，它允许在创建视图时限制对视图的插入和更新操作。通过合理使用 WITH CHECK OPTION，可以确保只有符合特定条件的数据才能被插入或更新到视图中，从而保护数据库中的数据完整性。在设计数据库时，可以考虑使用 WITH CHECK OPTION 来实现细粒度的数据访问权限控制，提高数据库的安全性和可靠性

## MySQL 触发器
MySQL 触发器是一种数据库对象，它可以在特定的数据库表上自动执行一系列的操作，例如插入、更新或删除数据，当特定的事件（例如数据的插入、更新或删除）发生时触发。MySQL 触发器是一种强大的工具，可以用于实现数据库的自动化行为，例如数据验证、数据关联、审计日志等。

MySQL 触发器通常由 SQL 语句组成，定义了触发器要执行的操作。MySQL 支持三种类型的触发器：

BEFORE 触发器：在执行实际的数据操作之前触发，例如在插入、更新或删除数据之前执行某些操作，例如数据验证、数据转换等。

AFTER 触发器：在执行实际的数据操作之后触发，例如在插入、更新或删除数据之后执行某些操作，例如生成审计日志、更新相关数据等。

INSTEAD OF 触发器：在执行实际的数据操作之前触发，并可以在触发器中替代原始的数据操作，例如在插入、更新或删除数据之前执行自定义的数据操作，而不是执行原始的数据操作。

MySQL 触发器可以在创建表时定义，也可以在表创建后通过 ALTER TABLE 语句来添加、修改或删除。触发器可以基于特定的表和事件（插入、更新、删除）来触发，并可以包含条件、循环、异常处理等复杂逻辑。

## MySQL CREATE TRIGGER 创建触发器
数据验证和约束：可以通过触发器在数据插入、更新或删除前后进行验证和约束，确保数据库中的数据满足特定的业务规则和限制条件。
数据补全和处理：可以通过触发器在数据插入或更新前后进行自动补全和处理，例如自动生成序列号、计算字段值等。
数据审计和日志记录：可以通过触发器在数据插入、更新或删除时记录审计日志，用于追踪数据变更历史和安全审计。
数据复制和同步：可以通过触发器在数据插入、更新或删除时自动将数据复制到其他表或数据库，实现数据的同步和复制

MySQL 的触发器是一种强大的数据库特性，可以在数据库表上定义一组操作，自动在特定事件发生时触发执行。通过 CREATE TRIGGER 语法，我们可以创建自定义的触发器，用于实现数据验证、数据处理、数据审计等业务需求。但需要注意，滥用触发器可能导致性能问题和复杂性增加，因此在使用触发器时应慎重考虑，并遵循最佳实践

BEFORE INSERT 触发器的语法如下：
CREATE TRIGGER trigger_name
BEFORE INSERT
ON table_name FOR EACH ROW
BEGIN
    -- 触发器操作
END;

其中，trigger_name 是触发器的名称，可以自定义；table_name 是触发器所属的表名；FOR EACH ROW 表示对表中的每一行数据都执行触发器操作；BEGIN 和 END 之间是触发器操作的具体内容。

BEFORE INSERT 触发器通常用于在插入数据之前自动执行一些辅助性的操作，如数据验证、数据补全、数据处理等。以下是一些常见的使用场景：

数据验证：在插入数据之前，对数据进行验证，例如检查数据的完整性、合法性、唯一性等。
数据补全：在插入数据之前，对缺失的数据进行补全，例如设置默认值、自动生成字段值等。
数据处理：在插入数据之前，对数据进行处理，例如将数据进行格式化、转换、加密等。

