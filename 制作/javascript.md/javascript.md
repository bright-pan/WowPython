#书写方式
```

<div class="box" onclick="alert('hello world')"></div>

<head> <script> alert('hello world') </script> </head>

<head> <script src="js/demo.js"></script> </head>

```

#注释
单行 //
多行 /    /

#变量
var   ---variable

string
number
boolean
undefined
null
object

##匈牙利方法

object
array
string
intager
boolean
float
function
regexp

#JS获取元素方法

<script type="text/javascript">
    var oDiv = document.getElementById("div1");
</script>

如放head中，解决方法：
window.onload = function(){ XX }

通过.获取属性
<script type="text/javascript">

window.onload = function(){
    var oInput1 = document.getElementById("input1);
    var oInput2 = document.getElementById("input2);
    var oA = document.getElementById("link1");


    //读取属性

    var sVal1 = oInput1.value;
    var sVal2 = oInput2.value;

    //写（设置）属性
    // oA.style.vall = val2;
    
    oA.style[sVall] = sVal2;

</script>


}

#函数执行



