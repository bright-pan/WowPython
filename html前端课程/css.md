## CSS 引入方法
// 外部样式表
<head>
    <link rel="stylesheet" type="text/css" href="style.css">
</head>

// 内部样式表
<head>
    <style type="text/css">
        p{
            margin:10px;
        }
    </style>
</head>

//内嵌样式
<p style="color:red">Sample Text</p>

# CSS 语法

.m-usrlist{
    margin:0 0 30px;   
}


.m-userlist .list{
    position: relative;
    height: 100px;
    overflow:hidden;
}

## 简单选择器
<style type="text/css">
    p{
        color:blue;
    }
</style>

## 类选择器

.className 以.开头

<style type="text/css">
    p{
        color: blue;
    }
    .special{
        color: orange;
    }
    .blod{
        font-weight:bold;
    }


## id 选择器
# idName 以# 开头且只能出现一次， .className相同
<div>
    <p id="special">Sample Pargraph</p>
</div>

<style type="text/css">
    #special{
        color:red;
    }
</special>

## 通配符选择器

