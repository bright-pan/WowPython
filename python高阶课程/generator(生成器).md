## 生成器
生成器是一类特殊的迭代器（generator)


## 创建生成器的方法
```
L = [x * 2 for x in range(5)]
G = (x * 2 for x in range(5))
# L 是一个列表，G是一个生成器

```

## 创建生成器方法2
```
def fib(n):
    current = 0
    num1, num2 = 0, 1
    while current < n:
        num = num1
        num1, num2 = num2, num1 + num2
        current += 1
        yield num
    return "done"


```

在使用生成器实现的方式中，我们将迭代器__next__方法中实现的基本逻辑放到一个函数中来实现，但是将每次迭代返回数值的return换成了yield，此时新定义的函数便不再是函数，而是一个生成器。

## 总结
- 使用yield关键字的函数不再是函数，而是生成器。
- yield关键字有两点作用：
保存当前运行状态（断点），然后暂停执行，即将生成器（函数）挂起
将yield关键字后面表达式的值作为返回值返回，此时可以理解为起到了return的作用
可以使用next()函数让生成器从断点除继续执行，即唤醒生成器（函数）

## send() 唤醒
使用send()函数可以在唤醒的同时向断点处传入一个附加数据。
