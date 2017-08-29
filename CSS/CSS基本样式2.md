<!-- TOC -->

- [1. CSS 连接](#1-css-连接)
    - [1.1. 链接的四种状态](#11-链接的四种状态)
- [2. CSS 列表](#2-css-列表)
- [3. CSS 表格](#3-css-表格)

<!-- /TOC -->

# 1. CSS 连接
## 1.1. 链接的四种状态

```
a:link 普通未被访问的链接

a:visited 用户已访问的链接

a:hover 鼠标指针位于链接的上方

a:action 链接被点击的时刻

```
```
a:link{color:#FF0000;}
```

可修改background-color设置链接背景颜色
link属性中加入text-decoration属性

# 2. CSS 列表
通过list-style  -type属性控制标记类型，也可加入图片list-style-image
简写列表样式，将列表的属性设置于一个声明中 li{list-style:url(example.gif) square}

# 3. CSS 表格
border-collapse 设置是否把表格边框合并为单一的边框
