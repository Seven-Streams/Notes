# Optimization

## Lec 2

Weierstrass极值定理：

$$
S\ \text{is compact},f:S\to\R\text{ is continuous on }S,f \text{ is bounded and has both}\\
\text{min and max values.}
$$

方向导数：

$$
\nabla_vf(x_0)=\lim_{h\to 0}\frac{f(x_0+hv)-f(x_0)}{h}
$$

偏导数就是取单位向量。

可微：

$$
\lim_{x\to x_0}\frac{||f(x)-f(x_0)-J(x-x_0)||}{||x-x_0||}=0
$$

其中，$\text{d}f(x_0)=J,\nabla f(x_0)=J^T$

一般地，有：

$$
\nabla_vf(x_0)=\nabla f(x_0)^Tv
$$

一阶必要条件：

$$
f\text{ is diffenrential, }\text{for any feasible direction }v,\nabla_v f(x^*)\geq 0
$$

如果$x^*$是个内点，那么上式应为$\nabla f(x^*)=0$

Schwarz's theorem：

$$
f:\Omega\subset\R^n\to\R,x\in\Omega \text{ s.t }B(x,\varepsilon)\sub\Omega,f\text{ has continuous }\frac{\partial^2f}{\partial x_ix_j}\\
\text{forall }i,j,\text{then }\frac{\partial^2f}{\partial x_ix_j}=\frac{\partial^2f}{\partial x_jx_i}
$$

二阶必要条件：

$$
f\text{ is twice continuously differentiable, }\forall v\in\R^n\\
v^T\nabla^2f(x^*)v\geq 0
$$

Sylvester's criterion:

- $A$ 是正定的，等价于所有顺序主子式大于零。

- $A$ 是半正定的，等价于所有主子式不小于零。

- 如果所有顺序主子式大于零，且$\text{det}(A)\geq0$，那么$A$ 是半正定的。

二阶充分条件：

$$
f:\R^n\to\R\text{ is a twice continuously differentiable function, }\\
\nabla f(x^*)=0,\nabla^2f(x^*)>0
$$

## Lec 3

### lines, rays and segments

通过不相同两点$x,y$的直线可以表示为：

$$
\theta x+(1-\theta)y,\theta\in\R
$$

类似地，射线和线段就可以表示为：

$$
\theta x+(1-\theta)y,\theta\geq0\\
\theta x+(1-\theta)y,\theta\in[0,1]
$$

为了简便，在之后，我们记$1-\theta$为$\bar\theta$.

### convex sets

我们称一个$\R^n$中的集合，当且仅当：

$$
x\in C,y\in C,\theta\in[0,1]\implies\theta x+\bar\theta y\in C
$$

我们称这样，系数和为1的组合为$x,y$的凸组合。

空集，直线类，点，超平面，半平面，仿射空间，凸多面体$\{x|Ax\leq b\}$不等号表征各个元素比较，范数球，椭圆，半正定矩阵等都是凸的。

仿射空间$\{x|Ax=b\}$是凸多面体。因为等号可以由两个不等式组合得到。

### convexity preserving operations

两个凸集取交，还是凸集。

将凸集进行仿射变换，结果还是凸集。

仿射变换的逆变换也是保凸的。

### convex hull

考察$x_1,...,x_m\in \R^n$，我们称：$\sum_{i=1}^m\theta_ix_i$为前述点的凸组合。其中，我们规定$\theta_i\geq0,\sum_{i=1}^m\theta_i=1$

如果前述点在一凸集中，那么这样的凸组合一定在该凸集中。这一点可以通过两个两个逐次吃下去来证明。

我们称包含集合$S$的最小凸集为$S$的凸包，记作$\text{conv}(S)$

实际上，凸包就是$S$中的凸组合构成的集合。

### simplexes

考虑点$x_0,...,x_m\in\R^n$，我们称这些点是仿射独立的，如果$x_i-x_{i-1}$之间全都线性独立。

仿射独立的充要条件是$\sum_{i=0}^mc_i=0,\sum_{i=0}^mc_ix_i=0\implies\forall i\in[m],c_i=0$

一个m维的单纯形，指的是给出的m+1个仿射独立点的凸包。

符合直觉的，零维单纯形是个点，一维单纯形是个线段，二维单纯形是个三角形，三维单纯形是个四面体。

我们称由标准基向量构成的单纯形为probability n-simplex，它应该在n+1维中存在。我们称由零向量和所有标准基向量构成的单纯形为unit n-simplex，它在n维中存在。

单纯形实际上可以看作由$\R^m$到$\R^n$的一个线性变换。

### convex cones

我们称一个集合是个锥，如果$x\in C\implies\theta x\in C,\theta\geq0$

凸锥，就是凸的锥。从直觉上看，凸锥感觉像是几条锥边封闭出的一个空间。

一个集合是凸锥，当且仅当：

$$
x_1,x_2\in C,\theta_1,\theta_2\geq0\implies \theta_1x_1+\theta_2x_2\in C
$$

我们称$x_1,...,x_m$的锥组合为：

$$
\sum_{i=1}^m\theta_ix_i,\forall i\in[m],\theta_i\geq0
$$

我们称一个集合$S$的锥包(conic hull)为包含一个$S$的最小凸锥，记作$\text{cone}(S)$

### projection onto convex set

我们称$x$与集合$C$之间的距离为$\text{dist}(x,C)=\inf_{z\in C}||x-z||$

如果这样的$C$是非空的，封闭的并且是凸的，那么一定存在唯一的$\hat x$，使得$\text{dist}(x,C)=||x-\hat x||$，我们把这样的$\hat x$称作$x$在$C$上的投影，记作$P_C(x)$.显然，一个点的投影倘若等于其本身，那么它一定在$C$中。

从直觉上想，封闭的在保证存在性，凸在保证唯一性。

如果$C$是非空的，封闭的，凸的，那么$<x-\hat x,z-\hat x>\leq 0,z\in C$，也就是说，这些向量之间的夹角一定不是锐角。

投影运算是非扩张的。也就是说，$||P_C(x)-P_C(y)||\leq||x-y||$

如果C是非空的，封闭的，并且是凸的，那么$x_0\not\in C,\exists w\in \R^n-\{0\},s.t. \sup_{x\in C}<w,x>\ <\ <w,x_0>$

这是因为$wx=<w,x_0>$确立了一个超平面。从直觉上想，这在描述外点和闭凸集之间线性可分。

### supporting and separating hyperplane theorems

我们考虑$\partial C$上一点$x_0$，那么存在超平面$P=\{x:w^Tx=w^Tx_0\}$，如果其满足：$<w,x>\leq<w,x_0>,\forall x\in C$，那么我们称这样的超平面为集合$C$在$x_0$处的支撑超平面。对于非空凸集而言，这样的支撑超平面在边界处总是存在的。

凸集具有很好的性质，它的内点与其闭包的内点相同。它的边界点与其闭包的边界点也相同。

对于两个非空不相交凸集$C_1,C_2$而言，它们一定可以被一个超平面可分。也就是说，$\exist w\in \R^n-\{0\},b\in \R,w^Tx\leq b, x\in C_1;w^Tx\geq b,x\in C_2$

具体的证明方式，可以考虑$C:\{x|x=x_1-x_2,\forall x_1\in C_1,\forall x_2\in C_2\}$由于这两个集合之间是不相交的，因此零向量一定不在这个集合中。

因此，我们只需要考虑$<w,x>\leq 0,\forall x\in C$。之后可得。

Farkas' lemma:$A\in\R^{m\times n},b\in\R^m$，那么这两个集合当中有且仅有一个是空的：

$$
S_1=\{x\in\R^n:Ax=b,x\geq0\}\\
S_2=\{y\in R^m:A^Ty\leq 0,b^Ty>0\}
$$

第一个集合是空集，当且仅当$b$在$\text{cone}(A)$内。$A^Ty\leq 0$等价于所有所有$\text{cone}(A)$内的点$z$,有$z^Ty\leq 0$
