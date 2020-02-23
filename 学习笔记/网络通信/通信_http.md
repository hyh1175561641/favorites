# 本篇笔记如何使用？

**内容记录**

* 主要记录不常用的功能，常用知识为节省版面可以不记
* 写代码的经验，可以记例子
* 容易出错或经常被遗忘的点
* 技巧，妙用
* 学到的英文单词
* 链接



**标记规范**

```markdown

# 标题（#）
内容或简述（普通内容）
`css
代码（）
`
1. 技巧，遗忘点和出错点（123）

**new word**
- 单词（-）

**链接**
[链接]()

```







# 简介

HTTP (Hypertext Transfer Protocol，超文本传输协议)是在万维网上进行通信时所使用的协议方案。HTTP是Web客户端与服务器交互文档和信息时所使用的协议



HTTP的应用不仅仅是浏览Web内容，尤其是采用SOAP和XML-RPC这样的Web服务



# Web基础

## URL-统一资源定位器

一个统一资源定位器URL用于定位万维网上的文档

URL编码会将字符转换为可通过因特网传输的格式

比如，Web浏览器通过URL从web服务器请求页面，URL的网页地址，`http://www.runoob.com`

**语法规则**

`scheme://host.domain:port/path/filename`

- scheme定义因特网服务的类型，比如http
- host定义域主机，比如http默认主机是www
- domain定义因特网域名，比如google.com
- :port定义主机上的端口号，比如http默认端口号是80
- path定义服务器上的路径，如果省略则表示根目录
- filename定义文档或者资源名称，比如index.html

最常见的scheme有，http https ftp file

**URL编码**

URL只能使用ASCII字符集，通过因特网发送

如果URL包含ASCII以外的字符，必须转换为有效的ASCII格式

URL使用%后面跟随两位十六进制的数来替换非ASCII字符

URL不能包含空格，通常使用+来替代空格

编码字符集并未规定，但一般使用utf-8

[编码到底用的是什么字符集](http://www.ruanyifeng.com/blog/2010/02/url_encoding.html)



**URL编码函数**

JavaScript、PHP、ASP 都提供了对字符串进行URL编码的函数。

JavaScript 中使用 encodeURI() 函数，PHP 中使用rawurlencode() 函数，ASP 中使用 Server.URLEncode() 函数。

备注：JavaScript函数将空格编码成%20





# 状态码







404 - 找不到文件或目录。

500 - 内部服务器错误。(出处：w3school实例测试出现过)



# 首部参考



# 参考书目

《HTTP权威指南》[美]David Gourley   Brian Totty   Marjorie Sayer   Sailu Reddy   Anshu Aggarwal著 人民邮电出版社 ISBN 978-7115281487

[运行实例：Joe的五金商店](http://joes-hardware.com)

这本书的附录有丰富的MIME类型，MIME国际字符集，各国语言缩写代码




















