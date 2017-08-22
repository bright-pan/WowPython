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
re.match是用来进行正则匹配检查的方法，若字符串匹配正则表达式，则match方法返回匹配对象（Math Object）。否则返回None(注意不是空字符串)。

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

## search方法
```
import re
result =re.search("itcast","hello itcast")
result.group()
# "itcast"

```

## 表示数量
## 匹配邮箱账号
re.search("^[0-9_A-Za-z]{4-20}@163\.com$", "sdjfklsadjlfkasjfl@163.com").group()
