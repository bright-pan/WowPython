<!-- TOC -->

- [1. HTML 文本标签](#1-html-文本标签)
    - [1.1. 超链接](#11-超链接)
    - [1.2. 组合内容标签](#12-组合内容标签)
    - [1.3. 文档章节](#13-文档章节)
    - [1.4. 引用](#14-引用)
    - [1.5. 格式化](#15-格式化)
    - [1.6. 强调](#16-强调)
- [2. 列表](#2-列表)
    - [2.1. 无序列表](#21-无序列表)
    - [2.2. 有序列表](#22-有序列表)
    - [2.3. 自定义列表](#23-自定义列表)
- [3. HTML引入](#3-html引入)
    - [3.1. 嵌入](#31-嵌入)
    - [3.2. 资源标签](#32-资源标签)
    - [3.3. 表格](#33-表格)
    - [3.4. 表单](#34-表单)
    - [3.5. 实体字符](#35-实体字符)

<!-- /TOC -->

# 1. HTML 文本标签
## 1.1. 超链接
```
<a href="#achor">Achor Point<a>
<section id="achor">Achor Content</setion>
```
## 1.2. 组合内容标签
```
<div>
<p>
<ol>
<ul>
<dl>
<pre>
<blockquote>
```

## 1.3. 文档章节
```
<body>
<header>
<nav>
<aside>
<article>
<section>
<footer>
```
## 1.4. 引用
```
<cite> 引用作品的名字、作者的名字
<q> 引用一小段文字
<blockquote> 引用大块文字
<pre> 保存格式化的内容
<code> 引用代码
```
## 1.5. 格式化
```
<b> 加粗 <i> 斜体
```
## 1.6. 强调
```
<em> 斜体，着重于强调内容，会改变语义的强调<strong>粗体。着重于强调内容的重要性。
```
# 2. 列表
## 2.1. 无序列表
```
<ul>
	<li>标题</li>
	<li>结论</li>
</ul>
```
## 2.2. 有序列表
```
<ol>
	<li>第一</li>
	<li>第二</li>
</ol>
```

## 2.3. 自定义列表
```
<dl>
	<dt>作者</dt>
	<dd>爱因斯坦</dd>
	<dt>作品</dt>
	<dd>相对论</dd>
	<dd>时间与空间</dd>
</dl>
```
# 3. HTML引入
```
<blockquote cite="http://example.com">
	<p>Sample Quote</p>
</blockquote>
```

## 3.1. 嵌入
```
<iframe src=""></iframe>

<object type="application/x">
	<param name="movie" value="book.pdf">
</object>

track引入字幕，autoplay加载后自动播放 loop循环播放
```

## 3.2. 资源标签
img中套用map以及area可以实现点击某部分图片触发一个间接
```
<img src="mama.jpg" width=100 height=100 usemap="#map" />
<map name="map">
	<area shap="rect" coords="0,0,50,50" href="" alt="">
	<area shap="circle" coords="75,75,25" href="" alt="">
</map>
```

## 3.3. 表格
```
<table>
	<caption>table title and/or explanatory text</caption>
	<thead>
		<tr>
			<th>header</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>date</td>
		</tr>
	</tbody>
</table>
```
使用colspan=val 进行跨列，使用rowspan=val进行跨行。

## 3.4. 表单
```
<form action="webcreation_submit" method="get" accept-charset="utf-8">
	<fieldset>
		<legend>title or explanatory caption</legend>
		<lable><input type="text/submit/hidden/button/sct" name="" value=""></lable>
	</fieldset>
</form>
```
## 3.5. 实体字符
```
&gt;

&lt;

&nbsp;
```


	