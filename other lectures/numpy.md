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
# a = [127, -128, -127]
```

## 使用numpy内置的创建函数

```python
a = np.arange(2, 10, 2)
# a = [2, 4, 6, 8]
```

类似于python中的方式。但是产生的是一个numpy数组。

```python
a = np.linspace(1., 4., 6)
# a = [1., 1.6, 2.2, 2.8, 3.4, 4.]
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
# b = [1, 4]
```

如果输入的对象是一个二维矩阵，那么会返回一个一维np数组，值为对角线上的元素。

```python
a = np.vander([1, 2, 3, 4], 4)
# a为
# [[1, 1, 1, 1],
#  [8, 4, 2, 1],
#  [27, 9, 3, 1],
#  [64, 16, 4, 1]]
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
# a = [2, 3, 3, 4, 5, 6]
```

可以看到，这样对b操作，也会影响到原有的a。

```python
a = [1, 2, 3, 4, 5, 6]
b = a[:2].copy()
b += 1
# a = [1, 2, 3, 4]
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
