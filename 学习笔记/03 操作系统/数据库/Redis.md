# 简介

## 概述

Redis是一种NoSQL技术，它的性能十分优越，可以支持每秒几十万次的读写操作，性能远超数据库，并且还支持集群、分布式、主从同步等配置，原则上可以无限扩展，让更多的数据存储在内存中，更让人欣慰的是它还支持一定的事务能力，这保证了高并发的场景下数据的安全和一致性

**NoSQL技术**

这是一种基于内存的数据库，且提供一定的持久化功能。

Redis和MongoDB是当前使用最广泛的NoSQL

**Redis是远程的**

有客户端和服务端两个部分，可以部署在不同的两个机器上，可以使用自定义的协议进行传输和交互

通常说的Redis是指服务端，特殊情况才说Redis客户端

**Redis是基于内存的**

所有的数据和结构都存储在内存中，操作非常高速，性能远远优于硬盘MySQL，比较吃内存的软件

**Redis是非关系型数据库**

关系型数据库在存储之前必须定义好数据字典，后续的存储数据按照数据字典进行存储，而Redis不需要定义数据字典



**应用场景**

当做缓存

当系统接口速度慢的时候，缓存某些数据，再次使用数据的时候，就不需要再使用MySQL的操作了，直接到Redis缓存中取数据，这是提升系统性能最常用的方法之一

当做队列

Redis提供一个list结构，pop和push操作，Redis保证这两个操作是原子性，基于这个特性，可以把Redis当做队列来使用

当做数据存储

直接把Redis当做数据存储来使用，所有的增删改查都直接从Redis中操作

这样操作的基础是因为有非常完备的硬盘持久化机制，有两个配合的机制，可以定期持久化到硬盘中，这样就保证了Redis数据的完整性和安全性



## 历史

在*Redis in Active*这本书中，Redis的发明者Salvatore Sanfilippo。因为找不到合适的工具来解决手头上的问题而发明的



## 安装与配置

### 源码安装

在linux系统中，下载源码，预装软件gcc  tcl (是一门语言)

### 服务端的安装

`tar -xf redis-x.x.x.tar.gz`

cd redis目录

make

在src文件下有redis-cli和redis-server

sudo make install，将生成的二进制文件放到/usr/local/bin目录下

which redis-server 检测命令的位置

redis/src/redis.conf 配置文件

拷贝到/home/user/config/redis/redis.conf

修改文件的配置项`daemonize no/yes`前台启动no还是yes后台启动

`port 6379`修改成7200，启动的端口

启动服务端命令：redis-server redis-conf

ps aux|grep redis-server 检测启动项

### 客户端

which redis-cli

接下来使用redis-cli登录redis-server

如果直接登录redis-cli则报错，Connection refused（），默认端口是6379，默认ip是本机

redis-cli -p 7200 -h 127.0.0.1   如果修改了端口，则要指定端口

光标变成127.0.0.1:7200>

```
127.0.0.1:7200> info
```











## 命令行参数

```bash
$ redis-server --help


$ redis-cli --help
```







# Redis数据类型



## 字符串String

可以存储的值是字符串、整数或浮点，统称为元素

可以对字符串进行操作，对整数类型加减

key-value (string/int/float)

key是字符串

```bash
> set string1 yeyeye  #设置字符串
OK
> get string1  # 获取字符串
"yeyeye"
> set string2 4 # 设置整形
OK
> get string2 # 获取整形
"4"
> incr string2 # 整形自增1
(integer) 5
> get string2 # 获取整形
"5"
> decrby string2 2 # 整形减法
(integer) 3
> get string2 # 获取被减掉之后的值
"3"
```







## 列表List

List集合是一个有序的列表

一个序列集合且每个节点都包好了一个元素

可以对序列两端推入、或弹出元素修剪，查找或移除元素

列表分左右，（左边推入，右边弹出是队列）（左边推入和弹出是栈空间）

```bash
>lpush list1 12 # 左边插入
(integer) 1
>lpush list1 13
(integer) 2
>rpop list1 # 右边弹出 先进先出，后进后出
"12"
# list中的元素可以是重复的，但是集合没有重复的
>lpush list2 12
>lpush list2 13
>lpush list2 13
(integer) 3
>llen list2 # 列出list中元素的个数
(integer) 3


```







## 散列Hash

有key-value的散列组，其中key是字符串，value是元素

按照key进行增加删除，key必须是惟一的

散列结构要求键必须不一样，但是值可以相等

```bash
>hset hash1 key1 12 # 插入散列键值 key1-12
(integer) 1
>hget hash1 key1 # 获取散列hash1中的key1
"12"
>hset hash1 key2 13 # 插入散列键值 key2-13
(integer) 1
>hset hash1 key3 13 
(integer) 1
>hlen hash1 # 查看散列有多少元素
(integer) 3
>hset hash1 key3 14 # 修改key3的值
(integer) 0
>hget hash1 key3
"14"
>hmget hash1 key1 key2 # 一次性获取get的值
1) "12"
2) "13"
>

>

```









## 集合Set

使用无序的方式存储多个不相同的元素

从集合中插入或者删除元素

每个元素都不一样，可以对元素中的值进行添加和删除，检查一个元素是否在这个集合中

```bash
>sadd set1 12 # 插入元素
(integer) 1
>scard set1 # 查看有多少元素
(integer) 1
>sadd set1 13
(integer) 1
>sadd set1 13 # 插入两个相同的元素
(integer) 0
>scard set1 # 查看有多少元素
(integer) 2
>sismember set1 13 # 判断13是否在这个集合中
(integer) 1
>srem set1 13 # 从集合中删除13
(integer) 1
>sismember set1 13
(integer) 0



```









## 有序集合Sort Set

也叫有序分数集合，和散列很相似，也存储一个映射，分数和元素的映射，score可以看做是一个排行榜，排行榜还隐藏一个排行的属性，每个元素都有一个排行属性rank，从0开始表示分数值是最小的，随着score的变大而变大

带分数的score-value有序集合，其中score为浮点，如果score的值一样，则按照value的字母顺序排列，value为元素，value必须是全局唯一

集合插入删除，按照分数范围查找

```bash
>zadd zset1 10.1 val1 # score为10.1 value为val1的元素
(integer) 1
>zadd zset1 11.1 val2
(integer) 1
>zadd zset1 9.2 val3
(integer) 1
>zcard zset1
(integer) 3
>zrange zset1 0 2 withscores # 打印0-2的元素，附带分数
1) "val3"
2) "9.1999999999"
3) "val1"
4) "10.1"
5) "val2"
6) "11.1999999999"
>zrank zset1 val2 # 查看一下val2的排名
(integer) 2
>zadd zset1 12.2 val3 # 修改val3的分数
(integer) 0
>zrange zset1 0 2 withscores
# 排名顺序是 val1 val2 val3
>

>
```







# Redis命令













# 和Python的交互



# php的拓展Redis





# 搭建主从服务器









# 集群













# 单词











refuse 拒绝

refused 遭到拒绝的

connection 连接，关系，人脉

connection refused 连接被拒绝



# 参考书目

《Redis实战》[美]Josiah L. Carlson 人民邮电出版社 ISBN 978-7115402844

[中文支持网站和源代码](http://redisinaction.com)





# 链接

[Redis官网教程](https://redis.io)

[Redis中文官方网站](http://www.redis.cn)

[runoob 简单教程](https://www.runoob.com/redis/redis-tutorial.html)

[Redis入门文章](https://www.jianshu.com/p/56999f2b8e3b)