











[TOC]



# 简介





## 安装

在Ubuntu上，到官网下载使用

Tar zxvf navicat112_mysql_cs_x64.tar.gz解压

./start_navicat

如果跳出窗口询问是否安装wine环境，点取消

## 配置

**中文乱码**

将export LANG="en_US.UTF-8" 改为 export LANG="zh_CN.UTF-8"

**重置软件**

删除用户目录下的.navicat64目录

cd ~; rm -r .navicat64







## 连接数据库

输入名字 

ip

端口

用户名

密码

可以连接测试

## 新建数据库

数据库名

字符集选 utf8 -- UTF-8 Unicode

排序规则选 utf8_general_ci



## 新建数据表

添加字段

字段名

类型

长度

小数点

null

主键

表名

## 增删改数据

如果新数据不符合要求，不会改变原来的数据

Navicat需要在底下打对勾才能生效







