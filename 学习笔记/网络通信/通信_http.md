# 本篇笔记如何使用？

**内容记录**

* 



**标记规范**

```markdown

# 标题（#）
内容或简述（普通内容）
​```
代码（）
​```
```







# 简介

HTTP (Hypertext Transfer Protocol，超文本传输协议)是在万维网上进行通信时所使用的协议方案。HTTP是Web客户端与服务器交互文档和信息时所使用的协议



HTTP的应用不仅仅是浏览Web内容，尤其是采用SOAP和XML-RPC这样的Web服务



# 基础内容

## URL-统一资源定位符

URI是一类更通用的资源标识符，URL是它的一个子集。由两个主要的子集URL和URN构成，URL是通过描述资源的位置来标识资源的，而URN则是通过名字来识别资源的，与他们所处位置无关。

URL是因特网资源的标准化名称，是浏览器寻找信息是所需的资源位置。通过URL，人类和应用程序才能找到、使用并共享因特网上的大量数据资源。

**语法规则**

一个统一资源定位器URL用于定位万维网上的文档。第一部分是URL方案(scheme)，告知Web客户端怎样访问资源。第二部分是指服务器的位置，告知Web客户端资源位于何处。第三部分是资源路径，说明了请求的是服务器上的哪个特定的本地资源。

Mailto , ftp, rtsp,ftp,smtp

大多数URL方案都是建立在由这9个部分构成的通用格式上：

`scheme://user:password@host.domain:port/path;params?query#frag`

- scheme方案-使用什么协议

scheme定义因特网服务的类型，使用什么协议，方案组件必须以一个字母符号开始，与第一个冒号隔开，方案名与大小写无关。比如http https ftp file smtp mailto rtsp

- user用户

某些方案访问资源时需要用户名，后面用@分隔。比如ftp，如果没有指定用户名和密码，浏览器自动插入一个用户名和密码（IE浏览器发送IEUser，网景浏览器发送mozilla）

- password密码

用户名后面可能要包含密码，中间由冒号分隔

- host定义域主机

资源宿主服务器的主机名或点分IP地址，用点分隔。比如http默认主机是www

- domain定义因特网域名，比如google.com
- :port定义主机上的端口号，比如http默认端口号是80
- path定义服务器上的路径，由斜杠分开，如果省略则表示根目录
- params参数

为应用程序提供了访问资源所需的所有附加信息参数为名/值对。URL可以包含多个参数字段，相互之间以及与路径的其余部分之间用分号分隔

```
ftp://prep.ai.mit.edu/pub/gnu;type=d
有一个参数type=d，参数名为type，值为d

http://www.joes-hardware.com/hammers;sale=false/index.html;graphics=true
hammers/index.html，这个路径段都分别有一个参数
```

- query查询

传递参数，用问号与其余部分分隔开来，可以包含多个名/值对，用&分隔，比如数据库的查询，通过提问或查询来缩小请求资源类型的范围

- frag片段

一小片或一部分资源的名字，不会将frag传递给服务器，而是客户端自己使用，用井字符分隔开来

**相对URL**

绝对URL：包含有访问资源所需要的全部信息

相对URL：是不完整的，必须从另一个基础 (base) URL进行解析，这保持一组资源的便携性，搬移一组文档的同时，仍然保持链接的有效性

```
若一个URL是http://www.joes-hardware.com/tools.html
则可以使用./hammers.html来代表另一个页面
```

基础URL：是作为相对URL的参考点使用的。可以出自这几个地方1.\<base\>标签，2.所属资源的URL，3.没有URL，有可能是不完整或损坏的URL

解析相对URL，拆分组件，继承父组件。详细方法见HTTP权威指南

**扩充URL**

有时用户不必输入完整的URL，浏览器自动扩展URL。

主机名扩展，比如输入yahoo.com，自动扩展www

历史扩展，把以前输入过的URL储存起来。

**URL编码**

URL编码会将字符转换为可通过因特网传输的格式

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



## 请求报文

HTTP报文是在HTTP应用程序之间发送的数据块。这些数据块以一些文本形式的元信息 (meta-information) 开头，这些信息描述了报文的内容及含义，后面跟着可选的数据部分。这些报文在客户端、服务器和代理之间流动。



HTTP报文是简单的格式化数据块，每条报文都包含一条来自客户端的请求，或者一条来自服务器的响应。有三部分组成：对报文进行描述的起始行 (start line) 、包含属性的首部 (header) 块、以及可选的包含数据的主体 (body) 部分。

请求报文的组成：

```
<method> <request-URL> <version>
<headers>

<entity-body>
```

换行符由两个字符组成，回车符(\r)和换行符(\n)，ASCII码分别是13和10，这个行的终止序列可以写作CRLF

## 响应报文

### 状态码

404 - 找不到文件或目录。

500 - 内部服务器错误。(出处：w3school实例测试出现过)



# 首部参考



# 参考书目

《HTTP权威指南》[美]David Gourley   Brian Totty   Marjorie Sayer   Sailu Reddy   Anshu Aggarwal著 人民邮电出版社 ISBN 978-7115281487

[运行实例：Joe的五金商店](http://joes-hardware.com)

这本书的附录有丰富的MIME类型，MIME国际字符集，各国语言缩写代码




















