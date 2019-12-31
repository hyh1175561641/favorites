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



# CSS

## 外部样式

``````css
<link rel="stylesheet" herf="css/index.css">
@charset "utf-8";/* 如果css文件有中文，设置字符集*/
``````

## 选择器
### 选择器权重
1. 下面选择器由权重由轻到重排序
2. 写在后面的选择器覆盖前面的选择器
3. 通配符选择器<标签选择器<类选择器<属性选择器<id选择器(单个选择器)
4. id名字只能出现一次，犹如身份证号

### 测试实例
```html
<!-- h.html -->
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <link rel="stylesheet" href="c.css">
	<title></title>
  <style>
    *{
      width:100px;
      height:100px;
    }
    div{
      background-color:#001;
    }
    .box{
      background-color:#002;
    }
    [name=one]{
      background-color:#003;
    }
    #zoo{
      background-color:#004;
    }
    
    
  </style>
</head>
<body>
  <div class="box" id="zoo" name="one" style="background-color:reed;"></div>
</body>
</html>
```


```css
/*c.css*/
div{
  background-color:#005;
}
.box{
  background-color:#006;
}
[name=one]{
  background-color:#007;
}
#zoo{
  background-color:#008;
}
```

### 组合选择器
后代选择器，用空格键隔开，
子元素选择器，用>隔开，不可跨代
兄弟选择器，用~隔开，只能选择下面的兄弟(所有兄弟)
邻居选择器，用+隔开，选择下边第一个邻居
选择器分组，用,隔开，设置共同的样式

## 基本样式

### 尺寸

```css
div{
	height:100px;
	width:100px;
	max-height:100px;
	max-width:100px;
	min-height:100px;
	min-width:100px;
}

```

### 背景

```css
div{
	background:red;/*复合样式*/
	background-color:red;
  background-position-x:0%;
  background-position-y:0%;
  background-repeat: repeat;
  background-attachment:scroll;
  background-image:none;
  background-size:auto;
  background-orgin:padding-box;
  background-clip:border-box;
}
```

### 文本
```css
p{
color:;/*文本颜色*/
direction:ltr,rtl;/*文本阅读方向，向右对齐，标点符号反了，字的顺序没变*/
line-height:normal,15px,%,数字(与当前数字相乘);/*行高*/
letter-spacing:normal,10px;/*字母间隔，可取负值*/
text-align:left,right,center;/*水平对齐，还有一个justify不常用值*/
text-decoration:none,overline,line-through,
  underline,blink;/*文本一条线修饰，可以多个值同时使用*/
	a{text-decoration: none;}
text-indent:50px,50%;/*文本缩进，可负值*/
text-shadow:;/**/
text-transform:none,uppercase,lowercase,capitalize;/*大小写转换*/
unicode-bidi:;/**/
white-space:normal/*默认值，合并空白符成一个，忽略换行符*//*处理空白符，空格、换行和 tab 字符*/
						pre/*空白被保留，类似<pre>标签*/
						nowrap/*文本不换行*/
						pre-wrap/*空白符保留，换行符保留*/
						pre-line;/*合并空白符，换行符保留*/
word-spacing:normal,10px;/*字（单词）间隔，可取负值，单词之间间距为5px*/
vertical-align:;/**/
}
```
1. text-indent:注意：一般来说，可以为所有块级元素应用 text-indent，但无法将该属性应用于行内元素，图像之类的替换元素上也无法应用 text-indent 属性。不过，如果一个块级元素（比如段落）的首行中有一个图像，它会随该行的其余文本移动。
   提示：如果想把一个行内元素的第一行“缩进”，可以用左内边距或外边距创造这种效果

2. white-space:

   | 值       | 空白符 | 换行符 | 自动换行 |
   | :------- | :----- | :----- | :------- |
   | pre-line | 合并   | 保留   | 允许     |
   | normal   | 合并   | 忽略   | 允许     |
   | nowrap   | 合并   | 忽略   | 不允许   |
   | pre      | 保留   | 保留   | 不允许   |
   | pre-wrap | 保留   | 保留   | 允许     |

   

### 字体

```css
p{
font:;
	font-style:normal,italic,oblique;/*斜体*/
	font-weight:normal/*粗细*/
							bold/*粗体*/
							bolder/*更粗的字体*/
							lighter/*更细的字体*/
							100-900/*400等同于normal，700等同于bold*/;
	font-stretch:normal;/**/
	line-height:normal;/*行高*/
	font-size:medium 16px,small 13px,large 18px,x-small 10px,/*大小*/
						x-large 24px,xx-small 9px,xx-large 32px/*7个级别，绝对大小值*/
						smaller/*比父元素更小，相对大小值*/
						larger/*比父元素更大，相对大小值*/
						16px/*固定单位大小*/
						100%/*百分比大小*/;
	font-size-adjust:none;/**/
	font-family:"行楷-简";/*字体系列，两个单词用引号括起来*/
	font-variant:normal,small-caps;/*字母异性*/
		font-variant-caps:normal;
		font-variant-alternates:normal;
		font-variant-east-asian:normal;
		font-variant-ligatures:normal;
		font-variant-numeric:normal;
		font-variant-position:normal;
		font-vatiant-settings:normal;
font-kerning:auto;/**/
font-optical-sizing:auto;/**/
font-language-override:normal;/**/
font-feature-settings:normal;/**/
}

```
1. italic让文字斜体，oblique使没有斜体属性的文字倾斜（通过计算得到）（不太支持）
2. Serif(有衬线)，大量文字内容区域。Sans Serif(无衬线)，标题，醒目的区域。

### 链接

```css
div{
target:;
	target-name:;
	target-new:;
	target-position:;
}
```

### 列表

```css
div{
list-style:;
	list-style-image:;
	list-style-position:;
	list-style-type:;
}
```

### 表格

```css
div{
border-collapse:;
border-spacing:;
caption-side:;
empty-cells:;
table-layout:;
}
```



## 盒子模型

### 边框
```css
div{
border:;
	border-style:;
	border-width:;
	border-color:;
	border-bottom:;
		border-bottom-color:;
		border-bottom-style:;
		border-bottom-width:;
	border-left:;
		border-left-color:;
		border-left-style:;
		border-left-width:;
	border-right:;
		border-right-color:;
		border-right-style:;
		border-right-width:;
	border-top:;
		border-top-color:;
		border-top-style:;
		border-top-width:;

/*css3*/
border-radius:左上右下  右上左下;
border-radius:左上  右上左下  右下;
border-radius:左上  右上  右下  左下;
border-radius:;
	border-bottom-left-radius:;
	border-bottom-right-radius:;
	border-top-left-radius:;
	border-top-right-radius:;

border-image:;
	border-image-outset:;
	border-image-repeat:;
	border-image-slice:;
	border-image-source:;
	border-image-width:;
box-shadow:;
}
```

### 轮廓

```css
div{
outline:;
	outline-color:;
	outline-style:;
	outline-width:;
}
```


### 内边距

```css
div{
padding:上下 两边;
padding:上  两边  下;
padding:top right bottom left;
	padding-bottom:;
	padding-left:;
	padding-right:;
	padding-top:;
}
```

### 外边距

```css
div{
margin:上下  两边;
margin:上  两边  下;
margin:top right bottom left;
	margin-bottom:;
	margin-left:;
	margin-right:;
	margin-top:;
}
```




border边框颜色随着文字颜色变化而变化


## 定位

### 定位



### 浮动



## 变换


### css3过渡
```css
transition:width 1s linear 2s;
	transition-property:width; --none --all --property
	transition-duration:1s; --time
	transition-timing-function:linear; --ease --ease-in --ease-out --ease-in-out --cubic-bezier(n,n,n,n)
	transition-delay:2s;

<!DOCTYPE html>
<html>
<head>
<style> 
div{
width:100px;
height:100px;
background:yellow;
transition-property:width 1s linear 2s;
}
div:hover{
width:200px;
}
</style>
</head>
<body>
	<div></div>
</body>
</html>
```

1. 部分没有被写的属性变换将在一瞬间完成。
2. timing-function最常用的是linear

**New Word**

- transition 过渡转变
- property 属性 ，财产
- duration 持续，持续的时长
- timing 定时，调速，时间选择
- function 功能，函数
- delay 延期 推迟 耽搁
- ease 容易，舒适，减轻，缓解

### css3动画



