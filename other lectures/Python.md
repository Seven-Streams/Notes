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
