





[TOC]

# 简介

MySQL 是一个关系型数据库管理系统，由瑞典 MySQL AB 公司开发，目前属于 Oracle 公司。MySQL 是一种关联数据库管理系统，关联数据库将数据保存在不同的表中，而不是将所有数据放在一个大仓库内，这样就增加了速度并提高了灵活性。

MySQL 是开源的，所以你不需要支付额外的费用。

MySQL 支持大型的数据库。可以处理拥有上千万条记录的大型数据库。

MySQL 使用标准的 SQL 数据语言形式。优化的SQL查询算法，有效地提高查询速度

MySQL 可以运行于多个系统上，并且支持多种语言。这些操作系统包括Linux、Windows、AIX、FreeBSD、HP-UX、MacOS、NovellNetware、OpenBSD、OS/2 Wrap、Solaris等。这些编程语言包括 C、C++、Python、Java、Perl、PHP、Eiffel、Ruby 和 Tcl 等。

支持多线程，充分利用CPU资源

提供多语言支持，常见的编码如GB2312、BIG5、UTF8

提供TCP/IP、ODBC、JDBC等多种数据库连接途径

MySQL 对PHP有很好的支持，PHP 是目前最流行的 Web 开发语言。

MySQL 支持大型数据库，支持 5000 万条记录的数据仓库，32 位系统表文件最大可支持 4GB，64 位系统支持最大的表文件为8TB。

提供用于管理、检查、优化数据库操作的管理工具

支持多种存储引擎，常用InnoDB和MyISAM引擎，InnoDB支持事务处理与外键和行级锁

MySQL软件采用了双授权政策，它分为社区版和商业版，由于其体积小、速度快、总体拥有成本低，尤其是开放源码这一特点，一般中小型网站的开发都选择MySQL作为网站数据库

MySQL 是可以定制的，采用了 GPL 协议，你可以修改源码来开发自己的 MySQL 系统。

在线DDL更改功能

复制全局事务标识

复制无崩溃从机

复制多线程从机

行级锁：多个任务修改同一行的时候，会先向这一行上锁，完成之后解锁，类似的还有表级锁。】



数据库文件存放在/var/lib/mysql文件夹下，只有root才能进入，管理文件内容使用MySQL软件来操作，使用Show databases;展示出来的数据库和上面文件夹的内容对应着





## 概念





## 历史



## Ubuntu安装和配置

**服务器安装**

sudo apt-get install mysql-server 一键安装

sudo service mysql start 启动MySQL

ps aux|grep mysql 查看进程是否有mysql服务

sudo service mysql stop 停止MySQL

sudo service mysql restart 重启MySQL

**客户端安装**

sudo apt-get install mysql-client

Mysql --help

Mysql -uroot -pmysql   参数和值之间可以没有空格



**配置文件**

/etc/mysql/mysql.cnf

Bind-address 默认是127.0.0.1服务器绑定

port 默认是3306，端口

datadir 默认是/var/lib/mysql 数据库目录

general_log_file 默认是/var/log/mysql/mysql.log 普通日志目录

log_error 默认是/var/log/mysql/error.log 表示错误日志



```sh
# 默认的库有
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
```

## Mac安装和配置

```bash
在~目录下的./.bash_profile文件末尾添加两行
export PATH=$PATH:/usr/local/mysql/bin
export PATH=$PATH:/usr/local/mysql/support-files
输入"source ~/.bash_profile"让配置文件生效
$ echo $PATH

sudo mysql.server stop # 停止MySQL服务
sudo mysql.server restart # 重启MySQL服务
sudo mysql.server status # 查看MySQL服务状态

```

[Mac安装MySQL](https://www.cnblogs.com/nickchen121/p/11145123.html)

## 开发环境

可以使用Navicat软件操作数据库



## 命令行

```
$ mysql --help
mysql  Ver 14.14 Distrib 5.5.60, for debian-linux-gnu (armv8l) using readline 6.3
Copyright (c) 2000, 2018, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Usage: mysql [OPTIONS] [database]
  -?, --help          Display this help and exit.
  -I, --help          Synonym for -?
  --auto-rehash       Enable automatic rehashing. One doesn't need to use
                      'rehash' to get table and field completion, but startup
                      and reconnecting may take a longer time. Disable with
                      --disable-auto-rehash.
                      (Defaults to on; use --skip-auto-rehash to disable.)
  -A, --no-auto-rehash 
                      No automatic rehashing. One has to use 'rehash' to get
                      table and field completion. This gives a quicker start of
                      mysql and disables rehashing on reconnect.
  --auto-vertical-output 
                      Automatically switch to vertical output mode if the
                      result is wider than the terminal width.
  -B, --batch         Don't use history file. Disable interactive behavior.
                      (Enables --silent.)
  -b, --binary-as-hex Print binary data as hex
  --character-sets-dir=name 
                      Directory for character set files.
  --column-type-info  Display column type information.
  -c, --comments      Preserve comments. Send comments to the server. The
                      default is --skip-comments (discard comments), enable
                      with --comments.
  -C, --compress      Use compression in server/client protocol.
  -#, --debug[=#]     This is a non-debug version. Catch this and exit.
  --debug-check       Check memory and open file usage at exit.
  -T, --debug-info    Print some debug info at exit.
  -D, --database=name Database to use.
  --default-character-set=name 
                      Set the default character set.
  --delimiter=name    Delimiter to be used.
  --enable-cleartext-plugin 
                      Enable/disable the clear text authentication plugin.
  -e, --execute=name  Execute command and quit. (Disables --force and history
                      file.)
  -E, --vertical      Print the output of a query (rows) vertically.
  -f, --force         Continue even if we get an SQL error.
  -G, --named-commands 
                      Enable named commands. Named commands mean this program's
                      internal commands; see mysql> help . When enabled, the
                      named commands can be used from any line of the query,
                      otherwise only from the first line, before an enter.
                      Disable with --disable-named-commands. This option is
                      disabled by default.
  -i, --ignore-spaces Ignore space after function names.
  --init-command=name SQL Command to execute when connecting to MySQL server.
                      Will automatically be re-executed when reconnecting.
  --local-infile      Enable/disable LOAD DATA LOCAL INFILE.
  -b, --no-beep       Turn off beep on error.
  -h, --host=name     Connect to host.
  -H, --html          Produce HTML output.
  -X, --xml           Produce XML output.
  --line-numbers      Write line numbers for errors.
                      (Defaults to on; use --skip-line-numbers to disable.)
  -L, --skip-line-numbers 
                      Don't write line number for errors.
  -n, --unbuffered    Flush buffer after each query.
  --column-names      Write column names in results.
                      (Defaults to on; use --skip-column-names to disable.)
  -N, --skip-column-names 
                      Don't write column names in results.
  --sigint-ignore     Ignore SIGINT (CTRL-C).
  -o, --one-database  Ignore statements except those that occur while the
                      default database is the one named at the command line.
  --pager[=name]      Pager to use to display results. If you don't supply an
                      option, the default pager is taken from your ENV variable
                      PAGER. Valid pagers are less, more, cat [> filename],
                      etc. See interactive help (\h) also. This option does not
                      work in batch mode. Disable with --disable-pager. This
                      option is disabled by default.
  -p, --password[=name] 
                      Password to use when connecting to server. If password is
                      not given it's asked from the tty.
  -P, --port=#        Port number to use for connection or 0 for default to, in
                      order of preference, my.cnf, $MYSQL_TCP_PORT,
                      /etc/services, built-in default (3306).
  --prompt=name       Set the mysql prompt to this value.
  --protocol=name     The protocol to use for connection (tcp, socket, pipe,
                      memory).
  -q, --quick         Don't cache result, print it row by row. This may slow
                      down the server if the output is suspended. Doesn't use
                      history file.
  -r, --raw           Write fields without conversion. Used with --batch.
  --reconnect         Reconnect if the connection is lost. Disable with
                      --disable-reconnect. This option is enabled by default.
                      (Defaults to on; use --skip-reconnect to disable.)
  -s, --silent        Be more silent. Print results with a tab as separator,
                      each row on new line.
  -S, --socket=name   The socket file to use for connection.
  --ssl               Enable SSL for connection (automatically enabled with
                      other flags).
  --ssl-ca=name       CA file in PEM format (check OpenSSL docs, implies
                      --ssl).
  --ssl-capath=name   CA directory (check OpenSSL docs, implies --ssl).
  --ssl-cert=name     X509 cert in PEM format (implies --ssl).
  --ssl-cipher=name   SSL cipher to use (implies --ssl).
  --ssl-key=name      X509 key in PEM format (implies --ssl).
  --ssl-verify-server-cert 
                      Verify server's "Common Name" in its cert against
                      hostname used when connecting. This option is disabled by
                      default.
  --ssl-mode=name     SSL connection mode.
  -t, --table         Output in table format.
  --tee=name          Append everything into outfile. See interactive help (\h)
                      also. Does not work in batch mode. Disable with
                      --disable-tee. This option is disabled by default.
  -u, --user=name     User for login if not current user.
  -U, --safe-updates  Only allow UPDATE and DELETE that uses keys.
  -U, --i-am-a-dummy  Synonym for option --safe-updates, -U.
  -v, --verbose       Write more. (-v -v -v gives the table output format).
  -V, --version       Output version information and exit.
  -w, --wait          Wait and retry if connection is down.
  --connect-timeout=# Number of seconds before connection timeout.
  --max-allowed-packet=# 
                      The maximum packet length to send to or receive from
                      server.
  --net-buffer-length=# 
                      The buffer size for TCP/IP and socket communication.
  --select-limit=#    Automatic limit for SELECT when using --safe-updates.
  --max-join-size=#   Automatic limit for rows in a join when using
                      --safe-updates.
  --secure-auth       Refuse client connecting to server if it uses old
                      (pre-4.1.1) protocol.
  --server-arg=name   Send embedded server this as a parameter.
  --show-warnings     Show warnings after every statement.
  --plugin-dir=name   Directory for client-side plugins.
  --default-auth=name Default authentication client-side plugin to use.

Default options are read from the following files in the given order:
/etc/my.cnf /etc/mysql/my.cnf /usr/etc/my.cnf ~/.my.cnf 
The following groups are read: mysql client
The following options may be given as the first argument:
--print-defaults        Print the program argument list and exit.
--no-defaults           Don't read default options from any option file.
--defaults-file=#       Only read default options from the given file #.
--defaults-extra-file=# Read this file after the global files are read.

Variables (--variable-name=value)
and boolean options {FALSE|TRUE}  Value (after reading options)
--------------------------------- ----------------------------------------
auto-rehash                       TRUE
auto-vertical-output              FALSE
binary-as-hex                     FALSE
character-sets-dir                (No default value)
column-type-info                  FALSE
comments                          FALSE
compress                          FALSE
debug-check                       FALSE
debug-info                        FALSE
database                          (No default value)
default-character-set             auto
delimiter                         ;
enable-cleartext-plugin           FALSE
vertical                          FALSE
force                             FALSE
named-commands                    FALSE
ignore-spaces                     FALSE
init-command                      (No default value)
local-infile                      FALSE
no-beep                           FALSE
host                              (No default value)
html                              FALSE
xml                               FALSE
line-numbers                      TRUE
unbuffered                        FALSE
column-names                      TRUE
sigint-ignore                     FALSE
port                              3306
prompt                            mysql> 
quick                             FALSE
raw                               FALSE
reconnect                         TRUE
socket                            /var/run/mysqld/mysqld.sock
ssl                               FALSE
ssl-ca                            (No default value)
ssl-capath                        (No default value)
ssl-cert                          (No default value)
ssl-cipher                        (No default value)
ssl-key                           (No default value)
ssl-verify-server-cert            FALSE
table                             FALSE
user                              (No default value)
safe-updates                      FALSE
i-am-a-dummy                      FALSE
connect-timeout                   0
max-allowed-packet                16777216
net-buffer-length                 16384
select-limit                      1000
max-join-size                     1000000
secure-auth                       FALSE
show-warnings                     FALSE
plugin-dir                        (No default value)
default-auth                      (No default value)
```



# MySQL术语

人们通常用数据库这个术语来代表他们使用 的数据库软件。这是不正确的，它是引起混淆的根源。确切 地说，数据库软件应称为DBMS(数据库管理系统)。数据库 是通过DBMS创建和操纵的容器。数据库可以是保存在硬设备 上的文件，但也可以不是。在很大程度上说，数据库究竟是 文件还是别的什么东西并不重要，因为你并不直接访问数据 库;你使用的是DBMS，它替你访问数据库。 

**数据库管理系统**：(Database-Management System,DBMS)

**数据库database**：数据库是一些关联表的集合，数据库有数据表，数据表里才是数据

**数据表table**：表是数据的矩阵，看起来像一张完整的表格

**模式(schema)** ：关于数据库和表的布局及特性的信息。 

**字段**：一列，相同类型的数据

**记录**：一行，一组完整的数据用来描述一个事物的各个属性

**冗余**：存储两倍的数据，冗余降低了性能，但是提高了数据的安全性

**主键primary key**：主键是惟一的，主要用来查询数据

**外键**：用来关联两个表

**复合键**：将多个列作为一个索引键，一般用于复合索引

**索引**：使用索引可快速访问数据库表中的特定信息。索引是对数据库表中一列或多列的值进行排序的一种结构。类似于书籍的目录

**参照完整性**：参照的完整性要求关系中不允许引用不存在的实体。与实体完整性是关系模型必须满足的完整性约束条件，目的是保证数据的一致性

**表头**：每一列的名称

**值**：行的具体信息

**键**：键的值在当前列中具有唯一性

column 列

row 行

# MySQL的操作

事务：一组sql操作，要么都成功，要么都失败



关键字：必知必会附录E

不能使用关键字命名库名，表名，列名和其他数据库对象



**注释**

```sql
--这是单行注释
/*
**这是多行注释
*/
```



## 数据库操作

```bash
$ mysql -u root -p mima
```

```mysql
-- 退出sql
> quit
> exit
> Ctrl+d
```



**数据库操作**

```mysql
-- 数据库操作
SHOW DATABASES; -- 显示所有的数据库列表
CREATE DATABASE test; -- 创建数据库
CREATE DATABASE test charset=utf8; -- 指定字符集
USE test; -- 使用数据库
DROP DATABASE test; -- 删除数据库

如果想重命名一个数据库，最好的办法是重新建立一个新的数据库
显示当前数据库名使用函数 database();


mysql> SHOW CREATE DATABASE test; -- 查看创建数据库的语句
/*!40100 DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci */ /*!80016 DEFAULT ENCRYPTION='N' */
 -- 默认字符集设置utf8mb4  字段utf8mb40900aici
 -- 默认加密是'N'
```

**数据表操作**

```mysql
-- 数据表操作
SHOW TABLES test; -- 显示表

-- 创建表，指定字段(字段 类型 约束[,字段 类型 约束])
-- 两个字段，并且指定类型
-- 约束的内容
-- primary key -- 主键
-- not null -- 不为空
-- auto_increment -- 自动增长
-- default 0 -- 默认值
CREATE TABLE test(id int, name varchar(30));
CREATE TABLE tpid( -- 设置一个id主键
  id int unsigned primary key not null auto_increment,
  name varchar(30)
);
-- 例子
CREATE TABLE students(
  id int unsigned not null auto_increment primary key,
  name varchar(30),
  age tinyint unsigned default 0,
  high decimal(5,2),
  gender enum("男","女","中性","保密") default "保密",
  cls_id int unsigned
);

-- 查看表的结构
-- Field Type Null Key Default Extra
SHOW COLUMNS FROM tt;
或者 DESC tt;

ALTER TABLE students RENAME TO stu; -- 修改表名
DROP TABLE tt; -- 删除表

mysql> show create table students;
| Table    | Create Table                                                                                                                                                                                                                                                                                                                                                                                        
| students | CREATE TABLE `students` (
  `id` int unsigned NOT NULL AUTO_INCREMENT,
  `name` varchar(30) DEFAULT NULL,
  `age` tinyint unsigned DEFAULT '0',
  `high` decimal(5,2) DEFAULT NULL,
  `gender` enum('男','女','中性','保密') DEFAULT '保密',
  `cls_id` int unsigned DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=2 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci         
1 row in set (0.00 sec)
-- ENGINE默认引擎
-- AUTO_INCREMENT自动增长的值

```


```mysql
-- 修改已有的表结构
 -- 添加字段
ALTER TABLE students ADD birthday datetime;
 -- 重命名字段 change 原名 新名 类型及约束
ALTER TABLE students CHANGE birthday birth datetime not null;
ALTER TABLE students CHANGE birthday birth date default "2000-01-01";
 -- 修改字段 modify 字段名 类型及约束
ALTER TABLE students MODIFY birth date not null;
 -- 删除字段
ALTER TABLE students DROP birthday;
```

**数据行操作**

```mysql
-- 插入数据 students(id,name,age,high,gender,cls_id);
-- 这里省略字段名，值必须按照先后顺序依次全部填写
INSERT INTO students VALUES(0,"老王",18,175.00,"男",2);
 -- 主键可以插入0/null/default，都会自动增长
 -- gender枚举类型可以填下标1/2/3/4代替字符串
 
-- 插入数据指定字段，可以为null和有默认值的字段可以不填
INSERT INTO students 
  (id,name,age,high,gender,cls_id)
  VALUES
  (0,"老王",18,175.00,"男",2);
  
-- 多行数据插入，
INSERT INTO students VALUES(0,"老李",18,175.00,"男",2),(0,"老赵",18,175.00,"男",2);
INSERT INTO students (name, gender) VALUES("老李",1),("老赵",1);
```

```mysql
-- 更新数据
UPDATE students SET gender=1; -- 慎用，这个命令更改表中的所有数据
UPDATE students SET gender=2 WHERE name="老李";
UPDATE students SET gender=2 WHERE id=3; -- 一般选择唯一确定的值
UPDATE students SET gender=2,age=33 WHERE id=3;
```

```mysql
-- 删除数据
DELETE FROM students; -- 慎用，清空数据表
DELETE FROM students WHERE name="老王"; -- 条件删除
-- 在真实使用环境中，使用一个字段来表示数据是否作废，而不是真正的删除这些数据
ALTER TABLE students ADD is_delete bit default 0; -- 添加一个表示删除的字段
UPDATE students SET is_delete=1 WHERE id=6;
```



## 数据查询

```mysql
-- 查询数据
SELECT * FROM students; # 选择数据库并且
SELECT * FROM test.tt; # 显示库下的表的字段
```
```mysql
-- 指定字段查询，按照顺序查询
SELECT id,name,gender FROM students;
SELECT students.name,students.gender FROM students;

-- 字段别名
SELECT name as 姓名,gender as 性别 FROM students;

-- 表的别名
SELECT name, gender FROM students;
SELECT s.name, s.gender FROM students as s;
-- SELECT students.name FROM students as s;-- 错误

-- 消除重复行
SELECT DISTINCT gender FROM students; -- 性别重复的消除
```
```mysql
-- 条件查询，> < >= <= = !=
SELECT * FROM students WHERE id>6; -- 比较运算符>
SELECT name,age FROM students WHERE id>6; -- 显示的字段可以不同于查询的条件

-- 逻辑查询 and or not
SELECT name,age FROM students WHERE age>18 and age<28;
```

```mysql
-- 模糊查询，很少使用
-- %替换零个或多个
-- _替换1个
SELECT name FROM students WHERE name="小";
SELECT name FROM students WHERE name LIKE "小%"; -- 小字开头的值 "%小%"名字包含小字
SELECT name FROM students WHERE name LIKE "__";-- 两个字的名字
SELECT name FROM students WHERE name LIKE "___";-- 三个字的名字
SELECT name FROM students WHERE name LIKE "__%";-- 至少两个字的名字

-- 正则查询
-- . : 匹配任意单个字符
-- * ： 匹配0个或多个前一个得到的字符
-- [] : 匹配任意一个[]内的字符，[ab]*可匹配空串、a、b、或者由任意个a和b组成的字符串。
-- ^ : 匹配开头，如^s匹配以s或者S开头的字符串。
-- $ : 匹配结尾，如s$匹配以s结尾的字符串。
-- {n} : 匹配前一个字符反复n次。
SELECT name FROM students WHERE name RLIKE "^周.*";-- 周开头的值 "^周.*伦$"周开头伦结尾中间随意
```



```mysql
-- 范围查询
-- in(1,3,8)表示在一个非连续的范围内
SELECT name FROM students WHERE age IN(12,18,34);
-- not in(1,3,8)表示在一个不在 非连续的范围内
SELECT name FROM students WHERE age NOT IN(12,18,34);
                          WHERE age BETWEEN 18 AND 34;-- between and 表示在一个连续的范围内
                          WHERE age NOT BETWEEN 18 AND 34; -- 表示不在一个连续范围内
                          WHERE age NOT (BETWEEN 18 AND 34); -- 错误，这里不能加括号
                          WHERE NOT age BETWEEN 18 AND 34;-- 两截，NOT跟着范围查询
-- 空判断 is null,  is not null
SELECT name FROM students WHERE height IS NULL;-- 空值
SELECT name FROM students WHERE height IS NOT NULL;-- 不为空

```



```mysql
-- 数据排序，DESC降序，ASC升序
-- age从小到大排序
SELECT * FROM students ORDER BY age;
SELECT * FROM students ORDER BY age ASC/ DESC;
SELECT * FROM students WHERE gender=1 ORDER BY score;
-- order by支持多个字段排序
-- 先按照age排序，后按照id排序
SELECT * FROM students ORDER BY age ASC, id DESC;
SELECT * FROM students ORDER BY age ASC, height DESC;

```





```mysql
-- 聚合函数，一般会得出一个结论
-- count()总数
SELECT COUNT(*) FROM students WHERE gender=1;-- 查看男性有多少人
-- max()最大值
SELECT MAX(age) FROM students WHERE gender=2;-- 女性最高值
-- min()最小值
同max
-- sum()总和
SELECT SUM(age) FROM students;-- 年龄之和
-- avg()平均值,银行为了精确存储数据，可以先乘以100再存储，计算完成之后再还原小数点
SELECT AVG(age) FROM students;
SELECT SUM(age)/ COUNT(*) FROM students;-- 效果相同
-- round()
SELECT ROUND((SUM(age)/COUNT(*)),2) FROM students;-- 保留2位小数，四舍五入
```



```mysql
-- 分组，要和聚合函数一起用
SELECT gender,COUNT(*) FROM students GROUP BY gender;-- 各性别的人数
SELECT gender,AVG(age) FROM students GROUP BY gender;-- 各性别的平均年龄
-- group_concat()
SELECT gender,GROUP_CONCAT(name) FROM students GROUP BY gender;-- 各性别人的名字
SELECT gender,COUNT(*) FROM students WHERE gender=1 GROUP BY gender;-- 男性的人数
SELECT gender,GROUP_CONCAT(name) FROM students WHERE gender=1 GROUP BY gender;-- 男性的名字
SELECT gender,GROUP_CONCAT(name,"_",age," ",id) FROM students WHERE gender=1 GROUP BY gender;-- 男性的名字,年龄,id
-- having
SELECT gender,GROUP_CONCAT(name),avg(age) FROM students GROUP BY gender HAVING AVG(age)>30;-- 平均年龄超过30的性别和其中的人
SELECT gender,GROUP_CONCAT(name) FROM students GROUP BY gender HAVING COUNT(*)>2;-- 性别中人数多于2的信息



```

```mysql
-- 分页



```

```mysql

```

```mysql

```

```mysql

```

```mysql

```

```mysql

```

## 数据库函数

[数据库函数](https://www.runoob.com/mysql/mysql-functions.html)

[数据库函数](https://www.cnblogs.com/luxd/p/9916677.html)

[MySQL函数大全](https://www.cnblogs.com/xuedognqing/p/5080057.html)

**数学函数**

```mysql
select ABS(); -- 绝对值
```

**字符串函数**

```mysql

```

**日期时间函数**

```mysql
select NOW(); -- 显示当前时间

```
**条件判断函数**

```mysql

```

**系统信息函数**

```mysql
SELECT VERSION(); -- 显示版本信息
SELECT DATABASE(); -- 显示当前数据库名
SELECT USER(); -- 显示当前用户名
SELECT STATUS(); -- 显示服务器状态
SELECT VARIABLES(); -- 显示服务器配置变量
```

**加密函数**

```mysql

```

**格式化函数**

```mysql

```

**其他函数**

```mysql

```

# 数据库约束

在表中为了更加准确的存储数据，保证数据的正确有效，在创建表的时候，为表添加一些强制性的验证，包括数据字段的类型，约束

## 数据类型

原则：够用就行，尽量使用取值范围小的，而不用大的，这样可以更多的节省存储空间

[具体数据类型](https://www.cnblogs.com/-xlp/p/8617760.html)

[mysql数据类型](http://blog.csdn.net/anxpp/article/details/51284106)

[数据类型 runoob](https://www.runoob.com/mysql/mysql-data-types.html)

对于图片、音频、视频等文件，不存储在数据库中，而是上传到某个服务器上，然后把媒体路径存储在数据库中

**整数**

BIT 1位 八分之一字节 只能存0或1    BIT(8)8个比特

TINYINT   1字节  unsigned 255  signed -128-127

SMALLINT   2字节  unsigned 65536  signed -32768~32767

MEDIUMINT   3字节  unsigned 16777215  signed -8388608~8388607

INT/INTEGER   4字节  unsigned 4294967295  signed

BIGINT   8字节  unsigned 18446744073709551615

**小数**

FLOAT 4字节 

DOUBLE 8字节

DECIMAL表示浮点数，如decimal(5,2)表示共存5位数，小数占2位

**字符串**

CHAR表示固定长度的字符串，大小255，如char(3)，'ab'会补一个空格'ab '

VARCHAR可变长度的字符串，大小255，如varchar(3)，'ab'会存成'ab'

TEXT字符串表示存储大文本，大小65536，当字符大于4000时推荐使用



| CHAR       | 0-255字节           | 定长字符串                      |
| ---------- | ------------------- | ------------------------------- |
| VARCHAR    | 0-65535 字节        | 变长字符串                      |
| TINYBLOB   | 0-255字节           | 不超过 255 个字符的二进制字符串 |
| TINYTEXT   | 0-255字节           | 短文本字符串                    |
| BLOB       | 0-65 535字节        | 二进制形式的长文本数据          |
| TEXT       | 0-65 535字节        | 长文本数据                      |
| MEDIUMBLOB | 0-16 777 215字节    | 二进制形式的中等长度文本数据    |
| MEDIUMTEXT | 0-16 777 215字节    | 中等长度文本数据                |
| LONGBLOB   | 0-4 294 967 295字节 | 二进制形式的极大文本数据        |
| LONGTEXT   | 0-4 294 967 295字节 | 极大文本数据                    |



**日期时间**

DATE，4字节，如'2020-01-01'

TIME，3字节，如'12:29:59'

YEAR，1字节，如'2017'

DATETIME，8字节，如'2020-01-01 12:29:59'

TIMESTAMP，4字节，如'1970-01-01 00:00:01'UTC~'2038-01-19 03:14:07' UTC

**枚举类型**

enum把可能出现的结果列举出来，如性别，语言

索引值从1开始。1，2，3，4，5，6......

## 约束

主键 primary key：物理上存储的顺序

非空 not null：此字段不允许填写空值

唯一unique：此字段的值不允许重复

默认default：当不填写此值时会使用默认值，如果填写时以填写为准

外键foreign key：对关系字段进行约束，当为关系字段填写值时，会到关联的表中查询此值是否存在。外键约束虽然可以保证数据的有效性，在数据crud（增改删查）时，会降低数据库的性能，不推荐使用，建议一般在逻辑层进行控制







# 事务

一般来说，事务是必须满足4个条件（ACID）：：原子性（**A**tomicity，或称不可分割性）、一致性（**C**onsistency）、隔离性（**I**solation，又称独立性）、持久性（**D**urability）。

- 原子性：一个事务（transaction）中的所有操作，要么全部完成，要么全部不完成，不会结束在中间某个环节。事务在执行过程中发生错误，会被回滚（Rollback）到事务开始前的状态，就像这个事务从来没有执行过一样。
- 一致性：在事务开始之前和事务结束以后，数据库的完整性没有被破坏。这表示写入的资料必须完全符合所有的预设规则，这包含资料的精确度、串联性以及后续数据库可以自发性地完成预定的工作。
- 隔离性：数据库允许多个并发事务同时对其数据进行读写和修改的能力，隔离性可以防止多个事务并发执行时由于交叉执行而导致数据的不一致。事务隔离分为不同级别，包括读未提交（Read uncommitted）、读提交（read committed）、可重复读（repeatable read）和串行化（Serializable）。
- 持久性：事务处理结束后，对数据的修改就是永久的，即便系统故障也不会丢失。



# 导出数据

```mysql
$ mysqldump -u root -p test > dump.sql
```









# 单词



encryption 加密，加密术

extra 额外的，特别的，格外的

dump 转存数据，转储，转储数据，倾倒，倾销



# 链接

[runoob MySQL教程](https://www.runoob.com/mysql/mysql-tutorial.html)

[官方文档](https://dev.mysql.com/doc/)

[数据类型 官方文档](https://dev.mysql.com/doc/refman/5.7/en/string-types.html)

[MySQL8.0 文档](https://dev.mysql.com/doc/refman/8.0/en/)

# 参考资料

《MySQL必知必会》[英]Ben Forta著 人民邮电出版社 ISBN 978-7-115-19112-0

《数据库系统:面向应用的方法》《数据库系统基础》 





























