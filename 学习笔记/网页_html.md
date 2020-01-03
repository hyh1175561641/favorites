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
`<ul>,<ol>,<li>,<dir>,<dl>,<dt>,<dd>,<menu>,<menuitem>,<command>`

### 表格
`<table>,<caption>,<th>,<tr>,<td>,<thead>,<tbody>,<tfoot>,<col>,<colgroup>`

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


### 颜色

**三原色法则**

>255，0，0 红色
>0，255，0 绿色
>0，0，255 蓝色
>255，255，0 黄色
>0，255，255 青色
>255，0，255 紫色
>靠左红 靠右蓝 中间绿 左中黄 右中青 两边紫
>红橙黄绿青蓝紫


**表示法**

1. red颜色名字
2. rgb(x,x,x)  十进制
3. rgba(x,x,x,alpha) 透明度
4. rgb(x%,x%,x%)  百分之几
5. #rrggbb  十六进制
6. hsl(hue,saturation,lightness)
7. hsla(h,s,l,a)

注：Hue 是色盘上的度数（从 0 到 360） - 0 (或 360) 是红色，120 是绿色，240 是蓝色。Saturation 是百分比值；0% 意味着灰色，而 100% 是全彩。Lightness 同样是百分比值；0% 是黑色，100% 是白色。

**常用颜色名**

1. aqua(浅绿)
2. black
3. blue
4. fuchsia
5. gray(灰)
6. green
7. lime(绿黄)
8. maroon
9. navy
10. olive
11. orange
12. purple
13. red
14. silver
15. teal(蓝绿色)
16. white
17. yellow
18. brown(棕色)
19. pink
20. indigo(靛青)
21. cyan(蓝绿)
22. sand(沙色)
23. khaki(卡其色)
24. amber(琥珀色)

**常用色彩搭配**
五色之变不可胜观

### 字体

Font&Typeface：font是指某套具有同样样式、尺寸的字形；typeface则是一或多个font在一或多个尺寸的集合。
字体样式：有衬线(Serif)，大量文字内容区域。无衬线(Sans Serif)，标题，醒目的区域。等宽字体(Monospace)，显示代码。
字形：常规体(regular)，细体(light)，粗体(bold)，斜体(italic)，黑体(black)
字体类型：TureType&OpenType.（OpenType更强大，遇到时特别标注）

**常用字体名称**

通用字体:

"Times" 泰晤士报首次采用，之后博得大众青睐(times.ttc,times.ttf)
"Time New Roman" 可以使用"Times"替代 (times.ttf) OpenType
"Courier"  世界上最知名的字形
"Courier New"  常用于代码显示，可以使用"Courier"替代 (cour.ttf) OpenType

其他常见的字体：黑体 宋体 新宋体 仿宋 楷体 华文黑体 华文楷体 华文宋体 隶书 幼圆 Verdana Tahoma

Windows 10:

"Arial"  Microsoft Monotype 无衬线(arial.ttf) OpenType

"SimSun"  中易宋体(simsun.ttc) OpenType
"MingLiu"  细明体 华康科技(mingliu.ttc) TrueType
"Microsoft Yahei UI"  微软雅黑 无衬线黑体 方正版权(msyh.ttc) OpenType
"Microsoft Yahei UI Bold"  微软雅黑Bold 无衬线黑体 方正版权(msyhbd.ttc) OpenType
"Microsoft Yahei UI Light"  微软雅黑Light 无衬线黑体 方正版权(msyhl.ttc) OpenType



MacOS:

"Helvetica"  Apple(Helvetica.ttc) TrueType  Helvetica是苹果电脑的默认字体，与微软常用的Arial字体相似

Hiragino Sans GB 冬青黑体 苹果电脑默认字体(Hiragino Sans GB.ttc) OpenType PostScript
"STSong"  华文宋体(Songti.ttc) TrueType



Linux:



字体特征和用法：

1. Georgia,Times New Roman属于Serif(有衬线)字体。
2. Arial,Tahoma,Verdana,属于Sans Serif(无衬线)字体。
3. 宋体，细明体属于有衬线字体
4. 黑体，幼圆体属于无衬线字体
5. 正文Serif，标题Sans Serif。
6. font-family默认采用Tahoma. Tahoma是英文Windows操作系统的默认字体，这个字体比较均衡，显示中英文混排很不错，是经久耐看的一款字体。
7. Mac OS X系统有一款比Tahoma更典雅的系统默认字体：Helvetica，非Mac系统的Helvetica字体都是Rip版。
8. Arial是早期Windows英文系统的默认字体，XP和Vista上都是Tahoma。
9. 最后的sans-serif是针对强悍的Linux DIY族。Linux默认只有kernel，字体完全由用户自定义，针对这部分用户，sans-serif可能能派上用场。
10. 最后，无论在XP还是Vista下，不指定网页的中文字体时，默认就是宋体。因此font-family里的'宋体'是多余的，可以省去。
11. [百度搜索"Serif和Sans-serif字体的区别"](baidu.com)



**常见字体公司**
Microsoft：美国微软公司(Microsoft Corporation)
Apple：美国苹果电脑公司(Apple Computer, Inc.)
Monotype：蒙纳字体(The Monotype Corporation)
中易：北京中易中标电子信息技术有限公司(Beijing ZhongYi Electronics,Co.)
北大方正 Founder ：北京北大方正电子有限公司(Beijing Founder Electronics Co.,Ltd.)
华文SinoType：M州华文印刷新科技有限公司(Changzhou SinoType Technology Co.,Ltd.)
华康科技DynaComware：（今名“威锋数位”）(DynaComware Corp.)
蒙纳香港Monotype：(Monotype Hong Kong Ltd. and Monotype Imaging Inc.)
Diwan：英国Diwan公司(Diwan Science and Information Technology Ltd.)

**New Word**

- bold  黑体的，大胆的，厚颜无耻的，英勇的
- condensed  浓缩的，扼要的，窄体
- regular  定期的，整齐的，普通的，经常的
- italic  斜体的，斜体字
- expanded  扩体，展开的
- monospace 等宽，等宽字体，单间隔，单间隔字体

**链接**
[如何选择字体(font-family)](https://blog.csdn.net/SmCai/article/details/86304808)


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





# 链接：

htmlcss基础
[w3cschool](https://www.w3school.com.cn)

[runoob](https://www.runoob.com)

[MDN Web 文档](https://developer.mozilla.org/zh-CN/docs/Web/HTML)

前端工具



其他

[前端文档汇总](https://blog.csdn.net/qq_39197547/article/details/82789464)