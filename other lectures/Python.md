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
