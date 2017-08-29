# CSS基础语法规则

selector{
  declaration1;
  declaration2;
}

# 选择器的分组

h1, h2, h3{
  color:red;
}

## 选择器的派生
li strong{
  color:red;
}

## id选择器
以#定义，常用id选择器建立派生选择器

#pid a{
  color:#00755f;
}
#divid{
  color:red;
}


## 类选择器
.divclass{
  color:red;

}

和id一样，class也可用作派生选择器：
.pclass a{
  color:green;
}

## 属性选择器
对带有指定属性的HTML元素进行设置样式
[title]{color:red;}

title="te"的所有元素设置样式：
[title=te]{
  color:red;
}
