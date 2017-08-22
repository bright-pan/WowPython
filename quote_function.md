## 闭包
### 函数引用

```
# 定义一个函数
def test(number):
    # 在函数内部再定义一个函数，并且这个函数用到了外边函数的变量，那么将这个函数以及用到的一些变量称之为闭包

    def test_in(number_in):
        print("in test_in 函数， number_in is %d" % number_in)
        return number + number_in
        # 这里返回的就是闭包的结果
    return test_in

# 给test函数赋值，这个20就是给参数number
ret = test(20)

# 注意这里的100其实给参数number_in
print(ret(100))  
print(ret(200))


```

## 看一个闭包的实际例子

```
def line_conf(a, b):
    def line(x):
        return a * x + b
    return line

line1 = line_conf(1, 1)
line2 = line_conf(4, 5)

print(line1(5))
print(line2(5))

```

> 闭包思考
1. 闭包似优化了变量，原来需要类对象完成的工作，闭包也可以完成
2. 由于闭包引用外部函数的局部变量，则外部函数的局部变量没有及时释放，消耗内存

## 修改外部函数中的变量
```
# python3中
def counter(start = 0):
    def incr():
        nonlocal start
        start += 1
        return start
    return incr

c1 = counter(5)
print(c1())

```

```
# python2 中

def counter(start = 0):
    count = [start]
    def incr():
        count[0] += 1
        return count[0]
    return incr

c1 = counter(5)
print((c1)) #6
print((c1)) #7

```

## LEGB 规则
locals → enclosingfunction → globals → builtins

```
a = 1     # 全局变量 globals

def fun():
    a = 2      # 闭包变量 enclosing

    def inner_fun():
        a = 3      # 局部变量 locals
        print("a = %d" % a)
    return inner_fun

f = fun()
f()


```

- builtins, 内建模块的命名空间。

python在启动的时候会自动为我们载入很多的内建函数、类，比如dict, list, type, print,
这些都位于__builtin__ 模块中，可以使用dir(__builtin__)来查看。
