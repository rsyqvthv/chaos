# Python代码

python 的代码风格是非常优雅、明确和简单. 

```python
import this
```

> Tim Peters的《Python的禅意》。
>
> 美丽的比丑陋的好。
> 明确的比含蓄的好。
> 简单的比复杂的好
> 复杂的比庞杂的好
> 扁平的比嵌套的好。
> 稀疏的比密集的好。
>
> 可读性很重要。
>
> 特殊的情况并不特殊，不足以打破规则。
> 虽然实用性要胜过完美。
>
> 错误永远不应该让它无声的通过。
> 除非是刻意让其沉默。
>
> 在面对模棱两可的情况下，拒绝猜测的诱惑。
>
> 应该有一个, 最好只有一个, 简明的方法去实现.
> 虽然这种简明一开始可能并不明显，除非你是荷兰人(python的发明之一是个荷兰人, 觊觎python的开始并不简明. 那时是perl的天下, 是一个可以用多种方法实现同一个任务的编程语言)。
>
> 现在去做总比不做要好。
> 虽然不做要比当下的情况好。
>
> 如果执行很难解释清楚，那这就是个坏执行。
> 如果执行很容易解释，那它只可能是个好执行。
>
> 命名空间是一个非常棒的想法, 我们要多多使用它!

## 寻求帮助

获取一个模块的使用方法: 首先导入模块, 然后使用`help(module)` 或者 `dir(module|function)`, 前者详细, 后者简要.

```python
import datetime
help(datetime.datetime)
```

```python
import datetime
dir(datetime.datetime)
```

在cmd中, 可以使用更简单的方法, 使用`pydoc`, 列出的是详细版.

```cmd
python -m pydoc datatime.datetime
```



## 灵活的赋值

```python
a,b,c = 1,2,3
```

```python
a,b,*c,d=(1,2,3,4,5,6)
print("a=",a,"b=",b,"c=",c,"d=",d)
>>> a= 1 b= 2 c= [3, 4, 5] d= 6
```



## 使用下划线分隔大数

```python
num1 = 10_000_0000 # 用下划线让数字更易读
num2 = 10_000_000
total = num1 + num2 
print(f"{total:,}") # 增加逗号分割
# 110,000,000 
```



## 输入密码时使用 getpass

```python
>>> from getpass import getpass
>>> password2 = getpass("请输入密码：")
请输入密码： # 这里不显示输入
>>> password2
'123456'
```



## 循环遍历用enumerate

```python
for index, item in enumerate(['a', 'b', 'c']):
  print(index, item)
```

使用enumerate同时得到index和item, 比 `for i in range(len(li))` 要好.

## 使用 zip

让合并两个list更加清晰.

```python
names = ['艾米莉亚·克拉克','基特·哈灵顿','麦茜·威廉姆斯','彼特·丁拉基']
roles = ['丹妮莉丝·坦格利安','琼恩·雪诺','艾莉亚·史塔克','提利昂·兰尼斯特']

for name,role in zip(names,roles):
    print(f"{name} 扮演 {role}")
```

```python
>>> a=['a','b','c']
>>> b=[1,2,3,4,5]
>>> c=['A','B','C','D']
>>>
>>> list(zip(a,b,c)]
[('a', 1, 'A'), ('b', 2, 'B'), ('c', 3, 'C')]
```



## PEP8

`CamelCase` 作为类的名字

`UPPER_WITH_UNDERSCORES` 作为常量

`lower_with_underscores` 作为变量, 方法, 模块的名称.

避免使用lambda.

## 善用单行(推导式)

- 单行可以用在 列表, 集合和字典中. 
- 推导式指由一个序列推导出另外一个序列.
- 通常包含: 输入序列, 判定表达, 运算变量, 输出序列.

优雅的方式:

```python
a_list = [1, 2, 3, 4]
added_two_to_even = [x+2 for x in a_list if x%2 == 0]
```

复杂一些的可以用map和filter, 但可读性差一些:

```python
map(lambda e: e**2, filter(lambda e: type(e) == types.IntType, a_list))
```

## 三元表达式

```python
condition = True
x = 1 if condition else 0
print(x)
```



## 使用上下文管理器with自动关闭文件

```python
with open(file, 'r') as f:
  input = f.read()
```

## 使用迭代器和生成器

@question 有待了解

## 使用 map 函数

```
map(function, iterable, ...)
```

第一个参数 function 以参数序列中的每一个元素调用 function 函数，返回包含每次 function 函数返回值的新列表。

```python
map(lambda x: x ** 2, [1, 2, 3, 4, 5])  # 使用 lambda 匿名函数
>>> [1, 4, 9, 16, 25]
```

## 使用 reduce 函数

```
reduce(function, iterable[, initializer])
```



用传给 reduce 中的函数 function（有两个参数）先对集合中的第 1、2 个元素进行操作，得到的结果再与第三个数据用 function 函数运算，最后得到一个结果。

```python
reduce(lambda x, y: x+y, [1,2,3,4,5])  # 使用 lambda 匿名函数
>>> 15
```



## 善用 itertools

```python
from itertools import combinations
names = 'ABC'
for combination in combinations(names, 2):
    print(combination)
''' Output -
    ('A', 'B')
    ('A', 'C')
    ('B', 'C')
'''
```

## 善用 collections

这又是一个值得使用的标准库 collections，它提供替代内置的数据类型的多个容器，如 defaultdict、OrderedDict、namedtuple、Counter、deque 等，非常使用，而且比自己实现要安全稳定的多。

@question: 有待了解

## 不要过度使用类

在使用 Python 时，可以在函数和模块的帮助下复用代码。除非绝对需要，否则不必创建类。

# incoming

[python 基础系列--可迭代对象、迭代器与生成器](https://mp.weixin.qq.com/s?__biz=MzU0OTg3NzU2NA==&mid=2247483827&idx=1&sn=6a661c78b3f0db2e4c94cee1ddc3b036&chksm=fba863e0ccdfeaf628a112bcfe9401b3933fe5b359e17ff4345d6fcfddf7103c4460cd3d1c5d&scene=21#wechat_redirect)

[6 个值得玩味的 Python 代码](https://mp.weixin.qq.com/s?__biz=MzU0OTg3NzU2NA%3D%3D&idx=1&mid=2247484126&scene=21&sn=3e3a65fb5a13ceab8f44efb8fee4690d#wechat_redirect)

