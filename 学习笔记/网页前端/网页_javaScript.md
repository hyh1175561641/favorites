# 本篇笔记如何使用？

**内容记录**

* 主要记录不常用的功能，常用知识为节省版面可以不记
* 标题下关键字
* 写代码的经验，可以记例子
* 容易出错或经常被遗忘的点
* 技巧，妙用
* 学到的英文单词
* 链接



**标记规范**

```markdown

# 标题（#）
**关键字** **关键字** **关键字**
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

[TOC]

# JavaScript

## 简介
### 历史

1. 1995年JavaScript诞生，最初命名为LiveScript，由Brendan Eich(布兰克·艾登)发明，用时十天，在网景导航者浏览器上首次实现。JavaScript最初用来验证输入的表单。
2. 竞争对手为微软的VBScript后改名为JScript。
3. 1997年，ECMA（欧洲计算机制造商协会）将其标准化，重新命名为ECMAScript，用的最多的名字还是JavaScript。
4. 截至 2012 年，所有浏览器都完整的支持ECMAScript 5.1，旧版本的浏览器至少支持ECMAScript 3 标准。
5. 2015年6月17日，ECMA国际组织发布了ECMAScript 的第六版，该版本正式名称为 ECMAScript 2015，但通常被称为ECMAScript 6 或者ES6。
6. 一般es6指的是，2015年之后的所有版本。

### 作用

能够改变文档内容，对网页行为进行编程

### 组成
1. ECMAScript：描述了该语言的语法和基本对象。
2. DOM(文档对象模型)：描述了处理网页内容的方法和接口。是针对XML但经过拓展用于HTML的应用程序编程接口。W3C制定
3. BOM(浏览器对象模型)：描述了浏览器进行交互的方法和接口。

**New Word**
DOM:Document Object Model
API:Application Programming Interface 接口
W3C:World Wide Web Consortium 万维网联盟

### HTML中使用JavaScript

```html
<script type="脚本的MIME类型（必选属性）text/javascript"
        language="JavaScript 用type代替 废弃"
        charset="UTF-8 外部脚本使用的字符编码 浏览器经常忽略 不常用"
        src="外部脚本文件"
        async="async 脚本异步执行 仅适用外部脚本(使用src属性时)"
        defer="延迟脚本执行，直到页面加载为止 外部脚本"
        ></script>
<!--如果元素内部的代码没有位于某个函数中，那么这些代码会在页面被加载时被立即执行-->

<noscript>如果浏览器不支持脚本，此内容将替代</noscript>
```

多种执行外部脚本的方法：
1. 如果 async="async"：脚本相对于页面的其余部分异步地执行（当页面继续进行解析时，脚本将被执行）。
2. 如果不使用 async 且 defer="defer"：脚本将在页面完成解析时执行。
3. 如果既不使用 async 也不使用 defer：在浏览器继续解析页面之前，立即读取并执行脚本。
4. 如果您的脚本不会改变文档的内容，可将 defer 属性加入到 \<script\> 标签中，以便加快处理文档的速度。因为浏览器知道它将能够安全地读取文档的剩余部分而不用执行脚本，它将推迟对脚本的解释，直到文档已经显示给用户为止。





- 浏览器从上往下解析，写在上面的script最先被读取
- script可以写在head标签内，可以在body标签内，可以在body标签之后
- head头部的link和script src=。。。先读取完成才会加载body内容，延长页面的加载时间
- script标签写在body里面，页面在完全加载之前就先显示
- script写在body下边，浏览器自动会解析到body标签里最后一个元素

## 基本语法

**标识符**
1. 区分大小写，避免冲撞关键字。
2. 第一个字符是字母，下划线\_，美元符号$或数字。
3. 第一个后面的字符是字母，下划线，美元符号或数字。
4. 标识符的字母也可以包含“拓展的ASCII”或Unicode字母字符，不推荐这样。
5. ECMAScript语言风格建议使用驼峰大小写格式，首字母小写，剩下单词首字母大写。

**注释**
```javascript
//单行注释

/*
* 这是多行注释
* （块级）注释
*/
```

**严格模式**
```javascript
function doSomething(){
	"use strict";
	//函数体
}
//严格模式下，JavaScript的执行结果会有很大不同
```

**语句**
以分号结尾


**New Word**
Identifier Expected 期望标识符
Type Identifier Expected 缺类型标识符

### 数据类型

**变量**
关键字var  变量名message  = 值;
`var message="Happy birthday";`


1. 未初始化的变量保存值`undefined`。
2. 修改变量值的同时也可以改变值的类型，但是不推荐改变值的类型。

**初始化多个变量**

初始化多个变量，用逗号分开：

```javascript
var message = "hi",
    found = false,
    age = 29;
```



**typeof操作符**
typeof操作符检测给定变量的数据类型，返回某个字符串：
`undefined``boolean``string``number``object``function`
总共有6种可能的值。
1. typeof的操作数可以是变量也可以是数值字面量。
2. typeof是一个操作符而不是函数，圆括号可有可无。
3. 调用typeof null会返回"object"，因为特殊值null被认为是一个空的对象引用。

**New Word**

- numeric literal 数值文字，数值字面量



**Undefined未定义**

声明了变量，但是未赋值



**Null**





**boolean布尔值**





**number数值**





**string字符串**





**object对象**





### 操作符





### 语句



### 函数



### 作用域


1. `var message="hi";//局部变量` var操作符定义的变量将成为定义该变量的作用域中的局部变量，函数退出值被销毁。
2. `message="hi";//全局变量` 省略var操作符，变量会变成全局变量，但不推荐使用



### 引用类型







## 面向对象







## 函数表达式







## BOM




## DOM








# 书籍翻阅记录

## 《JavaScript高级程序设计（第3版）》[美]Nicholas C.Zakas 著 李松峰 曹力 译 人民邮电出版社 ISBN 978-7-115-27579-0
[随书源码](http://www.wrox.com/WileyCDA/WroxTitle/Professional-JavaScript-for-Web-Developers-3rd-Edition.productCd-1118026691,descCd-DOWNLOAD.html)

[Professional JavaScript for Web Developers, 3rd Edition - Wrox](http://www.wrox.com/WileyCDA/WroxTitle/Professional-JavaScript-for-Web-Developers-3rd-Edition.productCd-1118026691.html) 

[Professional JavaScript for Web Developers, 3rd Edition - Wrox](http://www.wrox.com/WileyCDA/WroxTitle/Professional-JavaScript-for-Web-Developers-3rd-Edition.productCd-1118026691,descCd-DOWNLOAD.html) 

1.1 1.2

3.1.* 3.3 3.4 3.4.1 




# 链接



# 框架

swiper