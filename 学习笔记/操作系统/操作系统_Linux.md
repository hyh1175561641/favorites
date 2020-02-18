# 如何使用本篇文档？

**规范**





[TOC]





临时放命令的地方

su

exit





# 计算机概论







# Linux的起源于发展





# 安装与配置



# 系统账号

/etc/passwd系统上的账号和一般身份用户与root账户

/etc/shadow记录了账号的密码

/etc/group记录了组名

# 文件权限和目录

## 用户和用户组

**用户和用户组的概述**

Linux是个多人多用户系统，文件权限是一个非常健全的安全防护措施。为了限制自己，用户组及其他人的使用，Linux有用户和用户组，每一个文件都有三种属性。账号使用一个文件时，先判断自己是否为文件的拥有者，再判断是否是组员，如果都不是，则为其他人。root具有最高权限，可以做任何事情

注意：

- 任何一个文件都具有用户(User)，群组(Group)，其他人(Others)三种身份的权限

- 账号可以有多个用户组

## Linux文件权限

**Linux文件权限的属性**

###### ls命令

显示目录内容

```bash
ls [-alrtAFR] [name...]
-a 显示所有的文件和目录，包括名称开头为"."的隐藏档
-l 将文件形态、权限、拥有者、文件大小的详细列表列出
-r 将文件以相反的次序显示（默认次序是英文字母次序）
-t 将文件依建立时间先后次序列出
-A 同-a，但是不列出"."和".."（当前目录和父目录）
-F 在列出的文件名称之后加一个符号，可执行档加"*"，目录加"/"
-R 若目录下有文件夹，所有文件夹的所有文件都列出
--full-time 列出完整的时间格式，包括年月日时间和时区
--help 帮助
常用方法：
ls -al 当前目录下的所有文件的详细信息
```

```bash
# 示例
[root@hyh /]# ls -al
total 68
dr-xr-xr-x. 18 root root  4096 Dec 15 02:11 .
dr-xr-xr-x. 18 root root  4096 Dec 15 02:11 ..
-rw-r--r--   1 root root     0 Oct  8 09:17 .autorelabel
lrwxrwxrwx.  1 root root     7 Oct  8 17:13 bin -> usr/bin
dr-xr-xr-x.  5 root root  4096 Dec 17 03:21 boot
drwxr-xr-x  19 root root  2960 Dec 15 12:31 dev
drwxr-xr-x. 79 root root  4096 Dec 17 03:48 etc
drwxr-xr-x.  3 root root  4096 Dec 15 12:24 home
lrwxrwxrwx.  1 root root     7 Oct  8 17:13 lib -> usr/lib
lrwxrwxrwx.  1 root root     9 Oct  8 17:13 lib64 -> usr/lib64
drwx------.  2 root root 16384 Oct  8 17:13 lost+found
drwxr-xr-x.  2 root root  4096 Apr 11  2018 media
drwxr-xr-x.  2 root root  4096 Apr 11  2018 mnt
drwxr-xr-x.  2 root root  4096 Apr 11  2018 opt
dr-xr-xr-x  87 root root     0 Dec 15 12:31 proc
dr-xr-x---.  5 root root  4096 Dec 17 03:47 root
drwxr-xr-x  24 root root   660 Dec 17 03:48 run
lrwxrwxrwx.  1 root root     8 Oct  8 17:13 sbin -> usr/sbin
drwxr-xr-x.  2 root root  4096 Apr 11  2018 srv
dr-xr-xr-x  13 root root     0 Dec 17 03:26 sys
drwxrwxrwt.  9 root root  4096 Feb 17 08:17 tmp
drwxr-xr-x. 13 root root  4096 Oct  8 17:13 usr
drwxr-xr-x. 19 root root  4096 Oct  8 09:17 var
```

```bash
drwxr-xr-x. 19 root root  4096 Oct  8 09:17 var
# 上面的示例中，文件属性依次是
# 权限drwxr-xr-x. 链接19 拥有者root 用户组root 文件容量4096 日期Oct  8 09:17 文件名var
```

第一列是文件的类型与权限，共有十个字符

- 第一个字符是指文件的类型
- 当为[d]，则是目录
- 当为[-]，则是文件
- 当为[l]，则是链接目录
- 当为[b]，则是块设备文件，可供存储的周边设备
- 当为[c]，则是字符设备文件，串行端口设备，列如键盘，鼠标
- 当为[s]，则是套接字文件，通常用在网络数据连接，最常在/var/run目录中看到
- 当为[p]，则是管道文件，特殊的文件类型，解决多个程序同时存取一个文件所造成的错误。FIFO是first-in-first-out(先进先出)的缩写
- 接下来的九个字符，三个为一组，代表文件的权限
- 第一组是文件拥有者的权限，第二组是加入用户组，第三组是其他账号
- 三组都是rwx组合，r(read)代表可读，w(write)代表可写，x(execute)代表可执行，如果没有权限则出现[-]

第二列代表有多少文件名链接到此节点(inode)，

第三列表示这个文件拥有者的账号

第四列表示这个文件的所属用户组

第五列表示这个文件的容量大小，默认单位为Bytes

第六列表示这个文件的最近修改日期

第七列显示文件名

注意：

- 如果提示permission deny，权限设置错误
- 不论用户组是什么，账号是最主要的主角
- 目录与文件的权限意义不同，对于目录来说，可读代表，可写代表，可执行代表



**Linux文件权限的修改**

若要修改文件的第一列权限，第三列拥有者，第四列用户组，使用下面三个命令

###### chmod命令

修改文件的权限，SUID、SGID、SBIT等特性

chmod数字修改法，r用4代表，w用2代表，x用1代表

chmod符号修改法，u代表用户 g代表组 o代表其他 a代表所有，rwx代表要改变的权限，+加入 -移除 =设置

```bash
chmod
-R 进行递归修改，将目录下的所有子文件子目录都更新
常用方法：
chmod 754 test.sh # 执行文件，其他人可以运行但不能修改
chmod 664 text.txt # 普通代码文件，可修改，其他人只能阅读
chmod u=rwx go=rx test.sh # 执行文件，可修改可执行，其他人不能修改
chmod a+w text.txt # 所有人可写入
chmod a-x test.sh # 所有人都不可执行
```

###### chown命令

修改文件的拥有者，账号必须是已经存在的，还可以顺便修改用户组

```bash
chown
-R 进行递归修改，将目录下的所有子文件子目录都更新为这个拥有者
常用方法：
chown ownername file
chown ownername:groupname file
```

###### chgrp命令

修改文件的用户组，用户组必须是已经存在的

```bash
chgrp
-R 进行递归修改，将目录下的所有子文件子目录都更新为这个用户组
常用方法：
chgrp groupname file
```





**Linux文件权限的重要性**

文件权限最大重要性的是在数据安全性上面。可以保护系统功能，防止系统文件被修改或删除。可以团队协同开发。可以防止不明人士捣乱





###### cp命令

复制文件

```bash
cp
--help
常用方法：
cp 源文件 目标文件
```



# 磁盘与文件系统







# 文件与文件系统的压缩











# 进程管理和SELinux









# 系统服务daemon









# 计划任务和日常维护





# 日志文件









# 启动流程









# 软件安装







# 系统设置与备份







# 图形界面













# 内核编译与管理







# 英语单词





invalid 无效的，残疾的，有病的

deny 否定，否认，拒绝

permission 允许，许可，权限

# 参考书目

《鸟哥的Linux私房菜 基础学习篇（第四版）》鸟哥著，人民邮电出版社 ISBN 978-7115472588

# 链接

[鸟哥的Linux私房菜网页版](http://linux.vbird.org)

[Linux命令大全](https://www.runoob.com/linux/linux-command-manual.html)