<!-- TOC -->

- [1. 文本标签](#1-文本标签)
- [2. 组合内容标签](#2-组合内容标签)
- [3. 文档章节](#3-文档章节)
- [4. 引用](#4-引用)
- [5. 格式化](#5-格式化)
- [6. 强调](#6-强调)

<!-- /TOC -->
# 1. 文本标签
```
<!-- iframe中打开连接 -->
<a href="http://baidu.com" title="baidu" target="iframe-name">baidu</a>
<iframe name="iframe-name" frameborder="0"><iframe>

<!-- 页面中的锚点 -->
<a href="#achor">Achor Point</a>
<section id="achor">Achor Content</section>

<!-- 邮箱及电话 -->
<a href="mailto:sample@me.com" title="Email">Contact Us</a>

<!-- 多个邮箱地址 -->
<a href="sample-address@me.com, saple-address0@me.com" title="Email">Contact Us</a>

<!-- 添加抄送,主题和内容 -->
<a href="mailto:sample-address@me.com?cc=admin@me.com&subject=Help&body=sample-body-text" title="Email">Contact Us</a>

<!-- 电话示例 -->
<a href="tel:999999" title="Phone">Ring Us</a>

```

# 2. 组合内容标签

```
<pre>
<code>
<div>
<p>
<ol>
<ul>
<dl>
<blockquote>

```
# 3. 文档章节
```
<body>页面内容 <header> 文档头部 <nav> 导航 <aside> 侧边栏
<article>定义外部内容（如外部引用的文章）<section>一个独立的块
<footer>尾部
```
# 4. 引用
```
<cite> 引用作品的名字、作者的名字等
<q> 引用一小段文字
<blockquote> 引用大块文字
<pre> 保存格式化内容（其空格、换行等格式不会丢失）
<code> 引用代码
```
# 5. 格式化
```
<b> 加粗 <i> 斜体
```
# 6. 强调
```
<em> 斜体，着重于强调内容。
会改变语义的强调<strong>粗体。着重于强调内容的重要性。
```

