## 正则表达式

## re模块操作

```
# re 模块的使用过程
# -*- coding:utf-8 -*-

# 导入re模块
import re

# 使用match方法进行匹配操作
result = re.match(正则表达式，要匹配的字符串)

# 如果上一步匹配到数据的话，可以使用group方法来提取数据
result.group()

```
re.match是用来进行正则匹配检查的方法，若字符串匹配正则表达式，则match方法返回匹配对象（Math Object）。
否则返回None(注意不是空字符串)。

re模块示例（匹配以itcast开头的语句）

```
# -*- coding:utf-8 -*-

import re

result = re.match("itcast", "itcast.cn")
result.group()

```

## 表示字符

| 字符     |功能                     |
| :------ | :-------------           |
| .       | 匹配任意一个字符（除了\n） |
| []      | 匹配[]中列举的字符         |
|\d       | 匹配数字0-9               |
|\D       | 匹配非数字，即不是数字     |
| \s      | 匹配空白，空格或Tab        |
|\S       | 匹配非空白                |
|\W       | 匹配非单词字符            |

### 示例

```
import re

ret = re.match(".", "a")
ret.group()

ret = re.match(".", "M")
ret.group()


```
### 示例2：[]

```
import re
# 如果hello的首字符小写，那么正则表达式需要小写的h
ret = re.match("h", "hello Python")
ret.group()

# 如果hello的首字符大写，那么正则表达式需要大写的H
ret = re.match("H", "Hello Python")
ret.group()
ret = re.match("[hH]", "Hello Python")
ret.group()



```
```
## 原始字符串
mm = "c:\\a\\b\\c"

print(mm) # c:\a\b\c
re.match("c:\\\\", mm).group()   # "c:\\"

ret = re.match("c:\\\\", mm).group()
print(ret)  # c:\

ret = re.match(r"c:\\a", mm).group()
print(ret)   # c:\a

ret = re.match(r"c:\a", mm).group()  # 报错
```
## search方法
```
import re
result =re.search("itcast","hello itcast")
result.group()
# "itcast"

```

## 表示数量
| 字符 | 功能     |
| :------------- | :------------- |
|   *      | 匹配前一个字符出现0次或者无线次，即可有可无     |
|  +     | 匹配前一个字符出现1次或者无限次，即至少有1次   |
|   ？    |  匹配前一个走出现1次或者0次，即要么有1次，要么没有  |
|  ｛m｝     |  匹配前一个字符出现m次  |
|   ｛m,｝    | 匹配前一个字符至少出现每次   |
|    ｛m,n｝   |  匹配前一个字符出现从m到n次  |


示例：
```
import re

ret = re.match("[A-Z][a-z]*", "Mm")
ret.group()

ret = re.match("[A-Z][a-z]*", "Aabcdef")
ret.group()

```
 示例2:
 ```
 import re

 ret = re.match("[a-zA-Z_]+[\w_]*", "_name")
 ret.group()

 ret = re.match("[a-zA-Z_]+[\w_]*","_name")
 ret,group()

 ret = re.match("[a-zA-Z_]+[\w_]*", "2_name")
 ret.group()

 ```
示例3：
```
# 匹配出0-99之间的数字

import re

ret = re.match("[1-9]?[0-9]", "7")
ret.group()

ret = re.match("[1-9]?[0-9]", "33")
ret.group()

ret = re.match("[1-9]?[0-9]", "09")
ret.group()

```

示例：
需求：匹配8-20位密码，可以是大小写，英文字母、数字、下划线

```
import re

ret = re.match("[a-zA-Z0-9_]{6}","12a324ef")
ret.group()

ret = re.match("[a-zA-Z0-9_]"{8,20}","4321423fdfewq234324fefwe")
ret.group()



```


## 匹配邮箱账号
re.search("^[0-9_A-Za-z]{4-20}@163\.com$", "sdjfklsadjlfkasjfl@163.com").group()

## 表示边界

| 字符 | 功能     |
| :------------- | :------------- |
| ^       | 匹配字符串开头       |
|$|匹配字符串结尾|
|\b|匹配一个单词的边界|
|\B|匹配非单词的边界|

## 匹配分组

| 字符 | 功能     |
| :------------- | :------------- |
|    丨   | 匹配左右任意一个表达式      |
|（ab)|将括号中字符作为一个分组|
|\num|引用分组num匹配到的字符串|
|(?P< name >)|分组起别名|
|(?P=name)|引用别名为name 分组匹配到的字符串|


## python 贪婪和非贪婪
```
s = "This is a number 234-342-432-342"
r = re.match(".+(\d+-\d+-\d+-\d+)", s)
r.group(1)

r = re.match(".+?(\d+-\d+-\d+-\d+)", s)
r.group(1)
