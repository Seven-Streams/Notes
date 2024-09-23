# list

list$\iff$ vector

支持下标访问。

append(x) $\iff$ push_back(x)

del(i) $\iff$ erase(it)

pop(i) $\iff$ erase(it)

pop() $\iff$ pop_back()

其中，pop方法有返回值。返回值为被删除的元素。

remove(x) $\iff$ erase(find(x))

insert(i, x)  $\iff$ insert(it, x)

sort：永久排序。

sorted：暂时性排序。

reverse：永久反向。

len() $\iff$ size()

```python
items = [1, 2, 3, 4, 5]
for item in items:
    print(item)
```

遍历。

```python
numbers = list(range(1,6)) 
print(numbers)
```

这样会输出1,2,3,4,5。以1为begin，6为end。

```python
even_numbers = list(range(2,11,2)) 
print(even_numbers)  
```

类似地。步长为2，仅此而已。

对于数值列表，我们有min，max，sum这些函数。

具有和numpy一样的切片规则：从begin到end。

在python中，直接进行列表拷贝，不会产生一个新的副本，实际上是对原有列表的一个引用。如果要复制x这个列表，可使用x[:]表示之。

元组：使用圆括号的列表。并且长度不可变。

在列表中，我们可以使用

```python
a = [1, 2, 3]
print(5 in a)
print(6 not in a)
```

这样的方式可以达到vector中count的效果。

列表作为if语句的条件，那么为空的情况下，返回false，否则返回true。

# 条件判断

python中具有elif关键字。可以与if连用，也可以和else连用，形成if-elif-else结构。

# Dictionary

在python中，我们使用大括号来表示字典。可以使用类似于cpp中map的方式，即通过下标进行新增键值对。同样的，我们可以通过下标中填入键，从而实现对值的访问。要想删除键值对，我们只需要使用del函数，比如del test['to_delete']即可。to_delete为键值。

```python
map = {}
map[0] = 0
map[1] = 1
map[2] = 2
for key, value in map.items():
```

使用这样的方式，可以实现对字典的遍历。

```python
map = {}
map['a'] = 0
map['b'] = 1
map['c'] = 2
for key in map.keys():
```

这样是对键的遍历。

需要注意的是，dictionary不同于map，在遍历输出的过程中顺序是不保证的。所以，我们可以使用这样的句子来保证输出的顺序性。字典的键值类型可以是不同的。

```python
map = {}
map['a'] = 0
map['b'] = 1
map['c'] = 2
for key in sorted(map).keys():
```

类似的，使用values方式，可以实现对值的遍历。

在python中，也具有set类型。set可以认为是不可重复的list。

在字典中，我们也可以将列表和字典存储在其中。

# 函数

python中的函数，除非传入常量，不然都是传址进行操作的。

```python
def A(*paras):
    ...
```

使用这样的单星号方式，可以传入不定长的参数。

```python
def A(**paras):
    ...
```

使用这样的双星号方式，可以传入不定长的关键字参数。

```python
from A import *
```

使用这样的方式，可以从模块中导入所有的函数。

# 类

```python
def __init(self, A, B):
    ...
```

这是一个默认的方法。可以类比于Cpp中的构造函数。创建实例的时候会自动地进行调用。self类似于Cpp中的this指针，实现了对本身的调用。

在定义的过程中，有一点和Cpp中不同。假定类中有一个名为name的成员变量，在Cpp中，我们只需要简单地写name就可以实现对这个成员的使用。但是在Python中，则不可如是。应当使用self.name实现对自身成员变量的调用。

在定义成员函数的过程中，一般都会把第一个参数设置为self，从而实现对自身的引用。

Python中的类依旧可以实现继承。可以使用这样的代码：

```python
super().__init__(paras)
```

这一点和Cpp中还是比较类似的。实现了委托构造。

子类中依旧可以实现对父类函数的重载。但是，不需要父类声明为虚函数。非常方便。

# Python的IO

Python中实现对文件的读入，采用如下的代码。

```python
with open('test.txt') as file:
    content = file.read()
    print(content)
```

read函数在到达文件末尾后，会返回一个空行。是故，会多打印一行空白。

但是，我们可以使用rstrip函数，从而实现对空行的跳过。比如，我们可以改写为

```python
print(content.rstrip())
```

windows系统中，我们使用的是反斜杠来表示相对路径中的层次关系。其他系统中，则是使用/。

如果我们想要逐行进行读取，那么我们可以使用这样的代码。

```python
with open('test.txt') as file:
    for line in file:
        print(line)
```

同样的，在每次读取时都会多产生一行空白。这是因为换行符的存在。

```python
with open('test.txt') as file:
    lines = file.readlines()
for line in lines:
    print(line)
```

使用这种方式，我们就是把所有的文本全部读入到了一个列表中。列表中的每一个元素，即为每一行。

```python
with open('114514.txt', 'w') as file:
    file.write('好')
```

使用这种方式，我们可以实现文件写。并且，如果欲使对象进行换行。则须在最后添上一个换行符。

如果我们不需要新建一个文件，那么我们可以将'w'改成'a'。

在python中，我们使用try-except来处理异常，效果类似于try-catch。在except块后，我们可以使用一个else块，来处理除了异常外的其他情况。

使用split函数，可以将读入的文件流分块。其会根据空格将文件流切片。

Python中有个语句pass，从而表示让Python什么都不做。

```python
person1 = True
person2 = Fsonalse
if person1:
    print('You agree!')
else:
    pass
if person2:
    print('You agree!')
else:
    pass
```

此外，我们可以使用json库来实现对json文件的读写。

```python
import json
with open('x.json', 'w') as file:
    a = [1, 2, 3]
    json.dump(a, file)
```

如是，我们就实现了对json文件的写入。如果我们想要读出对应的内容，那么我们可以使用json.load函数。

```python
with open('x.json') as file:
    a = json.load(file)
```

如是，便可从json文件中读出想要获得的数据。

# 测试代码

类似于assert，在python中，我们可以引入unittest库。

```python
self.assertEqual(a, 12313)
```

类似的方法还有assertNotEqual,assertTrue, assertFalse, assertIn, assertNotIn

这样，显然就是在判断是否相等。在最后，我们可以用这样的代码来启动测试。

```python
unittest.main()
```

所有以test_开头的方法都会自动执行。

对于要测试的类，我们可以引入一个setup()方法，从而达到在开始测试使创建出一个用setup方法产生的类进行测试。
