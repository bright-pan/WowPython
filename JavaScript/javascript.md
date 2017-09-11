
# 写入HTLM
document.write("<h1>This is a heading</h1>");
document.write("<p>This is a paragraph</p>");

#对事件做出反应
<button type="button" onclick="alert("Welcome!")">点击这里</button>

#改变HTML内容
x=document.getElementById("demo") //查找元素
x.innerHTML="Hello JavaScript"; //改变内容

#改变HTML图像
element=document.getElementById("myimage")
if(element.src.match("bulbon")){
element.src="/i/eg.gif"};
else
{
element.src="/i/egbulbon.gif";
}

#验证输入
var x=document.getElementById("demo").value;
if(x==""||isNaN(x)){
alert("Not a Number");
}


if isNaN(x){alert("Not Numeric")};
