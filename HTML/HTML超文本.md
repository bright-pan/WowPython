# 给文字及图片添加超链接
// 添加网址链接
<a href="http://baidu.com">baidu</a>
// 链接到另一个HTML
<a href="lianjie.html">another HTML</a>
// 给图片添加超链接
<a href="http://baidu.com"><img src="tubiao.png" /></a>
// 超链接打开方式 target=_self/_blank
<a href="http://baidu.com" target="_blank">baidu</a>
// 添加提示消息 title
<a href="http://badu.com" title="this word will link to the web of baidu">baidu</a>
// 超链接实现书签 anchor
<a href="跳转目的地名称">跳转</a>
<a name="跳转目的地名称">跳转目的地</a>

# HTML表格
## table标签tr td
<table align="center" border="1">
	<tr>
	<td>first row and first column</td>
	<td>first row and second column</td>
	<td>first row and third column</td>
	</tr>

	<tr>
	<td>second row and first column</td>
	<td>second row and second column</td>
	<td>second roe and second column</td>
	
	</tr>




</table> 

## 合并单元格
colspan:列数
rowspan:行数

<table align="center" border="15">
	<tr>
	<td align="center" colspan="2">first row first column</tr>
	</tr>

	<tr>
	<td rowspan="2">second row and first column</td>
	<td>second row and second column</td>
	<td>second row and third column</td>
	</tr>

	<tr>
	<td>third row and first column</td>
	<td>third row and second column</td>
	</tr>


</table> 

## table 其他标签
<th> 表头
<caption> 标题
属性cellpadding="" 设置单元格边距
属性bgcolor="" 设置表格背景颜色
属性background="" 以某张图片作为表格背景

# HTML图像
## 插入图片
// 在body属性中加入background属性添加背景图片
<body background="./qwe.gif">
// 插入图片
<img src="路径加文件名">
加入align属性，bottom/middle/top调整对其
相对字体左右可加参数right

## 调整图片尺寸
width="80" height="80"

## 创建图像映射
<map>用来制定图片，<area>用来指定超链接区域
<img src="xx.jpg" usemap="#mp"/>
<map name="mp" id="mp">
	<area>
	...
	</area>
</map>
// area标签中会涉及shape, coords, href属性
shape:rect/circle/poly/default




