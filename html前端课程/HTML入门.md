<!-- TOC -->

- [1. html概述](#1-html概述)
- [2. html 基本结构](#2-html-基本结构)
- [3. 常用标签与实体字符](#3-常用标签与实体字符)
- [4. CSS 入门](#4-css-入门)
- [5. css属性](#5-css属性)
    - [5.1. 宽高](#51-宽高)
    - [5.2. 边框](#52-边框)
    - [5.3. 线形](#53-线形)
    - [5.4. 常用样式属性](#54-常用样式属性)
- [6. 选择器](#6-选择器)

<!-- /TOC -->


# 1. html概述

HTML (HyperText Mark-up Language) <br>

超文本标记语言

# 2. html 基本结构

```
<!DOCTYPE html>
<html lang="zh-cn">

    <head>
        <meta charset="utf-8">
        <title>我的个人主页</title>
    </head>

    <body>
        hi guys  欢迎学习前端课程！
    </body>

</html>

```

# 3. 常用标签与实体字符

| 标签       | 说明   |
| :--------- | :----- |
| h1-h6      | 标题   |
| div 或span | 块标签 |
| p          | 段落   |
| br         | 换行   |

```
注释
<!-- 内容 -->

插入图片
<img src="images/pic.jpg" alt="图片">

a链接
<a href= "链接目标地址", target="_blank"或"_self">内容</a>
```


```
# 常用实用字符

&nbsp;   空格

&lt;  <

&gt;  >
```

# 4. CSS 入门
- 行内式

- 嵌入式
```
<head>
    <style>
        p{color:red}
    </style>
</head>
```

- 外链式

```
<head>
    <link href="./css/text.css">
</head>
```


# 5. css属性
## 5.1. 宽高
- width

- height

- background

## 5.2. 边框

- connect

- padding

- border

- margin

## 5.3. 线形
- solid

- dash

- point

- double

## 5.4. 常用样式属性

color：red;

font-size:12px;

font-family:"Microsoft Yahei";

font-weight:bold; 或者normal;

line-height:24px;

text-decoration:none;




# 6. 选择器

- 标签选择器

- 类选择器
- 层级选择器

