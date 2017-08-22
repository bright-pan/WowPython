## 迭代器
可以通过for……in……这类语句迭代读取一条数据供我们使用的对象称之为可迭代对象。（Iterable）

## 如何判断一个对象是否可迭代
isinstance()
```
from cllections import Iterable
isinstance([], Iterable)

```

## 迭代器
可迭代对象通过 __iter__ 方法向我们提供一个迭代器，我们迭代一个可迭代对象时候，实际上就是先获取该对象提供的一个迭代器，然后通过这个迭代器来一次获取对象中的每一个数据。
那么也就是说，一个具备了 __iter__ 的方法的对象，就是一个可迭代对象。

```
class MyList(object):
    def __init__(self):
        self.container = []
    def add(self, item):
        self.container.append(item)
    def __iter__(self):
    """返回一个迭代器"""
    # 暂时忽略如何构造一个迭代对象
        pass

mylist = mylist
from collections import Iterable
isinstance(mylist, Iterable)

True


# 这回测试发现添加了 __iter__ 方法的mylist对象已经是个可迭代对象了
```

## iter()函数与 next()函数
可以通过iter()函数获取可迭代对象的迭代器

完成最后一个数据后，再次调用next()函数会抛出StopItertion的异常。

## 一个实现了 __iter__ 和 __next__ 方法的对象，就是迭代器。

```
class MyList(object):
    "自定义一个可迭代对象"
    def __init__(self):
        self.items = []

    def add(self, val):
        self.items.append(val)

    def __iter__(self):
        myiterator = MyIterator(self)
        return myiterator


class MyIterator(object):
    """自定义的供上面可迭代对象使用的一个迭代器"""
    def __init__(self, mylist):
        self.mylist = mylist
        # current用来记录当前访问到的位置
        self.current = 0

    def __next__(self):
        if self.surrent < len(self.mylist.items):
            item = self.mylist.items[self.current]
            self.current += 1
            return item
        else:
            raise StopItertion

    def __iter__(self):
        return self

if __name__ == "__main__":
    mylist = MyList()
    mylist.add(1)
    mylist.add(2)
    mylist.add(3)

    for num in mylist:
        print(num)


```


## 迭代器应用场景
0， 1， 1， 2， 3， 5， 8， 13， 21……

```
class FibIterator(object):
    """斐波那契数列迭代器"""
    def __init__(self, n):
    """
    :param n: int, 指明生成数列的前n个数
    """
    self.n = n
    # current用来保存当前生成到数列中的第几个数了
    self.current = 0
    self.num1 = 0
    self.num2 = 1

def __next__(self):
    if self.current < self.n:
        num = self.num1
        self.num1, self.num2 = self.num2, self.num1 + self.num2
        self.current += 1
        return num
    else:
        raise StopIteration
def __init__(self):
    return self

if __name__ == "__main__":
    fib = FibIterator(10)
    for num in fib:
        print(num, end="")




```

## 并不是只有for循环能接收可迭代对象
```
li = list(FibIterator(15))
print(li)

tp = tuple(FibIterator(6))
print(tp)

```
