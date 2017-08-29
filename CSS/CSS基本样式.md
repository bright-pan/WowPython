<!-- TOC -->

- [1. CSS背景](#1-css背景)
    - [1.1. CSS3 背景](#11-css3-背景)
- [2. CSS 文本样式](#2-css-文本样式)

<!-- /TOC -->


# 1. CSS背景
```
background-attachment 背景图像是否固定或者随着页面的其余部分滚动:fixed

background-color 设置元素的背景颜色

background-image 把图片设置为背景 ：url("python.png")

background-position 设置背景图片的起始位置 center top

backgroud-repeat 设置图片是否可重复 

no-repeat不能重复，repeat可重复，repeat-x可X轴重复，repeat-y可y轴重复
```

## 1.1. CSS3 背景
background-size 规定背景图片的尺寸
background-origin 规定背景图片的定位区域
background-clip 规定背景的绘制区域


```
body{
  backgound-image:url("python.png");
  background-repeat:no-repeat;
  background-size:100px 100px;

}
```
# 2. CSS 文本样式
```
color 文本颜色

direction 文本方向

line-height 行高

letter-spacing 字符间距

text-align 对齐元素中的文本

text-decoration 向文本添加修饰

text-indent 缩进元素中文本的首行：5em;

text-transform 元素中的字母

unicode-bidi 设置文本方向

white-space 元素中空白的处理方式

word-space 字间距
```