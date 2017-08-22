## 装饰器

```
# 定义函数：完成包裹数据
def makeBold(fn):
    def wrapped():
        return "<b>" + fn() + "</b>"
    return wrapped

# 定义函数：完成包裹数据
def makeItalic(fn):
    def wrapped():
        return "<i>" + fn() + "</i>"
    return wrapped

@makeBold
def test1():
    return "hello world-1"

@makeItalic
def test2():
    return "hello world-2"

@makeItalic
@makeBold
def test3():
    return "hello world-3"


print(test1())
print(test2())
print(test3())



```

## 装饰器的功能
1. 引入日志
2. 函数执行时间统计
3. 执行函数前预备处理
4. 执行函数后清理功能
5. 权限校验等场景
6. 缓存

## 装饰器示例
```
# 无参数的函数

from time import ctime, sleep

def timefun(func):
    def wrappedfunc():
        print("%s called at %s" % (func.__name__, ctime()))
        func()
    return wrappedfunc

@timefun
def foo():
    print("I am foo")

foo()
sleep(2)
foo()
```

```
# 被装饰的函数有函数

from time import ctime, sleep

def timefun(func):
    def wrappedfunc(a, b):
        print("%s called at %s" % (func.__name__, ctime()))
        print(a, b)
        func(a, b)
    return wrappedfunc

@timefun
def foo(a, b):
    print(a + b)

foo(3, 5)
sleep(2)
foo(2, 4)

```
```
# 被装饰的函数有不定长参数

from time import ctime, sleep
def timefun(func):
    def wrappedfunc(*args, **kwargs):
        print("%s called at %s" % (func.__name__, ctime()))
        func(*args, **kwargs)
    return wrappedfunc

@timefun
def foo(a, b, c):
    print(a + b + c)

foo(3, 5, 7)
sleep(2)
foo(2, 4, 9)
```

```
# 装饰器中的return
from time import ctime, sleep

def timefun(func):
    def wrappendfunc():
        print("%s called at %s" % (func.__name__, ctime()))
        func()
    return wrappedfunc

@timefun
def foo():
    print("I am foo")

@timefun
def getInfo():
    return "-----haha____"

foo()
sleep(2)
foo()

print(getInfo())

# 一般情况下，为了让装饰器更通用，可以有return

```

```
# 装饰器带参数，在原有装饰器的基础上，设置外部变量
# decorator2.py

from time import ctime, sleep

def timefun_arg(pre="hello"):
    def timefun(func):
        def wrappedfunc():
            print("%s called at %s %s" % (func.__name__, ctime(), pre))
            return func()
        return wrappedfunc
    return timefun

@timefun_arg("itcast")
def foo():
    print("I am foo")

@timefun_arg("python")
def too():
    print("I am too")


foo()
sleep(2)
too()

# 可以理解为 foo() == timefun_arg("itcast")(foo)()

```
```
# 类装饰器
装饰器函数其实是这样一个接口约束，它必须接受一个callable对象作为参数，然后返回一个callable对象。在python中一般callable对象都是函数，但也有例外。只要某个对象重写了 __call__() 方法，那么这个对象就是callable的。

class Test():
    def __call__(self):
        print("call me!")

t = Test()
t()   # call me!
```

```
# 类装饰器demo

class Test(object):
    def __init__(self, func):
        print("------初始化------")
        print("func name is %s" % func.__name__)
        self.__func = func

    def __call__(self):
        print("-----装饰器中的功能------")
        self.__func()
"""
说明：
当用Test来装作装饰器对test函数进行装饰的时候，首先会创建Test的实例对象
并会把test这个函数名当作参数传递到__init__方法中
即在__init__方法中的func变量指向了test函数体

test函数相当于指向了用Test创建出来的实例对象

当在使用test()进行调用时，就相当于让这个对象(),因此会调用这个对象的__call__方法

为了能够在__call__方法中调用原来test指向的函数体，所以在__init__方法中就需要一个实例属性来保存这个函数体的引用

所以才有了self.__func = func 这句代码，从而在调用__call__方法中能够用到test之前的函数体

@Test
def test():
    print("---test---")

test()
showpy()


"""
