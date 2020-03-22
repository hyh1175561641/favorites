# 简介

## 概述

Redis是一种NoSQL技术，它的性能十分优越，可以支持每秒几十万次的读写操作，性能远超数据库，并且还支持集群、分布式、主从同步等配置，原则上可以无限扩展，让更多的数据存储在内存中，更让人欣慰的是它还支持一定的事务能力，这保证了高并发的场景下数据的安全和一致性

**NoSQL (not only SQL)技术**

不支持SQL语法，存储结构都是采用key-value形式，没有通用的语言

这是一种基于内存的数据库，且提供一定的持久化功能。

Redis和MongoDB是当前使用最广泛的NoSQL



**关系型数据库和NoSQL数据库的比较**

适用的场景不同，sql数据库适合用于关系特别复杂的数据查询场景，nosql则反之

SQL对事务的支持非常完善，而NoSQL基本不支持事务，两者不断的取长补短，呈现融合趋势

事务，一组sql操作，要么都成功，要么都失败

**Redis是远程的**

有客户端和服务端两个部分，可以部署在不同的两个机器上，可以使用自定义的协议进行传输和交互

通常说的Redis是指服务端，特殊情况才说Redis客户端

**Redis是基于内存的**

所有的数据和结构都存储在内存中，操作非常高速，性能远远优于硬盘MySQL，比较吃内存的软件

支持数据持久化，可以将内存中的数据保存在磁盘中，重启的时候可以再次加载进行使用

**Redis是非关系型数据库**

关系型数据库在存储之前必须定义好数据字典，后续的存储数据按照数据字典进行存储，而Redis不需要定义数据字典

支持主从模式的数据备份，即master-slave模式

**应用场景**

当做缓存 (ehcache/memcached)

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

`tar -xf redis-x.x.x.tar.gz`或

`tar -zxvf redis-x.x.x.tar.gz`

如果讲究的话，sudo mv ./redis-x.x.x  /usr/local/redis

cd redis目录

make

这里可以make test测试依赖

在src文件下有redis-cli和redis-server，还有redis-benchmark性能测试工具，redis-check-aof AOF文件修复工具，redis-check-rdb RDB文件检索工具（Redis持久化文件就是RDB文件）

sudo make install，将生成的二进制文件放到/usr/local/bin目录下

which redis-server 检测命令的位置

redis/src/redis.conf 配置文件

拷贝到/home/user/config/redis/redis.conf或/etc/redis目录下

**修改配置文件redis.conf**

`bind 127.0.0.1` 绑定ip

修改文件的配置项`daemonize no/yes`前台启动no还是yes后台启动，是否以守护进程yes运行

`port 6379`修改成7200，启动的端口

`dbfilename dump.rdb`数据持久化写入的文件

`dir /var/lib/redis`数据文件存储路径，记得创建好文件

`logfile /var/log/redis/redis-server.log`日志文件

`database 16`数据库默认有16个

`slaveof`主从复制，类似于双机备份，搭建主从需要

[还可以设置密码](https://www.cnblogs.com/aspsea/articles/10964606.html)

**启动服务端**

启动服务端命令：redis-server redis-conf

ps aux|grep redis-server 检测启动项



如果可以使用sudo service redis start/stop/restart启动和停止最好

### 客户端

which redis-cli

接下来使用redis-cli登录redis-server

如果直接登录redis-cli则报错，Connection refused，默认端口是6379，默认ip是本机

redis-cli -p 7200 -h 127.0.0.1   如果修改了端口，则要指定端口

光标变成127.0.0.1:7200>

```bash
127.0.0.1:7200> info # 服务器信息

127.0.0.1:7200> ping
PONG # 连接成功


127.0.0.1:7200> select 5 # 默认连接到0号数据库,切换到5号
OK


127.0.0.1:7200[5]> # 提示符会变
```











## 命令行参数

```bash
$ redis-server --help
Usage: ./redis-server [/path/to/redis.conf] [options]
       ./redis-server - (read config from stdin)
       ./redis-server -v or --version
       ./redis-server -h or --help
       ./redis-server --test-memory <megabytes>

Examples:
       ./redis-server (run the server with default conf)
       ./redis-server /etc/redis/6379.conf
       ./redis-server --port 7777
       ./redis-server --port 7777 --replicaof 127.0.0.1 8888
       ./redis-server /etc/myredis.conf --loglevel verbose

Sentinel mode:
       ./redis-server /etc/sentinel.conf --sentinel






$ redis-cli --help
redis-cli 5.0.5

Usage: redis-cli [OPTIONS] [cmd [arg [arg ...]]]
  -h <hostname>      Server hostname (default: 127.0.0.1).
  -p <port>          Server port (default: 6379).
  -s <socket>        Server socket (overrides hostname and port).
  -a <password>      Password to use when connecting to the server.
                     You can also use the REDISCLI_AUTH environment
                     variable to pass this password more safely
                     (if both are used, this argument takes predecence).
  -u <uri>           Server URI.
  -r <repeat>        Execute specified command N times.
  -i <interval>      When -r is used, waits <interval> seconds per command.
                     It is possible to specify sub-second times like -i 0.1.
  -n <db>            Database number.
  -x                 Read last argument from STDIN.
  -d <delimiter>     Multi-bulk delimiter in for raw formatting (default: \n).
  -c                 Enable cluster mode (follow -ASK and -MOVED redirections).
  --raw              Use raw formatting for replies (default when STDOUT is
                     not a tty).
  --no-raw           Force formatted output even when STDOUT is not a tty.
  --csv              Output in CSV format.
  --stat             Print rolling stats about server: mem, clients, ...
  --latency          Enter a special mode continuously sampling latency.
                     If you use this mode in an interactive session it runs
                     forever displaying real-time stats. Otherwise if --raw or
                     --csv is specified, or if you redirect the output to a non
                     TTY, it samples the latency for 1 second (you can use
                     -i to change the interval), then produces a single output
                     and exits.
  --latency-history  Like --latency but tracking latency changes over time.
                     Default time interval is 15 sec. Change it using -i.
  --latency-dist     Shows latency as a spectrum, requires xterm 256 colors.
                     Default time interval is 1 sec. Change it using -i.
  --lru-test <keys>  Simulate a cache workload with an 80-20 distribution.
  --replica          Simulate a replica showing commands received from the master.
  --rdb <filename>   Transfer an RDB dump from remote server to local file.
  --pipe             Transfer raw Redis protocol from stdin to server.
  --pipe-timeout <n> In --pipe mode, abort with error if after sending all data.
                     no reply is received within <n> seconds.
                     Default timeout: 30. Use 0 to wait forever.
  --bigkeys          Sample Redis keys looking for keys with many elements (complexity).
  --memkeys          Sample Redis keys looking for keys consuming a lot of memory.
  --memkeys-samples <n> Sample Redis keys looking for keys consuming a lot of memory.
                     And define number of key elements to sample
  --hotkeys          Sample Redis keys looking for hot keys.
                     only works when maxmemory-policy is *lfu.
  --scan             List all keys using the SCAN command.
  --pattern <pat>    Useful with --scan to specify a SCAN pattern.
  --intrinsic-latency <sec> Run a test to measure intrinsic system latency.
                     The test will run for the specified amount of seconds.
  --eval <file>      Send an EVAL command using the Lua script at <file>.
  --ldb              Used with --eval enable the Redis Lua debugger.
  --ldb-sync-mode    Like --ldb but uses the synchronous Lua debugger, in
                     this mode the server is blocked and script changes are
                     not rolled back from the server memory.
  --cluster <command> [args...] [opts...]
                     Cluster Manager command and arguments (see below).
  --verbose          Verbose mode.
  --no-auth-warning  Don't show warning message when using password on command
                     line interface.
  --help             Output this help and exit.
  --version          Output version and exit.

Cluster Manager Commands:
  Use --cluster help to list all available cluster manager commands.

Examples:
  cat /etc/passwd | redis-cli -x set mypasswd
  redis-cli get mypasswd
  redis-cli -r 100 lpush mylist x
  redis-cli -r 100 -i 1 info | grep used_memory_human:
  redis-cli --eval myscript.lua key1 key2 , arg1 arg2 arg3
  redis-cli --scan --pattern '*:12345*'

  (Note: when using --eval the comma separates KEYS[] from ARGV[] items)

When no command is given, redis-cli starts in interactive mode.
Type "help" in interactive mode for information on available commands
and settings.

```







# Redis数据类型

每条数据都是一个键对值，键是字符串，而且键的类型不能重复

## 字符串String

可以存储的值是字符串、整数或浮点，统称为元素

可以存储二进制，任何格式的数据，如JPEG图像数据或JSON对象描述信息等，最多可容纳的数据长度是512M

可以对字符串进行操作，对整数类型加减

key-value (string/int/float)

key是字符串

```bash
> set string1 yeyeye  #设置字符串
> get string1  # 获取字符串


> mset a1 python a2 java a3 c # 设置多个键多个值
> mget a1 a2 a3 # 获取多个值

> append a1 haha # 在字符串后面追加一段值

> incr string2 # 整形自增1
> decrby string2 2 # 整形减法

> setex sring3 3 aa # 设置过期时间，3秒后不可用






```



[字符串runoob](https://www.runoob.com/redis/redis-strings.html)

```bash
APPEND # 字符串后面追加一段值
BITCOUNT
BITFIELD
BITOP
BITPOS
DECR
DECRBY # 整形减法
GET # 获取字符串
GETBIT
GETRANGE
GETSET
INCR # 整形自增
INCRBY
INCRBYFLOAT
MGET # 获取多个键
MSET # 设置多个值
MSETNX
PSETEX
SET # 设置字符串
SETBIT
SETEX # 设置过期时间
SETNX
SETRANGE
STRLEN
```







## 列表Lists

List集合是一个有序的列表

一个序列集合且每个节点都包好了一个元素

可以对序列两端推入、或弹出元素修剪，查找或移除元素

列表分左右，（左边推入，右边弹出是队列）（左边推入和弹出是栈空间）

key-[value (string/int/float),value (string/int/float)]

```bash
>lpush list1 12 # 左边插入，在同一侧插入弹出是栈空间
>lpop list1 # 左边弹出
>rpush list1 13 # 右边插入，一侧插入另一侧弹出是队列
>rpop list1 # 右边弹出
>linsert list1 before 13 12.5 # 在13前面插入12.5 
>linsert list1 after 12 12.5 # 在12后面插入12.5 

# list中的元素可以是重复的，但是集合没有重复的

>llen list2 # 列出list中元素的个数

>lrange l1 0 4 # 列出列表的从哪到哪的数据

```



[列表](https://www.runoob.com/redis/redis-lists.html)

```bash
BLPOP
BRPOP
BRPOPLPUSH
LINDEX
LINSERT # 在某个元素的前面或后面插入数据
LLEN # 列出元素的个数
LPOP # 列表左侧弹出数据
LPUSH # 列表左侧插入数据
LPUSHX
LRANGE # 列出区间内的数据
LREM
LSET
LTRIM
RPOP # 列表右侧弹出数据
RPOPLPUSH
RPUSH # 列表右侧插入数据
RPUSHX
```







## 散列Hashes

有key-value的散列组，其中key是字符串，value是元素

按照key进行增加删除，key必须是惟一的

散列结构要求键必须不一样，但是值可以相等

key-[key-value (string/int/float),key-value (string/int/float)]

```bash
>hset hash1 key1 12 # 插入散列键值 key1-12
>hget hash1 key1 # 获取散列hash1中的key1

>hmset hash1 key1 13 key2 14 # 设置多个值
>hmget hash1 key1 key2 # 一次性获取get的值

>hlen hash1 # 查看散列有多少元素
>hkeys hash1 # 获取指定键所有的属性

>hvals hash1 # 获取所有属性的值
>hdel hash1 # 删除散列的键，如果使用del命令，会删除整个散列表
```



[哈希](https://www.runoob.com/redis/redis-hashes.html)

```bash
HDEL # 删除散列的键
HEXISTS
HGET # 获取散列值
HGETALL
HINCRBY
HINCRBYFLOAT
HKEYS # 获取指定键所有的属性
HLEN # 查看散列有多少元素
HMGET # 获取多个散列值
HMSET # 设置多个散列值
HSCAN
HSET # 插入散列值
HSETNX
HSTRLEN
HVALS # 获取所有属性的值
```

```
注意：如果出现了这个错误
MISCONF Redis is configured to save RDB snapshots, but is currently not able to persist on disk. Commands that may modify the data set are disabled. Please check Redis logs for details about the error.
Redis被配置为保存数据库快照，但它目前不能持久化到硬盘。用来修改集合数据的命令不能用。hset修改集合不能用
原因：强制关闭Redis快照导致不能持久化
将stop-writes-on-bgsave-error设置为no
127.0.0.1:6379> config set stop-writes-on-bgsave-error no

```

[Redis修改hash报错解决方案](https://www.jianshu.com/p/3aaf21dd34d6)



**单词**

field 字段 信息组 栏

## 集合Sets

使用无序的方式存储多个不相同的元素

从集合中插入或者删除元素

每个元素都不一样，可以对元素中的值进行添加和删除，检查一个元素是否在这个集合中

key-[value (string/int/float),value (string/int/float)]

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



[集合](https://www.runoob.com/redis/redis-sets.html)

```bash
SADD
SCARD
SDIFF
SDIFFSTORE
SINTER
SINTERSTORE
SISMEMBER
SMEMBERS
SMOVE
SPOP
SRANDMEMBER
SREM
SSCAN
SUNION
SUNIONSTORE
```







## 有序集合Sorted Sets

也叫有序分数集合，和散列很相似，也存储一个映射，分数和元素的映射，score可以看做是一个排行榜，排行榜还隐藏一个排行的属性，每个元素都有一个排行属性rank，从0开始表示分数值是最小的，随着score的变大而变大

带分数的score-value有序集合，其中score为浮点，如果score的值一样，则按照value的字母顺序排列，value为元素，value必须是全局唯一

集合插入删除，按照分数范围查找

key-[value (string/int/float)-score,value (string/int/float)-score]

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



[有序集合](https://www.runoob.com/redis/redis-sorted-sets.html)

```bash
BZPOPMAX
BZPOPMIN
ZADD
ZCARD
ZCOUNT
ZINCRBY
ZINTERSTORE
ZLEXCOUNT
ZPOPMAX
ZPOPMIN
ZRANGE
ZRANGEBYLEX
ZRANGEBYSCORE
ZRANK
ZREM
ZREMRANGEBYLEX
ZREMRANGEBYRANK
ZREMRANGEBYSCORE
ZREVRANGE
ZREVRANGEBYLEX
ZREVRANGEBYSCORE
ZREVRANK
ZSCAN
ZSCORE
ZUNIONSTORE
```





# Redis命令

## 键 keys

```bash
keys * # 查找所有的keys，可以使用正则  (keys a* 查找a开头的键)

del key1 key2 ...# 删除指定的key（一个或多个）
exists key # 查询一个key是否存在 存在返回1 不存在返回0
type a1 # 获取key的存储类型
# 如果没有指定过期时间，值则一直存在，直到使用del移除
expire a1 3 # 设置一个key的过期秒数
ttl a1# 获取key的有效时间，过期的键返回-2



dump key # 导出key的值
expireat key timestamp # 设置一个UNIX时间戳的过期时间
migrate#原子性的将key从Redis的一个实例移到另一个实例
move 移动一个key到另一个数据库
object # 检查内部的再分配对象
persist # 移除key的过期时间
pexpire # 设置key的有效时间以毫秒为单位
pexpireat # 设置key的到期UNIX时间戳以毫秒为单位
pttl # 获取key的有效毫秒数
randomkey # 返回一个随机的key
rename # 将一个key重命名
renamenx # 重命名一个key，新的key必须是不存在的key
restore #
sort # 对序列，集合，有序集合排序
wait # 
scan # 增量迭代key
```





```bash
DEL
DUMP
EXISTS
EXPIRE
EXPIREAT
KEYS
MIGRATE
MOVE
OBJECT
PERSIST
PEXPIRE
PEXPIREAT
PTTL
RANDOMKEY
RENAME
RENAMENX
RESTORE
SCAN
SORT
TOUCH
TTL
TYPE
UNLINK
WAIT
```





## 事务 Transactions



```bash
DISCARD
EXEC
MULTI
UNWATCH
WATCH
```







## 脚本 Scripting





```bash
EVAL
EVALSHA
SCRIPT DEBUG
SCRIPT EXISTS
SCRIPT FLUSH
SCRIPT KILL
SCRIPT LOAD
```







## 连接 Connection



```bash
AUTH
ECHO
PING
QUIT
SELECT
SWAPDB
```





## 服务器 Server

```bash
> config get loglevel # 查看配置
> config get * # 查看所有配置
> config set loglevel "notice" # 修改配置

> save # 当前数据库的备份
```

[参数说明](https://www.runoob.com/redis/redis-conf.html)

[数据库的备份](https://www.runoob.com/redis/redis-backup.html)

```bash
BGREWRITEAOF
BGSAVE
CLIENT GETNAME
CLIENT ID
CLIENT KILL
CLIENT LIST
CLIENT PAUSE
CLIENT REPLY
CLIENT SETNAME
CLIENT UNBLOCK
COMMAND
COMMAND COUNT
COMMAND GETKEYS
COMMAND INFO
CONFIG GET
CONFIG RESETSTAT
CONFIG REWRITE
CONFIG SET
DBSIZE
DEBUG OBJECT
DEBUG SEGFAULT
FLUSHALL
FLUSHDB
INFO
LASTSAVE
MEMORY DOCTOR
MEMORY HELP
MEMORY MALLOC-STATS
MEMORY PURGE
MEMORY STATS
MEMORY USAGE
MONITOR
REPLICAOF
ROLE
SAVE # 备份数据
SHUTDOWN
SLAVEOF
SLOWLOG
SYNC
TIME
```



## Cluster





```bash
CLUSTER ADDSLOTS
CLUSTER COUNT-FAILURE-REPORTS
CLUSTER COUNTKEYSINSLOT
CLUSTER DELSLOTS
CLUSTER FAILOVER
CLUSTER FORGET
CLUSTER GETKEYSINSLOT
CLUSTER INFO
CLUSTER KEYSLOT
CLUSTER MEET
CLUSTER NODES
CLUSTER REPLICAS
CLUSTER REPLICATE
CLUSTER RESET
CLUSTER SAVECONFIG
CLUSTER SET-CONFIG-EPOCH
CLUSTER SETSLOT
CLUSTER SLAVES
CLUSTER SLOTS
READONLY
READWRITE
```







## Geo



```bash
GEOADD
GEODIST
GEOHASH
GEOPOS
GEORADIUS
GEORADIUSBYMEMBER
```







## HyperLogLog



```bash
PFADD
PFCOUNT
PFMERGE
```







## 发布订阅Pub/Sub



```bash
PSUBSCRIBE
PUBLISH
PUBSUB
PUNSUBSCRIBE
SUBSCRIBE
UNSUBSCRIBE
```



## Streams

```bash
XACK
XADD
XCLAIM
XDEL
XGROUP
XINFO
XLEN
XPENDING
XRANGE
XREAD
XREADGROUP
XREVRANGE
XTRIM
```







# 主从服务器

master用来写数据，slave用来读数据，网站的读写比是1：10

一个master可以用有多个slave，一个slave又可以拥有多个slave，如此下去，形成了强大的多级服务器集群架构

slave备份主服务的数据，通过主从配置可以实现读写分离

**主配置**

修改配置文件，IP绑定bind

**从配置**

复制一份主配置文件，重命名为slave.conf

IP绑定bind，确保能和主通信

从配置中的端口port不能和主端口冲突（如果主从在同一台机器上）

`slaveof 192.168.0.1 6379`主服务器的地址和端口

**启动服务**

主 redis-server redis.conf

从 redis-server slave.conf

Redis-cli -h 192.168.0.1 -p 6379 info Replication 查看信息，主从都能看

用redis-cli登录，主能读写，从只读







# 集群













# php的拓展Redis

安装

php -m 可以查看php有哪些拓展（还需要查看是否安装了phpize和php-config）

yum install php-devel（PHP的拓展开发包）

wget https://github.com/phpredis/phpredis/archive/develop.zip

（PHP Redis拓展）

安装源码步骤

unzip develop.zip

Phpize

./configure --with-php-config=/usr/bin/php-config

Make/make install

php.ini -- extension=redis.so

[具体步骤看 慕课网Redis教程](https://www.imooc.com/video/14335)







# 单词







unstable 不稳定的，动荡的，异变的（官网download）

stable 稳定的

refuse 拒绝

refused 遭到拒绝的

connection 连接，关系，人脉

connection refused 连接被拒绝（Redis连接未指定端口）



# 参考书目

《Redis实战》[美]Josiah L. Carlson 人民邮电出版社 ISBN 978-7-115-40284-4

[中文支持网站和源代码](http://redisinaction.com)





# 链接

[Redis官网教程](https://redis.io)

[Redis中文官方网站](http://www.redis.cn)

[runoob 简单教程](https://www.runoob.com/redis/redis-tutorial.html)

[Redis入门文章](https://www.jianshu.com/p/56999f2b8e3b)