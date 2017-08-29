<!-- TOC -->

- [1. HTML列表](#1-html列表)
    - [1.1. 有序列表](#11-有序列表)
    - [1.2. 无序列表](#12-无序列表)
    - [1.3. 定义性列表](#13-定义性列表)
- [2. HTML块](#2-html块)
- [4. HTML表单](#4-html表单)

<!-- /TOC -->
# 1. HTML列表
## 1.1. 有序列表
```
<ol>
	<li>balabala</li>
</ol>

```

type属性："a"/"i"/"A"/"I"

start属性：决定起始地


## 1.2. 无序列表

ul

各种小符号分为Disc(默认)/Circle小圈/square方点

```
<ul type="circle">
	<li>hadoop</li>
	<li>linux</li>
</ul>
```

## 1.3. 定义性列表
```
<dl> <dt>术语 <dd>解释器

<dl>
	<dt>hadoop</dt>
	<dd>it's useful!</dd>
	<dt>is's nice</dt>
</dl>
```

# 2. HTML块

块级元素(block):总是独占一行，表现为另起一行开始，而且其后的元素也必须另起一行显示;
```<h1>/<p>/<ul>/<table>```;

内联元素(inline):和相邻的内联元素在同一行。```<b>/<td>/<a>/<img>```;


# 3. HTML布局
```网页布局可以通过<table>元素，或者<div>元素实现。```
```
<html>
<body bgcolor="gray">

<table width="1000">
	<tr>
		<td colspan="2" style="background-color:royalblue">
			<h1 align="center">book store</h1>
		</td>
	</tr>

	<tr valign="top">
		<td style="background-color:darkorange;width:300px">
			<dl>
				<dt>list of book</dt>
				<dd>
					<ol>
						<li>hadoop</li><li>linux</li>
					</ol>
				</dd>
			</dl>
		</td>

		<td style="background-color:forestgreen;height:500px;width:700px;">
			<h1 style="font-size:20px;text-align:center">the sumary of the book</h1>
		I will lead you to travel in the season og linux
		</td>
	</tr>

	<tr>
		<td colspan="2" style="blackground-color:powderblue;text-align:center;height:100px">good good study day day up</td>

</table>
</body>
</html>
```

# 4. HTML表单
```
<input type="text" name="username"><br />
```
text 文本
 
password 暗文密码

radio 单选

checkbox 多选框









