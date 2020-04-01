## 





[TOC]



# 简介

jQuery 是一个 JavaScript 库。

jQuery 极大地简化了 JavaScript 编程。

目前jQuery兼容于所有主流浏览器, 包括Internet Explorer 6!

## 下载

可以通过多种方法在网页中添加 jQuery。 您可以使用以下方法：

从 [jquery.com](http://jquery.com/download/) 下载 jQuery 库

从 CDN 中载入 jQuery, 如从 Google 中加载 jQuery

[官网下载方法](https://jquery.com/download/)

两个版本，一个精简压缩，一个未压缩

- Production version - 用于实际的网站中，已被精简和压缩。
- Development version - 用于测试和开发（未压缩，是可读的代码）

## 配置



```html
本地引用
<head>
<script src="jquery-1.10.2.min.js"></script>
</head>

CDN（内容分发网络）
<head>
<script src="https://code.jquery.com/jquery-3.4.1.js"></script>
</head>

百度CDN
<head>
<script src="https://apps.bdimg.com/libs/jquery/2.1.4/jquery.min.js">
</script>
</head>
```

**使用 Staticfile CDN、百度、又拍云、新浪、谷歌或微软的 jQuery，有一个很大的优势：**

许多用户在访问其他站点时，已经从百度、又拍云、新浪、谷歌或微软加载过 jQuery。所以结果是，当他们访问您的站点时，会从缓存中加载 jQuery，这样可以减少加载时间。同时，大多数 CDN 都可以确保当用户向其请求文件时，会从离用户最近的服务器上返回响应，这样也可以提高加载速度。



## 其他

在浏览器输入$.fn.jquery查看版本

# 基础操作

jQuery库包含以下功能：

- HTML 元素选取
- HTML 元素操作
- CSS 操作
- HTML 事件函数
- JavaScript 特效和动画
- HTML DOM 遍历和修改
- AJAX
- Utilities

## 选择器

jQuery 选择器基于元素的 id、类、类型、属性、属性值等"查找"（或选择）HTML 元素。 它基于已经存在的 CSS 选择器

```javascript
$("*")通配符选择器
$(this)当前HTML元素
$("p")标签选择器
$("#id")id选择器
$(".class")类选择器
$("[href]")属性选择器
$(":buttom")选取所有 type="button"的<input>元素和<button>元素
```





## 事件

页面对不同访问者的响应叫做事件。

```javascript
//鼠标事件
click()
dblclick()
mouseenter()
mouseleave()
hover()


//键盘事件
keypress()
keydown()
keyup()


//表单事件
submit()
change()
focus()
blur()

//文档事件
load()
resize()
scroll()
unload()

//窗口事件
```



## 效果

```javascript
//基本


//滑动

//淡入淡出

//自定义

//设置
```











# 单词

# 实战

[imooc项目](https://www.imooc.com/video/8983)

# 链接

[官网](https://jquery.com)

[官网文档](https://api.jquery.com)

[其他文档查询](http://jquery.cuishifeng.cn)

[runoob教程](https://www.runoob.com/jquery/jquery-tutorial.html)