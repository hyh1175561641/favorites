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


[TOC]

# HTML

## 根标签
`<!DOCTYPE>,<html>,<head>,<body>,<!--...-->`


## 头部标签,元数据

`<head>,<meta>,<link>,<title>,<base>,<basefont>`


## 样式
`<style>,<div>,<span>`

## 基础标签

### 内容大纲
`<header>,<footer>,<section>,<article>,<aside>,<address>,<details>,<dialog>,<summary>,<h1-h6>,<hgroup>,<main>,<nav>`


### 文本格式
`,<br>,<hr>,<p>`

### 链接
`<a>`
锚点[4种锚点方法](https://blog.csdn.net/this_ITBoy/article/details/76020658)

### 表单
`<form>,<input>,<textarea>,<button>,<select>,<optgroup>,<option>,<label>,<fieldset>,<legend>,<isindex>,<datalist>,<keygen>,<output>`

### 列表

```html
<ol type="有序列表"
    start
    reversed
    ></ol>
<ul type="无序列表"></ul>
<li type="列表项"></li>
<dl 定义列表：一前一后的一种样式></dl>
<dt 定义列表的项目></dt>
<dd 定义列表的描述></dd>
```

### 表格



```html

<table border="15px(宽度)"
       frame
       rules
       summary
       width
       cellspacing
       cellpadding
       align用样式替代
       bgcolor用样式替代
       ></table>
<tr align="对齐方式"
    bgcolor="用样式代替"
    char
    charoff
    valign
    ></tr>
<th abbr
    align
    axis
    bgcolor
    char
    charoff
    colspan
    headers
    height
    nowrap
    rowspan
    scope
    valign
    width
    ></th>
<td 同th标签></td>


<caption><thead><tbody><tfoot><col><colgroup>


```
```html
<table border="1">
	<tr>
  	<th></th>
  	<th></th>
  </tr>
  <tr>
  	<td></td>
    <td></td>
  </tr>
</table>
```

## 框架
`<frame>,<frameset>,<noframes>,<iframe>`

## 图像
`<img>,<map>,<area>,<canvas>,<figcaption>,<figure>`

```html
<img alt="必须属性" src="必须属性" height,width,
     ismap,
     longdesc,
     vspace>
```
图像无法显示时用alt属性值替代图片

## 媒体
`<audio>,<source>,<track>,<video>`

## 编程脚本

`<script>,<noscript>,<applet>,<embed>,<object>,<param>`

见`./网页_html.md`

## 全局属性

```html
<tag title="鼠标悬停显示的内容"></tag>
```
title属性鼠标悬停时显示此段文字”是\<form\>\<a\>元素的常用属性

## 事件

## 其他






# 其他

### 长度单位
**绝对长度**

1. px像素
2. cm厘米，mm毫米
3. in英寸(=96px)
4. pt  (72pt=1in)
5. pc (=12pt)

**相对长度**
1. em (=16px默认值)适应于当前字体尺寸
2. % 百分号 适应于当前字体的百分比
3. ex 适应于当前字体字母x的高度
3. ch 数字0的宽度
4. rem 根元素\<html\>的font-size
5. vw 浏览器宽度的1%
6. vh 浏览器高度的1%
7. vmin 浏览器宽和高较小的那个的1%
8. vmax 浏览器宽和高较大的那个的1%



### SEO三大标签

```html
<title>这里写标题（百度28个字）</title>
<meta name="description" content="这里写描述(不超过120个汉字)" />
<meta name="Ketwords" content="这里写关键字（限制在6~8个词左右）" />
```
- description是搜索结果的简述



###  ico图标

放在根目录底下

```html
<link rel="shortcut icon" href="favicon.ico" type="image/x-icon"/>
<!-- http://www.jd.com/favicon.ico --> 
```





ico制作网站www.bitbug.net


# 具体实例

## 组成网页的基本元件

导航栏
```html

```


轮播图
```html

```




# 书籍翻阅记录

## 《HTML5权威指南》[美]Adam Freeman 人民邮电出版社 IBSN 978-7-115-33836-5

## 《HTML5与CSS3权威指南》 陆凌牛 机械工业出版社 IBSN 978-7-111-51442-8



# 链接：

htmlcss基础
[w3cschool](https://www.w3school.com.cn)

[runoob](https://www.runoob.com)

[MDN Web 文档](https://developer.mozilla.org/zh-CN/docs/Web/HTML)

前端工具



其他

[前端文档汇总](https://blog.csdn.net/qq_39197547/article/details/82789464)