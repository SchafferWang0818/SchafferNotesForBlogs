---

title: 前端基础之CSS / CSS3 样式属性
categories: "前端"
tags: 
     - 前端
     - CSS/CSS3
---
# 前端基础之CSS / CSS3 样式属性 #
<!--more-->
<br>
## background ##
```
	background: url(img/HBuilder.png) red repeat-x 20px 20px;
```

- 属性连写 无论背景颜色和图片都必须设置水平和竖直的位置。其他无顺序可言。



background相关属性			|	 属性含义
						-	|	-
`background-repeat`			|	`repeat` 默认重复<br>`no-repeat`不重复平铺<br>`repeat-x` 横向重复平铺<br>`repeat-y `纵向重复平铺
`background-attachment` 	|	`Scroll`默认值，**随滚动条滚动 **<br>`fixed`不随滚动条滚动
`background-position`		|	**背景位置的设置 , 同时设置两个固定数值参数时分别代表水平和竖直的位置 ;** <br>参数包括：固定数值，center，left，right，top，bottom
`(CSS3)background-clip`		|	背景颜色的定位区域，<br>包括 `content-box`、`padding-box`、`border-box`
`(CSS3)background-size`		|	背景图片大小,先宽后高
`(CSS3)background-origin`	|	背景图片的定位区域，<br>包括 `content-box`、`padding-box`、`border-box`
	
```
background-position: center center;
background-position: bottom right;
background-position: 30% 20%; 
background-position: 30px 20px;
background-position-x: center;
background-position-y: center;
```
背景图片的定位区域如下:

![背景图片的定位区域](http://www.w3school.com.cn/i/background-origin.gif)

---
## text ##
属性				|	描述
				:-	|	:-
`color`				|	文本颜色。
`direction`			|	文本方向。
**`line-height`**		|	文本行高。
**`letter-spacing`**	|	字符/字的间距。
**`word-spacing`**	|	单词/字间距，**仅在有空格的情况生效**。
`text-align`			|	文本对齐。左，中，右。
`text-decoration`		|	文本修饰（线）。
`text-indent`			|	文本首行缩进，可正可负。CSS2.1 之前可继承。
`text-transform`		|	文本大小写转换。<br>`none`　　　　　不做任何改动<br>`uppercase`　　　全大写<br>`lowercase`　　　全小写<br>`capitalize`　　每个单词的首字母大写，**仅在有空格的情况生效**
`white-space`			|	文本空白处理，查看以下表格。
`font-family`			|	字体，**多个字体名称用于向后逐个兼容**
`(CSS3)text-shadow`	|	文本阴影，包含 ：<br>`h-shadow`　　向右的阴影宽度<br>`v-shadow`　　向下的阴影宽度<br>`blur`　　　　阴影模糊半径<br>`color`　　　阴影颜色
`(CSS3)word-wrap`	|	`break-word` 　　文本中长单词可拆分换行
`(CSS3)column-count`	|	文字分为水平方向 N 列显示
`(CSS3)column-gap`		| 	列之间的间隔大小
`(CSS3)column-rule`<br>需兼容		|	`column-rule-color`	列间隔的颜色。<br><br>`column-rule-style`	列间隔的样式。包括 `none.hidden.dotted.dashed.solid.`<br>`double.groove.ridge.inset.outset`<br><br>`column-rule-width` 	列间隔的宽度。包括: <br>`固定值.thin.medium.thick`
`(CSS3)column-width`		|	每列的宽度,可固定数值 <br>`auto` 浏览器决定列宽
`(CSS3)column-span`		|	[**父标签分列的情况下, 当前标签可以跨越的列数**](http://www.w3school.com.cn/cssref/pr_column-span.asp)<br>`all`　　完全展开<br> `1`　　　只跨越一列

`white-space`值	|	空格	|	换行	|	自动换行
			:-	|	----|	-	|	----	
`normal`		|	合并	|	忽略	|	允许
`nowrap`		|	合并	|	忽略	|	不允许
`pre`			|	保留	|	保留	|	不允许
`pre-wrap`		|	保留	|	保留	|	允许
**`pre-line`**	|	合并	|	保留	|	允许

---

## 列表list ##
主要设置列表前方的标志。

属性				|	描述
				-	|	-
`list-style	`			|	属性连写
`list-style-image`		|	将图象设置为列表项标志。`url(../../.../1.jpg)`
`list-style-position`	|	设置列表中列表项标志的位置 ( inside 偏内侧 、outside 偏外侧)
**`list-style-type`**	|	设置列表项标志的类型。


`list-style-type`值		|	描述
				-	|	-
none				|	无序：无标记。
disc					|	无序：默认实心圆。
circle				|	无序：空心圆。
square				|	无序：实心方块。
decimal				|	有序：数字。
decimal-leading-zero	|	有序：0开头的数字标记。(01, 02, 03, 等。)
lower-roman			|	有序：小写罗马数字(i, ii, iii, iv, v, 等。)
upper-roman			|	有序：大写罗马数字(I, II, III, IV, V, 等。)
lower-alpha			|	有序：小写英文字母The marker is lower-alpha (a,b, c, d, e, 等。)
upper-alpha			|	有序：大写英文字母The marker is upper-alpha (A, B, C, D, E, 等。)
lower-greek			|	有序：希腊字母(α, β, γ, 等。)
lower-latin			|	有序：小写拉丁字母(a, b, c, d, e, 等。)
upper-latin			|	有序：大写拉丁字母(A, B, C, D, E, 等。)
hebrew				|	有序：传统的希伯来编号方式
armenian			|	有序：传统的亚美尼亚编号方式
...					|	...

---
## 表格 table、tr、th、td ##
- **默认table及table的所有子元素都有边框border但宽度为0。**
- 文字对齐方式`text-align`,`vertical-align`

属性						|	描述
			:-			|	:-
**`border-collapse`**	|	**设置是否把表格边框合并为单一的边框。<br> `= collapse` 合并内外部边框；<br> `= separate` 显示内外部边框；**
**`border-spacing`**	|	**单元格边框的距离**
**`text-align`**		|	文字**左、中、右**对齐
**`vertical-align`**	|	文字**上、中、下**对齐
**`caption-side`	**	|	**设置表格标题的位置，与`<caption></caption>`一起使用。**
`empty-cells`			|	设置是否显示表格中的空单元格。<br> `= hide`　　　隐藏空的单元格；<br> `= show`　　　显示空的单元格；
`table-layout`			|	设置显示单元、行和列的算法。

---
## 边框 border ##
border属性					|	属性
			:-				|	:-
`border-width`				|	边框宽度
`border-style`				|	边框样式 。<br>`solid`　　　实线<br>`dotted`　　点线<br>`dashed`　　虚线<br>`hidden`　　与`none` 相同,解决应用于表时边框的冲突<br>`double`　　双线的宽度等于 `border-width` 的值。
`border-color`				|	边框颜色
`(css3)border-radius`			|	创建圆角
`(css3)box-shadow`			| 	`h-shadow`　　向右的阴影宽度<br>`v-shadow`　　向下的阴影宽度<br>`blur`　　　　可选, 阴影模糊半径<br>`spread`　　　可选, 阴影尺寸大小<br>`color`　　　可选, 阴影颜色<br>`inset`　　　可选, 内部阴影,默认不设置为外部
`(css3)border-image`			|	由以下属性构成:
`(css3)border-image-source`	|	边框图片路径。	
`(css3)border-image-slice`		|	边框图片向内偏移。	
`(css3)border-image-width`		|	边框图片的宽度。	
`(css3)border-image-outset`	|	边框图像区域超出边框的量。	
`(css3)border-image-repeat`	|	边框图像平铺(`repeated`)、铺满(`rounded`)、拉伸(`stretched`)。
---
## 转换 transform (CSS 3)  ##
注意: <font color=red>**transform样式 需要完成 浏览器内核适配**。</font>

2D/3D变换	|	释义
-|-
`translate　(0px,0px)`|	平移
`translate3d(0px,0px,10px)`|	平移3D
`translateX/Y/Z(x)`	|	用于 X / Y /(3D)Z 方向的平移。
`scale 　(1,1)`|缩放
`scale3d (1,1,1)`|缩放3D
`scaleX/Y/Z(0.3)`	|	用于 X  /Y /(3D)Z 方向的缩放。
`rotate　(angle)`|旋转
`rotate3d(k_x,k_y,k_z,angle)`|旋转3D ,` angle_x = k_x * angle`
`rotateX/Y/Z(x)`	|	用于 X / Y /(3D)Z 方向的旋转。
`skew(angle,angle)` |错切
`skewX/Y(angle)`	|沿着 X / Y 轴的 2D 倾斜转换。
`matrix(0,0,0,0,0,0)`|矩阵完成转换
`matrix3d(`<br>　　　　`n,n,n,n,`<br>　　　　`n,n,n,n,`<br>　　　　`n,n,n,n,`<br>　　　　`n,n,n,n　)`|矩阵完成3D转换

---
## 动态转换 transition  (CSS 3) ##
注意: <font color=red>**transition样式 需要完成 浏览器内核适配**。</font>

`transition`连写内容		| 	释义
					:-	|	:-
`transition-property`		|	过渡效果对应的 CSS 属性名称。	
`transition-duration`		|	过渡效果花费的时间。默认是 0。	
`transition-timing-function`	|	过渡效果的时间曲线。默认是 "ease"。	
`transition-delay`			|	过渡效果何时开始。默认是 0。

---
## 动画 animation (CSS 3) ##
注意: <font color=red>**animation样式 与 @keyframes 需要完成 浏览器内核适配**。</font>

```
@keyframes frame-name0
{
	0%   {background: red; left:0px; top:0px;}
	25%  {background: yellow; left:200px; top:0px;}
	50%  {background: blue; left:200px; top:200px;}
	75%  {background: green; left:0px; top:200px;}
	100% {background: red; left:0px; top:0px;}
}
@-moz-keyframes frame-name0 /* Firefox */
{
	...
}

......

@keyframes frame-name1
{
	from {background: red; left:0px; top:0px;}
	to{background: blue; left:200px; top:200px;}
}

.tab1{
	animation: frame-name0 5s;
	-moz-animation: frame-name0 5s;	/* Firefox */
	...
}

```
属性					|	描述	
:- 						|	:-
`@keyframes`			|	规定动画。	
`animation`				|	动画简写属性，除了 `animation-play-state` 属性。	
`animation-name`			|	@keyframes 动画的名称。	
`animation-duration`		|	动画一个周期的时间。默认是 0。	
`animation-timing-function`	|	[**动画速度曲线`cubic-bezier(n,n,n,n)`。<br>`ease`、`linear`、<br> `ease-in`、`ease-out `、 `ease-in-out` 、<br> `step-start` 、 `step-end`**](http://blog.csdn.net/qq_23269747/article/details/76152689)
`animation-delay`			|	动画延时时长。默认是 0(s or ms)。	
`animation-iteration-count`	|	动画播放次数。默认是 1。	
`animation-direction`		|	动画是否逆向播放(下个周期)。<br>正向　　　`normal` <br>反向　　　`reverse`<br>正向交替　`alternate`<br>反向交替　`alternate-reverse`	
`animation-fill-mode`		|	[**对象动画时间之外的状态。<br>`none`、`both`、`forwards` 、`backwards`**](https://www.w3cplus.com/css3/understanding-css-animation-fill-mode-property.html)
`animation-play-state`		|	动画是否正在运行`(running , 默认)`或暂停`(paused)`。

---
