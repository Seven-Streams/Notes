# Tensor中的常见操作

```python
import torch
X = torch.arange(12)#创建存有数字0~11的一维张量
print(X.shape)#显示张量的形状
X = X.reshape(3, 4)#将张量转换为3*4的形状
print(X.numel())#张量中的元素个数
Z = torch.zeros((2, 3, 4))#创建一个全0的张量，形状为2*3*4
O = torch.ones((2, 3, 4))#创建一个全1的张量，形状为2*3*4
R = torch.randn((3, 4))#创建一个形状为3*4的张量，其中的数据符合均值为0，标准差为1的正态分布
print(R)
L = torch.tensor([[1, 2, 3], [4, 5, 6]])
print(L)
A = torch.tensor([1, 2, 3, 8])
B = torch.tensor([2, 3, 3, 2])
print(A + B)
print(A - B)
print(A * B)
print(A / B)
print(A ** B)#A中每个元素的B中元素次方
E = torch.exp(A)#转化为e的k次方
print(E)
print(torch.cat((X, X), dim=0))#竖直连接，不改变总列数
print(torch.cat((X, X), dim=1))#水平连接，不改变总行数
print(A == B)#结果也是张量。元素为True和False
print((A == B).sum())#求和，得到单元素张量
T1 = torch.arange(3).reshape((3, 1))
T2 = torch.arange(2).reshape((1, 2))
print(T1 + T2)#broadcasting mechanism,这会自动扩展元素进行计算
print(A[-2])#A的倒数第二个元素
print(A[1:3])#index为2和3的元素
print(X[1, 3])#第一行第三列元素
X[0:2, :] = 12#改变了第二三行所有的元素
print(X)
Y = X
X += Y#这样的操作等价于 X[:] = X + Y; X = X + Y会重新分配内存，不佳
#更新时，使用X[:]=<expression>可以原地更新
W = torch.tensor([1.2])
print(W.item())#这两种方式都可以把单元素张量转化为Py标量
print(float(W))
```

# Panda的使用

```python
import pandas as pd
data = pd.read_csv('data.csv')
print(data)
inputs, outputs = data.iloc[:, 0:2], data.iloc[:, 2]#取索引
inputs = pd.get_dummies(inputs, dummy_na=True)
#该函数会把内容转换为独热编码。
#dummy_na为True，表示会补充缺省值
```

# Linear Algebra

```python
import torch
A = torch.arange(20).reshape((5, 4))
print(A.T)#转置
B = A.clone()#令B等于A的副本。若为B=A，则会导致二者共享相同内存
A_sum0 = A.sum(axis=0)
print(A_sum0)#按行降维。每行的元素相加。
Total = A.sum(axis=[0, 1])#按行按列均相加
print(Total)
print(A.mean(dtype=float))#平均值
sum_A = A.sum(axis=1, keepdims=True)#这样可以保持轴数不变
print(sum_A)
A = A.cumsum(axis=0)#这样得到的是A按行的元素累积总和
print(A)
x = torch.tensor([0, 1, 2, 3])
y = torch.ones(4, dtype=torch.long)
print(torch.dot(x, y))#点积
print(torch.mv(A, x))#矩阵向量积
B = torch.ones(4, 3, dtype=torch.long)
print(torch.mm(A, B))#矩阵矩阵乘积
v = torch.tensor([3.0, 4.0])
print(torch.norm(v))#L2范数
print(torch.abs(v).sum())#L1范数
print(torch.norm(A,dtype=float))#矩阵的弗罗贝尼乌斯范数
```

# Automatic Differentiation

```python
import torch
x = torch.arange(4.0, requires_grad=True)#需要梯度
print(x.grad)
y = 2 * torch.dot(x, x)
print(y)
y.backward()#反向传播函数计算梯度
print(x.grad)
x.grad.zero_()
y = x * x
u = y.detach()#将此前的计算分离，反向传播时不会流经
z = u * x
z.sum().backward()
print(x.grad == u)
```
