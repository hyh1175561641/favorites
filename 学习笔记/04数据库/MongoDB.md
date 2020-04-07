











[TOC]



# 简介

MongoDB是用C++语言编写的非关系型数据库。高性能、易部署、易使用，存储数据十分方便



NoSQL非关系型数据库

关系型relational数据库有各种相互关联的表格

非关系型数据库可以想象成一个json格式的大字典

MySQL拓展性差，大数据下IO压力大，表结构更改困难

MongoDB易拓展，大数据量高性能，灵活的数据模型，[高可用](https://www.cnblogs.com/shizhiyi/p/7750530.html)（HA  High Availability）

缺点：数据重复存储，占用大量的空间



relational   关系型(数据库)，相关的，亲属的

## 安装

sudo apt-get install -y mongodb-org

源码安装

tar zxvf mongodb-linux-ubuntu.tgz

sudo mv -r mongodb-linux-ubuntu/  /usr/local/mongodb

Export PATH=/usr/local/mongodb/bin:$PATH

sudo mongod --config /usr/local/mongodb/mongod.conf

## 配置

sudo service mongodb start

sudo service mongodb stop

sudo service mongodb restart

ps ajx | grep mongod

/etc/mongod.conf

Port : 27017

日志：/var/log/mongodb/mongod.log

mkdir ~/data 

mongod --dbpath ~/data

## 命令行

```
$ ./mongo -h
MongoDB shell version v4.2.5
usage: ./mongo [options] [db address] [file names (ending in .js)]
db address can be:
  foo                   foo database on local machine
  192.168.0.5/foo       foo database on 192.168.0.5 machine
  192.168.0.5:9999/foo  foo database on 192.168.0.5 machine on port 9999
  mongodb://192.168.0.5:9999/foo  connection string URI can also be used
Options:
  --ipv6                               enable IPv6 support (disabled by 
                                       default)
  --host arg                           server to connect to
  --port arg                           port to connect to
  -h [ --help ]                        show this usage information
  --version                            show version information
  --verbose                            increase verbosity
  --shell                              run the shell after executing files
  --nodb                               don't connect to mongod on startup - no 
                                       'db address' arg expected
  --norc                               will not run the ".mongorc.js" file on 
                                       start up
  --quiet                              be less chatty
  --eval arg                           evaluate javascript
  --disableJavaScriptJIT               disable the Javascript Just In Time 
                                       compiler
  --enableJavaScriptJIT                enable the Javascript Just In Time 
                                       compiler
  --disableJavaScriptProtection        allow automatic JavaScript function 
                                       marshalling
  --retryWrites                        automatically retry write operations 
                                       upon transient network errors
  --disableImplicitSessions            do not automatically create and use 
                                       implicit sessions
  --jsHeapLimitMB arg                  set the js scope's heap size limit

Authentication Options:
  -u [ --username ] arg                username for authentication
  -p [ --password ] arg                password for authentication
  --authenticationDatabase arg         user source (defaults to dbname)
  --authenticationMechanism arg        authentication mechanism
  --gssapiServiceName arg (=mongodb)   Service name to use when authenticating 
                                       using GSSAPI/Kerberos
  --gssapiHostName arg                 Remote host name to use for purpose of 
                                       GSSAPI/Kerberos authentication

TLS Options:
  --tls                                use TLS for all connections
  --tlsCertificateKeyFile arg          PEM certificate/key file for TLS
  --tlsCertificateKeyFilePassword arg  Password for key in PEM file for TLS
  --tlsCAFile arg                      Certificate Authority file for TLS
  --tlsCRLFile arg                     Certificate Revocation List file for TLS
  --tlsAllowInvalidHostnames           Allow connections to servers with 
                                       non-matching hostnames
  --tlsAllowInvalidCertificates        Allow connections to servers with 
                                       invalid certificates
  --tlsFIPSMode                        Activate FIPS 140-2 mode at startup
  --tlsCertificateSelector arg         TLS Certificate in system store
  --tlsDisabledProtocols arg           Comma separated list of TLS protocols to
                                       disable [TLS1_0,TLS1_1,TLS1_2]

FLE AWS Options:
  --awsAccessKeyId arg                 AWS Access Key for FLE Amazon KMS
  --awsSecretAccessKey arg             AWS Secret Key for FLE Amazon KMS
  --awsSessionToken arg                Optional AWS Session Token ID
  --keyVaultNamespace arg              database.collection to store encrypted 
                                       FLE parameters
  --kmsURL arg                         Test parameter to override the URL for 
                                       KMS

file names: a list of files to run. files have to end in .js and will exit after unless --shell is specified
```





## 概念

db就是一组collection，类似关系型数据库的库，单个实例可以支持多个库，每一个db都有自己的集合和权限

collection就是一组document，类似关系型数据库的一个表

document是MongoDB中数据的基本单位，类似关系型数据库表的行，但是比行要复杂多

key是document中的键的名称，类似关系型数据库中表的列，但是这个key不想关系数据库那样子被限定

每个document都有一个特殊的键 _id ，这个键值是唯一的，相当于关系型数据库中的表的主键

MongoDB存储的数据库是以BSON（Binary JSON）的格式的，BSON是一种二进制的json数据。通过BSON，MongoDB可以方便地存储无模式（scheme）数据

# 基础部分

## 数据库操作

```bash
show dbs
show databases # 显示所有数据库

use dddd # 切换到dddd数据库
db # 显示当前数据库

db.dropDatabase() # 删除当前数据库

```

## 集合操作

```bash
show collections # 显示集合

# 手动创建集合，也可以不创建集合，插入第一条数据自动创建集合
db.createCollection(NAME,OPTIONS) # 写上名字和选项
db.createCollection("stu",{capped:true,size:10})
  # capped选项false表示不设置上限，true表示设置上限
  # size当capped值为true时，表示上限大小，当文件到达上限时，覆盖之前的数据，单位是字节

# 删除集合
db.stu.drop()

```





## 数据类型

[MongoDB数据类型](https://www.jianshu.com/p/5369120365d2)

Object ID ：文档的id
String： 字符串，最常用，必须是utf-8
Boolean：布尔值，true 或者false
Integer：整数
Double：浮点数
Arrays：数组或者列表，多个值存储到一个键
Object：用于嵌入文档，即一个值为一个文档
Null：存储null值
Timestamp：时间戳
Date：存储当前日期或时间unix时间格式





9.43
















# 链接

[MongoDB官网](https://www.mongodb.com)

[MongoDB官方英文文档](https://docs.mongodb.com/manual/)

[MongoDB runoob](https://www.runoob.com/mongodb/mongodb-tutorial.html)

















