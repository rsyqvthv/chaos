# generators

## 概念

A generator is a function that produces a **sequence of results** instead of a single value. Instead of returning a value, you generate a series of values (using the yield statement). Typically, you hook it up to a **for-loop**. 

生成器生成一组结果, 而不是返回数值. 一般内部都会有for-loop

```python
def countdown(n):
 while n > 0:
 yield n
 n -= 1
>>> for i in countdown(5):
... print i,
...
5 4 3 2 1
>>>
```

Calling a generator function **creates an generator object**. However, it **does not start running the function**. yield produces a value, but suspends the function.

The function **only executes on next()**, Function resumes on next call to next(), When the generator returns, iteration stops. 

调用生成器会生成一个生成器对象, 其结果是函数运行的值. 

生成器函数可以通过next()方法真正的一步一步的运行其中的函数, 每次一步.



通常带有return的for-loop循环都会生成一个完整的数值, 占用一定内存.

而如果function的结果从**第一个到任意一个都可以通过算法推演**, 那么只记录这个算法, 就可以获得任意结果, 这样节省内存. 这种机制就是生成器.

## 生成generator方法1

```python
li = [x*2 for x in range(10)] # 生成list

gen = (x*2 for x in range(10)) # 生成generator
```

打印gen的结果可以重复next(gen)来获得, 更多的是使用**for-loop来获得**.

```python
next(gen) 

for g in gen:
    print(g)
```



除了简单的for-loop, 一些复杂些的function也可以变成生成器, 只要满足"可以从第一个元素开始，推算出后续任意的元素"这个规则即可.

## 生成generator方法2

将复杂的函数变为generator, 简单的可以将`print(b)`变为`yield b`就可以了.

generator和函数的执行流程不一样。

函数是顺序执行，遇到`return`语句或者最后一行函数语句就返回。

而变成generator的函数，在每次调用`next()`的时候执行，遇到`yield`语句返回，**再次执行时从上次返回的`yield`语句处继续执行。**

```python
def odd():
    yield 1 # 第一次next()停这里
    yield 3 # 再next()从这里开始, 并停这里.
    yield 5 # 在next()从这里开始, 并停这里.
```

运行:

```python
>>> next(odd())
1
>>> next(odd())
3
>>> next(odd())
5
>>> next(odd())
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
StopIteration
```

## 获取return的方法

但是用`for`循环调用generator时，想拿到generator的`return`语句的返回值, 就必须捕获`StopIteration`错误，返回值包含在`StopIteration`的`value`中：

```python
>>> g = fib(6)
>>> while True:
...     try:
...         x = next(g)
...         print('g:', x)
...     except StopIteration as e:
...         print('Generator return value:', e.value)
...         break
```

要理解generator的工作原理，它是在`for`循环的过程中不断计算出下一个元素，并在适当的条件结束`for`循环。

对于函数改成的generator来说，遇到`return`语句或者执行到函数体最后一行语句，就是结束generator的指令，`for`循环随之结束。



## todo: http://www.dabeaz.com/coroutines/Coroutines.pdf

## 生成器管道 Generators as Pipelines

重点是要明白 `yield` 语句作为数据的生产者而 for 循环语句 作为数据的消费者。当这些生成器被连在一起后，每个 yield 会将一个单独的数据元 素传递给迭代处理管道的下一阶段。这种方式一个非常好的特点是每个生成器函数很小并且都是独立的。

使用这种方式的内存效率很高。适合大量的数据需要处理，但是不能将它们一次性放入内存中的案例。

## Yield as an Expression

