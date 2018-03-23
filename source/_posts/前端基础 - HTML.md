---

title: 前端基础之HTML
categories: "前端"
tags: 
     - 前端
     - HTML 
---
# 前端基础 - HTML #
HTML(hyper text markup language，超文本标记语言) 。
- 超文本：能实现网页链接跳转的文本叫做超文本。
- 标记：html 标签。

HTM：早起系统不支持四位写法。

<!--more-->
### 结构 ###
	
```
	<!DOCTYPE html>
	<!-- 单标签。DOCTYPE 在JavaScript中区分大小写， html中不区分 -->
	<html>
		<head>
		
			<title>标签的标题</title>
			
			<meta charset="UTF-8"/>
			
			<script src="test.js" type="text/javascript" charset="utf-8">
			</script>
			<script type="text/javascript">
			</script>
			
			<style type="text/css">
			</style>
			
			<link rel="stylesheet" type="text/css" href="test.css"/>
		</head>
		
		<body>页面内的所有内容都要放到这里</body>
	</html>
	<!-- 双标签。 -->
```
---
### 标签 ###
#### 标签间的关系 ####

根据 **嵌套关系** 可分为:
- 嵌套
- 并列

根据 **显示方式的不同** 可分为:(可以通过"`display`"属性互相转换)

- **块级元素(block) **: **<font color=red>元素独占一行</font>，可以设置宽高，子块级元素默认完全填充父层级**。例如：`div，p，li，h1...`
	
- **行内元素(inline)**: 与其他行内元素共享同一行，设置宽高不生效。例如：`span，strong，font，a...`
	**行内元素可以使用 "`display: inline-block;`" <font color=red>转换为行内块元素时宽高生效</font>**
- **行内块元素(inline-block)** : 与其他行内元素共享同一行，可以设置宽高。例如：`input，image ...`

#### 标签解析 ####
- 单标签:
	
	```html
		<hr>： 横线
		<br>： 换行
		<embed src="链接/地址" hidden="true">：补充标签
		
				注:hidden用于 隐藏/显示;
	```
- 双标签:
	
	```html
		<h1></h1>、<h2></h2>...<h6></h6>：标题
		<p></p>：段落
		
		尽量使用有语义的标签，或使用css样式代替
		<font size = "10" color = "red"></font>：文字
		<strong></strong>	、<b></b>：文字加粗
		<em></em>			、<i></i>：文字斜体
		<del></del>			、<s></s>：文字删除
		<ins></ins>			、<u></u>：文字下横线
	
	```
- 功能标签

	```
		- 图片: <img src="图片路径/图片名称 (涉及相对路径与绝对路径)" 
				alt="占位名称" 
				title="名称"
				width="100"
				height="100"> 
		- 超/锚链接: <a href="链接"
					title ="鼠标扫过时的文字"
					target="_self"> 占位文字 或 子标签</a>
			
				注：
					1.  target  =  "_self"：当前网页打开； = "_blank"：新标签页打开；
					2.  target - 全局属性 ：在<head>中使用<base target = "_blank"> ；
					3.  href - 锚链接 ：href 中通过 "#"与其他标签id名称 配合使用完成当页跳转；
					4.  href - 伪下载 ：href 设置其他文件链接； IIS 中需要设置MIME 类型；
	
		- 列表: 
			1. 无序: 使用css 完成 type 格式的更多改变
					<ul type="square(方块) | circle(圆圈) | ... "> 
						<li>item</li> 
						<li>item</li>
						... 
						<li>item</li> 
					</ul>
					
			2. 有序: 
					<ol type=" a | A | i | I | ... " start="3"> (排序方式)
						<li>item</li> 
						<li>item</li>
						... 
						<li>item</li> 
					</ol>
					
				注: start ： 从设定type的第N个开始;
				
			3. 自定义: 
					<dl>
						<dt>小标题</dt>
						<dd>自动缩进内容1</dd>
						<dd>自动缩进内容2</dd>
						...
					</dl>
	
		- 补充标签:<embed src="链接/地址" hidden="true">
		
				注:hidden用于 隐藏/显示;
			
		- 跑马灯: <marquee 
					width = "200"
					height = "200"
					bgcolor="red"
					behavior = " alternate | scroll | slide " 
					direction = " down | left | right | up "
					loop = "-1">滚动的文字/标签</marquee>
		
				注: 
					1. behavior : 设置滚动方式
						1. alternate(来回滚动)
						2. scroll(单向重复)
						3. slide(单向不重复)
					2. direction : 设置滚动方向, down | left | right | up 
					3. loop :  滚动次数, -1时一直滚动
	```
- meta 标签：编码格式、关键字、描述、重定向、是否被查询

	```
		指令集/编码格式 ,UTF-8 、US-ASC II 、GBK 、GB2312 、unicode、Big5
		<meta 
			charset = "utf-8">  
			
		网站优化之关键词
		<meta 
			name = "keywords"  
			content = "android,ios,java,html,javascript"> 	
			
		网站描述
		<meta 
			content="描述内容" 
			name="description">	
			
		网站优化之重定向
		<meta 
			content="refresh" 
			http-equiv="2;url=https://www.baidu.com"> 两秒之后跳转至设置的网页
		
		告诉搜索引擎站点的作者
		<meta  
			name="Author"  
			content="你的姓名">
		
		网站文件和链接是否可以被查询
		<meta   
			name="Robots" 
			content= "all|none|index|noindex|follow|nofollow"> 
			
			all：			文件/链接可以被查询； 
			none：			文件/链接都不可以被查询； 
			index：			文件将被检索； 
			noindex：		文件将不被检索，链接可被查询；
			follow：			链接可以被查询；  
			nofollow：		文件可被检索，链接不可被查询。 
	```

- link标签 ：引入css 样式表、设置标签图标

	```
		引入外部样式表
		<link 
			href="teamviewer.css" 
			rel="stylesheet" 
			type="text/css">
			
		设置标签图标,限定ico格式
		<link 
			href="teamviewer.ico" 
			rel="icon" >
	
	```
-  表格
	**表格外部使用  `<table>` 包裹，<br>使用 `<th>`设置自动加粗的标题，<br>使用  `<tr>` 设置行，<br>使用 `<td>` 设置列/单元格**
	
	属性:
	1. `cellspacing`：单元格之间线的内边距；
	2. `cellpadding`：文字距离单元格边框左侧的距离；
	3. `align`：( table 设置 )表格相对于外部对齐 或 (** `tr / td`** 设置 )内部文字对齐，`center | left | right` ；
	4. `<caption>` 用于设置表格内部标题/表头；
	5. `colspan` ：="4"， 用于`<td>`横向单元格合并；
	6. `rowspan`：用于`<td>` 纵向合并；
	7. `border`： 通用属性---边界(可连写)，边界宽度；
	8. `bordercolor`：通用属性---边界，边界颜色；
	```
	 <table width="500" 
	 	height="400"  
	 	bgcolor="pink" 
	 	border="10" 
	 	bordercolor="red"
	 	cellspacing="1"
	 	cellpadding="20">
	 	
	 	<caption> <h2> 表格内部标题 </h2> </caption>
	 	
                <tr bgcolor="red">
                     <th>标题1</th>
                     <th>标题2</th>
                     <th>标题3</th>
                     <th>标题4</th>
                </tr>
                <tr bgcolor="green">
                     <td>数据1</td>
                     <td>数据2</td>
                     <td>数据3</td>
                     <td>数据4</td>
                </tr>
                <tr bgcolor="blue">
                     <td>数据5</td>
                     <td>数据6</td>
                     <td>数据7</td>
                     <td>数据8</td>
                </tr>
         </table>
	```
	*使用 `<thead>` 设置头部，<br>使用 `<tfoot>` 设置尾部，<br>使用 `<tbody>` 设置中部，作为主要显示内容，可以支持搜索引擎<br>(由于兼容性差,一般不使用)*
	```
		<table width="1000" height="1000" align="center" bgcolor="green" cellspacing="2" cellpadding="2">
			<caption>
				<h3>这是一个表格标题</h3>
			</caption>
			<thead>
				<tr bgcolor="white" align="center">
					<th>标题1</th>
					<th>标题1</th>
					<th>标题1</th>
					<th>标题1</th>
				</tr>
			</thead>
			<tbody>
				<tr align="center" bgcolor="white">
					<td>数据1</td>
					<td>数据1</td>
					<td>数据1</td>
					<td>数据1</td>
				</tr>
			</tbody>
			<tfoot>
				<tr align="center" bgcolor="white">
					<td>数据1</td>
					<td>数据1</td>
					<td>数据1</td>
					<td>数据1</td>
				</tr>
			</tfoot>

		</table>
	```
- 表格合并：使用 `rowspan`|`colspan` 属性，进行 竖直 | 水平合并。

	```
	<table width="1000" height="1000" align="center" bgcolor="green" cellspacing="2" cellpadding="2">
			<caption>
				<h3>这是一个表格标题</h3>
			</caption>
			<tr bgcolor="white" align="center">
				<th>标题1</th>
				<th>标题1</th>
				<th>标题1</th>
				<th rowspan="2">竖向合并</th>
				
			</tr>
			<tr align="center" bgcolor="white">
				<td>数据1</td>
				<td>数据1</td>
				<td>数据1</td>
			</tr>
			<tr align="center" bgcolor="white">
				<td>数据1</td>
				<td colspan="2">水平合并</td>
				<td>数据1</td>
			</tr>

		</table>
	```	
- 表单
	- 组成 
		- 提示信息
		- 表单控件
		- 表单域
	- 标签、属性、控件
		```
		<form action="form_action.js" method="post">
			<fieldset>
				<legend>用户信息</legend>
				<!-- fieldset 与 legend 配合使用,圈定区域 设置名称 -->
				用户名:&nbsp;<input type="text" name="userName1" id="username" value="TextForInput" maxlength="10" readonly="readonly" disabled="disabled" /><br>

				<!--input: 	
						name		输入框名称
						value		输入框内容
						type 		输入类型  
										text(文本)
										password(密码)
										radio(单选)应设置相同的name，checked="checked"为默认选中;
										checkbox(多选)
										file(文件选择上传)
										reset(清空input输入内容)
										submit(提交按钮)
										button(onclick 属性与javascript 配合使用)
										image(使用src设置路径,点击效果与submit相同)
						maxlength 	最大输入长度
						readonly 	="readonly"	不可输入
						disable		="disable"	非激活状态，不可使用
			-->
				密码:&nbsp;<input type="password" name="pwd" id="pwd" value="" maxlength="16" /><br>

				<!--单/多选按钮-->
				性别:
				<input type="radio" name="rb" id="gender1" value="" checked="checked" />男
				<input type="radio" name="rb" id="gender2" value="" disabled="disabled" />女<br> 性别2:
				<input type="checkbox" name="cb" checked="checked" />男
				<input type="checkbox" name="cb" />女

				<!--下拉列表-->
				<br> 下拉选择:
				<select multiple="multiple">
					<option>选项1</option>
					<option>选项2</option>
					<option>选项3</option>
					<option selected="selected">选项4</option>
					<!--select 下拉列表 为option/optgroup
						multiple	多选
					option
						selected 	默认选中项
					opgroup
						label		分组名称
				-->
				</select>

				<select multiple="multiple">
					<optgroup label="group1>>>">
						<option>group1选项1</option>
						<option>group1选项2</option>
						<option>group1选项3</option>
						<option>group1选项4</option>
					</optgroup>
					<optgroup label="group2>>>">
						<option>group2选项1</option>
						<option>group2选项2</option>
						<option>group2选项3</option>
						<option>group2选项4</option>
					</optgroup>
				</select>

				<br /> 自我描述:<br />
				<textarea >输入框的内容</textarea>

				<!--输入框-->
				<input type="datetime" /><br />
				<input type="tel" /><br />
				<input type="email" /><br />
				<input type="url" /><br />

				<!--选择输入框-->
				<input type="color" /><br />
				<input type="date" /><br />
				<input type="datetime-local" /><br />
				<input type="month" /><br />
				<input type="week" /><br />

				<!--搜索框-->
				<input type="search" /><br />

				<!--文件选择及按钮-->
				<input type="file" /><br />
				<input type="reset" /><br />
				<input type="image" src="img/HBuilder.png" />
				<input type="button" value="button" />
				<input type="submit" />
			</fieldset>
		</form>

		```
		- form
			- action 表示处理逻辑
			- method =" get | post " 表示表单信息的传输方式,get将用户输入的信息显示出来,安全性差,post方式更安全
		- fieldset 与 legend 配合使用,圈定区域 设置名称
		- textarea 为可拉伸输入框
		- input: 	
			- name		输入框名称
			- value		输入框内容
			- type 		输入类型  
				- text			(文本)
				- password		(密码)
				- radio			(单选)应设置相同的name，checked="checked"为默认选中;
				- checkbox		(多选)
				- file				(文件选择上传)
				- reset			(清空input输入内容)
				- submit			(提交按钮)
				- button			(onclick 属性与javascript 配合使用)
				- image			(使用src设置路径,点击效果与submit相同)
				- url				(网址判断,必须以http开头)
				- email			(邮箱判断)
				- number		(只能输入数字,使用step 可以以N为等差进行设置)
				- range			(设置max 与step 起到进度条的效果)
			- maxlength 	最大输入长度
			- readonly 	="readonly"	不可输入
			- disable		="disable"	非激活状态，不可使用
		- select 下拉列表 为option/optgroup
			- multiple 属性	多选
			- option 标签
				- selected 	默认选中项
			- optgroup标签
				- label		分组名称 
		- <font color = red>**表单优化写法**</font>
			```
			<label for="pwd"> 密码:&nbsp;</label>
			<input type="password" name="pwd1" id="pwd" value="" maxlength="16" />
			```			

- 无语义标签 `<span>`、`<div>`、`<p>` 尽少使用，可以使用`<p>` 代替`<div>`的使用
---
### 路径 ###
- 相对路径

	- 同一路径/文件夹下
	- 下一级目录中
	- 上一级目录下: **使用 `../`跳出一层(当前)文件夹**


- 绝对路径: 带有 磁盘路径 或 网页地址 的路径为绝对路径。

---
### 特殊字符对照表 ###

**常用字符表**
![常用字符表](https://i.imgur.com/ryywt6G.png)

完整特殊字符表
![1](https://i.imgur.com/Mj1h0a8.png)![2](https://i.imgur.com/ZH91RUV.png)

---

