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



# 简介
## 历史

1. 1995年JavaScript诞生，最初命名为LiveScript，由Brendan Eich(布兰克·艾登)发明，用时十天，在网景导航者浏览器上首次实现。JavaScript最初用来验证输入的表单。
2. 竞争对手为微软的VBScript后改名为JScript。
3. 1997年，ECMA（欧洲计算机制造商协会）将其标准化，重新命名为ECMAScript，用的最多的名字还是JavaScript。
4. 截至 2012 年，所有浏览器都完整的支持ECMAScript 5.1，旧版本的浏览器至少支持ECMAScript 3 标准。
5. 2015年6月17日，ECMA国际组织发布了ECMAScript 的第六版，该版本正式名称为 ECMAScript 2015，但通常被称为ECMAScript 6 或者ES6。
6. 一般es6指的是，2015年之后的所有版本。



## 简介

JavaScript是脚本语言，浏览器读取代码时，逐行地执行脚本代码。

对于传统编程来说，会在执行前对所有代码进行编译。



## 运行环境



## 开发环境



## 在HTML中使用

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

# 基本语法

**标识符**
1. 区分大小写，避免冲撞关键字。
2. 第一个字符是字母，下划线\_，美元符号$或数字。
3. 第一个后面的字符是字母，下划线，美元符号$或数字。
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


**字面量**

固定的值称为字面量。比如数字，字符串，`5+6`，数组，对象，函数

**变量**

变量是用于储存数据值

- 修改变量值的同时也可以改变值的类型，但是不推荐改变值的类型。

**初始化多个变量**

初始化多个变量，用逗号分开：

```javascript
var message = "hi",
    found = false,
    age = 29;
```


**严格模式**
```javascript
function doSomething(){
	"use strict";
	//函数体
}
//严格模式下，JavaScript的执行结果会有很大不同
```

**关键字**



**字符集**

JavaScript使用Unicode字符集

## 数据类型

**创建变量**

用`var`关键词声明变量，用等号向变量赋值。

可以用逗号声明或赋值多个变量

```javascript
var name="Doe",age,gender=1;
```

**typeof操作符**
typeof操作符检测给定变量的数据类型，返回某个字符串：
`undefined` `boolean` `string` `number` `object` `function`
总共有6种可能的值。

1. typeof的操作数可以是变量也可以是数值字面量。
2. typeof是一个操作符而不是函数，圆括号可有可无。
3. 调用typeof null会返回"object"，因为特殊值null被认为是一个空的对象引用。

```javascript
typeof "John"// 返回 string
typeof 3.14// 返回 number
typeof NaN// 返回 number
typeof false// 返回 boolean
typeof [1,2,3,4]// 返回 object
typeof {name:'John', age:34}// 返回 object
typeof new Date()// 返回 object
typeof function(){}// 返回 function
typeof myCar// 返回 undefined (如果 myCar 没有声明)
typeof null// 返回 object
```



### Undefined

undefined是一个没有设置值的变量

未初始化的变量保存值`undefined`

任何变量都可以通过设置值为undefined来清空

一个不存在的变量，变量名拼写错误也是undefined

```javascript
//未声明的变量可以typeof，但不可以使用
var age;//声明但是未初始化
alert(age);//undefined
alert(ageee);//产生错误
typeof age;//undefined
typeof ageee;//undefined
```



### Null

null是一个只有一个值的特殊类型，表示“什么都没有”，表示一个空对象引用（空对象指针）。

```javascript
//null和undefined的值相等，但类型不相等
typeof undefined //undefined
typeof null //object
null === undefined //false
null == undefined //true
```

如果定义的变量将来用于保存对象，那么最好初始化为null



### boolean布尔值

布尔类型只能有两个值：true或false。都是小写

Boolean()函数，可以将任何数据类型转换为Boolean值

各种类型的值转换为Boolean值，true和false

|Boolean|ture|false|
|----|----|----|
|String|任何非空字符串|空字符串|
|Number|任何非零数字值（包括无穷大）|0和NaN|
|Object|任何对象|null|
|Undefined|n/a|undefined|

n/a(或N/A)是not applicable的缩写，意思是”不适用“


### number数值

**整数**

```javascript
var intNum=34;//十进制
var octalNum=070;//八进制
var octalNum1=079;//如果超出0-7，解析为十进制79
var x3=0xA;//十六进制
```

八进制在严格模式下是无效的

进行算术计算时，八进制和十六进制表示的数值都转换成十进制数值

**小数**

```javascript
var floatNum = 34.00;
var floatNum = 123e5;//12300000
```

浮点数值的最高精度是17位小数

小数采用的是基于IEEE754方案

**数值范围**

-Infinity负无穷

Infinity正无穷

**NaN**

NaN，即非数值（Not a Number）是一个特殊的值，

**Number对象**

```javascript
对象
constructor//返回对创建此对象的Number函数的引用
MAX_VALUE//可表示的最大的数
MIN_VALUE//可表示的最小的数
NEGATIVE_INFINITY//负无穷大，溢出时返回该值
POSITIVE_INFINITY//正无穷大，溢出时返回该值
NaN//非数字值
prototype//允许您可以向对象添加属性和方法

方法
isFinite()//检测指定参数是否为无穷大
toExponential()//把对象的值转换为指数计数法
toFixed()//把数字转换为字符串，结果的小数点后有指定位的数字
toPrecision()//把数字格式化为指定的长度
toString()//把数字转化为字符串，使用指定的基数
valueOf()//返回一个Number对象的基本数字值
```





### string字符串

```javascript
//字符串是储存字符的变量，可以是单双引号中的任意文本
var name='Bill Gates';
var name="Bill Gates";

//在使用引号时，避免引号冲突
var answer = "It's alright";
var answer = 'He is called "Johnny"';

//可以在文本字符串中使用反斜杠进行换行
document.write("你好\
世界！");
```

如果对数值使用引号，该值会被当做文本来处理

**字符串的使用**

```javascript
//使用索引位置来访问字符串中的每个字符
var name = "Bill Gates";
var character = name[5];//G

//可以使用转义字符
var answer = 'It\'s alright'
var answer = "He is called \"Johnny\""
//字符串中可使用的转义字符有 \' \" \\ \n \r \t \b \f

//字符串的长度
var txt = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
var sln = txt.length;
```



**字符串对象**

```javascript
//通常的字符串是原始值，可使用字符创建：var firstName = "John"
//也可以使用new关键字将字符串定义为一个对象：var first = new String("John")
//不要创建String对象，会拖慢执行速度
var x = "John";//typeof x //String
var y = new String("John");//typeof y //Object
(x === y) //false,因为x是字符串，y是对象
```



```javascript
//String对象的属性和方法
//String对象属性
String.constructor//对创建该对象的函数的引用
String.lenght//字符串的长度
String.prototype//允许您向对象添加属性和方法

//String对象方法
String.charAt()//返回在指定位置的字符
String.charCodeAt()//返回在指定的位置的字符的Unicode编码
String.concat()//连接两个或更多字符串，并返回新的字符串
String.fromCharCode()//将Unicode编码转为字符
String.indexOf()//返回某个指定的字符串值在字符串中首次出现的位置
String.includes()//查找字符串中是否包含指定的子字符串
String.lastIndexOf()//从后向前搜索字符串，并从起始位置（0）开始计算返回字符串最后出现的位置
String.match()//查找找到一个或多个正则表达式的匹配
String.repeat()//复制字符串指定次数，并将它们连接在一起返回
String.replace()//在字符串中查找匹配的子串， 并替换与正则表达式匹配的子串

String.search()//查找与正则表达式相匹配的值
String.slice()//提取字符串的片断，并在新的字符串中返回被提取的部分
String.split()//把字符串分割为字符串数组
String.startsWith()//查看字符串是否以指定的子字符串开头
String.substr()//从起始索引号提取字符串中指定数目的字符
String.substring()//提取字符串中两个指定的索引号之间的字符
String.toLowerCase()//把字符串转换为小写
String.toUpperCase()//把字符串转换为大写
String.trim()//去除字符串两边的空白
String.toLocaleLowerCase()//根据本地主机的语言环境把字符串转换为小写

String.toLocaleUpperCase()//根据本地主机的语言环境把字符串转换为大写
String.valueOf()//返回某个字符串对象的原始值
String.toString()//返回一个字符串

//String HTML 包装方法
//HTML返回包含在相对应的HTML标签中的内容
String.anchor()//创建 HTML 锚。
String.big()//用大号字体显示字符串。
String.blink()//显示闪动字符串。
String.bold()//使用粗体显示字符串。
String.fixed()//以打字机文本显示字符串。
String.fontcolor()//使用指定的颜色来显示字符串。
String.fontsize()//使用指定的尺寸来显示字符串。
String.italics()//使用斜体显示字符串。
String.link()//将字符串显示为链接。
String.small()//使用小字号来显示字符串。
String.strike()//用于显示加删除线的字符串。
String.sub()//把字符串显示为下标。
String.sup()//把字符串显示为上标。
```





### object对象



### function函数

**代码**：按照编写顺序依次执行的每条语句

**代码块**：可以一并地执行语句序列

**函数**：函数是由事件驱动的或当它被调用时执行的可重复使用的代码块。问题来了，函数是由事件驱动的这是什么意思，什么是事件驱动？百度JavaScript事件驱动机制。

```javascript
//函数包裹在花括号里，前面使用关键词function
function functionname(){
  //执行代码
}

//调用函数时，可以传递参数，必须以一致的顺序出现
function myFunction(name, job){
  alert("Welcome" + name + ", the " + job);
}//Welcome Harry Potter, the Wizard
myFunction('Harry Potter','Wizard');

//带有返回值的函数，使用return语句时，函数会停止，返回指定值
function myFunction(){
  var x=5;
  return x;//返回值5
}
var myVar = myFunction();//函数调用将被返回值取代
```



## 引用数据类型

引用类型写在这里有些靠前，不过凑合吧

```javascript
//可以使用关键词"new"声明其类型，JavaScript变量均为对象，声明一个变量时，就创建了一个新的对象？？？？？？这句话对吗？皆为对象吗
var carname = new String;
var x = new Number;
var y = new Boolean;
var cars = new Array;
var person = new Object;
```



### Object对象

```javascript
//对象由花括号分隔。在对象内部，对象的属性以名称和值对的形式来定义
var person = {firstname:"John", lastname:"Doe", id:5566};

//可以折行
var person = {
  firstname:"John",
  lastname:"Doe",
  id:5566
};

//访问对象属性
name = person.lastname;
name = person["lastname"];

//对象定义了一个函数，并作为对象的属性储存
var person = {
  firstname:"John",
  lastname:"Doe",
  id:5566,
  fullName: function(){
    return this.firstName + "" + this.lastName();
  }
};

//调用对象函数，如果访问对象的属性，则返回字符串
name = person.fullName();//John Doe
name = person.fullName;//function(){return this.firstName + "" + this.lastName();}
```





### Array数组

```javascript
//创建数组
var cars = new Array();
cars[0]="Saab";
cars[1]="Volvo";
cars[2]="BMW";
var cars2 = new Array("Saab","Volov","BMW");
var cars=["Saab","Volvo","BMW"];//简写
```



### RegExp正则表达式

正则表达式，在代码中常简写为regex、regexp、RE。使用单个字符串来描述、匹配一系列符合某个句法规则的字符串搜索模式

[以后慢慢看](https://www.runoob.com/js/js-regexp.html)



### Date日期

```javascript
Date.getDate()//从Date对象返回一个月中的某一天(1~31)
Date.getDay()//从Date对象返回一周中的某一天(0~6)
Date.getFullYear()//从Date对象以四位数字返回年份
Date.getHours()//返回Date对象的小时(0~23)
Date.getMilliseconds()//返回Date对象的毫秒(0~999)
Date.getMinutes()//返回Date对象的分钟(0~59)
Date.getMonth()//从Date对象返回月份(0~11)
Date.getSeconds()//返回Date对象的秒数(0~59)
Date.getTime()	返回//1970年1月1日至今的毫秒数
```



### Math数学





### 类型转换

```javascript
//判断数据类型，由于typeof 数组返回是object类型，所以这种方法无法判断数组类型

//constructor属性返回所有JavaScript变量的构造函数
"John".constructor//返回函数String(){[native code]}
(3.14).constructor//返回函数Number(){[native code]}
false.constructor//返回函数Boolean(){[native code]}
[1,2,3,4].constructor//返回函数Array(){[native code]}
{name:'John', age:34}.constructor//返回函数Object(){[native code]}
new Date().constructor//返回函数Date(){[native code]}
function () {}.constructor//返回函数Function(){[native code]}

//使用construction属性来检查对象是否为数组
var fruits = ["Banana", "Orange", "Apple", "Mango"];
document.getElementById("demo").innerHTML = isArray(fruits);
function isArray(myArray) {
    return myArray.constructor.toString().indexOf("Array") > -1;
}//true
```

[以后再看吧](https://www.runoob.com/js/js-type-conversion.html)



## 操作符

算术运算符，赋值运算符，字符串连接运算符，比较运算符，逻辑运算符，条件运算符

```javascript
//算术运算符
+加法
-减法
*乘法
/除法
%取模
++自增
--自减

//赋值运算符
=赋值
+=等同于 x+=y x=x+y
-=等同于 x-=y x=x-y
*=等同于 x*=y x=x*y
/=等同于 x/=y x=x/y
%=等同于 x%=y x=x%y

//字符串+运算符
text1 = "What a very";
text2 = "nice day";
text3 = text1 + text2;//What a verynice day
text4 = text1 + " " + text2;//What a very nice day
//如果其中有一个数字，把数字变成字符串，再进行拼接
x = 5 + 5;//10
y = "5" + 5;//55
z = "Hello" + 5;//Hello5

//比较运算符，计算结果是true或者false
==等于
===绝对等于（值和类型都相等）
!=不等于
!==不绝对等于（值和类型至少有一个不相等）
>大于
<小于
>=大于或等于
<=小于或等于

//逻辑运算符
&& and
|| or
! not

//条件运算符
A?B:C

//位运算符
& AND
| OR
~ 取反
^ 异或
<< 左移
>> 右移
```



## 语句

通常在每条可执行的语句结尾添加分号;或者在一行中编写多条语句;

### if...Else语句

条件语句基于不同的条件来执行不同的动作

```javascript
//if语句，只有当指定条件是true时，使用该语句来执行代码
if(condition){
  //条件为true时执行的代码
}

//if...else语句,只有条件为true时执行代码，条件为false时执行其他代码
if(condition){
  //条件为true时执行的代码
}else{
  //条件不为true时执行的代码
}

//if...else if...else语句，该语句选择多个代码块之一来执行
if(condition1){
  //条件1为true时执行的代码
}else if(condition2){
  //条件2为true时执行的代码
}else{
  //当条件1和条件2都不为true时执行的代码
}
```

### switch语句

基于不同的条件来执行不同的动作


```javascript
//switch语句，该语句来选择多个代码块之一来执行
switch(n){//首先设置表达式n，然后与下面每一个case语句相比较，如果匹配则执行代码
  case 1:
    1;
    break;//使用break组织代码自动的向下一个case执行
  case 2:
    2;
    break;
  default://default匹配不存在时做的事情
    0;
}
```

### for循环

循环可以将代码块执行指定的次数

```javascript
for(var i=0;i<10;i++){//初始化语句；判断语句；更新语句
  //语句循环10次
}

//循环遍历对象的属性
var person = {fname:"Bill", lname:"Gates", age:56};
for(x in person){
  txt = txt + person[x];
}
```



### while循环

只要指定条件为true，循环就可以一直执行代码块

```javascript
while(i<5){
  //只要变量小于5，循环一直进行
}

do{
  //在检查条件是否为真之前，先执行一次代码
}
while(i<5);
```



### break和continue语句

break语句跳出循环，continue用于跳过循环的一个迭代

```javascript
//break跳出switch()语句
//break可以跳出循环
for(i=0;i<10;i++){
  if(i==3){break;}
  x = x + "The number is " + i + "<br>";
}//i等于3之后都没有

//continue中断循环中的迭代，然后继续循环下一个迭代
for(i=0;i<10;i++){
  if(i==3){continue;}
  x = x + "The number is " + i + "<br>";
}//i等于3跳过了

//label标签
label:statements
break labelname;//跳出有标签的代码块
continue labelname;
```




## 作用域

作用域是可访问变量的集合，在JavaScript中，对象和函数同样也是变量

```javascript
//函数作用域，变量在函数内部声明，变量为局部作用域，只能在函数内部访问，执行完毕自动销毁
function myFunction(){
  var carName = "Volvo";//内部可以调用
}//外部不能访问

//全局变量，变量在函数外定义，网页中所有脚本和函数均可以使用
var carName = "Volvo";//外部可以调用
function myFunction(){
  //内部可以调用
}
//如果变量在函数内没有声明，该变量为全局变量
function myFunction(){
  carName = "Volvo";
}

//变量的生命周期在它声明时初始化，局部变量在函数执行完毕后销毁，全局变量在页面关闭后销毁
//函数参数只在函数内起作用，是局部变量
```




1. `message="hi";//全局变量` 省略var操作符，变量会变成全局变量，但不推荐使用
2. 如果把值赋给尚未声明的变量，这会作为一个window属性，`carname="Volvo"`这将声明window的一个属性carname
3. 在HTML中，全局变量是window对象，所有数据变量都属于window对象[runoob 作用域](https://www.runoob.com/js/js-scope.html)

```javascript
//这个东西搞不懂，以后慢慢琢磨
日期2020-02-11

//非严格模式下给未声明变量赋值创建的全局变量，是全局对象的可配置属性，可以删除。
var var1 = 1; // 不可配置全局属性
var2 = 2; // 没有使用 var 声明，可配置全局属性

console.log(this.var1); // 1
console.log(window.var1); // 1

delete var1; // false 无法删除
console.log(var1); //1

delete var2; 
console.log(delete var2); // true
console.log(var2); // 已经删除 报错变量未定义
```







## 面向对象







## 异常



### Error对象





# Canvas绘图



# 地理定位

[runoob地理定位](https://www.runoob.com/html/html5-geolocation.html)

# 对JavaScript的总结

JavaScript能够改变文档内容，对网页行为进行编程

1. ECMAScript：描述了该语言的语法和基本对象。
2. DOM(文档对象模型)：描述了处理网页内容的方法和接口。是针对XML但经过拓展用于HTML的应用程序编程接口。W3C制定
3. BOM(浏览器对象模型)：描述了浏览器进行交互的方法和接口。
   



# New Word

Identifier Expected 期望标识符

Type Identifier Expected 缺类型标识符

DOM:Document Object Model 

API:Application Programming Interface 接口 

W3C:World Wide Web Consortium 万维网联盟




# 书籍翻阅记录

《JavaScript高级程序设计（第3版）》[美]Nicholas C.Zakas 著 李松峰 曹力 译 人民邮电出版社 ISBN 978-7-115-27579-0
[随书源码](http://www.wrox.com/WileyCDA/WroxTitle/Professional-JavaScript-for-Web-Developers-3rd-Edition.productCd-1118026691,descCd-DOWNLOAD.html)

[Professional JavaScript for Web Developers, 3rd Edition - Wrox](http://www.wrox.com/WileyCDA/WroxTitle/Professional-JavaScript-for-Web-Developers-3rd-Edition.productCd-1118026691.html) 

[Professional JavaScript for Web Developers, 3rd Edition - Wrox](http://www.wrox.com/WileyCDA/WroxTitle/Professional-JavaScript-for-Web-Developers-3rd-Edition.productCd-1118026691,descCd-DOWNLOAD.html) 






# 链接

[runoob](https://www.runoob.com/js/js-tutorial.html)

[runoob js参考手册](https://www.runoob.com/jsref/jsref-tutorial.html)





# 框架

swiper