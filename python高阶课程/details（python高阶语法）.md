## 1. import 模块
```
import sys 搜索路径

sys.path
```

### 1.1 程序执行时导入模块路径
```
sys.path.append("/home/itcast")

sys.path.insert(0, "/home/itcast")
```
### 1.2 重新导入模块

reload(模块名)


## 2. 局部变量和全局变量
```
locals()

globals()
```

## 3. is ==

is 是比较两个引用是否指向了同一对象（引用比较）。
== 是比较两个对象的值是否相等（值比较）。

## 4. __eq__


定义__eq__方法,重新实现==比较方法
定义类的等号行为
判断self对象是否等于other对象
```
class NewPerson(object):
		def __init__(self, name):
				self.name = name
		def __eq__(self, person_obj):
				"""执行==时调用的方法"""
				return self.name == person_obj.name




```
## 5. 深拷贝 浅拷贝
- copy.copy 对对象顶层的拷贝
- copy.deepcopy 对对象所有层次进行拷贝
