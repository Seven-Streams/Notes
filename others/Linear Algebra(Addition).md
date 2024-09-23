# 向量空间拾遗

## 组(list)和长度(length)的定义

设$n$是**非负整数**。我们称$n$个有顺序的元素是一个长度为$n$的组，表示为$(x_1,...,x_n)$。两个组相等当且仅当长度和其中的元素均相等。

特殊地，我们称长度为2的组是有序对(pair)，长度为3的组是有序三元组(triple)。所有的组一定是有限长度的，因为$n$是非负整数。长度为0的组也是可以的。

组中的元素**可以重复**，是**有序的**。

## $F^n$的定义

$F^n$是F中元素组成的长度为n的组的集合。我们称这个组中的第j个元素为这个组的第j个坐标。

## 域的性质

对域定义的两种运算满足交换律和结合律。存在乘法单位元和加法单位元。存在加法逆元，对于非0元素存在乘法逆元，满足数乘的分配律。

## $F^S$的定义

令$S$是一个集合，我们用$F^S$表示S到F的所有函数的集合。

也就是说，每一个F中的n元组，我们可以将其视为一个$[n]\to F$的函数。

## 子空间的和

我们首先需要定义子集的和。子集的和，定义为在每一个子集中挑选出一个元素，将其相加所能得到的所有的和所构成的集合。

子空间的和依旧是子空间。并且，它们的和是包含这些子空间的**最小子空间**。

## 直和

$$
若U_1+...+U_m中的每一个元素可以唯一表示为\\
u_1+...+u_m,其中u_j\in U_j，那么称这样的子空间和为直和。\\
记作U_1\oplus ...\oplus U_m
$$

子空间之间的和是直和，当且仅当0表示为$u_1+...+u_m$时，每一个$u_j$都等于0。

两个子空间之间的和是直和，当且仅当两个子空间的交集中只有0。

# 有限维向量空间拾遗

多项式是一个向量空间。

多项式$p$的次数：系数不为0的最高项的次数，记作$deg(p)$规定恒等于0的多项式次数为$-\infin$。

我们用$P_m(F)$表示系数在$F$中并且次数不超过$m$的所有多项式构成的集合。$P(F)$表示系数在$F$中的所有多项式构成的集合。

对于有限维的向量空间$V$而言，对于$\forall$子空间$U$，$\exist$子空间$W,s.t.V=U\oplus W$

$$
\dim(U_1+U_2)=\dim U_1+\dim U_2 -\dim(U_1\cap U_2)
$$

# 线性映射拾遗

定义：$L(V,W)$表示$V$到$W$的所有线性映射的集合。这是一个线性空间。

零空间（核）的定义，指的是$T\in L(V,W)，V$中被$T$映射为$0$的向量子集。remark：考虑矩阵时，把矩阵看做是线性映射。

零空间是V的子空间。

像是W的子空间。

当齐次线性方程组中，变量数多于方程时，齐次线性方程组一定有非零解。

remark：我们可以把它考虑成一个矩阵，并且列数多于行数。那么零空间的维数一定不为0。

一个线性映射是可逆的，当且仅当它是双射。它的逆是唯一的。

同构，指的就是可逆的线性映射。如果两个向量空间之间存在一个同构，那么这两个向量空间是同构的。$F$上的两个有限维向量空间同构，当且仅当其维数相同。

我们定义，向量空间到自身的线性映射称为**算子**。

$L(V)$表示$V$上全体算子所组成的集合。

假设$V$是有限维，$T\in L(V)$。若$T$是单射（满射），则$T$是可逆的。

我们定义，向量空间$V_1,V_2,...,V_m$的积$V_1\times V_2\times ...\times V_m=\{(v_1,...,v_m):v_i\in V_i\}$

向量空间的积也是个向量空间。

向量空间积的维数显然等于各向量空间的维数之和。

定义$\tau(u_1,...,u_m)=u_1+...+u_m$则$U_1+...+U_m$是直和当且仅当$\tau$为单射。

设$V$是有限维的，$U_1,...,U_m$均为$V$的子空间。则$U_1+...+U_m$是直和当且仅当$\dim(U_1+...+U_m)=\sum_{i=1}^m\dim U_i$

我们定义$v+U=\{v+u:u\in U\},U\subset V,v\in V$

我们称$V$的形如$v+U$的子集为$V$的仿射子集。仿射子集$v+U$平行于$U$。remark：这里的平行需要注意维数的问题。

设$U\subset V$,商空间$V/U$指$V$所有的平行于$U$的仿射子集的集合。即$V/U=\{ v+U : v\in V\}$

平行于$U$的两个仿射子集要么相等，要么不相交。

商空间上的加法和标量乘法比较特殊。

$$
(v+U)+(w+U)=(v+w)+U\\
\lambda(v+U)=(\lambda v)+U
$$

商空间也是个向量空间。

设$U$是$V$的子空间，商映射$\pi:\pi(v)=v+U$

$\dim V/U=\dim V-\dim U$

$T\in L(V,W)$，定义$\tilde T:V/ null(T)\to W,\tilde T(v+null(T))=T(v)$

我们定义$V$上的线性泛函是$V\to F$的线性映射。

$V$上的所有线性泛函构成的向量空间称为$V$的对偶空间，记作$V'$。

若$V$是有限维的，对偶空间的维数与原空间维数相同。

对偶基是对偶空间的一组基。

若$T\in L(V,W)$，$T$的对偶映射是$T'\in L(W',V')$，若$\phi\in W',T'(\phi)=\phi\circ T$

$(ST)'=T'S'$，对偶映射的其他运算是平凡的。

零化子的定义：$U\subset V,U^0=\{\phi\in V':\forall u\in U,\phi(u)=0\}$

$null(T')=(range\ T)^0$

$U^0$是$V$的子空间。并且，$\dim U+\dim U^0=\dim V$

$T$满射，等价于$T'$单射。

$\dim range (T')=\dim range(T)$

$M(T')=(M(T))^T$

转置和对偶之间有很大的相关性，行秩等于列秩。

# 多项式

$p,s\in P(F),s\not=0,\exist !q,r\in P(F),s.t.\\ p=sq+r,\deg r < \deg s$

多项式$s\in P(F)$是$p\in P(F)$的因式$iff\ \exist q\in P(F),s.t.p=sq$

多项式的每个零点对应一个一次因式。

多项式零点个数不超过多项式次数。

实系数多项式的非实零点**成对**出现。

# 本征值、本征向量、不变子空间

## 不变子空间

$$
T\in L(V),U\subset V,iff\forall u\in U,Tu\in U
$$

则称$U$在$T$下不变。

接下来，考虑一维（不包括$Z$)的不变子空间。就有$Tv=\lambda v$

这里，我们就得到了特征值（本征值）。$v$就是特征向量。

当$U$是$V$下的不变子空间时，我们做出如下定义：

限制算子：$T|_U\in L(U),T|_U(u)=Tu,u\in U$

商算子：$T/U\in L(V/U),(T/U)(v+U)=Tv+U,v\in V$

我们定义$T^m\in L(v),m\in N,T^0=I,T^m=TTT...T,T^{-m}=(T^{-1})^m$

$T\in L(V),p\in P(F),z\in F,p(z)=a_0+a_1z+...+a_mz^m.\\ p(T)=a_0I+a_1T+...+a_mT^m$

$pq(T)=p(T)q(T)=qp(T)=q(T)p(T)$

所以，算子的任意两个多项式是交换的。

复向量空间上，每个算子一定有特征值。这是代数学基本定理确定的。

对于复向量空间上的每个算子，存在一组基，使得算子对应的矩阵是上三角矩阵。

设$T\in L(V),v_1,...,v_n$是$V$的基，则以下条件等价：

$$
T对应矩阵为上三角矩阵\\
\forall j\in[n],span(v_1,...,v_j)在T下不变\\
$$

如果$T\in L(V)$关于$V$的某个基有上三角矩阵，则矩阵可逆当且仅当对角线上元素都不为零。在这种上三角矩阵中，特征值就是对角线上的元素。也就是，0不是它的特征值。

特征空间的定义已经知道了。若$V$是有限维，$T\in L(V)$，互异的特征值$\lambda_1,\lambda_2,...,\lambda_m$对应的特征空间的和是直和。

$T\in L(V)$可对角化，当$T$关于$V$的某个基有对角矩阵。也就是说，它的特征向量构成一组基。

# 内积空间

范数的定义：$||x||=\sqrt{<v,v>}$

内积的抽象定义：

$$
u,v\in V,(u,v)\to F\\
<v,v>\geq0\\
<v,v>=0\iff v = 0\\
<u+v,w>=<u,w>+<v,w>\\
<\lambda u,v>=\lambda<u,v>\\
<u,v>=\overline {<v,u>}
$$

欧几里得内积：

$$
<(w_1,...,w_n),(z_1,...,z_n)>=w_1\bar {z_1}+...+w_n\bar {z_n}
$$

内积空间，就是带有内积的向量空间。

故，$||v||=0\iff v=0\\ \forall \lambda\in F,||\lambda v||=|\lambda|||v||$

两个向量正交，iff$<u,v>=0$

$|<u,v>|\leq||u||||v||$

$||u+v||\leq||u||+||v||$

$||u+v||^2+||u-v||^2=2(||u||^2+||v||^2)$

标准正交的向量组

向量可以写成标准正交基的线性组合

$\dim(V)<\infin,T\in L(V),T$关于$V$的某个标准正交基有上三角矩阵。

里斯表示定理：$\dim(V)<\infin,\phi\in L(V,F),\exist!u\in V,s.t.\forall v\in V,\phi(v)=<v,u>$

证明方式：正交分解

$if\ U\subset V,\dim(U)<\infin,V=U\oplus U^\perp$

$if\ U\subset V,\dim(U)<\infin,U=(U^\perp)^\perp$

定义正交投影$P_U$

$$
U\subset V,\dim(U)<\infin,P_U\in L(V)\\
v\in V,v=u+w,u\in U,w\in U^\perp,P_Uv=u
$$

到子空间距离最小的问题

# 内积空间上的算子

伴随的定义：$T\in L(V,W),T^*:W\to V,\forall v\in V,\forall w\in W \\ <Tv,w>=<v,T^*w>$

伴随定义的合理性来源于里斯表示定理。当$w$给定时，$<Tv,w>$是一个线性泛函。所以，$\exist!u\in V,s.t.<Tv,w>=<v,u>,u=T^*w$

$T\in L(V,W),T^*\in L(W,V)$

$(S+T)^*=S^*+T^*$

$(\lambda T)^*=\bar\lambda T^*$

$(T^*)^*=T$

$I^*=I$

$(ST)^*=T^*S^*$

$$
null(T^*)=(range T)^\perp\\
range(T^*)=(nullT)^\perp\\
nullT=(range(T^*))^\perp\\
rangeT=(null(T^*))^\perp
$$

共轭转置的定义是符合直觉的。

$T\in L(V,W),T^*\in L(W,V)$，在基相同的前提下，二者的矩阵互为共轭转置。

定义了伴随的概念，我们可以定义**自伴性(厄米特性）**:$T=T^*$

也就是说，自伴算子对应的每个矩阵的特征值都是实数。

$$
F=C,iff\ T\in L(V),T:V\to0,\forall v\in V,<Tv,v>=0\\
F=C,iff\ T\in L(V),T\ is\ self-adjoint,\forall v\in V,<Tv,v>\in R
$$

$$
if\ T=T^*,\forall v,<Tv,v>=0,then\ T=0
$$

我们在这里可以定义**正规的(normal)**:$T\in L(V),iff\ TT^*=T^*T$

$T\ is\ normal\iff\forall v,||Tv||=||T^*v||$

如果$T$是正规的，那么$T$和$T^*$有相同的特征向量。

正规算子的线性独立的特征向量相互正交。

复谱定理：下述三条等价

$$
F=C,T\in L(V)\\
1)T\ is\ normal.\\
2)V\ has\ a\ basis\ consisted\ of\ orthonormal\ eigenvectors.\\
3)T\ has\ a\ diagonal\ matrix\ with\ an\ orthonormal\ basis.
$$

实谱定理

二次式可逆性：

$$
T\in L(V)\ is\ self-adjoint,b,c\in R,b^2<4c\\
T^2+bT+cI\ is\ invertible.\\
Because\ (T^2+bT+cI)v\not=0,that\ implies\ it's\ injective.
$$

$T\in L(V)\ is\ self-adjoint,U\subset V$,$U$在$T$下不变，那么$U^\perp$在$T$下亦不变；$T|_U\in L(U),T|_{U^\perp}\in L(U^\perp)$均是自伴的。

下述三条等价：

$$
F=R,T\in L(V)\\
1)T\ is\ self-adjoint.\\
2)V\ has\ a\ basis\ consisted\ of\ orthonormal\ eigenvectors.\\
3)T\ has\ a\ diagonal\ matrix\ with\ an\ orthonormal\ basis.
$$

$$
T\in L(V)是正的\iff T\ is\ self-adjoint,\forall v\in V,<Tv,v>\geq0
$$

$$
if\ U\subset V,P_U\ is\ a\ positive\ operator.\\
if\ T\in L(V)\ is\ self-adjoint,b ^2-4c<0,then\\
T^2+bT+cI\ is\ positive.
$$

我们可以定义算子的平方根：$R$是$T$的平方根$\iff R^2=T$

正算子有多种刻画的方式。若$T\in L(V)$，则下列条件等价。

$$
T\ is\ a\ positive\ operator.\\
T\ is\ self-adjoint\ and\ all\ the\ eigenvalues\ of\ M\geq0\\
T\ has\ a\ positive\ square\ root.\\
T\ has\ a\ self-adjoint\ square\ root.\\
\exist R\in L(V),s.t.T=R^*R
$$

每个正算子只有唯一的正平方根。

$S\in L(V)$是等距同构$\iff \forall v\in V,||Sv||=||v||$

在实内积空间上的等距同构，我们称之为**正交算子**，复内积空间上的等距同构，我们习惯性称之为**酉算子**。

$S\in L(V)$，则以下条件是等价的。

$$
S是等距同构。\\
\forall u,v\in V,<Su,Sv>=<u,v>\\
if\ e_1,...,e_n\ are\ orthonormal\\
Se_1,...,Se_n\ are\ orthonormal\ too.\\
S^*S=I\\
SS^*=I\\
S^*是等距同构。
S\ is\ invertible,S^{-1}=S^*
$$

考虑复内积空间上的等距同构的描述。

$$
S是等距同构\iff V\ has\ an\ orthornormal\ basis\ consisted\\
of\ all\ the\ eigenvectors,and\ each\ eigenvalue\ equals\ to\ \underline + 1
$$

**极分解**

$$
T\in L(V),\exist S\in L(V)为等距同构，s.t.\ T=S\sqrt{T^*T}
$$

$$
T\in L(V),T's\ singular\ values\ are\ the\ eigenvalues\ of\ \sqrt{T^*T}
$$

$$
T\in L(V)\ has\ singular\ values\ s_1,...,s_n,\\
V\ has\ two\ orthronormal\ bases\ e_1,...,e_n\ and\ f_1,...,f_n,s.t.\\
\forall v\in V,Tv=s_1<v,e_1>f_1+...+s_n<v,e_n>f_n
$$

或者，奇异值可以这样描述

$$
T\in L(V),T's\ singular\ values\ are\ the\ non-minus\ square\\
roots\ of\ T^*T's\ eigenvalues,with\ \dim(E(\lambda,T^*T))\ times\ repetations.
$$

# 复向量空间上的算子

显然有：

$$
T\in L(V),\{0\}=null\ T^0\subset\ null\ T^1\subset\ ...\\
if\ \exist m\in N^+,null\ T^m=null\ T^{m+1},then\\
null\ T^m=null\ T^{m+1}=null\ T^{m+2}=...
$$

$$
T\in L(V),n=\dim(V),null\ T^n=null\ T^{n+1}=null\ T^{n+2}=...
$$

零空间是会停止增长的。

因为，在每一个严格包含的关系处，空间的维数至少会增加1。

$$
V=null\ T^{\dim V}\oplus range\ T^{\dim V}
$$

在这里，我们需要引入广义特征向量的概念。

$T\in L(V),\lambda$是$T$的特征值，$v\in V$称为$T$相应于$\lambda$的**广义特征向量**，$v\not=0,\exist j\in N^+,s.t.(T-\lambda I)^jv=0$

我们相应地，也可以定义广义特征空间，$G(\lambda,T)$。

$T\in L(V),\lambda \in F$，$T$相应于$\lambda$的广义特征空间定义为$T$相应于$\lambda$的所有广义特征向量的集合，包括$0$。

对于广义特征空间，我们有这样的表示方式：

$$
T\in L(V),\lambda\in F,G(\lambda,T)=null(T-\lambda I)^{\dim V}
$$

广义特征向量具有这样的特点。

$$
T\in L(V),\lambda_1,...,\lambda_m\ are\ distinct\ eigenvalues,\\
v_1,...,V_m\ are\ generalized\ eignvectors,then\\
they\ are\ linearly\ independent.
$$

考虑到我们现在一直在研究幂算子，我们可以引入幂零（nilpotent)这个概念。

一个算子是**幂零**的$\iff\exist j\in N^+,T^j=0$

$N\in L(V)$是幂零的，则$N^{\dim V}=0$

如果$N$是幂零的，那么$V$中存在一组基，使得它的矩阵不仅是上三角的，而且对角线上所有元素均为0。

在定义了广义特征向量之后，我们就可以考虑对算子进行分解了。

$T\in L(V),p\in P(F)$，则$null\ p(T),range\ p(T)$在$T$下不变。

$V$是复向量空间，$T\in L(V)$,$\lambda_1,...,\lambda_m$为不同特征值，则：

$$
V=G(\lambda_1,.T)\oplus...\oplus G(\lambda_m,T)\\
G(\lambda_j,T)在T下不变\\
(T-\lambda_jI)|_{G(\lambda_j,T)}均是幂零的。

$$

所以，当$V$是复向量空间，$T\in L(V)$，V有一个由广义特征向量所组成的基。

$T\in L(V),T$的特征值$\lambda$的重数定义为相应的广义特征空间$G(\lambda,T)$的维数，即$\dim null(T-\lambda I)^{\dim V}$

由于上述中，广义特征空间的直和构成整个空间，所以重数之和显然等于$\dim V$

此处的重数，与代数重数值相同。但是，几何重数指的是特征空间的维数。

若$V$是复向量空间，$T\in L(V),\lambda_1,...,\lambda_m$是$T$的所有不同的特征值，重数分别为$d_1,...,d_m$，那么存在一个基，使得$T$关于这组基有分块对角矩阵。并且，每一个块状矩阵都是$d_j\times d_j$的上三角矩阵。

$N\in L(V)$是幂零的，那么$(I+N)$有平方根。

$V$是复向量空间，$T\in L(V)$若是可逆的，那么$T$有平方根。

我们这样定义$T\in L(V)$的特征多项式。设$T$的特征值为$\lambda_1,...,\lambda_m$，重数分别为$d_1,...,d_m$，则其特征多项式称为$(z-\lambda_1)^{d_1}...(z-\lambda_m)^{d_m}$

设$V$是复向量空间，$T\in L(V)$，$q$是$T$的特征多项式，那么$q(T)=0$

特征多项式的次数恰为$\dim V$，特征多项式的零点恰好是$T$的特征值。

考虑到归一化的重要性，我们可以引入首一多项式的概念。即，最高次数的项的系数为1的多项式。

$T\in L(V),\exist!p,p(T)=0,p$是次数最小的首一多项式。我们把这样的$p$称为$T$的极小多项式。

又因为$q(T)=0$，所以$q$是$T$的极小多项式的多项式倍。$T$极小多项式的零点恰好是$T$的特征值。

在定义了这些内容之后，我们可以来讨论若尔当型。

$$
N\in L(V)是幂零的，\exist v_1,...,v_n\in V,m_1,...,m_n\in N,s.t.\\
N^{m_1}v_1,...,N^0v_1,...,N^{m_n}v_n,...,N^0v_n是V的基\\
N^{m_1+1}v_1=...=N^{m_n+1}v_n=0
$$

$$
T\in L(V),V的基称为T的若尔当基if\ T关于这组基有分块对角矩阵\\
\begin{bmatrix}
A_1&&0\\
&...&\\
0&&A_p
\end{bmatrix}\\
A_i=\begin{bmatrix}
\lambda_i&1&&0\\
&...&...&\\
&&...&1\\\
0&&&\lambda_j
\end{bmatrix}
$$

也就是说，通过线性变换，每一个向量映成其前一个向量复合上一定长度的自身。

# 实向量空间上的算子

考虑$V$是一个实向量空间，我们定义其**复化**为$V\times V$，其元素是有序对$(u,v)$，$u,v\in V$我们不妨将其写作$u+iv$

$V\subset V_C$，$V_C$显然是复向量空间。

如果$v_1,...,v_n$为$V$作为实向量空间的一组基，那么它们也是$V_C$作为复向量空间上的一组基。$V$和$V_C$维数相等。

根据空间的复化，我们类似地，也可以定义算子的复化。$V$是实向量空间，$T\in L(V)$，$T$的复化定义为$T_C(u+iv)=Tu+iTv,T_C\in L(V_C)$

$T_C$的矩阵显然等于$T$的矩阵，二者选取的基相同。

每一个算子都有一维或者二维的不变子空间。

$T_C$的极小多项式等于$T$的极小多项式。

$T_C$的实特征值和$T$的实特征值相同。如果$\lambda\in C$是$T_C$的特征值，那么$\bar\lambda$也是$T_C$的特征值，且重数相同。也就是成对出现。因此，奇数维实向量空间上的算子一定有特征值。同时，$T$的复化$T_C$的特征多项式的系数也都是实数。

$V$是实向量空间，$T\in L(V)$，则$T$的特征多项式的系数均为实数，次数为$\dim V$,$T$的特征值为特征多项式的所有实零点。

在实内积空间上，我们有这样对二维实内积空间正规算子的描述。

$$
T正规但不自伴。\\
T关于V的每个标准正交基的矩阵都有\begin{bmatrix}
a&-b\\
b&a
\end{bmatrix}的形式，b\not=0\\
T关于V的某个标准正交基矩阵有\begin{bmatrix}
a&-b\\
b&a
\end{bmatrix}的形式，b>0
$$

这三个条件是等价的。

倘若$V$是内积空间，$T\in L(V)$是正规的，$U\subset V$是$T$下的不变子空间，那么

$$
U^\perp在T下不变\\
U在T^*下不变\\
(T|_U)^*=(T^*)|_U\\
T|_U\in L(U)和T|_{U^\perp}\in L(U^\perp)都是正规算子。
$$

实内积空间上，正规算子可以这样刻画：

$$
V的某个标准正交基使得T关于这个基有分块对角矩阵\\
每个块要么是1\times 1矩阵，要么是形如\begin{bmatrix}
a&-b\\
b&a
\end{bmatrix}的2\times2矩阵，b>0
$$

实内积空间上，等距同构可以这样刻画：

$$
V的某个标准正交基使得T关于这个基有分块对角矩阵\\
每个块要么是由1或-1构成的1\times 1矩阵，\\要么是形如\begin{bmatrix}
\cos\theta&-\sin\theta\\
\sin\theta&\cos\theta
\end{bmatrix}的2\times2矩阵，\theta\in(0,\pi)
$$

# 迹与行列式

算子的迹为按重数重复的全部特征值之和。其等于特征多项式中$z^{\dim V -1}$系数的相反数。

方阵的迹定义为对角线的元素之和。$trace(AB)=trace(BA)$

算子的迹与基的选取无关，其迹与矩阵的迹相同。

迹具有可加性。

算子的行列式是按照重数重复的全体特征值之积。

行列式等于特征多项式中的常数项乘上$(-1)^{\dim V}$

$T$的特征多项式等于$\det(zI-T)$

行列式具有可乘性。

$|\det T|=\det\sqrt{T^*T}$
