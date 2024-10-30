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

所有的锥包都是封闭的。

## convex functions

凸函数的定义：

- $\text{dom}(f)=S$是个凸集。

- $\forall x, y\in S,\theta\in[0,1],f(\theta x+\bar\theta y)\leq\theta f(x)+\bar\theta f(y)$

也就是琴生不等式成立。

严格凸函数的定义：上述第二点改为$\theta\in(0,1),f(\theta x+\bar\theta y)<\theta f(x)+\bar\theta f(y)$

- $f凸\iff -f凹$

- $f严格凸\iff -f严格凹$

对于一个凸函数$f$而言，其上相异两点$x,y$，下列两条中有且只有一条成立：

- $f(\theta x+\bar\theta y)<\theta f(x)+\bar\theta(y),\theta\in (0,1)$

- $f(\theta x+\bar\theta y)=\theta f(x)+\bar\theta(y),\theta\in[0,1]$

严格凸，实际上再说第二部分是不存在的，也就是说没有哪部分可以用$y=w^T x+b$的形式来表示。

也就是说，函数曲线要么在函数两点连线的下方，要么就是连线。不能和连线有别的相交点。

凸函数的零阶条件：

$$
f\ is\ convex\iff\forall x\in \text{dom}(f),\forall d,g(t)=f(x+td)\ is\ convex\ \\
on\ \text{dom}(g)=\{t:x+td\in\text{dom}(f)\}
$$

这件事情实际上在描述，从任何一个超平面去截这个函数，在切面上应该是凸的。

对于一个凸函数，如果我们想把它的定义域从$S$扩展到$R^n$，那么我们只需要给所有不在$S$中的点定义为$+\infin$即可。这两个函数的凸性是相同的。

凸函数的一阶条件：

可微函数$f$定义在一个开凸集上，那么$f\ is\ convex\ \iff f(y)\geq f(x)+\nabla f(x)^T(y-x),\forall x, y\in \ \text{dom}(f)$

这件事情在描述切线放缩法。

如果我们要求$x,y$相异，把$\geq$改为$>$，那么就变成了严格凸的充分必要条件。

因此，对于凸函数而言，如果$\nabla f(x)=0$，那么这个点一定是全局最小值。

凸函数的二阶条件：

$$
f\ is\ convex\iff\nabla^2f(x)\ is\ positive\ semidefinite.
$$

但是，$\nabla^2 f(x)\ is\ positive\ semidefinite$为$f(x)$是严格凸的充分不必要条件。但是对于二次函数$x^TQx+b^Tx+c$而言($Q\ is\ a\ symmetric$)，这一点是充要条件。因为$\nabla^2f(x)=2Q$

对于凸函数而言，如果有局部最小值，那么一定有全局最小值。但是，凸函数不一定有局部最小值。

对于严格凸函数而言，全局最小值如果存在，一定只有一个点。但是，如果全局最小值只可以在一个点处取到，并不意味着这是个严格凸函数。比如绝对值函数。

**sublevel sets**（下水平集）：在定义域中，所以函数值小于某个值$\alpha$的自变量所构成的集合，记作$C_\alpha$

凸函数的下水平集，和凹函数的上水平集都是凸集。但是，非凸函数的下水平集可能都是凸集。比如$\sqrt {|x|}$

epigraph:$f:S\sub \R^n\to \R,\text{epi}\ f=\{(x,y)\in \R^{n+1}:x\in S, y\ge f(x)\}$

定理：$f\ is\ convex\iff \text{epi}\ f\ is\ a\ convex\ set$

凸集的投影，也一定是凸集。

凸函数的一阶条件，暗示着$f(x_0)+\nabla f(x_0)^T(x-x_0)$是$\text{epi}\ f$ 的支撑超平面。

几个不等式：

- Jensen's inequality:$f(\theta x+\bar\theta y)\leq\theta f(x)+\bar\theta f(y),\theta\in [0,1],f\ is\ convex, x,y\in \text{dom}(f)\\=:\theta=0,1$

- Holder's inequality:$\sum_{i=1}^n|x_iy_i|\leq||x||_p||y||_p,p\in(1,+\infin)\\ =:x(y)=0$

- Minkowski's inequality:$||x+y||_p\leq ||x||_p+||y||_p,p\in(1,+\infin)$

### Convexity-preserving operations

- 函数的锥组合，$f(x)=\sum_{i=1}^mc_if_i(x),c_i\ge 0$

- 仿射变换，$f(x)=g(Ax+b)$

- 函数的复合，$f(x)=h(g_1(x),...,g_m(x))$

- 逐点取最大值，即$f(x)=\sup_{i\in I}f_i(x)$

- 部分最小值，$f(x)=\inf_{y\in C}g(x,y)$

函数的锥组合中，不能使用减、乘、除运算。

对于函数的复合而言，我们有：

- $h\ is\ convex,\ h\ is\ increasing,\ g\ is\ convex\implies f\ is\ convex$

- $h\ is\ convex,\ h\ is\ decreasing,\ g\ is\ concave\implies f\ is\ convex$

- $h\ is\ concave,\ h\ is\ increasing,\ g\ is\ concave\implies f\ is\ concave$

- $h\ is\ concave,\ h\ is\ decreasing,\ g\ is\ convex\implies f\ is\ concave$

求二阶导时可以观察到这一点。对于定义域延拓，相似的结果也成立。

逐点取最小值的话，结果不一定是个凹函数。我们对它不能保证任何事情。

## Linear Programming

线性规划问题，就是求一个多元线性函数在约束条件下的最值问题。所有的不等式约束条件，我们都可以通过乘上负一来改变不等号的方向。同时，所有的等式约束都可以用两个不等式约束来表示。从而，所有的约束条件都可以被表示为小于不等式。同时，我们可以把所有的变量要求是非负的。我们可以通过在不等式约束的每一个式子上加上一个松弛变量，把不等式化为等式。这样就可以把约束条件写为$Ax=b$的形式。通过对每一行的系数操作，我们也可以保证$b$是一个全非负的向量。同时，我们要求所有松弛变量都是非负的。然后，我们可以把每个变量化为$x_i^+-x_i^-$的形式。这样可以保证$x_i^+$和$x_i^-$都是非负的。

满足上面这一串要求的线性规划问题形式，我们称之为线性规划的标准形式。

### 线性规划基本定理

线性规划问题的最优解如果存在，那么一定是顶点。

我们定义，如果$x\in R^n$是一个顶点，那么至少有$n$个线性独立的约束条件在$x$处取等。

我们定义，$x\in R^n$是凸集$C$的极点，如果它不能被表示为其他点的凸组合。对于所有的多面体$\{x|Ax\leq b\}$而言，顶点一定是极点，极点一定是顶点。多面体中有极点，当且仅当$P$中不包含直线，并且$P\neq \empty$.

因此，一种朴素的求解方法，就是把每一个顶点都枚举一遍。

### 单纯形法

我们称两个顶点是邻居，当且仅当它们都对同样的$n-1$个约束取等号。

单纯形法的主要思路，是从原点开始迭代，然后通过换元的方式增大我们的函数值。但问题是，原点并不总是一定在可行域内。如果我们已经发现$Ad\leq b$，那么我们可以令$y=d-x=y^+-y^-$，这样可以保证所有变量都非负。所以，对于约束条件$Ax=b$，我们可以将其改写为$Ax+s=b$，其中显然有一个解$x=0,s=b$。这样，我们就解决了可能找不到可行解的情况。然后，我们可以检查$s=0$是否在可行域内。

### 对偶法

考虑这样的问题：

$$
Q:\max(-b^Ty),s.t.\ -A^Ty\le -c, y\ge 0\\
Q:\min(-c^Tx),s.t.\ -A^Tx\ge -b,x\ge 0
$$

这两个问题是对偶问题。实际上，解决最大值的对偶问题，是通过约束的加减乘除，找到满足系数要求的最小值，作为原最大值的一个上界，之后说明可取来解决问题。由于这一点，我们有弱对偶定理：

$$
x\text{ is feasible for primal, and } y\text{ is feasible for dual}\implies c^Tx\leq b^Ty
$$

推论:如果$c^Tx$是无界的，那么对偶问题一定是无解的。

强对偶定理：如果原始问题有一个有穷的最优解$x^*$，那么对偶问题一定也有个有穷的最优解$y^*$，并且一定有$c^Tx^*=b^Ty^*$

我们之前有Farkas's lemma，说明$\{x\in\R^m|Ax=b,x>0\}$和$\{y\in\R^n|A^Ty\le 0,b^Ty>0\}$中有且只有一个是空的。

从而，我们可以得到推论：$A\in\R^{m\times n},b\in \R^m$，那么下面中一定有且仅有一个成立：

- $\exists x\in\R^n,Ax\ge b,x\ge0$

- $\exist y\in\R^m,A^Ty\ge 0,b^Ty<0,y\leq 0$

Complementary slackness:$x,y$分别是原始问题和对偶问题的可行解，那么$x,y$分别是最优解当且仅当$y^T(b-Ax)=0,x^T(A^Ty-c)=0$

也就是说，一项要么为零，要么等号可取。
