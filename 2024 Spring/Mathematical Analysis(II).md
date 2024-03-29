# 第一章 多元函数的极限与连续

一维时，定义极限，我们使用了绝对值。在更高的维度上，我们需要用距离来刻画极限的概念。

## 1、$R^n$上的度量与点列极限

实数系是有理数系的完备化。通过十进制和Dedkind分割构造成的实数系，尊重的是序结构，从而最先引出确界存在定理。而Contor的构造方法，尊重的是距离结构，从而最先引出Cauchy收敛原理。

在集合意义下的$R^n$,可以看做$n$个$R$的笛卡尔积，即

$$
\{(x^1,...,x^n)|x^i\in R\}
$$

$R^n$是$R$上的线性空间。因为它满足加法结构、数乘结构和分配律。

$R^n$是$R$上的内积空间。内积空间由线性空间和满足自范性、对称性和线性性的内积运算组成。

由内积，我们可以诱导出范数。比如，我们可以定义$||x||=\sqrt{<x,x>}$。所以，内积空间一定是赋范空间。

我们称线性空间和范数运算共同组成的空间为赋范空间。范数具有自范性，数乘线性性，满足$||x+y||\leq||x||+||y||$,即Cauchy-Schwarz不等式。该不等式可以用判别式法和内积证明。

进一步的，我们可以定义度量空间。设$d:X\times X\to R$,$d$满足自范性，对称性，三角不等式，那么我们就称$X$和$d$组成的这个空间是度量空间。任意一个集合，都一定有度量。我们只要取离散度量即可，即

$$
d(x,y)=0,x=y;d(x,y)=1,x\not=y
$$

对于任意的度量空间，我们定义与$a$的度量小于$r$的集合为以$a$为中心，$r$为半径的开球，称$a$的$r$邻域。开球不一定是个球，这取决于度量的取法。

随后，我们便可以定义点列极限。也就是说，当n足够大时，点与极限点之间的误差总是足够小。有限维时，点列收敛等价于各分量数列收敛。点列收敛具有唯一性、有界性，可以有加法和减法。

## 2、$R^n$上的拓扑

在一维上，闭区间的含义，是对取极限封闭。

我们取出$E\in R^n,x\in R^n$如果以x为中心，足够小的开球中，所有元素都在E中，我们称它为E的内点。所有内点构成的集合记作$E^\circ$。

类似地，我们可以定义出E的外点，只需改为都不在E中即可。

如果邻域中始终都有两部分，那么称其为边界点。E和内点没有必然联系。对于$R$,我们取$E=Q$，那么$R$是所有边界点，没有外点和内点。

如果在任何一个去心邻域中，都有集合中的无限个点，那么说明这个点可以被集合中的点逼近，我们称其为聚点。所有聚点构成的集合称为导集。也就是说，它等价于一串集合中的点列极限与之相等。

如果在足够小的邻域中，只有这个点本身属于这个集合，那么我们称这个集合为孤立点。

如果一个集合中，所有的点都是该集合的内点，那么我们称这个集合为开集。

如果一个集合的所有聚点都在该集合中，那么我们称这个集合为闭集。

我们称集合$\bar E=E\cup E'$为闭包。

$E^\circ$是包含于$E$的最大开集。

$\bar E$是包含$E$的最小闭集。

如果一个集合是闭集，那么它的补集是开集。

任意开集的并，仍为开集。

有限开集的交，仍为开集。

任意闭集的交，仍为闭集。

有限闭集的并，仍为闭集。

更抽象的地，我们可以定义出拓扑空间。设$X$为一个集合，$\tau\subset 2^X$，满足：

$$
\empty,X\in \tau\\
\{G_\lambda\in\tau|\lambda\in\Lambda\},\cup_{\lambda\in\Lambda}G_\lambda\in\tau\\
G_i\in\tau(i=1,2,...,m),\cap_{i=1}^mG_i\in\tau
$$

那么，$(X,\tau)$是一个拓扑空间。

## 3、$R^n$的基本定理

可以推广的是，有界点列必有收敛子列，Cauchy收敛原理，闭集套原理。

闭区间存在有限的开覆盖。

当在有限维的时候，B-W定理成立。方法非常简单，只要依次考虑不同的分量，取出符合要求的点列即可。

Cauchy收敛原理。如果收敛，显然是Cauchy列。反之，如果是Cauchy列，有两种说明方式。第一种是考虑B-W；另一种则是若考虑欧氏距离，那么Cauchy列可以说明每一个分量均小于$\epsilon$，每个分量收敛，即得之。

Cantor闭集套定理。要求，一方面是闭集的包含关系；另一方面，有$\lim_{k\to \infin}diam\ F_k=0$，我们定义$diam\ E=\sup_{x,y\in E}d(x,y)$

我们要说明，$\exist!\xi\in\cap_{k=1}^\infin F_k$

唯一性是显然的。存在性的话，我们可以在每个集合中依次取出一个点，组成一个点列。由Cauchy收敛原理，这组点列必然是收敛的。如果这组点列中有有限个不同点，那么我们已经取到了$\xi$。否则，就说明$\xi$是$F_k$的聚点，由闭集的性质易得。

从闭集套定理使用二分法，我们就可以得到B-W定理。

我们定义：$E\sub R^n,\{G_\lambda,\lambda\in\Lambda,E\sub\cup_{i=1}^mG_{\lambda_i}\}$

这样的集合称为$E$的一个开覆盖。如果一个集合取出任意一种开覆盖，都存在有限开覆盖，能够铺满整个集合，称这样的集合为紧集。

Henie-Borel定理：在有限维的情况下，紧集与有界闭集等价。

由紧集推出有界闭集，只需要取出$\cup_{j=1}^\infin B_j(0)$，即可说明其有界。同时，要证明其为闭集，只要证明其补集为开集。那么，我们取出其中任意一个元素，并且取出一个紧集的开覆盖，再取出这个元素的一邻域，保证与开覆盖不交，即说明是开集。须注意，此是在拓扑空间中即成立。还有一种在度量空间中成立的方式。假设有一个聚点在集合外，取$B_r(x),r={1\over n},n\in\N$，则为$\{R^n-{x}\}$的一个开覆盖。由聚点的性质，显然不可能是紧集，故成立。

由有界闭区间推出紧集，可以用反证法。为了简单考虑，我们考虑$R^2$。将闭矩形四等分，如果不是紧集，那么存在至少一个矩形不可被有限开覆盖。这样做足够多次，会与闭矩形套定理矛盾。故得之。

$$
紧集\iff自列紧集\implies 有界闭集
$$

主要要考虑维数的概念。

我们定义一个集合是有界的，指$\exist a\in X,r>0,s.t.\ K\sub B_r^k(a)$

考虑无限维的情况下，取$e_1,e_2...$即有界闭。但不为紧集。

## 4、连续映射

$D\in R^n\to R^m$称为n元m维函数。

定义极限的概念：$D\sub R^n$,$x_0$为$D$中聚点，$f:D-\{x_0\}\to R^m$

若$\exist A\in R^n,\forall \epsilon>0,\exist \delta>0,\forall x\in (B_\delta(x_0)\cap(D-\{x_0\})),||f(x)-A||<\epsilon$

则称$\lim_{x\to x_0}f(x)=A$

左右极限的概念在高维，显然不存在。

在高维中，存在多种趋向于同一点的方式。极限存在，当且仅当以任意一种方式趋向于其时，极限均相同。

在高维中，极限依旧具有唯一性、局部有界性、四则运算的性质。

我们也可以引入累次极限的方式。倘若$f(x,y)$对$y\neq y_0$有定义，假设$\lim_{x\to x_0}f(x,y)=\varphi(y)$存在。

定义$\lim_{y\to y_0}\lim_{x\to x_0}f(x,y)=\lim_{y\to y_0}\varphi(y)$

设$f$在$(x_0, y_0)$的某一去心邻域有定义，且$\lim_{x\to x_0}f(x,y)=A$

若$\forall y\neq y_0,\lim_{x\to x_0}f(x,y)$均存在，则$\lim_{y\to y_0}\lim_{x\to x_0}f(x,y)=A$

定义：$f:D\sub R^n\to R^m,x_0\in D$

若：$\forall\epsilon>0,\exist\delta>0,\forall x\in B_\delta(x_0)\cap D,||f(x)-f(x_0)||<\epsilon$

显然，孤立点处是连续的。倘若$f$在$D$上每一点均连续，那么记为$f\in C(D,R^m)$

## 5、连续映射之整体性质

考虑到连续函数在一维闭区间上时，具有有界性、最值性、介值性、一致连续性。我们的目标，就是把这些内容推广至高维。

Thm：$f\in C(K,R^m),K\sub R^n$,$K$是紧集，那么$f(K)$也是紧集。

有两种方式证明之。第一种，从自列紧性的角度出发。

$\lim_{l\to \infin}x_{kl}=\xi$

$\lim_{l\to\infin}f(x_{kl})=f(\xi)\in f(k)$

得证。

或者从开覆盖的角度考虑之。

$\{G_\lambda|\lambda\in\Lambda\}$为$V$之开覆盖,由作业中之定理，$f^{-1}(G_\lambda)$亦为开集。

所以，存在有限个$f^{-1}(G_{\lambda i})$，其之并集覆盖K。故，其像亦覆盖K，故为紧集。

是故$f(k)$在$R^m$中有界且闭，故最大最小值均在其中。

我们类似地定义一致连续，倘若对于一个足够小的误差，我们可以找到一个与误差无关之$\delta$，原像中任一点取出此般大小之邻域，其误差总是足够小。

类似地，我们可以用点列证明，此不再赘述。

倘用开覆盖证明，我们对于每一个点，我们可以取出满足$\epsilon$误差的邻域大小的$1\over 114514$的一邻域，使之成为一个新的开覆盖。从中必然能够挑出有限个区间。取此为新$\delta$，则得证。

$E\sub R^n,\gamma\in C([0,1],R^n)$

若$\gamma([0,1])\sub E$

则称$\gamma$为$E$中一条连续道路，$\gamma(0),\gamma(1)$分别为其起点与终点。如果一个集合是连通的，那么其中任意两点可以通过一条连通道路连接。

连续映射可以将连通集映射为连通集。我们只需要考虑函数$f\circ\gamma$即可说明这一点。

因此，在一维时，就体现为有界闭区间。

我们称一个聚点是凝聚点，当且仅当周围有不可数个集合中的点。

有界无限点集中至少有一个凝聚点。

我们称一个集合是无处稠密的，当且仅当$(\bar E)^\circ=\empty$

Cantor三分集：这是一个闭集。并且其导集等于其自身，并且是**无处稠密**的。

不连续点之集合为零测集，则可积。

在线性空间中，范数具有等价性。

$P$为投影， $P:\R^2\to \R$若$A\in\R^2$为紧集，则$P(A)$为紧集。

$A\in\R^n$为紧集$\iff F:\{A_x\}$为$\R^n$中的闭集族，$A\cap (\cap_\alpha A_\alpha)=\empty$则 $\exist$有限$A_i\in F,s.t.\ (\cap_{i=1}^kA_i)\cap A=\empty$

Lebesgue数：

$E\sub \R^n$为有界闭集，$\{G_\alpha\}$为$E$之有限开覆盖，则$\exist\sigma>0,s.t.if\ F\cap E\neq\empty,diam(F)<\sigma$则必有$G\in\{G_\alpha\},G\sub F$

$E\in\R^n$为一个连通集，若$E=A\cup B;A,B\neq\empty,A\cap B=\empty$

则$A'\cap B\neq\empty\ or\ A\cap B'\neq\empty$

道路连通可以推出连通。

倘若$E$连通，则$\bar E$亦连通。

可以构造$\bar E=A\cup B$，其为无交并。取出此二集合与$E$之交集，令之为$A_1,B_1$则此二集合不满足上述之性质，矛盾。

# 第二章 多元映射微分学

## 1、偏导数与微分

在一元时，可导就意味着可微。在多元时，对于每一个点，我们可以固定一个变量的值，然后在一个维度上求导数。

设$D\sub R^2$为一个开机，$f:D\to R$，定义偏导数为${\partial f\over \partial y}(x_0,y_0)=\lim_{\Delta y\to0}{f(x_0,y_0+\Delta y)\over \Delta y}$

为$f$在$(x_0,y_0)$处的偏导数。

若$\forall (x,y)\in D,{\partial f\over \partial y}$总存在，那么我们就得到了一个新的函数$\partial f\over\partial y$，称为$f$关于$y$的偏导函数。

如果我们对$f$对一个变量求偏导后，再次关于一个变量求偏导，那么我们就得到了高阶偏导。我们称${\partial f\over\partial x^i}$关于$x^j$的偏导为$f$的二阶偏导，可以记作$\partial^2 f\over\partial x^j\partial x^i$或$f_{x^ix^j}$

注意，变量的顺序在记法中有着严格要求。

Hamilton算子：$\nabla$

表示对每一个变量求偏导，我们把$\nabla f$称为$f$的梯度，也可以记作$grad(f)$

${\partial f\over\partial x},{\partial f\over\partial y}$在$(x_0,y_0)$的某个邻域中存在且有界，那么$f$在$(x_0,y_0)$处连续。

$f:D\sub R^n\to R,x\in R^n,v\in R^n$

$D_vf(x_0)=\lim_{t\to0^+}{f(x_0+tv)-f(x_0)\over t}$

称为$x_0$处关于$v$的方向导数，记作${\partial f\over\partial v}(x_0)$

此外，有$D_{\lambda v}f(x_0)=\lambda D_vf(x_0)$

从真正多元的观点去考虑，那么还是应该考虑可微。

$D\sub R^n\to R^m,x_0\in D,if\ \exist A\in M_{m\times n}(R),s.t.\\ f(x_0 +h)=f(x_0)+A(x_0)h+o(h)$

则称$f$在$x_0$处可微。$A(x_0)$称为$f$在$x_0$处的微分，可记作$f'(x_0),df(x_0),df|_{x_0}$

亦即：$\lim_{h\to0}{||f(x_0+h)-f(x_0)-A(x_0)h||_{R^m}\over||h||_n}=0$

对于线性主部的要求，一方面是线性的，另一方面，要求当在一个单位球内进行映射时，结果有界。

全微分公式：$f(x_0+\Delta x)=f(x_0)+\sum_{i=1}^n a_i\Delta x^i$

考虑到$f:M\to N$

$df|_{x_0}:T_{x_0}M\to T_{f(x_0)}N$

我们将$x^i$视作是一个函数，那么

$x^i:R^n\to R$

含义是取出第i个分量。

根据微分的定义，我们可以有：

$d_{x_i}|_p:R^n\to R$为一线性映射。故，此为一线性泛函。$d_{x_i}|_p\in (R^n)^*$

其值为$\vec e_i$

可微，可以推出函数在此处连续且偏导存在。我们可以用这样的Jacobi矩阵来刻画函数的线性主部。

$$
\begin{bmatrix}
{\partial f^1\over\partial x^1}(x_0)&...&{\partial f^1\over\partial x^n}(x_0)\\
...\\
{\partial f^m\over\partial x^1}(x_0)&...&{\partial f^m\over\partial x^n}(x_0)
\end{bmatrix}
$$

用矩阵的范数，可以确认这是个bounded的线性映射。如果这个映射是一个线性泛函，则其就是梯度了。如果我们在曲面上，欲最小化至一个点的距离，我们应当沿梯度在该点处切空间的投影方向。

局部Lipschitz连续：

在$R^n$的凸区域（连通开集）上的凸函数一定连续。凸区域：区域中任意两点连线仍然在该区域中。我们记定义域为$D$，则任意$D$中的紧集一定有界。我们可以考察闭矩形$H$，由凸函数的性质，其一定有上界，最大值在顶点处取得。由于是紧集，所以一定可以被有限个开矩形覆盖，那么我们把这些开矩形取成闭的，就可以说明其有上界。我们假设其没有下界，那么有$\{x_n\}\to\bar x,f(x_n)\to-\infin$,从而，当$|x_n-\bar x|<r$,$2\bar x-x_n\in B_r(\bar x)$

$f(\bar x)=f({1\over2}x_n+{1\over2}(2\bar x-x_n))\leq{1\over2}f(x_n)+{1\over 2}f(2\bar x-x_n)$

RHS趋于负无穷，不成立。

在多元中，可微可以推出连续，可以推出可导。

如果可导，在什么情况下可微呢？

我们记$J_f:D\to M_{m\times n}$

倘若其存在，且在目标点处连续，则可以推出可微。证明方法，则是将其式子写出，由于其连续，故可以应用中值定理，从而将每一项的误差压缩到足够小。从而得证。

rmk：切平面也是一种线性逼近。我们可以选出切平面中任意两个向量，从而计算出它们的法向量。之后，我们可以在目标点处选取任何曲线，根据复合函数求导，我们可以知道它们和法向量垂直。

cor：如果$f\in C^k(D,R)$，即$f$的任意$k$阶偏导均连续，那么$k$阶偏导与求导顺序无关。证明这一点，我们使用了差分的思想，通过不同的组合方式，得到这一结论。关键还是由于连续，从而可以使用微分中值定理。

## 2、复合映射求导

$g:D_g\to D_f,f:D_f\to R^m$

需要的条件是$g$在$(x_0,y_0)$可微，$f$在$g(f(x_0,y_0))$处可微。结果上看，就是二者的导数相乘。在分量形式上，

$$
y^i=f^i(x^1,...,x^k)\\
x^j=g^j(u^1,...,u^n)\\
y^i=f^i(g^1(u^1,...,u^n),...,g^k(u^1,...,u^n))\\
{\partial y^i\over\partial u^j}(u_0)=\sum_{l=1}^k{\partial y^i\over\partial x^l}(x_0)
{\partial x^l\over\partial u^j}(u_0)
$$

并且，如果$f',g'$连续，那么若$h=f\circ g,h'$也连续。

复合映射求导的证明，就是试图找出其线性主部，再说明误差足够小。不可以直接除掉$\Delta x$

一阶微分在形式上具有不变性。

无论x是独立自变量或是中间变量，都有$df=f'(x)dx$

在高维时，也成立这一点。

## 3、微分中值定理和Taylor公式

我们称一个集合是凸集，当集合中任意两点连线均在集合中。

如果一个集合不仅凸，而且是一个区域（连通且开），那么这个区域称为凸区域。在凸区域上，我们有微分中值定理：

$$
\forall x,y\in D,\exist\xi\in[x,y],s.t.\ f(y)-f(x)=f'(\xi)(y-x)
$$

如果$D\in R^n$是一个区域，$f:D\to R$可微，$\nabla f\equiv0$，那么$f$是一个常值函数。

Pf：对于区域中任意两点$x_0,x$，取一条连续道路$r$，定义$r(1)=x,r(0)=x_0$

考察$T_*=\sup\{t\in[0,1]|f(r(\tau)=f(x_0),\forall\tau\in[0,t]\}$

如果$T_*<1$由连续性，$f(r(T_*))=f(x_0)$，然后再取一个邻域，运用拉格朗日中值定理，可以说明一条折线上点取值相同，故矛盾。

如果微分中值定理想要推广到高维至高维的映射，那么我们显然不一定找得到合适的$\theta$,使得其成立等式。因此，我们有拟微分中值定理：

$$
f:D\sub R^n\to R^m
$$

若$f$可微，并且$D$是一个凸区域，那么有：

$$
||f(y)-f(x)||\leq||f'(\xi)_2||\ ||y-x||
$$

我们定义，$||A||_2=\sup_{||x||_2=1}{||Ax||\over ||x||}$

在数值上看，为最大奇异值。

高维映射至一维时的泰勒公式：

定义：$\Delta x\cdot\nabla=\sum_{i=1}^n\Delta x^i{\partial\over\partial x^i}$

从而，我们可以写出：

$f(x_0+\Delta x)=f(x_0)+(\Delta x\cdot\nabla)f(x_0)+{1\over2}(\Delta x\cdot\nabla)^2f(x_0)+...$

一般考虑前二阶即可。其中，我们有：

$$
(\Delta x\cdot\nabla)^2f(x_0)=\Delta x^TH(f)(x_0)\Delta x
$$

类似于二次型。我们定义：

$$
H(f)=({\partial^2 f\over\partial x^i\partial x^j})_{i,j=1}^n
$$

如果$H$正定，那么是严格极小值；如果$H$负定，那么是严格极大值。

## 4、隐函数与反函数定理

如果我们已经有了一些关系，即$f(x_1,y_1)=0$，在什么样的条件下，我们可以确认一个唯一的映射$y=f(x)$？$x\in R^n,y\in R^m$

从自由度的角度去分析，我们应当有$m$个关系。

如果我们已经知道了$F(x_0,y_0)=0$，我们希望解出$\Delta y=\widehat f(\Delta x)$

$$
F(x_0+\Delta x,y_0+\Delta y)=F(x_0,y_0)+F_x(x_0,y_0)\Delta x+F_y(x_0,y_0)\Delta y\\
\Delta y=-[F_y(x_0,y_0)]^{-1}F_x(x_0,y_0)\Delta x
$$

因此，需要$F_y(x_0,y_0)$可逆。在上式中，我直接省略了$O(\Delta x,\Delta y)$。这一步实质上把非线性问题化归到了线性问题。

如果我们已知$f(x_0)=y_0,f(x_0)+\Delta x=y_0+\Delta y$

如果$\Delta y$给定，我们需要怎样反解出$\Delta x$?

类似地，我们需要把非线性问题转化为线性问题。

$$
f(x_0)+f'(x_0)\Delta x+O(\Delta x)=y_0+\Delta y\\
\Delta x=[f'(x_0)]^{-1}\Delta y
$$

一元隐函数定理：

$$
(x_0,y_0)\in W\sub R^2\\
if\ F(x_0,y_0)=0,F\in C^1(W,R),F_y(x_0,y_0)\neq0,\\
then\ \exist V为开集,x_0\in V,s.t.\\
\forall x\in V,F(x,y)=0;\forall x\in V,-{{\partial F\over\partial x}(x,y)
\over {\partial F\over\partial y}(x,y)}|_{y=f(x)}
$$

其思想还是要把非线性的问题转化为线性的问题。首先，我们需要在相等处之导数不为0。不失一般性，可令其关于y之导数大于0。是故，可选出一合适大小之邻域，使此范围内其皆大于0。故函数在此范围内关于y严格单调递增。故，在零点相同之x处，对y施加微扰，可找到大于0及小于0之值。由连续性，我们可以在大于0、小于0处对x施加微扰，此依赖于连续性，可得在此类点附近的函数值符号。从而可以找到一唯一的y，确认一函数。对于多元，重复利用此规则，一次消去一个元即可。

一元反函数定理：需要维数相同。

$$
F(y,x)=y-f(x)\\
F(y_0,x_0)=y_0-f(x_0)=0\\
F\in C^1(W,R^n)\\
F_x(y_0,x_0)可逆
$$

$$
s.t.\ f^{-1}\in C^1(V,R^n)\\
(f^{-1})'(y)=(f'(x))^{-1}|_{x=f^{-1}y}
$$
