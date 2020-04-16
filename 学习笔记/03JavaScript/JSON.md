



[TOC]



# 简介

JSON(JavaScript Object Notation) 对象表示法。是一种轻量级的数据交换格式,它基于JavaScript的一个子集,易于人的编写和阅读,也易于机器解析。独立于语言和平台。JSON 解析器和 JSON 库支持许多不同的编程语言。 目前非常多的动态（PHP，JSP，.NET）编程语言都支持JSON。

与XML相似之处：都是纯文本，自我描述，层级结构，可以通过js进行解析，可使用ajax进行传输

与XML不同之处：没有结束标签，更短，读写更快，可使用内建eval()进行解析，使用数组，不使用保留字



# 历史

JSON 格式最初是由 Douglas Crockford 制定的



# 配置







# 语法

## JSON的值可以是：

- 数字（整数或浮点数）
- 字符串（在双引号中）
- 逻辑值（true或false）
- 对象（在花括号中）
- 数组（在方括号中）
- null



## 名称/值

```json
"age":33,//数字
"firstname":"john",//字符串
"male":true,//逻辑值
"zero":null//null
```
```javascript
等价于JavaScript语句
age=33
firstname=”john
male=true
zero=null
```



## JSON对象

```json
{"firstName":"John","lastName":"Doe"}//对象
```

```javascript
等价于JavaScript语句
firstName="John"
lastName="Doe"
```



## JSON数组

```json
["Porsche","BMW","Volvo"]//数组
{
  "employess":[
    {"firstName":"John","lastName":"Doe"},
    {"firstName":"Anna","lastName":"Smith"},
    {"firstName":"Peter","lastName":"Jones"}
  ]
}//数组
```

```javascript
等价于JavaScript语句
var employees = [
  {"firstName":"John","lastName":"Doe"},
  {"firstName":"Anna","lastName":"Smith"},
  {"firstName":"Peter","lastName":"Jones"}
];
//> employees[0].lastName;
//> Doe
```



## JSON文件

- JSON文件的文件类型是".json"
- JSON文本的MIME类型是"application/json"



## JSON转换和解析

JavaScript函数eval()可以将JSON文本转换为JavaScript对象

```javascript
var txt = '{ "employees" : [' +
'{ "firstName":"Bill" , "lastName":"Gates" },' +
'{ "firstName":"George" , "lastName":"Bush" },' +
'{ "firstName":"Thomas" , "lastName":"Carter" } ]}';

eval() 函数使用的是 JavaScript 编译器，可解析 JSON 文本，然后生成 JavaScript 对象。必须把文本包围在括号中，这样才能避免语法错误：

var obj = eval( "(" + txt + ")" );//转换，内建函数，使用的是JavaScript编译器
```

```javascript
使用 JSON 解析器将 JSON 转换为 JavaScript 对象是更安全的做法。JSON 解析器只能识别 JSON 文本，而不会编译脚本。

var obj = JSON.parse(txt);//解析，把JSON字符串转换成JavaScript对象
```

```javascript
var obj={ name:"Bill Gates", age:62, city:"Seattle"};
var myJSON = JSON.stringify(obj)//把JavaScript对象转换成字符串
```



转换和解析的区别：JSON 解析器的速度更快。eval()可编译并执行任何 JavaScript 代码，这是潜在的安全问题。而JSON.parse()只能识别文本，不会编译脚本，使用起来更安全



# 其他

```json
有时间翻译一下这个内容
JSON = null
    or true or false
    or JSONNumber
    or JSONString
    or JSONObject
    or JSONArray

JSONNumber = - PositiveNumber
          or PositiveNumber
PositiveNumber = DecimalNumber
              or DecimalNumber . Digits
              or DecimalNumber . Digits ExponentPart
              or DecimalNumber ExponentPart
DecimalNumber = 0
             or OneToNine Digits
ExponentPart = e Exponent
            or E Exponent
Exponent = Digits
        or + Digits
        or - Digits
Digits = Digit
      or Digits Digit
Digit = 0 through 9
OneToNine = 1 through 9

JSONString = ""
          or " StringCharacters "
StringCharacters = StringCharacter
                or StringCharacters StringCharacter
StringCharacter = any character
                  except " or \ or U+0000 through U+001F
               or EscapeSequence
EscapeSequence = \" or \/ or \\ or \b or \f or \n or \r or \t
              or \u HexDigit HexDigit HexDigit HexDigit
HexDigit = 0 through 9
        or A through F
        or a through f

JSONObject = { }
          or { Members }
Members = JSONString : JSON
       or Members , JSONString : JSON

JSONArray = [ ]
         or [ ArrayElements ]
ArrayElements = JSON
             or ArrayElements , JSON
```



# 链接

[JSON官网](https://www.json.org/json-en.html)

[W3school JSON](https://www.w3school.com.cn/json/index.asp)

[runoob JSON](https://www.runoob.com/json/json-tutorial.html)

[MDN_JSON文档](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON)

工具：

[runoob JSON在线解析工具](https://c.runoob.com/front-end/53)