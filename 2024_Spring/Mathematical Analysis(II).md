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

在开集中，连通等价于道路连通。

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

对于证明偏导数求导顺序无关类型的一个思路：化多元为一元，从单变量角度进行考虑，使用微分中值定理进行定义上的证明。

## 5、微分学的应用

一类问题是求切线、法向量、切平面等。这些部分见课本即可，无甚赘述之必要。

另一类问题是求极值问题。一类是没有约束的极值。这由Taylor公式和拟微分中值定理得到。另一类是等式约束的极值问题。在等式的约束下，实际上是要求一个曲面上函数的最值。如果一个点是极值点，那么显然有梯度等于0。我们称梯度为0的点为驻点。如果在驻点某邻域上有二阶连续偏导，倘Hf正定，那么为极小值点，倘负定，那么为极大值点，倘不定，那么不是极值点。如果半定，那么要进一步讨论。

如果是条件极值问题，比如说，我们想要最小化$f(x)$的值，$x\in R^n$,同时，$x$受到$g(x_1),...,g(x_r)$的约束。那么，我们可以看作是在$g$确定的曲面上$\Sigma$求极值问题。如果一个点是极值点，那么一定有$\nabla f(p_0)\parallel\nabla g(p_0)$

将其进一步表述为Lagrange乘子法：若$x_0$是极值点，并且

$$
\begin{bmatrix}
\nabla g_1\\
...\\
\nabla g_r
\end{bmatrix}
\begin{bmatrix}
x_1\\
...\\
x_n
\end{bmatrix}
$$

满秩，那么$\exist\lambda_0^1,...,\lambda_0^r\in R,s.t.(x_0,...,x_0^n,\lambda_0^1,...,\lambda_0^r)\in R^{n+r}$

定义Language函数为$L(x,\lambda)=f(x)-\sum_{i=1}^r\lambda^ig_i(x)$

使得$x_0$为驻点。

今日之课程绍介了基础的变分法。其思想大致如下。变分法想要解决的问题，是对函数的优化问题。我们假设目标函数$p$已经达到了最优，那么我们对其进行一定程度的扰动，应该附近导数都为0才对。我们假设扰动函数为$q$,然后我们研究函数$p+\epsilon q$在$\epsilon=0$时的导数。这个导数应当恒为0。随后，再解出$p$即可。

## 变分法的理论

考虑$T:X\to R$，$X$是函数空间，$T$是一个泛函。考虑$\bar\varphi$是$T$的一个极值点。那么，我们应当有$T'[\bar\varphi]=0$。所以，对于$\forall g\in X$，我们应当有$T'[\bar\varphi]g=0$

$T'[\bar\varphi]:T'_{\bar\varphi}X\to R$是一个线性泛函。

所以，应当有$\frac{d}{d\epsilon}|_{\epsilon=0}T[\bar\varphi+\epsilon g]=0$

# 第三章 多元积分学（平直空间）

首先，我们需要定义出什么是面积。

## 有界闭区间上的重积分

针对矩形而言，我们显然可以定义它的面积为长乘宽。

对于其他图形呢？

我们首先一个想法，就是画出很多的矩形方格。我们定义，完全落在图形内的矩形格子所构成的集合为A，所有与图形之交集不为空的矩形格子所构成的集合为B。

我们可以承认一个事实：随着网格的细化，A的面积不会减少，B的面积不会增加。并且，始终有$m(A)\leq m(B)$

我们定义：

$$
mD_*:=\sup\{m(A)|A\sub D,|A|<\infin\}\\
mD^*:=\inf\{m(B)|D\sub B,|B|<\infin\}
$$

如果$mD_*=mD^*$那么$D$就是可求面积集。

我们称$S$是零面积集，当$\forall\epsilon>0,\exist m<\infin,s.t.\cup_{j=1}^mI_j\sub S,\sum_{j=1}^mI_j<\epsilon$

$I_j$是一个小矩形。

如果将$m$改为可数个，那么我们就称$S$是零测集。

如果$D$是可求面积的，当且仅当存在有限个闭矩形构成的集合$A,B,s.t.A\sub D\sub\bar D\sub B,m(B)-m(A)<\epsilon$

$D$是可求面积的，当且仅当$\partial D$是零面积集。

如果取出可数个点，想要用矩形覆盖住它们，我们只需要让其面积以指数级数衰减就可以了。

如果$D_1,D_2$均可求面积，那么$D_1\cup D_2$也可以求面积。若$D_1^\circ\cap D_2^\circ=\empty$，则$m(D_1\cup D_2)=m(D_1)+m(D_2)$，这是符合直觉的。

$D_1\cap D_2$也可求面积。

$D_1 - D_2$也可求面积。

对于$\Gamma:(x(t),y(t)),t\in[\alpha,\beta]$,若$x(t)\in C[\alpha,\beta],y(t)\in C^1[\alpha,\beta]$，那么，$\Gamma$是零面积集。

如果$D\in R^2$的边界由有限条光滑曲线构成，那么$D$是可求面积的。

类似于一元时的情况，我们先定义出什么是划分。$D=\cup_{i=1}^n\Delta D_i$，保证每一个划分出的小面积都是可求面积的，每两个小面积之间的内点之间不交。

我们定义，$||\pi||=\max\{diam\ \Delta D_i\}$

从而，我们可以定义出Riemann积分：

$$
s(f,\pi,\{\xi_i\})=\sum_{i=1}^nf(\xi_i)m(\Delta D_i)
$$

如果$\lim_{||\pi||\to0}S(f,\pi,\xi)$存在，并且与$\pi,\xi$均无关，那么，我们称$f\in R(D)$,记这个极限为$\iint_Df(x,y)d\sigma$或者是$\iint_Df(x,y)dxdy$

$f\in R(D)\iff \lim_{||\pi||\to0}(\bar S(f,\pi)-\underline S(f,\pi))=0$

类似地，有勒贝格定理的推广：$f$有界且不连续点是零测集，那么$f$在$D$上可积。此为充要条件。

## 重积分的性质与计算

类似于一元时的情况，重积分具有线性可加性，区间可加性，乘积可积性，保序性，绝对可积性，第一积分中值定理。

Fubimi定理：$D=[a,b]\times[c,d],f\in R(D)$

若$\forall x\in[a,b],h(x)=\int_c^df(x,y)dy$有定义，则$h\in R[a,b],\int_a^bh(x)dx=\iint_Dfdxdy$

这个定理用划分的方式进行证明。我们先考虑固定一个维度，考虑取出另一维度中的$\xi_i$，$\xi_i$在$[x_{i-1},x_i]$之间。那么，有：

$$
\sum_{j=1}^m\inf_{(x,y)\in D_{ij}}f(x,y)\Delta y_j\leq\sum_{j=1}^mf(\xi_i,y)dy\leq
\sum_{j=1}^m\sup_{(x,y)\in D_{ij}}f(x,y)\Delta y_j
$$

随后，在不等式上乘上$\Delta x$

左侧就成为了Darboux小和，右侧就成为了Darboux大和。从而由迫敛性可得。

进行推论，倘$f\in C(D)$

$$
\iint_{D}f(x,y)dxdy=\int_a^bdx\int_{y_1{(x)}}^{y_2(x)}dyf(x,y)
$$

可以先x，也可以先y。

多元变量替换：$T:D\to D'$有连续偏导数，$\det T'\neq0$，$f\in C(D)$，或者是具有分段光滑边界的有界闭区域,且D是个单射。

则

$$
\iint_Df(x,y)dxdy=\iint_{D'}f(x(u,v),y(u,v))|J|dudv\\
J=\frac{\partial(x,y)}{\partial(u,v)}
$$

原因是，$J$的行列式刻画了这个变换导致的面积缩放比例。

如果是n元的变元替换的话，也是非常类似的：

$$
\int_{T(\Omega)}f(x)d^nx=\int_\Omega f(T(u))|\det T'(u)|du
$$

在二维情况下，证明的主要想法，就是把重积分化为黎曼和的形式，然后，我们希望说明：

$$
|\frac{\partial(x,y)}{\partial(u,v)}|_{(u_i,v_i)}|\Delta D_i|=|T(\Delta D_i)+o(1)|\Delta D_i|
$$

如果要严格化地证明，那么有这样的步骤：首先，证明本原映射可以做到这一点；然后，说明充分小的话，一切映射都可以看做本原映射的复合；最后，将区域分割，在每一个区域上重复应用这一点。

证明：

考虑本原映射$T:(u,v)\to(u,y(u,v))$

$$
T'(u,v)=\begin{bmatrix}
1&0\\
y_u&y_v
\end{bmatrix}
$$

故$y_v$不为0。假设导数连续，不失一般性，我们考虑小矩形。令$y_v>0$

$$
|T(\sigma)|=\int_a^bdx\int_{y(x,c)}^{y(x,d)}dz
$$

使用两次积分中值定理，再令$m(\sigma)\to0$就可以得到这一点。对于不规则的图形，分割成小矩形可得。

下一步，我们要说明任何的$T$都可以写成本原映射的复合。考虑到：

$$
\det
\begin{bmatrix}
x_u&x_v\\
y_u&y_v
\end{bmatrix}\neq0
$$

不妨设$y_v\neq 0$

考察$T_1:\xi=u,\eta=y(u,v)$,$T_1^{-1}:u=\xi,v=g(\xi,\eta)$

$T_2:x=x(\xi,g(\xi,\eta)),y=\eta$

则$T_2\circ T_1(u,v)=(x(u,v),y(u,v))$

由于用到了反函数定理，所以只有在局部才成立这一点。

最后一步，就是把原本的D划分成多个可求面积的区域交即可。

## 广义重(zhong4)积分

首先，我们让$D\sub R^2,\forall R>0,D\cap B_R(0)$是可求面积的，称一列可求面积的闭集列$\{D_j\}_{j=1}^\infin$为$D$的一个穷竭列，当：

$$
D_1\sub D_2\sub...\sub D\\
\forall 有界闭集F\sub D,\exist m,s.t.F\sub D_m
$$

在满足上述条件的基础上，如果$f\in R(F)$,任意一个穷竭列，$\lim_{n\to\infin}\iint_{D_n}fdxdy$存在且值相等，那么我们记之为$\iint_Dfdxdy$称之为$f$在D上的广义积分。

定理：$f\geq0,\{D_j\}$为$D$的某一个穷竭列，那么：

$$
\iint_Dfdxdy收敛\iff\lim_{n\to\infin}\iint_{D_n}fdxdy收敛
$$

右式等价于$\exist M>0,\forall n\iint_{D_n}fdxdy<M$

左推右是显然的。右推左，我们可以构造另一个穷竭列，使得其该穷竭列中的每一个区域恰包含于另一个穷竭列中的某一区域。

定理：$0\leq f\leq g$,$f$发散，则表示着$g$发散；$g$收敛，则表示着$f$收敛。

在高维情况下，一函数积分收敛，和一函数的绝对值积分收敛是等价的。这是因为穷竭列的选取是任意的。

一个函数的绝对值积分收敛，很容易就可以导出这个函数本身积分收敛，这是显然的。但是反过来的话，需要费些笔墨。

我们假定一个函数由正部$f^+$和负部$f^-$叠加而成。这两部分，我们都定义为非负值。那么，$f=f^+-f^-$

倘若$|f|=f^++f^-$发散，那么正部和负部中，至少有一部分是发散的。不失一般性，我们假设其正部是发散的。那么，为了说明整个$f$是发散的，一种直观的想法，就是多取一些正部，少挑选一些负部，从而达到我们想要的效果。

我们构造这样的一个穷竭列，

$$
\int_{D_{n+1}}f^+dx>2\int_{D_n}|f|dx+n
$$

由穷竭列和正部函数发散的特点，是可以实现的。

记：

$$
\Delta n=\overline{D_{n+1}-D_n}
$$

倘$f^+$在$\overline\Delta_n$Riemann可积，那么我们可以构造一个划分，这个划分的Darboux下和大于$\int_{\Delta_n}f^+dx-1$。只要划分足够细，那么我们一定可以达成这一条件。

我们定义$\Delta_n^+$为$\bar\Delta_n$的划分中，并非全为0的部分的并集。

随后，我们令：

$$
G_n=\overline{D_n\cup\Delta_n^+}
$$

由于$G_n$介于$D_n$和$D_{n+1}$之间，所以$\{G_n\}$也是个穷竭列。

从而：

$$
\int_{G_n}fdx=\int_{G_n}f^+dx-\int_{G_n}f^-dx\\
=\int_{D_n}f^+dx+\int_{\Delta_n}f^+dx-\int_{D_n}f^-dx\\
\geq0 + \int_{D_n}|f|dx+n-1-\int_{D_n}f^-dx\\
=\int_{D_n}f^+dx+n-1\to\infin
$$

这就可以说明原函数也是发散的。

对于广义重积分的计算，我们有这样的两个定理：

$D,T(D)$为平面区域，并且与$B_R(0)$的所有交都可求面积，并且$T:D\to T(D)$，$T\in C^1,\det(T')\neq0$,则：

$$
\iint_{T(D)}f(x,y)dxdy=\iint_Df(T(u,v))|\frac{\partial(x,y)}{\partial(u,v)}|dudv
$$

两侧具有相同的敛散性。

$D=[a,+\infin)\times[c,+\infin),f\in C(D)$

如果$\int_a^{+\infin}dx\int_c^{+\infin}dyf(x,y)$和$\int_a^{+\infin}dx\int_c^{+\infin}dy|f(x,y)|$

均存在，则$f$在$D$上广义可积，并且有：

$$
\int_Dfdxdy=\int_a^{+\infin}dx\int_c^{+\infin}dyf(x,y)
$$

# 第四章 第一类曲线和曲面积分

## 第一类曲线积分

什么是空间中曲线的长度？假设曲线可以被参数化：$r:[\alpha,\beta]\to R^n$,我们令$r(\alpha),r(\beta)$为曲线的两个端点。定义$[\alpha,\beta]$的一个划分$\pi$,考虑$\lim_{||\pi||\to0}\sum_{i=1}^n|P_{i-1}P_i|$，倘该极限存在，且与划分无关，那么称这个曲线是可求长度的，并且与这个极限值数值上相等。

我们定义，$\Gamma:r\in C^1([\alpha,\beta],R^n),r'(t)\neq0$的曲线为正则曲线。正则曲线一定是可求长度的。

考察函数$f$,倘$\lim_{||\pi||\to0}\sum_{i=1}^nf(\xi_i)|P_{i-1}P_i|$存在，并且与$\pi,\xi$无关，则称此极限为$f$在$\Gamma$上的第一类曲线积分，记为$\int_\Gamma fds$

第一类曲线积分与$\Gamma$的方向无关，符合线性性，区域可加性。

## 第一类曲面积分

曲面$\Sigma$

$$
\Sigma:\vec r:D\sub R^2\to R^n
$$

如何定义弯曲面的面积？但弯曲面足够小的时候，我们将其简化为线性情况加以考虑。从而有：

$$
\frac{|\vec r(\vec u_0+\sigma)|}{|\sigma|}\approx|\vec r_u\times\vec r_v|_{(u_0,v_0)}
$$

定义：$\Sigma$由参数化$r:D\sub R^2\to R^n$，$D$是具有分段光滑边界的有界闭区域，$r\in C^1(D,R^n)$,$|J_r|$列满秩，那么：

$$
M(\Sigma)=\int_D|\vec r_u(u,v)\times \vec r_v(u,v)|dudv
$$

一些小的trick：

$$
|\vec\alpha\times\vec\beta|=\sqrt{|\vec\alpha|^2|\vec\beta|^2-(\vec\alpha\cdot\vec\beta)^2}\\
E=\vec r_u\cdot\vec r_u\\
G=\vec r_v\cdot \vec r_v\\
F=\vec r_u\cdot\vec r_v\\
M(\Sigma)=\int_D\sqrt{E\cdot G-F^2}dudv
$$

此上称为Gauss系数。

考察一个线性映射，$r(u)=Au$，倘

$$
A=
\begin{bmatrix}
A'\\
0
\end{bmatrix}
$$

其中$A'$为一满秩方阵。那么，变换后的单位体积显然变为$|\det A'|$

$$
A^TA=(A')^TA'\\
\det(A^TA)=\det((A')^TA')=\det((A')^2)
$$

对于一般性的$A$的而言，我们可以找到一组标准正交基，使其变为上面的形式。

从而有：

$$
|r(D)|=\sqrt{\det(A'A)}|D|
$$

考察非线性的情况。

$$
r(u_0+\Delta u)=r(u_0)+r'(u_0)\Delta u+o(\Delta u)
$$

故，有

$$
|r(\sigma)|\approx|r'(u_0)\sigma|=\sqrt{\det(r'(u_0)^T(r'(u_0)))}|\sigma|
$$

我们定义：$\Sigma$为一正则曲面，有参数化$r\in C^1(D\sub R^2,R^3),J_r$满秩，$f\in C(\Sigma,R)$，定义$f$在$\Sigma$上的第一曲面积分如下：

$$
\iint_\Sigma fds=\iint_D f(\vec r(u,v))||\vec r_u\times\vec r_v||_{(u_0,v_0)}dudv
$$

# 第五章 第二类曲线与曲面积分及相关公式

## 第二类曲线积分

考虑向量场在定向曲线上的积分。

倘$\Gamma$为以$A$为起点的，$B$为终点的定向光滑曲线，在$\Gamma$的每一点处可取单位切向向量$\tau$，向量场$f$在$\Gamma$上的积分记为:

$$
\int_\Gamma f\cdot\tau ds
$$

实际上，之所以可以这样做，是因为$\tau=\vec s_i/||s_i||$

我们也可以将这个乘积写开来。就变成了：

$$
\int_\Gamma Pdx+Qdy+Rdz
$$

第二类曲线积分具有方向性。即方向相反，取值相反。同时，依旧具有线性性，路径可加性。

如果曲线可以被参数化，那么可以写作：

$$
\int_\Gamma f\cdot\tau ds=\int_\alpha^\beta f(r(t))\cdot r'(t)dt
$$

## 第二类曲面积分

首先，并不一定所有的曲面都可以选取出曲面的一侧。如果指定了曲面上一点的单位法向量，就可以通过连续变动的方式，确定曲面上每一点处的法向量，那么我们就称这个曲面是可定向曲面。说的更准确些，可以考虑一个不越过边界的，且经过$P$的闭曲线$\Gamma$,如果沿该曲线移动，并让单位法向量连续变动，回到$P$点时，若与起始法向量相同，那么就称其可以定向。

对于正则曲面而言，法向量为$\vec n=\underline+\frac{\vec r_u\times \vec r_v}{||\vec r_u\times\vec r_v||}$

对于可定向曲面而言，只要确定了在一点处，上式取正号或是负号，就可以说明在整个曲面上的符号情况。

我们定义，在正则并且可定向曲面$\Sigma$上倘若选定了定向，那么$\int_\Sigma\vec f\cdot\vec n ds$称为$\vec f$在$\Sigma$上的第二类曲面积分。

我们引入一个形式记号$d\vec s=\vec nds=(\cos\alpha ds,\cos\beta ds,\cos\gamma ds)$，每一项可以认为将曲面投影到了不同的平面上。

$$
\vec f=(P,Q,R)\\
\int_\Sigma\vec f\cdot\vec n=\int_\Sigma Pdy\wedge dz+Qdz\wedge dx+Rdx\wedge dy
$$

$\wedge$称为楔积，表示有方向的面积。

一般地，如果要考察$n$维空间中一般的$k$维曲面积分，我们可以选取$k$个坐标轴组成的子空间，并进行投影。共选取$C_n^k$个不同的子空间进行表征。

如果$\Sigma$由正则参数$\vec r:D\sub R^2\to R^3$给出，则$f\in C(\Sigma,R^3),\int_\Sigma\vec f\cdot\vec n ds=\int_D\vec f(\vec r(u,v))(\underline+)(\vec r_u\times\vec r_v)dudv$

## Green,Gauss,Stokes公式

Green公式考察对象为平面$D$。默认其定向指向纸外，$\partial D$的诱导定向，用右手大拇指指向$D$的定向，手心侧为$D$,四指指向方向即为$\partial D$的诱导定向。

$$
\iint_D(\frac{\partial Q}{\partial x}-\frac{\partial P}{\partial y})dxdy=\int_{\partial D}Pdx+Qdy
$$

Gauss公式考察对象为空间闭区域$\Omega$。规定边界定向指向$\Omega$外。那么，有

$$
\iiint_\Omega\nabla\cdot\vec Fdv=\iint_{\partial\Omega}\vec F\cdot\vec nds
$$

Stokes公式研究的是曲面$\Sigma$。定向方式和Green公式中一致。

$$
\iint_\Sigma(\nabla\times\vec F)\vec n ds=\int_{\partial\Sigma}\vec F\vec\tau ds
$$

总结而言，即为$\int_Mdw=\int_{\partial M}w$

Green公式在直观上的想法，是将区域划分为了很多小块，随后再进行共同积分。因为积分的方向性，在内部的边界上，结果都被抵消掉了。我们可以考察一小块区域的积分。由于差分，可以构造出导数的形式，从而得到Green公式的形式。

设$D$为平面有界区域，边界由有限条分段光滑曲线构成，具有诱导定向，$P,Q\in C^1(D),\text{then }\int_{\partial D}Pdx+Qdy=\iint_D(\frac{\partial Q}{\partial x}-\frac{\partial P}{\partial y})dxdy$

并且，对于平面上的有界闭区域，边界为分段光滑的简单闭曲线，有

$$
S=\int_{\partial D}xdy=-\int_{\partial D}ydx=\frac{1}{2}\int_{\partial D}xdy-ydx
$$

对于平面上的单连通区域，$P,Q\in C^1(D)$，以下四个命题等价。

一、$D$内，任意一条光滑或分段光滑闭曲线$\oint_L Pdx+Qdy=0$

二、$\int_L Pdx+Qdy$与路径无关。

三、存在$D$上的可微函数$U(x,y),s.t.\ dU=Pdx+Qdy$

四、$D$内，$\frac{\partial Q}{\partial x}=\frac{\partial P}{\partial y}$

对于有奇点的区域进行积分，可以将奇点附近挖掉，再进行Green公式。

单位外法向量为$\vec n$，另外一种常用形式为：

$$
\iint_D(\frac{\partial F}{\partial x} +\frac{\partial G}{\partial y}dxdy)=
\int_{\partial D}Fdy-Gdx\\
=\int_{\partial D}[F\sin(\tau, x)-G\cos(\tau, x)]ds\\
=\int_{\partial D}[F\cos(n,x)+G\cos(n,y)]
$$

类似于单连通区域的方式，我们定义三维空间中的一个区域是二维单连通区域，即对于区域中的任意一个曲面，都可以收缩为一个点。换言之，就是没有洞。

Gauss公式：对于一个二维单连通区域$\Omega$，边界$\partial\Omega$是分片光滑曲面。倘若对$\partial\Omega$赋予一个诱导定向，即指向$\Omega$外部。如果$\vec F\in C^1(\bar\Omega, R^3)$，则

$$
\iint_{\partial\Omega}\vec F\cdot\vec n ds=\iiint_\Omega\nabla\cdot\vec F dv
$$

证明方式：首先，我们要求每一个参数都能被另外两个参数限制在一个合适的连续范围内，然后，我们分三部分进行证明。如果一个区域可以被拆分为有限个上述的特殊区域，那么就可以得到证明。

我们定义$\vec F$在$P$点处的散度为$\nabla\cdot\vec F(P)=\lim_{V\to P}\frac{\int_{\partial V}\vec F\cdot d\vec S}{\mu(V)}$

其表示向量场在一个点附近是汇入还是流出，也记为$\text{div}\vec F$

Stokes公式：

$$
\int_{\partial\Sigma}\vec F\cdot\tau ds=\int_\Sigma(\nabla\times \vec F)d\vec S
$$

分量形式可以运用叉乘形式进行导出。一般地，倘若$\Sigma\sub R^2$，那么就退化为了Green公式。

倘若曲面$\Sigma$分别由两个自变量进行参数化，那么，就可以证明。一般而言，其思路为将曲面积分转化为重积分，然后，将重积分转化为别的曲面积分。

## 微分形式

0-form$\{f:R^3\to R\}$

1-form$\{Pdx+Qdy+Rdz|P,Q,R:R^3\to R\}$

2-form$\{Pdx\wedge dy+...|P,Q,R:R^3\to R\}$

3-form$\{A(x)dx\wedge dy\wedge dz\}$

外微分$d$的实质，就是将k-form化为k+1-form。

我们规定，外积具有分配律，具有反交换性，一个维度外积上自己值为0。也可以理解为面积为0。对于任意几何图形，求两次边界，结果就是0。

对于0-form进行外微分是平凡的。

广义Stokes定理：

$$
\int_M d\omega=\int_{\partial M}\omega\\
<d\omega, M>=<\omega,\partial M>
$$

# 函数项级数

## 一致收敛及其判定

点态收敛的概念：

固定一个$x$,$S(x)=\lim_{N\to+\infin}\sum_{n=1}^Na_n(x)$  并且$a_n(x)$在$E\sub R$上有定义，我们称$D=\{x\in E|\sum_{n=1}^\infin a_n(x)收敛\}$为$\{a_n(x)\}$的收敛域。我们称$\{a_n(x)\}$点态收敛于$S(x)$

在这里，我们需要一种更加强大的收敛性，也就是一致收敛性。

定义如下：

$$
\forall\varepsilon>0,\exist N(\varepsilon)\in N^+\\
\forall n>N(\varepsilon),\forall x\in D,|S_n(x)-S(x)|<\varepsilon
$$

那么就称$S_n$在$D$上一致收敛，记作$S_n\rightrightarrows S$

它的目标，就是为了抛开$x$，构造和$n$相关的收敛性质。

定义：$d_\infin (f,g)=\sup_{x\in D}|f(x)-g(x)|$

我们定义：$S_n\rightrightarrows S\iff \lim_{n\to\infin}d_\infin(S_n,S)=0$

定义这种一致收敛的概念，是为了更好地保持函数的连续性等性质。

倘$u_n(x)\in C[a, b]$，且函数$\sum_{n=1}^\infin u_n(x)$在$(a,b)$一致收敛，则$\sum_{n=1}^\infin u_n(a),\sum_{n=1}^\infin u_n(b)$均收敛，且函数$$\sum_{n=1}^\infin u_n(x)$在$[a,b]$一致收敛。

Cauchy收敛原理

$$
S_n\rightrightarrows S\iff \forall\varepsilon>0,\exist N\in\N,\\
\forall n>N, \forall p\in\N,\forall x\in D,|S_{n+p}(x)-S_n(x)|<\varepsilon
$$

一个显然的推论，就是

$$
\forall\varepsilon>0,\exist N\in\N,
\forall n>N, \\
\forall p\in\N,\forall x\in D,|\sum_{k=n+1}^{n+p}u_k(x)|<\varepsilon
$$

Weierstrass比较判别法：

$$
|u_n(x)|\leq a_n\in R,(\forall x\in D),\sum_{n=1}^\infin a_n<+\infin,\\
\sum_{n=1}^\infin u_n(x)在D上一致收敛
$$

函数项级数的A-D判别法：

$$
\sum_{n=1}^\infin a_n(x)b_n(x)在D上一致收敛，若以下条件之一满足：\\
\forall x\in D,\{a_n(x)\}关于n单调，且\{a_n\}一致有界，\sum_{n=1}^\infin b_n(x)\\
在D上一致收敛；\\
\forall x\in D,\{a_n(x)\}关于n单调，a_n\rightrightarrows 0,\\
B_n(x)=\sum_{k=1}^nb_k(x)一致有界
$$

一致有界，指的是$\exist M>0,\forall n,\forall x\in D,|a_n(x)|<M$

总而言之，一致就可以理解为与$x$无关。

一致收敛保证了连续性。如果一个函数列在区间上一致收敛于$f(x)$，并且函数列中每一个函数均连续，那么$f(x)$也连续。

倘函数列在开区间$D$内闭一致收敛于$S$,那么$S$在$D$一致收敛。亦即，连续性乃一局部性质。

倘函数列$S_n(x)\rightrightarrows S(x) $于区间$[a,b]$上，且$S_n(x)$于该区间上可积。则，$S(x)$于此区间上亦可积。且：

$$
\int_a^b S(x)=\int_a^b\lim_{n\to\infin}S_n(x)
$$

倘$S_n\in C^1[a,b]$，并且在区间上点态收敛，且$S_n'(x)\rightrightarrows \sigma$

则，$S_n$于区间上一致收敛至$S$，且$\frac{d}{dx}S(x)=\lim_{n\to\infin}S_n(x)=\sigma(x)$

对于连续性和可导性，则倘其于一开区间或半开半闭区间上连续，那么一致收敛之条件可以放宽至内闭一致收敛。

Dini定理:

函数列$S_n$点态收敛至$S$，且：

$$
S_n\in C[a,b]\\
S\in C[a,b]\\
\forall x\in[a,b], S_n(x)关于x单调
$$

则，其一致收敛。

## 幂级数

定义：形如$\sum_{n=0}^\infin a_n(x-x_0)^n$的级数。

关于幂级数的收敛，我们可以类似Cauchy判别法，考察：

$$
\bar\lim_{n\to\infin}\sqrt[n]{|a_nx^n|}=\bar\lim_{n\to\infin}\sqrt[n]{|a_n|}|x|
$$

如果上式小于1，那么幂级数$\sum_{n=0}^\infin a_nx^n$就是绝对收敛的。我们令$A=\bar\lim_{n\to\infin}\sqrt[n]{|a_n|}$,那么，我们就可以得到幂级数的收敛半径$R$.倘若$A\in \R^+$，那么收敛半径$R=\frac{1}{A}$。如果$A=\infin$，那么收敛半径为$0$。如果$A=0$,那么收敛半径为$\infin$.

Cauchy-Hadamard定理：

当$|x|<R$时，绝对收敛。大于$R$时，则发散。等于$R$时，则另行判定之。

此外，对于幂级数而言，逐项求导后或是逐项积分后，所得的级数收敛半径不变。但是端点处的行为可能发生变化。

d'Alembert判别法：

若$\lim_{n\to\infin}|\frac{a_{n+1}}{a_n}|=A$，则$\sum_{n=0}^\infin a_nx^n$之收敛半径为$\frac{1}{A}$

Abel第一定理：

倘$\sum_{n=0}^\infin a_nx^n$在$\xi$处收敛，那么$\forall |x|<|\xi|$，该级数依旧绝对收敛。倘$\sum_{n=0}^\infin a_nx^n$在$\eta$处发散，那么$\forall|x|>|\eta|$，该级数亦发散。但相等时，不可知。

Abel第二定理：

幂级数在收敛域中内闭一致收敛。倘在收敛域之边界上亦收敛，那么可在不含另侧端点的区间中内闭一致收敛。

在收敛域中的两点，具有逐项可积性。即先积分，后求极限和先求极限，后积分等价。逐项可导性亦类似。

利用这一点，我们可以计算高中时常用错位相消解决的问题。其思路，就是将其乘方的对象看做一个自变量，构造一个函数，使得求导后得到目标式子。

# Fourier级数

## 三角函数系

对于$\int_{-\pi}^\pi\cos mx\cos nx dx,\int_{-\pi}^\pi\sin mx\sin nxdx,\int_{-\pi}^\pi\cos nx\sin mxdx$，考察$m=n,m\not=n$或者均为0的情况，可以得到不错的积分值，称为三角函数系的正交性。这里可以使用积化和差公式进行推导。

如果函数$f$以$2\pi$为周期，且函数在区间$[a, b]$上可积或广义绝对可积，那么我们可以有：

$$
f(x)\sim\frac{a_0}{2}+\sum_{n=1}^\infin(a_n\cos nx + b_n\sin nx)
$$

并且，对于每一个系数，我们有：

$$
a_k=\frac{1}{\pi}\int_{-\pi}^\pi f(x)\cos kx dx\\
b_k=\frac{1}{\pi}\int_{-\pi}^\pi f(x)\sin kxdx
$$

如果一个函数为奇函数，那么$a_i$均为$0$.如果一个函数是偶函数，那么$b_i$均为0.

如果$f$在$[-T, T]$上有所定义，那么可以考虑用$\cos\frac{n\pi x}{T},\sin\frac{n\pi x}{T}$

倘若一个函数$f$越光滑，那么$a_n,b_n$的衰减速度也越快。

Riemann-Lebesgue引理：倘$f$于$[a,b]$上可积或广义绝对可积，那么：

$$
\lim_{\lambda\to\infin}\int_a^b f(x)\cos\lambda x dx=0\\
\lim_{\lambda\to\infin}\int_a^b f(x)\sin\lambda x dx = 0
$$

我们记录Fourier级数之部分和为$S_n[f](x)$

这从直觉上是好理解的。我们称其为n阶Fourier级数多项式。

假定$f$为周期为$2\pi$的函数。通过不断的分部积分和变元替换，我们可以得到：

$$
S_n[f](x)=\frac{1}{\pi}\int_{-\pi}^\pi f(x+u)\frac{\sin\frac{2n+1}{2}u}{2\sin\frac{u}{2}}du
$$

我们称$\frac{\sin\frac{2n+1}{2}u}{2\sin\frac{u}{2}}$为Dirichlet核。

更加一般化的情况，我们可以考察：

$$
S_n[f](x)-\frac{f(x+0)+f(x-0)}{2}\\
=\int_{0}^\pi\frac{f(x+u)-f(x+0)+f(x-u)-f(x-0)}{2}\cdot\frac{1}{\pi}D_n(x)du
$$

将其积分区间进行拆分，记上式中的被积对象为$h(u)$，将积分区间进行拆分，即：

$$
\int_0^\delta h(u)du+\int_\delta^\pi h(u)du
$$

我们只需要关注前一部分即可。因为由Riemann-Lesbegue引理，迫使后一部分趋向于0。

倘若：$f$于$[-\pi,\pi]$可积，于$x$处$f(x+0),f(x-0)$均存在，亦即，不要求函数连续，然需每一点处，两侧极限存在；且，有：

$$
\int_0^\delta\frac{f(x+u)-f(x+0)}{u}du\\
\int_0^\delta\frac{f(x-u)-f(x-0)}{u}du
$$

均绝对收敛，则：

$$
\lim_{n\to\infin}S_n[f](x)=\frac{1}{2}(f(x+0)-f(x-0))
$$

Dirichlet定理：

倘$f$以$2\pi$为周期，且分段可导，且至多有有限个极值点，那么有：

$$
\forall x\in[-\pi,\pi],\lim_{n\to\infin}S_n[f](x)=\frac{1}{2}[f(x+0)+f(x-0)]
$$

Rmk:倘$f\in C^2[-\pi,\pi]$,且$f(-\pi)=f(\pi),f'(\pi)=f'(-\pi)$，则$S_n[f]\rightrightarrows f$

倘$f(-\pi)=f(\pi)$且函数连续分段线性，那么我们所得的级数亦绝对收敛。

Weierstrass逼近定理：

$f\in C[-\pi,\pi]$,$f(-\pi)=f(\pi)$，则$\forall\varepsilon>0,\exist$有限的三角多项式$T(x)$，即$T(x)=a_0+\sum_{k=1}^l(a_k\cos kx+b_k\sin kx)$，从而使得$|f(x)-T(x)|<\varepsilon,\forall x\in[-\pi,\pi]$

此可通过用阶梯函数$g(x)$去逼近目标之$f(x)$，再用Fourier级数逼近之。

Weierstrass定理：

$$
f\in C[a, b],\forall\varepsilon>0,\exist P(x)
$$

其中$P(x)$为一个多项式函数。

$|f(x)-P(x)|<\varepsilon,\forall x\in[a, b]$

Fourier级数在内积空间中收敛。本质上，我们可以认为Fourier级数是"内积空间"$(R[-\pi,\pi],<f,g>=\int_{-\pi}^\pi fgdx$

在正交基$\{1,\sin kx, \cos kx,k\geq 1\}$的展开。

Bassel不等式：

$$
\frac{a_0^2}{2}+\sum_{k=1}^n(a_k^2+b_k^2)\leq\frac{1}{\pi}\int_{-\pi}^\pi f^2(x)dx
$$

Parseval等式：

$$
\frac{a_0^2}{2}+\sum_{n=1}^\infin(a_n^2+b_n^2)=\frac{1}{\pi}\int_{-\pi}^\pi f^2(x)dx
$$
