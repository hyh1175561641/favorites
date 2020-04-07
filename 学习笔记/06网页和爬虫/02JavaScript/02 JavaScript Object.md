





[TOC]



# JavaScript对象

本篇文档继续写JavaScript对象



# BOM



## window对象

[window对象](https://www.runoob.com/jsref/obj-window.html)

window对象表示浏览器中打开的窗口

注意：如果文档包含框架iframe，浏览器会为HTML文档创建一个window对象，并为每个框架创建一个额外的window对象
```javascript
属性
document//对Document对象的只读引用
history//对History对象的只读引用
location//用于窗口或框架的Location对象
navigator//对Navigator对象的只读引用
screen//对Screen对象的只读引用



closed//返回窗口是否被关闭
defaultStatus//设置或返回窗口状态栏中的默认文本
frames//
innerHeight//
innerWidth//
localStorage//
length//
name//
opener//
outerHeight//
outerWidth//
pageXOffset//
pageYOffset//
parent//
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





## Navigator对象

Navigator对象包含有关浏览器的信息

```javascript
属性
navigator.appCodeName//返回浏览器的代码名
navigator.appName//返回浏览器的名称
navigator.appVersion//返回浏览器的平台和版本信息
navigator.cookieEnabled//返回指明浏览器中是否启用cookie的布尔值
navigator.platform//返回运行浏览器的操作系统平台
navigator.userAgent//返回由客户端发送服务器的user-agent头部的值

方法
navigator.javaEnabled()//指定是否在浏览器中启用Java
navigator.taintEnabled()//规定浏览器是否启用数据污点
```



## Screen对象

Screen对象包含有关客户端显示屏幕的信息

```javascript
属性
screen.availHeight//返回屏幕的高度(不包括Windows任务栏)
screen.availWidth//返回屏幕的宽度(不包括Windows任务栏)
screen.colorDepth//返回目标设备或缓存器上的调色板的比特深度
screen.height//返回屏幕的总高度
screen.pixelDepth//返回屏幕的颜色分辨率(每像素的位数)
screen.width//返回屏幕的总宽度
```





## History对象

History对象包含用户(在浏览器窗口中)访问过的URL

History对象是window对象的一部分，可通过window.history属性对其进行访问

```javascript
属性
history.length//返回历史列表中的网址数

方法
history.back()//加载history列表中的前一个URL
history.forward()//加载history列表中的下一个URL
history.go()//加载history列表中的某个具体页面
```





## Location对象

Location对象包含有关当前URL的信息

Location对象是window对象的一部分，可通过window.location属性对其进行访问

```javascript
属性
location.hash//返回一个URL的锚部分
location.host//返回一个URL的主机名和端口
location.hostname//返回URL的主机名
location.href//返回完整的URL
location.pathname//返回URL的路径名
location.port//返回一个URL服务器使用的端口号
location.protocol//返回一个URL协议
location.search//返回一个URL的查询部分

方法
location.assign()//载入一个新的文档
location.reload()//重新载入当前文档
location.replace()//用新的文档替换当前文档
```



## 存储对象

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





# DOM概念



通过DOM可以访问JavaScript HTML文档的所有元素，当网页被加载时，浏览器会创建页面的文档对象模型（Document Object Model）。

文档模型是一个对象的树。JavaScript获得了足够的能力来创建动态的HTML。能够改变所有的HTML元素，属性，CSS样式，对所有事件做出反应。

可以通过id，标签名，类名找到HTML元素。

W3C DOM 标准被分为 3 个不同的部分：

- 核心 DOM - 针对任何结构化文档的标准模型
- XML DOM - 针对 XML 文档的标准模型
- HTML DOM - 针对 HTML 文档的标准模型

DOM中立于平台和语言接口，允许程序和脚本动态地访问和更新文档内容、结构和样式。是访问HTML和XML的编程接口

HTML文档中所有内容都是节点：整个文档是一个文档节点，每个 HTML 元素是元素节点，HTML 元素内的文本是文本节点，每个 HTML 属性是属性节点，注释是注释节点

## HTML DOM节点树

文档下根元素html

- 整个文档是一个文档节点
- 每个 HTML 元素是元素节点
- HTML 元素内的文本是文本节点，可以通过innerHTML 属性来访问文本节点的值
- 每个 HTML 属性是属性节点
- 注释是注释节点

节点父、子和兄弟

节点树中的节点彼此拥有层级关系。

我们常用**父（parent）**、**子（child）**和**同胞（sibling）**等术语来描述这些关系。父节点拥有子节点。同级的子节点被称为同胞（兄弟或姐妹）。

- 在节点树中，顶端节点被称为根（root）。
- 每个节点都有父节点、除了根（它没有父节点）。
- 一个节点可拥有任意数量的子节点。
- 同胞是拥有相同父节点的节点。











inner 内部的，内心的，精神的

# JavaScript DOM

## Document对象

[Document对象属性和方法 runoob](https://www.runoob.com/jsref/dom-obj-document.html)

```javascript
var x = document.getElementById("main")
var y = x.getElementByTagName("p")
var x = document.getElementsByClassName("intro")
```



```javascript
常用方法：
var 选择文档中的元素
document.getElementsByClassName() 	返回文档中所有指定类名的元素集合，作为 NodeList 对象。
document.getElementById() 	返回对拥有指定 id 的第一个对象的引用。
document.getElementsByTagName() 	返回带有指定标签名的对象集合。
document.getElementsByName() 	返回name属性的标签，不常用



document.activeElement 	返回当前获取焦点元素
document.addEventListener() 	向文档添加句柄
document.adoptNode(node) 	从另外一个文档返回 adapded 节点到当前文档。
document.anchors 	返回对文档中所有 Anchor 对象的引用。
document.applets 	返回对文档中所有 Applet 对象的引用。注意: HTML5 已不支持 <applet> 元素。
document.baseURI 	返回文档的绝对基础 URI
document.body 	返回文档的body元素
document.close() 	关闭用 document.open() 方法打开的输出流，并显示选定的数据。
document.cookie 	设置或返回与当前文档有关的所有 cookie。
document.createAttribute() 	创建一个属性节点
document.createComment() 	createComment() 方法可创建注释节点。
document.createDocumentFragment() 	创建空的 DocumentFragment 对象，并返回此对象。
document.createElement() 	创建元素节点。
document.createTextNode() 	创建文本节点。
document.doctype 	返回与文档相关的文档类型声明 (DTD)。
document.documentElement 	返回文档的根节点
document.documentMode 	返回用于通过浏览器渲染文档的模式
document.documentURI 	设置或返回文档的位置
document.domain 	返回当前文档的域名。
document.domConfig 	已废弃。返回 normalizeDocument() 被调用时所使用的配置。
document.embeds 	返回文档中所有嵌入的内容（embed）集合
document.forms 	返回对文档中所有 Form 对象引用。
document.images 	返回对文档中所有 Image 对象引用。
document.implementation 	返回处理该文档的 DOMImplementation 对象。
document.importNode() 	把一个节点从另一个文档复制到该文档以便应用。
document.inputEncoding 	返回用于文档的编码方式（在解析时）。
document.lastModified 	返回文档被最后修改的日期和时间。
document.links 	返回对文档中所有 Area 和 Link 对象引用。
document.normalize() 	删除空文本节点，并连接相邻节点
document.normalizeDocument() 	删除空文本节点，并连接相邻节点的
document.open() 	打开一个流，以收集来自任何 document.write() 或 document.writeln() 方法的输出。
document.querySelector() 	返回文档中匹配指定的CSS选择器的第一元素
document.querySelectorAll() 是 HTML5中引入的新方法，返回文档中匹配的CSS选择器的所有元素节点列表
document.readyState 	返回文档状态 (载入中……)
document.referrer 	返回载入当前文档的文档的 URL。
document.removeEventListener() 	移除文档中的事件句柄(由 addEventListener() 方法添加)
document.renameNode() 	重命名元素或者属性节点。
document.scripts 	返回页面中所有脚本的集合。
document.strictErrorChecking 	设置或返回是否强制进行错误检查。
document.title 	返回当前文档的标题。
document.URL 	返回文档完整的URL
document.write() 	向文档写 HTML 表达式 或 JavaScript 代码。
document.writeln() 	等同于 write() 方法，不同的是在每个表达式之后写一个换行符。


警告 !!!
在 W3C DOM核心，文档对象 继承节点对象的所有属性和方法。
很多属性和方法在文档中是没有意义的。
HTML 文档对象可以避免使用这些节点对象和属性：

  属性      方法 	      避免的原因
document.attributes 	文档没有该属性
document.hasAttributes() 	文档没有该属性
document.nextSibling 	文档没有下一节点
document.nodeName 	这个通常是 #document
document.nodeType 	这个通常是 9(DOCUMENT_NODE)
document.nodeValue 	文档没有一个节点值
document.ownerDocument 	文档没有主文档
document.ownerElement 	文档没有自己的节点
document.parentNode 	文档没有父节点
document.previousSibling 	文档没有兄弟节点
document.textContent 	文档没有文本节点
```





## 元素对象

[元素对象 runoob](https://www.runoob.com/jsref/dom-obj-all.html)

```js






element.accessKey 	设置或返回accesskey一个元素
element.addEventListener() 	向指定元素添加事件句柄
element.appendChild() 	为元素添加一个新的子元素
element.attributes 	返回一个元素的属性数组
element.childNodes 	返回元素的一个子节点的数组
element.children 	返回元素的子元素的集合
element.classList 	返回元素的类名，作为 DOMTokenList 对象。
element.className 	设置或返回元素的class属性
element.clientHeight 	在页面上返回内容的可视高度（不包括边框，边距或滚动条）
element.clientWidth 	在页面上返回内容的可视宽度（不包括边框，边距或滚动条）
element.cloneNode() 	克隆某个元素
element.compareDocumentPosition() 	比较两个元素的文档位置。
element.contentEditable 	设置或返回元素的内容是否可编辑
element.dir 	设置或返回一个元素中的文本方向
element.firstChild 	返回元素的第一个子节点
element.focus() 	设置文档或元素获取焦点
element.getAttribute() 	返回指定元素的属性值
element.getAttributeNode() 	返回指定属性节点
element.getElementsByTagName() 	返回指定标签名的所有子元素集合。
element. getElementsByClassName() 	返回文档中所有指定类名的元素集合，作为 NodeList 对象。
element.getFeature() 	返回指定特征的执行APIs对象。
element.getUserData() 	返回一个元素中关联键值的对象。
element.hasAttribute() 	如果元素中存在指定的属性返回 true，否则返回false。
element.hasAttributes() 	如果元素有任何属性返回true，否则返回false。
element.hasChildNodes() 	返回一个元素是否具有任何子元素
element.hasFocus() 	返回布尔值，检测文档或元素是否获取焦点
element.id 	设置或者返回元素的 id。
element.innerHTML 	设置或者返回元素的内容。
element.insertBefore() 	现有的子元素之前插入一个新的子元素
element.isContentEditable 	如果元素内容可编辑返回 true，否则返回false
element.isDefaultNamespace() 	如果指定了namespaceURI 返回 true，否则返回 false。
element.isEqualNode() 	检查两个元素是否相等
element.isSameNode() 	检查两个元素所有有相同节点。
element.isSupported() 	如果在元素中支持指定特征返回 true。
element.lang 	设置或者返回一个元素的语言。
element.lastChild 	返回的最后一个子节点
element.namespaceURI 	返回命名空间的 URI。
element.nextSibling 	返回该元素紧跟的一个节点
element.nextElementSibling 	返回指定元素之后的下一个兄弟元素（相同节点树层中的下一个元素节点）。
element.nodeName 	返回元素的标记名（大写）
element.nodeType 	返回元素的节点类型
element.nodeValue 	返回元素的节点值
element.normalize() 	使得此成为一个"normal"的形式，其中只有结构（如元素，注释，处理指令，CDATA节和实体引用）隔开Text节点，即元素（包括属性）下面的所有文本节点，既没有相邻的文本节点也没有空的文本节点
element.offsetHeight 	返回任何一个元素的高度包括边框和填充，但不是边距
element.offsetWidth 	返回元素的宽度，包括边框和填充，但不是边距
element.offsetLeft 	返回当前元素的相对水平偏移位置的偏移容器
element.offsetParent 	返回元素的偏移容器
element.offsetTop 	返回当前元素的相对垂直偏移位置的偏移容器
element.ownerDocument 	返回元素的根元素（文档对象）
element.parentNode 	返回元素的父节点
element.previousSibling 	返回某个元素紧接之前元素
element.previousElementSibling 	返回指定元素的前一个兄弟元素（相同节点树层中的前一个元素节点）。
element.querySelector() 	返回匹配指定 CSS 选择器元素的第一个子元素
document.querySelectorAll() 	返回匹配指定 CSS 选择器元素的所有子元素节点列表
element.removeAttribute() 	从元素中删除指定的属性
element.removeAttributeNode() 	删除指定属性节点并返回移除后的节点。
element.removeChild() 	删除一个子元素
element.removeEventListener() 	移除由 addEventListener() 方法添加的事件句柄
element.replaceChild() 	替换一个子元素
element.scrollHeight 	返回整个元素的高度（包括带滚动条的隐蔽的地方）
element.scrollLeft 	返回当前视图中的实际元素的左边缘和左边缘之间的距离
element.scrollTop 	返回当前视图中的实际元素的顶部边缘和顶部边缘之间的距离
element.scrollWidth 	返回元素的整个宽度（包括带滚动条的隐蔽的地方）
element.setAttribute() 	设置或者改变指定属性并指定值。
element.setAttributeNode() 	设置或者改变指定属性节点。
element.setIdAttribute() 	
element.setIdAttributeNode() 	
element.setUserData() 	在元素中为指定键值关联对象。
element.style 	设置或返回元素的样式属性
element.tabIndex 	设置或返回元素的标签顺序。
element.tagName 	作为一个字符串返回某个元素的标记名（大写）
element.textContent 	设置或返回一个节点和它的文本内容
element.title 	设置或返回元素的title属性
element.toString() 	一个元素转换成字符串
nodelist.item() 	返回某个元素基于文档树的索引
nodelist.length 	返回节点列表的节点数目。
```



## 属性对象

```js


attr.isId 	如果属性是 ID 类型，则 isId 属性返回 true，否则返回 false。
attr.name 	返回属性名称
attr.value 	设置或者返回属性值
attr.specified 	如果属性被指定返回 true ，否则返回 false
  	 
nodemap.getNamedItem() 	从节点列表中返回的指定属性节点。
nodemap.item() 	返回节点列表中处于指定索引号的节点。
nodemap.length 	返回节点列表的节点数目。
nodemap.removeNamedItem() 	删除指定属性节点
nodemap.setNamedItem() 	设置指定属性节点(通过名称)


```



## 事件对象

[续写事件对象](https://www.runoob.com/tags/ref-eventattributes.html)

```javascript
// ## 窗口事件属性 Window Event Attributes


```

```javascript
// ## 表单事件 Form Events
```

```javascript
// ## 键盘事件 Keyboard Events
onkeydown() 按下按键
onkeypress() 按下并松开按键
onkeyup() 松开按键
```

```javascript
// ## 鼠标事件 Mouse Events
onclick() 单击鼠标
ondblclick() 双击鼠标

onmousedown() 鼠标按下
onmouseup() 鼠标松开

 //over(在上面)只触发一次  move(移动)只要移动就不停触发
onmouseout() 鼠标移出
onmouseover() 鼠标悬浮

onmousemove() 鼠标移动
onmouseenter()
onmouseleave()

oncontextmenu() 鼠标右键触发并打开上下文


//HTML5：
ondrag() 拖动
ondragend() 拖动结束
ondragenter() 
ondragleave()
ondragover()
ondragstart()
ondrop() 

onmousewheel() 鼠标滚轮
onscroll() 滚动元素的滚条
```

```javascript
// ## 多媒体事件 Media Events
```

```javascript
// ## 其他事件
```

```javascript

```

```javascript

```

```javascript

```





## Console对象

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







## CSSStyleDeclaration对象

```js





```



## HTMLCollection对象



# 









