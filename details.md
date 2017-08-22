## import 模块

> import sys 搜索路径
> sys.path
n
### 程序执行时导入模块路径

> sys.path.append("/home/itcast")
  sys.path.insert(0, "/home/itcast")

## 重新导入模块

reload(模块名)


## 局部变量和全局变量

locals()
globals()


##

is 是比较两个引用是否指向了同一对象（引用比较）。
== 是比较两个对象的值是否相等（值比较）。

##### __eq__


## 深拷贝 浅拷贝
