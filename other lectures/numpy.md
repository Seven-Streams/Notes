# 1、创建np数组

一般而言，有六种办法。

## 用python中的list或tuple创建

```python
a_1d = np.array([1, 2, 3, 4])
a_2d = np.array([1, 2], [3, 4])
a_3d = np.array([[1, 2], [3, 4]], [[5, 6], [7, 8]])
```

上面这样，会创建一维，二维，三维的numpy数组。

在使用这种方式的时候，我们可以指定我们希望的类型。比如

```python
a = np,array([127, 128, 129], dtype=np.int8)
# a = array([127, -128, -127])
```

## 使用numpy内置的创建函数

```python
a = np.arange(2, 10, 2)
# a = array([2, 4, 6, 8])
```

类似于python中的方式。但是产生的是一个numpy数组。

```python
a = np.linspace(1., 4., 6)
# a = array([1., 1.6, 2.2, 2.8, 3.4, 4.])
```

可以看到，它的作用是把一个均匀的在一个区间中取k个值。

```python
I = np.eye(3)
#I is an identity matrix.
a = np.eye(3, 5)
# a is a conjunction of a 3*3 indentity matrix and two all-zero columns.
```

这是取恒等矩阵的方法。

```python
d = np.diag([1,2,3])
#一个三乘三的对角阵。值为1,2,3
x = np.diag([1,2,3], 1)
#意为，对角大斜线上方的第k条斜线的元素为1,2,3，说明这是个4*4的矩阵
```

这样可以获得对角矩阵。

```python
a = np.array([1, 2], [3, 4])
b = np.diag(a)
# b = array([1, 4])
```

如果输入的对象是一个二维矩阵，那么会返回一个一维np数组，值为对角线上的元素。

```python
a = np.vander([1, 2, 3, 4], 4)
# a为
# array([[1, 1, 1, 1],
#        [8, 4, 2, 1],
#        [27, 9, 3, 1],
#        [64, 16, 4, 1]])
```

也就是说，最后一列均为1，每一行为对应数字的几何级数。

```python
a = np.zeros((1, 1, 4))
b = np.ones((5, 1))
c = np.random(4, 1, 9)
```

这样子，可以按照我们想要的形状，创建对应数组。

```python
a = np.indices((1, 9, 8))
```

这样子，生成的数组中，其每一维的值，恰等于其每一维的索引号。比如说，a[114][514][1919] = (114, 514, 1919)

## 从已有的np数组变化而来

```python
a = [1, 2, 3, 4, 5, 6]
b = a[:2]
b += 1
# a = array([2, 3, 3, 4, 5, 6])
```

可以看到，这样对b操作，也会影响到原有的a。

```python
a = [1, 2, 3, 4, 5, 6]
b = a[:2].copy()
b += 1
# a = array([1, 2, 3, 4])
```

这样的话，我们就斩断了a与b之间的联系。从而可以对b直接进行操作，而不影响a。

```python
A = np.ones((2, 2))
B = np.eye(2, 2)
C = np.zeros((2, 2))
D = np.diag((-3, -4))
np.block([[A, B], [C, D]])
```

这样，我们可以生成分块矩阵：

$$
\begin{bmatrix}
A&B\\
C&D
\end{bmatrix}
$$

## 从硬盘数据生成

比较常见的方法就是：

```python
np.loadtxt('a.csv', delimiter=',')
```

这种方式我已经习惯会使用了。

剩下两种，就是从字节流，或者其他库函数生成。

# 2、numpy数组的索引

## 单元素索引

```python
x = np.arange(10)
# x[2] == 2
# x[-2] == 8
# x.shape == (10,)
```

如果我们要修改x的形状可以选择：

```python
x.shape = (2, 5)
# or x.shape = (2, -1)
# x[0] = array([0, 1, 2, 3, 4])
# x[1][0] = 5
# x[1, 0] = 5
```

在这种情况下，我们就修改了x的形状。如果填写-1表示缺省，让python自行计算。我们修改了其形状后，可以用x[0]来访问其第一行。有两种方式可以访问单个元素。但第二种方式似乎效率更高。

## 切片

```python
x = np.arange(10)
x = x[1: -3: 2]
# x = array([1, 3, 5])
x = np.arange(10)
x = x[7: 3: -1]
# x = array([7, 6, 5, 4])
```

这样可以控制步长对数组进行切片。

```python
x = np.arange(10)
x = x[5:]
# x = array([5, 6, 7, 8, 9])
x = np.arange(10)
x = x[:5]
# x = array([0, 1, 2, 3, 4])
x = np.arange(10)
x = x[1: 3]
# x = array([1, 2])
```

这种方式，可以从index=k开始，并且获取之后的所有元素。或者，获取到index=k为止的所有元素。如果指定了两端，那么就会按照规则获得中间一段。

```python
x = np.arange(27)
x.shape = (3, 3, 3)
x = x[:2]
# x = array(
#      [[[ 0,  1,  2],
#        [ 3,  4,  5],
#        [ 6,  7,  8]],
#
#       [[ 9, 10, 11],
#        [12, 13, 14],
#        [15, 16, 17]]])
```

如果输入的参数比维数少，那么之后的维数默认全选。

## 维数索引工具

```python
x = np.arange(27)
x.shape = (3, 3, 3)
a = x[..., 0]
b = x[:, :, 0]
# a = b
```

这是一个语法糖。使用省略号，表示之前的参数全选。

```python
x = np.arange(5)
x[:, np.newaxis] + x[np.newaxis, :]
#     [[0, 1, 2, 3, 4],
#      [1, 2, 3, 4, 5],
#      [2, 3, 4, 5, 6],
#      [3, 4, 5, 6, 7],
#      [4, 5, 6, 7, 8]]
```

在上面的式子中，np.newaxis可以同义地替换为None。什么意思呢？相当于可以改变它的维度，比如说，x[:, np.newaxis].shape为[5, 1], x[np.newaxis, :].shape为[1, 5]，然后运用广播机制，就得到了上面的结果。

## 使用numpy整型数组进行索引选择

```python
x = np.arange(10)
b = np.arange([1, 1, 4, 5, 1, 4])
c = x[b]
# c = array([1, 1, 4, 5, 1, 4])
```

也就是说，我们可以用numpy整型数组作为下标运算符中的参数，表示选取。

```python
y = np.arange(35).reshape(5, 7)
a = y[np.array([0, 2, 4]), 1]
b = y[np.array([0, 2, 4])]
c = y[np.array([0,2,4]), np.array([0,2,4])]
# a = array([1, 15, 29])
# c = array([0, 16, 32])
```

即，a为第一维选择0,2,4，第二维均为1。b则为第一维选择0,2,4，第二维全选。c则为选择了[0,0]，[2,2]，[4,4]三个元素。如c这种方式选取的话，两个数组的大小必须相同。

```python
x = np.array([[ 0,  1,  2],
              [ 3,  4,  5],
              [ 6,  7,  8],
              [ 9, 10, 11]
])
rows = np.array([[0, 0],
                 [3, 3]], dtype=np.intp)
columns = np.array([[0, 2],
                    [0, 2]], dtype=np.intp)
y = x[rows, columns]
# y = 
#array([[ 0,  2],
#       [ 9, 11]])
```

用这样的方法，可以在对应的位置获得自己想要的元素。

为了简化这一过程，我们可以这样操作：

```python
```python
x = np.array([[ 0,  1,  2],
              [ 3,  4,  5],
              [ 6,  7,  8],
              [ 9, 10, 11]
])
```

rows = np.array([0, 3], dtype=np.intp)
columns = np.array([0, 2], dtype=np.intp)
y = x[rows[:, np.newaxis], columns]

# y =

# array([[ 0,  2],

# [ 9, 11]])

```
这样可以使用广播机制，自动地进行剩余对象的补全。以此观之，newaxis的一个重要作用就是类似于转置的功效。

```python
x = np.arange(27)
x.shape = (3,3,3)
a = np.array([0,1])
b = x[a,a,a]
c = x[np.ix_(a,a,a)]
# b = array([0, 13])
# c =
# array([[[ 0,  1],
#         [ 3,  4]],
#
#        [[ 9, 10],
#         [12, 13]]])
```

ix_函数可以做到newaxis的效果。

## 布尔数组索引

```python
x = np.array([[1., 2.], [np.nan, 3.], [np.nan, np.nan]])
b = x[~np.isnan(x)]
# b = array([1., 2., 3.])
```

用逻辑函数的方法进行选取。

```python
x = np.array([1., -1., -2., 3])
x[x < 0] += 20
# x = array([ 1., 19., 18., 3.])
```

这样，可以定向地选择出numpy数组中想要的对象。

```python
x = np.arange(35).reshape(5, 7)
b = x > 20
b[:, 5]
# x = array([False, False, False,  True,  True])
```

这样，也可以做到类似的效果。

```python
x = np.array([[0, 1], [1, 1], [2, 2]])
rowsum = x.sum(-1)
a = x[rowsum <= 2, :]
# a = 
# array([[0, 1],
#        [1, 1]])
```

选取了行和小于等于2的所有元素。

```python
x = np.arange(30).reshape(2, 3, 5)
b = np.array([[True, True, False], [False, True, True]])
c = x[b]
```

这样的话，c就选取了x[0, 0, :], x[0, 1, :], x[1, 1, :], x[1, 2, :]

## 我们联合！——基本与高阶操作的混合

高阶操作依旧符合切片的需求。

```python
y = np.arange(35).reshape(5,7)
a = y[np.array([0, 2, 4]), 1:3]
# a =
# array([[ 1,  2],
#        [15, 16],
#        [29, 30]])
```

## 数组的作用域

```python
x = np.ones((2, 2), dtype=[('a', np.int32), ('b', np.float64, (3, 3))])
# x = 
# array([[(1, [[1., 1., 1.], [1., 1., 1.], [1., 1., 1.]]),
#         (1, [[1., 1., 1.], [1., 1., 1.], [1., 1., 1.]])],
#        [(1, [[1., 1., 1.], [1., 1., 1.], [1., 1., 1.]]),
#         (1, [[1., 1., 1.], [1., 1., 1.], [1., 1., 1.]])]],
#       dtype=[('a', '<i4'), ('b', '<f8', (3, 3))])
```

这样，可以认为是一个2*2的矩阵中，每个元素是a和b组成的一个混合型元素。

```python
b = x['a']
# b = 
# array([[1, 1],
#        [1, 1]])
```

可以用这种方式来访问混合元素中的一部分。

## 索引数组赋值

```python
x = np.arange(10)
x[2:7] = 1
# x = array([0, 1, 1, 1, 1, 1, 1, 7, 8, 9])
```

这样可以一起进行赋值。

```python
x = np.arange(10)
x[2:7] = np.arange(5)
# x = array([0, 1, 0, 1, 2, 3, 4, 7, 8, 9])
```

这样也是类似的效果。但是要注意尺寸问题。

```python
x = np.arange(1)
x[np.array([1, 1, 3, 1])] += 1
# x = array([0, 2, 2, 4, 4, 5, 6, 7, 8, 9])
```

如上所示的效果，不复赘述。

## 变量担当索引

```python
z = np.arange(81).reshape(3, 3, 3, 3)
indices = (1, 1, 1, 0:2)
x = z[indices]
# x = array([39, 40])
```

修改indices，我们可以获得不同的值。
