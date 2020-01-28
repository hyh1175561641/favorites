# 本篇笔记如何使用？

**内容记录**

* 主要记录不常用的功能，常用知识为节省版面可以不记
* 写代码的经验，可以记例子
* 容易出错或经常被遗忘的点
* 技巧，妙用
* 学到的英文单词，并标明出处
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
text-transform:none,uppercase,lowercase,capitalize;/*大小写转换*/
unicode-bidi:;/**/
white-space:normal/*默认值，合并空白符成一个，忽略换行符*/
  								/*处理空白符，空格、换行和 tab 字符*/
						pre/*空白被保留，类似<pre>标签*/
						nowrap/*文本不换行*/
						pre-wrap/*空白符保留，换行符保留*/
						pre-line;/*合并空白符，换行符保留*/
word-spacing:normal,10px;/*字（单词）间隔，可取负值，单词之间间距为5px*/

vertical-align:baseline(基线对齐) middle(中部对齐，x的交叉点) text-top(与父元素字体顶端对齐) text-bottom(与父元素字体底端对齐) sub(对齐下标) super(对齐上标) top(顶端对齐) bottom(底端对齐) 15px %;/*垂直对齐，基线是字母x的底边*/
  
/*css3*/
text-shadow:15px(左右位置，可负) 15px(上下位置，可负) 15px(模糊距离) color(颜色);/*文本阴影效果*/
word-wrap:normal(默认) break-word(对长单词或URL地址内部换行);/*允许拆分长单词分割换行*/
text-overflow:clip(修剪文本) ellipsis(末尾显示省略号) 字符串(代替被修剪的文本);/*文本溢出显示方式*/
word-break:;
}

p{/*省略号三部曲*/
  overflow:hidden;
  white-space:nowrap;
  text-overflow:ellipsis;
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

3. 行内元素的概念，顶线(text-top) 中线(middle) 基线(baseline) 底线(text-bottom) 行框(border) 顶端(top) 低端(bottom)




**New Word**

- wrap 包，缠绕，外套，围巾



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
list-style:url(img) square inside;
	list-style-type:disc(默认，实心圆) none(无标记) circle(空心圆) square(实心方块) decimal(数字) 其他样式见手册;/*列表前面的标记*/
	list-style-position:outside(默认) inside;/*标记的位置*/
	list-style-image:none url("img.png");/*图像作为标记*/
}
```

- 始终规定一个list-style-type以防图像不可用



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



### 多列

```css
div{
columns:;
  columns-count:;
  columns-fill:;
  columns-gap:;
  columns-rule:;
	  columns-rule-color:;
	  columns-rule-style:;
  	columns-rule-width:;
  columns-span:;
  columns-width:;
}
```





## 盒子模型

### 边框
```css
div{
border:;
	border-style:上 右 下 左（上 两边 下）（上下 两边）;
  	border-top-style:;
  	border-right-style:;
  	border-bottom-style:;
  	border-left-style:;
	border-width:15px thin(1px) medium(3px) thick(5px);
  	border-top-width:;
  	border-right-width:;
  	border-bottom-width:;
  	border-left-width:;
	border-color:transparent;/*边框颜色可以是透明*/
  	border-top-color:;
  	border-right-color:;
  	border-bottom-color:;
  	border-left-color:;
	border-top:;
		border-top-color:;
		border-top-style:;
		border-top-width:;
	border-right:;
		border-right-color:;
		border-right-style:;
		border-right-width:;
	border-bottom:;
		border-bottom-color:;
		border-bottom-style:;
		border-bottom-width:;
	border-left:;
		border-left-color:;
		border-left-style:;
		border-left-width:;

/*css3*/
border-radius:左上右下  右上左下;
border-radius:左上  右上左下  右下;
border-radius:左上  右上  右下  左下;
border-radius:15px %;/*border圆角边框*/
	border-top-left-radius:上 左;
	border-top-right-radius:上 右;
	border-bottom-right-radius:下 右;
	border-bottom-left-radius:下 右;

border-image:;
	border-image-outset:;
	border-image-repeat:;
	border-image-slice:;
	border-image-source:;
	border-image-width:;
box-shadow:;
}
```

1. 如果样式是none，那么宽度永远是0。
2. border默认width是3px。
3. border边框颜色随着文字颜色变化而变化。
4. 如果边框是透明的，那么内容的背景会延伸出来，与外边距为界。
5. 边框如果横竖交叉，一条边上的边框会变成梯形。

### 轮廓

```css
div{
outline:color style width;
	outline-color:invert;/*默认。执行颜色反转（逆向的颜色）。可使轮廓在不同的背景颜色中都是可见。*/
	outline-style:none,dotted(点状),dashed(虚线框),solid(实线框),double(双线框),groove(凹槽),ridge(凸槽),inset(凹边),outset(凸边);
	outline-width:thin,medium,thick,15px;
	
outline-offset:15px;/*css3,轮廓偏离*/
}
```

1. 如果样式是none，轮廓不会出现，宽度为0。
2. 始终在outline-color之前声明outline-style。元素只有获得轮廓以后才能改变其轮廓的颜色。
3. 轮廓和边框的区别，轮廓不占用空间，轮廓可能是非矩形。

**New Word**

- offset 抵消，补偿，偏离量


### 内边距

```css
div{
padding:上下 两边;
padding:上  两边  下;
padding:top right bottom left;/*不可取负值*/
	padding-bottom:15px,%;
	padding-left:;
	padding-right:;
	padding-top:;
}
```

1. 上下内边距的百分数相对于父元素宽度设置，而不是相对于高度。

### 外边距

```css
div{
margin:上下  两边;
margin:上  两边  下;
margin:top right bottom left;/*可取负值*/
	margin-top:15px,%;
	margin-right:;
	margin-bottom:;
	margin-left:;
}
```


1. 上下内边距的百分数相对于父元素宽度设置，而不是相对于高度。
2. 两个元素的垂直外边距相遇时，外边距会合并成两者的较大者。只有普通块元素的垂直外边距会发生合并，行内元素，浮动框或绝对定位之间的外边距不会合并。
3. 

### 用户界面css3

```css
/**/  /**/
div{
resize:none(不可调) horizontal(调宽) vertical(调高) both;/*用户可调整盒子尺寸*/
box-sizing:content-box(内边距和边框另外计算，买东西另外购买) border-box(包括了边框和内边距，赠送了大礼包);/*宽高容纳的范围*/
}
```



## 定位

css有三种定位方式：普通流，浮动和绝对定位

普通流：从上至下一个接一个的排列，框之间的垂直距离是由框的垂直外边距计算出来的。

浮动

绝对定位

### 定位

定位允许你定义元素框相对于正常位置应该出现的位置。

``` css
div{
display:none(不显示)/*元素生成的框类型*/
  			block(转换成块级元素)
  			inline(默认值，显示为内联元素)
			  inline-block(行内块元素)
  			list-item(作为列表显示)
				run-in(根据上线文作为块元素或内联元素显示)
			  compact(已删除)
			  marker(已删除)
			  table(块级表格 类似<table>)
			  inline-table(内联表格 类似<table>)
			  table-row-group(作为一或多个行的分组显示 类似<tbody>)
			  table-header-group(同上，类似<tbody>)
				table-footer-group(同上，类似<tbody>)
  			table-row(作为一个表格行显示 类似<tr>)
  			table-column-group(作为一个或多个列的分组来显示 类似<colgroup>)
  			table-column(作为一个单元格列显示 类似<col>)
			  table-cell(作为一个表格单元格显示 类似<td><th>)
  			table-caption(作为一个表格标题显示 类似<caption>);
visibility:visible(默认，可见) hidden(不可见，仍然占位) collapse(删除一行或一列表格，但是不影响表格布局);/*元素是否可见*/


/*绝对定位：*/
position: static(普通流，默认值) absolute(绝对定位，相对于static以外的第一个父元素) relative(相对定位) fixed(固定定位，相对浏览器窗口);/*元素的定位类型*/
top:auto % 15px;
right:;
bottom:;
left:;
overflow:visible(默认，内容溢出呈现在框外) hidden(溢出部分被隐藏) scroll(溢出部分会显示滚动条) auto(溢出有滚动条);/*内容溢出时*/
clip:rect(top,right,bottom,left) auto(不裁剪，默认值);/*裁剪绝对定位的元素*/
z-index:auto(默认) (写一个具体的数字);/*图层前后顺序*/


/*浮动定位*/
float:none(默认，不浮动) left(向左浮动) right(向右浮动);/*浮动*/
clear:none(默认) left(左侧不允许浮动) right(右侧不允许浮动) both(两边不允许浮动);/*清除浮动*/

cursor:;/*鼠标形状，共17种，见手册*/
}
```

- 相对定位仍保留原来的位置， 绝对定位的盒模型全部消失
- 绝对定位之后变成块级元素
- 绝对定位的元素的位置相对于最近的已定位祖先元素
- 绝对定位元素时，尽量使用left和top属性定位。
- absolute的right和bottom是相对于浏览器窗口定位的。

### 浮动

- 当一个元素浮动时，盒子模型脱离普通流，下面的元素将向上，浮动的元素覆盖底下的元素
- [以后再看吧](https://www.w3school.com.cn/css/css_positioning_floating.asp)

**内联元素（行内元素）和块级元素**

1. 行内元素只能包含数据和其他行内元素；块级元素可以包含行内元素和其他块级元素。块级元素占据一行，行内元素只包含几个字。块级元素创建比行内元素更”大型“的结构。块级元素会新起一行，行内元素会跟在同一行的后面。
2. 内联元素在一行中可以使用内边距，边框和外边距调整间距，但是不影响内联元素的高度，设置行高可以增加内联元素的高度。
3. 由一行形成的水平框称为行框(Line Box)。



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





## 其他

### css样式初始化

**浏览器原始样式**

- body元素外边距为8px
- h1~h6标题，p有外边距
- h1~h6标题自动加粗

**css reset类库样式重置**

```css
body,p,h1,h2,h3,h4,h5,h6,ul,ol,dl,dt,dd{
  margin:0;
  padding:0;
}
ul,ol{
  list-style:none;
}
a{
  color:#000;
  text-decoration:none;
}
```

- normalize.css







# 英文单词



outline 轮廓，大纲，框








# 参考资料

- [w3school](https://www.w3school.com.cn/css/index.asp)



















































