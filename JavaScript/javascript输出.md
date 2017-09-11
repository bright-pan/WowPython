#操作HTML元素
document.getElementById(id)

<script>
document.getElementById("demo").innerHTML="我的第一段Javascript"；
</script>

#写到文档输出
<body>
<script>
document.write("<p>我的第一段JavaScript</p>");
</script>

使用document.write()仅仅向文档输出写内容，如果在文档已完成加载后执行document.write,整个HTML页面江北覆盖；




