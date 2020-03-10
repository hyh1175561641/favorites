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



[toc]



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



## 报文

HTTP报文是在HTTP应用程序之间发送的数据块。这些数据块以一些文本形式的元信息 (meta-information) 开头，这些信息描述了报文的内容及含义，后面跟着可选的数据部分。这些报文在客户端、服务器和代理之间流动。

HTTP报文是简单的格式化数据块，每条报文都包含一条来自客户端的请求，或者一条来自服务器的响应。有三部分组成：对报文进行描述的起始行 (start line) 、包含属性的首部 (header) 块、以及可选的包含数据的主体 (body) 部分。

换行符由两个字符组成，回车符(\r)和换行符(\n)，ASCII码分别是13和10，这个行的终止序列可以写作CRLF

其中entity-body是可选的部分，主体可包含文本或二进制数据，也可以为空

## 请求报文

请求报文向Web请求一个动作

request message 请求报文的组成：

```
<method> <request-URL> <version>
<headers>

<entity-body>

例子
GET /img/g.gif HTTP/1.0
Host: www.host.com
```

### 方法

客户端希望服务器对资源执行的动作

**GET**

GET是最常用的方法，通常用于请求服务器发送某个资源

GET请求是在URL中发送的

**HEAD**

HEAD方法与GET方法类似，但服务器只返回首部，不返回主体。主要用来对首部进行检验，判断资源类型，查看对象状态码，测试资源是否被修改

**POST**

用来向服务器输入数据，通常用来支持HTML表单，对长度没有限制

POST请求是在HTTP消息主体中发送的

**PUT**

PUT方法会向服务器写入文档，允许用户创建Web页面

**TRACE**

TRACE对可能经过代理服务器传送到服务器上去的报文进行追踪，用法不明确，<u>具体内容查书</u>

**OPTIONS**

OPTIONS方法请求Web服务器告知其支持的各项功能

**DELETE**

DELETE方法是请求服务器删除请求URL所指定的资源



**拓展方法**

WebDAV HTTP扩展

**LOCK**允许用户锁定资源，防止别人同时对其进行修改

**MKCOL**允许用户创建资源

**COPY**便于在服务器上复制资源

**MOVE**在服务器上移动资源

注意：如果一台服务器要与HTTP 1.1兼容，只要为其资源实现GET方法和HEAD方法就可以了

**请求URL**

命名了所请求的资源，或者URL路径组件的完整URL，一般是服务器的绝对路径

**版本**

报文所使用的HTTP版本，主要版本号和次要版本号

HTTP/\<major\>.\<minor\>

**请求首部**

见后文

**请求报文主体部分**

实体的主体部分包含任意数据的数据块。可以省略

## 响应报文

响应报文将请求的结果返回客户端

response message 响应报文的组成：

```
<version> <status> <reason-phrase>
<headers>

<entity-body>

例子
HTTP/1.0 200 OK
Content-Type: image/gif
Content-Length: 8888

(二进制的图片流...)
```

**版本**

见请求报文

### 状态码

状态码为客户端提供了一种理解事务处理结果的便捷方式。

三位数字描述了请求过程中发生的情况，状态码的第一位数字描述一般类别

HTTP状态码被分成了五大类

**100-199信息提示**

100 - Continue 

101 - Switching Protocols

**200-299成功**

200 - OK  成功

201 - Created

202 - Accepted

203 - Non-Authoritative Information

204 - No Content

205 - Reset Content

206 - Partial Content

**300-399重定向表示资源已经被移走了**

300 - Multiple Choices

301 - Moved Permanently

302 - Found

303 - See Other

304 - Not Modified

305 - Use Proxy

307 - Temporary Redirect

**400-499客户端错误**

400 - Bad Request

401 - Unauthorized（未授权）  需要输入用户名和密码

402 - Payment Required

403 - Forbidden

404 - Not Found（未找到）  找不到文件或目录

405 - Method Not Allowed

406 - Not Acceptable

407 - Proxy Authentication Required

408 - Request Timeout

409 - Conflict

410 - Gone

411 - Length Required

412 - Precondition Failed

413 - Request Entity Too Large

414 - Request URI Too Long

415 - Unsupported Media Type

416 - Requested Range Not Satisfiable

417 - Expectation Failed

**500-599服务器错误**

500 - Internal Server Error  内部服务器错误

501 - Not Implemented  无法实现

502 - Bad Gateway

503 - Service Unavailable

504 - Gateway Timeout

505 - HTTP Version Not Supported

**原因短语**

原因短语和状态码总是成对出现，是数字状态码的可读版本，只对人类有意义

**响应首部**

主要内容见下面

**响应报文主体部分**

见后文

## 首部

首部和方法配合工作，共同决定了客户端和服务器能做什么事情

可以有零个或多个首部，每个首部都包含一个名字，后面跟着一个冒号，然后是一个可选的空格，接着是一个值，最后是一个CRLF。首部最后有一个空行CRLF结束，和实体主体隔开。有些版本要求有效的请求或响应报文中必须含有特定的首部

首部可以分成以下几类：通用首部，请求首部，响应首部，实体首部，扩展首部

```
首部延续行，可以提高可读性，多出来行前面要有一个空格或tab
Server: Test Server
	Version 1.0
等价于
Server: Test Server Version 1.0
```



**通用首部**

客户端和服务器都可以使用的首部

```
通用的信息性首部
Connection
Date
MIME-Version
Trailer
Transfer-Encoding
Update
Via
通用缓存首部
Cache-Control
Pragma
```



**请求首部**

```
请求信息首部
Client-IP
From
Host 给出了接收请求的服务器的主机名和端口号
Referer
UA-Color
UA-CPU
UA-Disp
UA-OS
UA-Pixels
User-Agent 将发起请求的应用程序名称告知服务器
Accept首部
Accept
Accept-Charset
Accept-Encoding
Accept-Language
TE
条件请求首部
Expect
If-Match
If-Modified-Since
If-None-Match
If-Range
If-Unmodified-Since
Range
安全请求首部
Authorization
Cookie
Cookie2
代理请求首部
Max-Forward
Proxy-Authorization
Proxy-Connection
```



**响应首部**

```
响应信息首部
Age
Public
Retry-After
Server
Title
Warning
协商首部
Accept-Ranges
Vary
安全响应首部
Proxy-Authenticate
Set-Cookie
Set-Cookie2
WWW-Authenticate
```



**实体首部**

```
实体信息首部
Allow
Location
内容首部
Content-Base
Content-Encoding
Content-Language
Content-Length
Content-Location
Content-MD5
Content-Range
Content-Type
实体缓存首部
ETag
Expires
Last-Modified
```



**扩展首部**

```

```







Content-Type说明主体是什么，MIME类型

Content-Length主体的长度



## 主体部分

主体部分就是HTTP要传输的内容，图片 视频 HTML文档 软件应用程序 信用卡事务 电子邮件





# 英语单词

guides 指南

redirect 重新寄送 再直接的 在直接询问 重定向

handler 处理者 管理者 处理程序

clipper 大剪刀 剪削者 理发剪 斩波器 截波器 限制器



# 链接

[RFC 2616](https://www.w3.org/Protocols/rfc2616/rfc2616.html)

[RFC 2616 HTTP/1.1 ietf](https://www.ietf.org/rfc/rfc2616.txt)

百度搜索"rfc 2616"

[HTTP指南  腾讯云开发者文档](https://cloud.tencent.com/developer/section/1189824)



# 参考书目

《HTTP权威指南》[美]David Gourley   Brian Totty   Marjorie Sayer   Sailu Reddy   Anshu Aggarwal著 人民邮电出版社 ISBN 978-7-115-28148-7

[运行实例：Joe的五金商店](http://joes-hardware.com)

这本书的附录有丰富的MIME类型，MIME国际字符集，各国语言缩写代码

还有URL编码还没补齐全，以后学爬虫再写吧


















