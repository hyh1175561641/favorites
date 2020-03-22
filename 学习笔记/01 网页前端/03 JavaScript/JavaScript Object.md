





[TOC]



# JavaScript对象

本篇文档继续写JavaScript对象



# BOM



### window对象

[window对象](https://www.runoob.com/jsref/obj-window.html)

window对象表示浏览器中打开的窗口

注意：如果文档包含框架iframe，浏览器会为HTML文档创建一个window对象，并为每个框架创建一个额外的window对象

```javascript
属性
closed//返回窗口是否被关闭
defaultStatus//设置或返回窗口状态栏中的默认文本
document//对Document对象的只读引用
frames//
history//
innerHeight//
innerWidth//
localStorage//
length//
location//
name//
navigator//
opener//
outerHeight//
outerWidth//
pageXOffset//
pageYOffset//
parent//
screen//
screenLeft//
screenTop//
screenX//
sessionStorage//
screenY//
self//
status//
top//

方法
alert()//显示带有一段消息和一个确认按钮的警告框
atob()//解码一个base-64编码的字符串
btoa()//创建一个base-64编码的字符串
blur()//把键盘焦点从顶层窗口移开
clearInterval()//取消由setInterval()设置的timeout
clearTimeout()//取消由setTimeout()方法设置的timeout
close()//关闭浏览器窗口
confirm()//显示带有一段消息以及确认和取消的对话框
createPopup()//创建一个pop-up窗口
focus()//把键盘焦点给予一个窗口
getSelection()//返回一个Selection对象，表示用户选择的文本范围或光标的当前位置
getComputedStyle()//获取指定元素的CSS样式
matchMedia()//
moveBy()//可相对窗口的当前坐标把它移动指定的像素
moveTo()//把窗口的左上角移动到一个指定的坐标
open()//打开一个新的浏览器窗口或查找一个已命名的窗口
print()//打印当前窗口的内容
prompt()//显示可提示用户输入的对话框
resizeBy()//按照指定的像素调整窗口的大小
resizeTo()//把窗口的大小调整到指定的宽度和高度
scrollBy()//按照指定的像素值来滚动内容
scrollTo()//把内容滚动到指定的坐标
setInterval()//在指定的周期（以毫秒记）来调用函数或计算表达式
setTimeout()//在指定的毫秒数后调用函数或计算表达式
stop()//停止页面载入
```





### Navigator对象

Navigator对象包含有关浏览器的信息

```javascript
属性
appCodeName//返回浏览器的代码名
appName//返回浏览器的名称
appVersion//返回浏览器的平台和版本信息
cookieEnabled//返回指明浏览器中是否启用cookie的布尔值
platform//返回运行浏览器的操作系统平台
userAgent//返回由客户端发送服务器的user-agent头部的值

方法
javaEnabled()//指定是否在浏览器中启用Java
taintEnabled()//规定浏览器是否启用数据污点
```



### Screen对象

Screen对象包含有关客户端显示屏幕的信息

```javascript
属性
availHeight//返回屏幕的高度(不包括Windows任务栏)
availWidth//返回屏幕的宽度(不包括Windows任务栏)
colorDepth//返回目标设备或缓存器上的调色板的比特深度
height//返回屏幕的总高度
pixelDepth//返回屏幕的颜色分辨率(每像素的位数)
width//返回屏幕的总宽度
```





### History对象

History对象包含用户(在浏览器窗口中)访问过的URL

History对象是window对象的一部分，可通过window.history属性对其进行访问

```javascript
属性
length//返回历史列表中的网址数

方法
back()//加载history列表中的前一个URL
forward()//加载history列表中的下一个URL
go()//加载history列表中的某个具体页面
```





### Location对象

Location对象包含有关当前URL的信息

Location对象是window对象的一部分，可通过window.location属性对其进行访问

```javascript
属性
hash//返回一个URL的锚部分
host//返回一个URL的主机名和端口
hostname//返回URL的主机名
href//返回完整的URL
pathname//返回URL的路径名
port//返回一个URL服务器使用的端口号
protocol//返回一个URL协议
search//返回一个URL的查询部分

方法
assign()//载入一个新的文档
reload()//重新载入当前文档
replace()//用新的文档替换当前文档
```



### 存储对象

Web 存储 API 提供了 sessionStorage （会话存储） 和 localStorage（本地存储）两个存储对象来对网页的数据进行添加、删除、修改、查询操作。

- localStorage 用于长久保存整个网站的数据，保存的数据没有过期时间，直到手动去除。
- sessionStorage 用于临时保存同一窗口(或标签页)的数据，在关闭窗口或标签页之后将会删除这些数据。

```javascript
属性
length//返回存储对象中包含多少条数据

方法
key()//返回存储对象中第N个键的名称
getItem()//返回指定键的值
setItem()//添加键和值，如果对应的值存在，则更新该键对应的值
removeItem()//移除键
clear()//清除存储对象中所有的键
```





[runoobHTML教程的存储内容](https://www.runoob.com/html/html5-webstorage.html)

[还有HTML数据库](https://www.runoob.com/html/html5-web-sql.html)

[HTML应用程序缓存](https://www.runoob.com/html/html5-app-cache.html)

[web workers](https://www.runoob.com/html/html5-webworkers.html)

[HTML服务器发送事件](https://www.runoob.com/html/html5-serversentevents.html)

[HTMLwebsocket](https://www.runoob.com/html/html5-websocket.html)




# DOM

通过DOM可以访问JavaScript HTML文档的所有元素，当网页被加载时，浏览器会创建页面的文档对象模型（Document Object Model）。文档模型是一个对象的树。JavaScript获得了足够的能力来创建动态的HTML。能够改变所有的HTML元素，属性，CSS样式，对所有事件做出反应。

可以通过id，标签名，类名找到HTML元素。



DOM中立于平台和语言接口，允许程序和脚本动态地访问和更新文档内容、结构和样式。可以访问HTML和XML



HTML文档中所有内容都是节点：整个文档是一个文档节点，每个 HTML 元素是元素节点，HTML 元素内的文本是文本节点，每个 HTML 属性是属性节点，注释是注释节点



### Document对象

```javascript
var x = document.getElementById("main")
var y = x.getElementByTagName("p")
var x = document.getElementsByClassName("intro")
```



```javascript
document.activeElement//返回当前获取焦点元素
document.addEventListener()
document.adoptNode(node)
document.anchors
document.baseURI
document.body
document.close()
document.
document.
document.
document.
document.
document.
document.
document.
document.
document.
document.
document.
document.
document.
document.
document.
document.
document.
document.
document.
```





### 元素对象



### 属性对象



### 事件对象



### Console对象

```javascript
Console.assert()//如果断言为false，则在信息到控制台输出错误信息
Console.clear()//清除控制台的信息
Console.count()//记录count的调用次数，一般用于计数
Console.error()//输出错误信息到控制台
Console.group()//在控制台创建一个信息分组
Console.groupCollapsed()//在控制台创建一个信息分组，但默认是可折叠的，类似group()
Console.groupEnd()//设置当前信息分组结束
Console.info()//控制台输出一条信息
Console.log()//控制台输出一条信息
Console.table()//以表格形式显示数据
Console.time()//计时器，开始计时间，与timeEnd联合使用
Console.timeEnd()//计时结束
Console.trace()//显示当前执行代码在堆栈中的调用路径
Console.warn()//输出警告信息
```







### CSSStyleDeclaration对象



### HTMLCollection对象



# 