# 一、向量简介

单位向量

向量的垂直

向量的点积

单位向量

# 二、矩阵

# 三、线性方程组

两种观点：直线的交点或者向量的和

# 四、矩阵求解线性方程组

系数矩阵

矩阵的乘积：定义，列的线性组合，行的线性组合，混合观点

方程组的pivot

上三角方程组

全等矩阵

# 五、矩阵计算法则

加法的交换律和结合律

乘法的结合律和分配律

矩阵可以视为是一个函数，将n维向量映射到m维上。

# 六、高斯消元

消元矩阵

置换矩阵

增广矩阵

分块矩阵

# 七、分块矩阵和乘法

分块要求：左侧分块的列等于右侧分块的行

# 八、逆矩阵

可逆性和逆矩阵的唯一性

矩阵可逆，则

$$
A\vec x=\vec b有唯一解。
$$

$$
(AB)^{-1}=B^{-1}A^{-1}
$$

# 九、转置和置换

矩阵转置的定义及性质

矩阵的对称性

$$
(AB)^T=B^TA^T

$$

$$
(A^{-1})^T=(A^T)^{-1}
$$

$$
A\vec x\cdot\vec y = \vec x A^T\cdot\vec y
$$

对于置换矩阵，有$P^{-1}=P^T$

对于对称矩阵，有$S=S^T$

# 十、线性空间

线性空间对标量乘法和加法封闭。

线性空间具有八大性质。两条结合律，两条分配律，一条交换律，逆元，**0**，以及单位标量数乘。

**Z**是只包含零向量的线性空间。它的基是空串。

向量加法等式具有消去律。

逆元具有唯一性。

# 十一、子空间

子空间必须是非空的线性空间。

子空间中运算规律继承自原空间。

子空间中必须包含零向量。

列空间

$$
A\vec x=\vec b
$$

iff**b**落在C(**A**)中时有解。

向量的span：所有向量线性组合的全体。

令**S**是**V**的一个子空间。那么span(**S**)是**V**中包含**S**的最小子空间。

零空间

# 十二、独立，基和维数

线性独立：和为零向量只有全零解。

零向量是线性相关的。

基：线性独立，张出空间

# 十三、线性空间的维数

线性空间基的个数

Steinitz向量交换律

由有无穷个元素的向量组成的线性空间，不可能有有限个基。

有限维情况下，子空间维数小于原空间。

# 十四、列秩

列秩即dim(C(**A**))。

**A**是一个m*n的矩阵。那么iff rank(A) = m,存在一个n *m的矩阵**B**，s.t.

$$
AB=I
$$

但是这并不意味着A可逆。

列秩等于行秩。iff矩阵满秩，矩阵可逆。

# 十五、初等阵和它们的逆

初等阵

置换阵

# 十六、高斯-乔丹法求矩阵的逆

满秩，即意味着有n个pivot

如果没有n个pivot，那就意味着消元会出现全0行。那么，就不可能可逆。

对角优势矩阵一定可逆

阶梯型

正规做法(?):依次检索每一列，将该列第一个不为零的提到最前面，将这一列消干净。

# 十七、矩阵的秩

最简阶梯型

所有初等阵不改变矩阵的秩

# 十八、零空间

零空间和列空间维数和等于列数

零空间的特解

主列和自由列

$$
A\vec x=\vec b的通解：利用零空间的特解。
$$

# 十九、正交性

两个平面正交，iff任意分别属于两个平面的向量均垂直。

行空间和零空间正交。

$$
A^{\perp} = \{\vec u|all\:\vec v \perp \vec u,\vec v \in A\}
$$

这个子空间与**A**正交。这个子空间是最大的和**A**正交的子空间。

任意一个空间中的向量，都可以进行正交分解。投影到两个正交的空间上。

# 二十、投影

直线上的投影

正交——最小的距离

目标空间矩阵

误差向量

如果**A**是满秩的，则：

$$
A^TA是满秩的。
$$

如果**A**不是满秩的，那么删去其中的一些列，保证列空间不变，化归为满秩的情况。

投影矩阵：利用正交性得到

# 二十一、最小二乘估计

最小二乘解：误差向量的长度。

# 二十一、正交基和格拉姆-施密特法

正交阵：每列垂直并为单位向量的方阵。

正交阵的逆矩阵是自身的转置。

如果每列垂直，那么每行也垂直。

正交阵作用在一个向量上，不会改变它的模。

正交阵作用在两个向量上，不会改变它们的夹角。

通过将向量在之前的列向量上的投影分解，可以得到垂直的向量。

m*n列的矩阵，如果每个列向量线性独立，那么就可以化归成每个列向量都是正交的单位向量的形式。

# 二十二、行列式

行列式表示向量张出的”体积“。

行列式对矩阵而言，具有列线性性，具有列相加不变性，具有标准化性。

列交换后，行列式值取反。（可由三条性质推得）

有全0列，有相同列，非满秩，那么行列式为0。

对于三角阵，行列式值等于所有对角线上元素的乘积。

# 二十三、行列式的计算

行列式与其转置相同。

这一点可以利用初等阵行列式与其转置相同，后归约可得。

行列式具有可乘性。

$$
det(AB)=det(A)det(B)
$$

证明：首先说明对初等阵，上式成立。随后，说明所有可逆阵都是初等阵的乘积，将其中一个矩阵分解即得。

对于正交阵，行列式绝对值为1。

所有可逆阵都是初等阵的乘积。

# 二十四、行列式的正式定义

逆序数的概念

符号由逆序数的奇偶性决定

余子式的定义，其符号由行和列共同决定

行列式的另一种计算方式：

$$
det(A)=\sum_{i=1}^na_{ij}C_{ij}
$$

或者

$$
det(A)=\sum_{j=1}^na_{ij}C_{ij}
$$

这种计算方法的证明：首先，利用行列式每列的线性性，然后利用行交换的反对称性，最后利用列加法时行列式的不变性可得。

克莱姆法则

$$
A\vec x=\vec b
$$

假定**A**是一个n* n的矩阵，想要求**X**i的值，那么我们可以构造矩阵C，s.t.

$$
C=\begin{bmatrix} 
\vec e_1 \:\ \vec e_2 \:\ ......\:\ \vec e_{i-1} \:\ \vec x \:\ ....... \:\ \vec e_n 
\end{bmatrix}
$$

那么，我们有

$$
AC=
\begin{bmatrix}
\vec a_1 \:\ \vec a_2 \:\ ...... \:\ \vec b \:\ ...... \:\ \vec a_n
\end{bmatrix}
$$

那么，我们就有

$$
det(A)x_i=det(AC)
$$

特殊地，当我们要求逆矩阵时，不过是解很多个A**x**= **b**罢了，我们可以得到

$$
x_{ij}=C_{ji}/det(A)
$$

这就是克莱姆法则求逆矩阵。

伴随矩阵的定义。其中，每个元素有：A*(i,j)=Cji，AA*=**I**

# 二十五、特征值与特征向量

$$
A\vec x =\lambda \vec x
$$

**x**是一个非零向量。那么，$\lambda(\lambda \in C)$就是A的一个特征值，**x**是与之对应的一个特征向量。

如果0是A的一个特征值，那就意味着A并非满秩。

对于一个对角阵而言，对角线上的每个值都是这个矩阵的一个特征值，对应的单位向量为与之对应的特征向量。并且这些向量**相互线性独立**。注意：前提是对角阵。

倘若特征值不同，其对应的特征向量必然线性独立。

Pf:

$$
\sum_{i=1}^kc_i\vec x_i=\vec 0 \:\ iff\:\ \forall i\in[k],i=0\\
if \:\ k=1,it's\:\ trivial.\\
Assuming\:\ that\:\ when\:\ k=n\\
\forall i\in[k],\vec x_i\:\ are\:\ linearly\:\ independent.\\
When\:\ there\:\ are\:\ n+1\:\ vectors,if\:\ they\:\ are\:\ linearly
dependent\\
\vec x_i=\sum_{j\in[k]\\ \{n\}}-{c_j\over c_i}\vec x_j \\
A\vec x_i=A\sum_{j\in[k]\\ \{n\}}-{c_j\over c_i}\vec x_j\\
\lambda_i \vec x_i=\sum_{j\in[k]\\ \{n\}}-{c_j\over c_i}\lambda_j \vec x_j\\
if\lambda_i = 0,{c_j\over c_i}=0,\vec x_i =\vec 0\\
if\lambda_i\not = 0\\
Thus,there\:\ is\:\ at\:\ least\:\ one {c_j\over c_i}\not=0\\
\vec x_i=\sum_{j\in[k]\\ \{n\}}-{c_j\over c_i}\vec x_j=\sum_{j\in[k]\\ 
\{n\}}-{c_j\over c_i}{\lambda_j\over \lambda_i }\vec x_j\\
It's\:\ a\:\ contradiction.
$$

考虑：

$$
P=A(A^TA^{-1})A^T
$$

$$
P\vec x = \lambda \vec x \:\ iff \:\ \vec x \in C(A) \:\ and \:\ \lambda = 1 \\
or\\
 \:\ \lambda=0 \:\ and \:\ \vec x \in N(A^T)
$$

我们可以得到：

$$
det(A-\lambda I)=0
$$

如果A是一个方阵，那么我们称(A-$\lambda$I)的行列式为A的特征多项式。

特征值可以是虚数。

对于一个n*n的方阵，在**C**上，有且仅有n个特征值（允许重复）。

# 二十六、矩阵的对角化

如果一个方阵可以被对角化，那么就意味着

$$
A=X\Lambda X^{-1} \\
\Lambda \ is \ a \ diagonal \ matrix.\\
X \ is \ invertible.
$$

那么，如果A可以被对角化，那么这意味着A有着n个线性独立的特征向量。若不然，显然X不可逆。

这意味着，只要A有n个特征值，它就一定可以被对角化。

# 二十七、对称矩阵

一个实对称矩阵的特征值**都是实数**。

Pf:

$$
\overline{Sx}=\overline{\lambda x}\\
\overline{x^T}\overline{S^T}=\overline{\lambda}\overline{x^T}\\
\overline{x^T}\overline{S}=\overline{\lambda}\overline{x^T}\\
\overline{x^T}\overline{S}x=\overline{\lambda}\overline{x^T}x\\
\lambda \overline{x^T}x=\overline{\lambda}\overline{x^T}x\\
(\lambda-\overline{\lambda})\overline{x^T}x=0
$$

一个d-正则图的邻接矩阵，它一定是对称的。

一个复数向量，可以将实部和虚部拆出来。实部向量和虚部向量中至少有一个是S的特征向量。

实对称矩阵中，可以找到一组特征向量，使之互相正交。

$$
\lambda_1(\vec x_1\cdot \vec x_2)=(\lambda_1 \vec x_1)\vec x_2\\
=(S\vec x_1)\cdot \vec x_2\\
=(S\vec x_1)^T \vec x_2\\
=\vec x_1^TS^T\vec x_2\\
=\vec x_1^TS\vec x_2\\
=\vec x_1^T\lambda_2\vec x_2\\
=\lambda_2(\vec x_1 \cdot \vec x_2)
$$

故，向量正交。

将特征向量标准化后，可以得到一个正交阵**Q**。

数学归纳法证明。

$Pf:$

$$
P^TSP=P^TS[\vec x_1\vec x_2...\vec x_n]\\
=[P^TS\vec x_1\:\ P^TS\vec x_2...P^TS\vec x_n]\\
=[P^T\lambda_1\vec x_1\:\ P^TS\vec x_2...P^TS\vec x_n]\\
=[\lambda_1\vec e_1 P^TS\vec x_2...P^TS\vec x_n]\\
=\begin{bmatrix}
\lambda1 & a^T\\
 0 & B\\
\end{bmatrix}\\
\vec a\in R^{n-1},B\:\ is \:\ a\:\ (n-1)\times (n-1)\:\ matrix.
$$

$$
(P^TSP)^T=P^TS^T(P^T)^T=P^TSP\\
\begin{bmatrix}
\lambda_1 & a^T\\
 0 & B\\
\end{bmatrix}=
\begin{bmatrix}
\lambda_1 & 0\\
a & B^T\\
\end{bmatrix}\\
Thus,\vec a=\vec 0,B=B^T
$$

随后继续归纳。

对于一个d-正则图的邻接矩阵，有一个特征值等于$d$并且对应的特征向量为$[{1\over n}{1\over n}...{1\over n}]^T$

对于一个d-正则图的邻接矩阵，它的最大特征值的绝对值不会超过d。

对于一个d-正则图，它是连通的，当且仅当$\lambda_1>\lambda_2$

如果一个连通d-正则图是二分图，当且仅当$\lambda_n=-\lambda_1=-d$时成立。

# 二十八、特征空间，几何重数和代数重数

一个特征值对应的全体特征向量，被称为该特征值对应的特征空间。

特征空间的维数不等于0。

 几何重数指某一个特征空间的维数。

代数重数指某一个特征值，在特征多项式等于0中的重根数。

代数重数$\geq$几何重数。

我们只要取与这个空间维数相同的向量，随后再取出整个空间的一组基。 

对于对称矩阵而言，它的代数重数等于几何重数。

进一步推广，如果一个矩阵可以对角化，当且仅当它的每一个特征值代数重数等于几何重数。

# 二十九、正定矩阵

如果一个**对称矩阵**所有的特征值均为正值，那么这个矩阵称为是正定的。

一个矩阵是正定的$iff$

$$
\forall \vec x\in R^n,\vec x \not=\vec 0,x^TSx>0
$$

$Pf:$

$$
\Lambda=Q^TSQ\\
let\:\ \vec y=Q^T\vec x,i.e.\vec x = Q\vec y\\
(Q\vec y)^TS(Q\vec y)=(y^TQ^T)SQ\vec y=y^T\Lambda \vec y
$$

对一个m*n的矩阵A，若rank(A)=n,那么$A^TA$是个对称阵，并且正定。

如果一个对称矩阵正定，那么它的行列式大于0。

一个对称阵是正定的iff它的所有顺序主子式都是正的。

# 三十、线性变换

线性函数：保持数乘的分配以及加法。

比如长度，就不是一个线性函数。

矩阵乘法，可以视为一个m维向量到n维向量的线性变换。

需要注意的是，线性变换不会改变线性组合的方式。

$$
\vec v_1,\vec v_2...,\vec v_n is\:\ a\:\ basis\:\ for\:\ V.\\
T_1,T_2\:\ are\:\ 2\:\ linear\:\ transformations.\\
if\forall i,T_1(\vec v_i)=T_2(\vec v_i),then\:\ T_1=T_2\\

$$

将$\vec v_i$视作在V内基的线性组合，那么我们可以建立一个V到$R^n$的映射，即该向量对基的系数。记为$T_{\overline v}$

# 三十一、线性变换的矩阵

$A_T$与线性变换一一对应。

操作上，是将原有的基$\bar v$中的每一个都用T作用，提取目标空间中基$\bar w$前每一项的系数。将所得的系数矩阵转置。

在我看来，所谓$A_T$，就是将系数进行变换。

基变换矩阵：

$$
[v_1...v_n]M=[v_1' ...v_n']\\
$$

M是从$\bar v 到\bar v'$的基变换。

$$
T_{\bar v}(v)=MT_{\bar v'}(v)
$$

# 三十二、线性变换的像和核

考虑线性变换$T:V\rightarrow W$

$$
Im(T):=\{T(v)|v\in V\}\\
Ker(T):=\{v\in V|T(v)=0\}
$$

它的像是W的子空间，它的核是V的子空间。

# 三十三、秩零空间定理

考虑$T:V\rightarrow W,dim(V)=dim(Im(T))+dim(Ker(T))$

这个可以用来证明秩与零空间维数的关系。

# 三十四、对偶

线性算子的定义：$L:V\rightarrow R$,即$L\in T(V,R)$

空间V的对偶空间定义为$T(V,R)$,记作$V'$

对偶空间是一个线性空间。

如果$v_1,v_2,...,v_n$是V的一组基，那么$L_1,L_2,...L_n$也是对偶空间的一组基，称为对偶基。其中

$$
L_i(v_i)=1,L_i(v_j)=0(i\not=j)
$$

相对的，我们定义

$$
T'(L)=LT
$$

T'(L)都是线性映射。

在选择对偶基的情况下，

$$
A_{T'}=A_T^T
$$

这是转置的直观意义。

# 三十五、对偶变换的像与核

零化子的定义：$U^0=\{L\in V'|L(u)=0\ for\ all\ u\in U\}$

零化子是V'的一个子空间。

如果V是有限维的，U是V的一个子空间，那么

$$
dim(U)+dim(U^0)=dim(V)
$$

我们因此得到

$$
Ker(T')=(Im(T))^0\\
dim(Ker(T'))=dim(Ker(T))+dim(W)-dim(V)\\
dim(Im(T'))=dim(Im(T))\\
Im(T')=(Ker(T))^0
$$

# 三十六、奇异值分解

对于任意的一个对称阵，我们都可以进行谱分解。即$\lambda_1,\lambda_2...,\lambda_n$为S的所有特征值，$\vec v_1,\vec v_2,...,\vec v_n$是对应的特征向量，那么我们可以得到：

$$
S=\lambda_1v_1v_1^T+...+\lambda_nv_nv_n^T
$$

这是通过对称阵的对角化，随后进行分块矩阵乘法而得的。

任何矩阵乘上一个满秩矩阵，不会改变这个矩阵的秩。

假定A为实系数m*n矩阵，$\sigma_1,\sigma_2,...,\sigma_r$是这个矩阵的奇异值，那么我们可以找到m *m的标准正交阵U，和n *n的标准正交阵T，从而有:

$$
A=U\Sigma V^T
$$

其中，我们有：

$$
\Sigma=
\begin{bmatrix}
D & 0_{r\times (n-r)}\\
0_{(m-r)\times r}& 0_{(m-r)\times(n-r)}
\end{bmatrix}
$$

D的定义如下：

$$
D=
\begin{bmatrix}
\sigma_1&0&...&0\\
0&\sigma_2&...&0\\
.&.&.&.\\
0&0&...&\sigma_r
\end{bmatrix}
$$

# 三十七、奇异值分解的证明

**Lemma1：**

$$
rank(A^TA)=rank(AA^T)=rank(A)
$$

要证明这一点，我们先证明第一项和第三项相等。考虑秩零空间定理，我们只需要证明二者的零空间相等即可。

随后，我们考虑转置的特点，将中间一项的秩转化为$A^T$的秩。这样，我们就得到了证明。

**Lemma2:**

$$
A^TA 和 AA^T都是半正定的。
$$

**Lemma3:**

$$
A^TA和AA^T都有r个非零的记重复特征值。其中，r=rank(A)
$$

要证明这一点，我们首先考虑到$A^TA$是一个对称阵。因此，它的所有非零特征值可以对应一组标准正交特征向量。随后，我们利用特征向量的定义，可以找到对应的一组标准正交向量组，它们一定都是$AA^T$的特征向量。

接下来，我们只需要证明$AA^T$没有其他的非零特征向量即可。

为了要说明这一点，我们需要利用它们的重数。

显然，若考虑它们的几何重数，因为$AA^T$中其他特征向量未被知晓，所以$A^TA$的非零特征值几何重数之和小于等于$AA^T$的非零特征值的几何重数之和。

但是考虑它们的代数重数，因为其他内容尚未知晓，有可能$A^TA$有更多的特征值。但是，$A^TA$的秩为r，因而它的代数重数之和不能大于r，也就是$AA^T$的代数重数之和。

故而，引理成立。

若$v_1,...,v_r$是$A^TA$的非零特征向量，那么${1\over \sqrt{\lambda_i}}Av_i$是为$AA^T$的特征向量。

若$\lambda_1,...,\lambda_r$为$A^TA$(或$AA^T$)的特征值，那么我们定义A有r个奇异值，并且$\sigma_i=\sqrt{\lambda_i}$

# 三十八、奇异值分解中的基与矩阵

因为

$$
A=U\Sigma V^T
$$

故而

$$
A=\sum_{i=1}^r\sigma_iu_iv_i^T
$$

由上式，我们可以得到$u_1,u_2,...,u_r$是为$C(A)$的一组基。由对称性，易知$v_1,v_2,...,v_r$是为$C(A^T)$的一组基。

由于$V$的定义，我们可以得到$v_{r+1},...,v_n$是$N(A)$的一组基。由对称性，$u_{r+1},...,u_{m}$是$N(A^T)$的一组基。

# 三十九、奇异值分解的几何应用

找到一组数据的最近似“解”。

$$
a_1,...,a_m\in R^n\\
目标是找到一个单位\omega,s.t. \sum_{i\in[m]}(\omega \cdot a_i)^2\ max\\

let\ A=
\begin{bmatrix}
a_1^T\\
.\\
.\\
.\\
a_m^T
\end{bmatrix}

\\上式=||A\omega||^2
$$

定理：如果A是一个m$\times$n的矩阵，并且$\sigma_1$是它最大的奇异值，那么：

$$
\max_{\omega\in R^n\ with \ ||\omega||=1  }||A\omega||^2=\sigma_1^2
$$

这个等式成立，当且仅当$\omega=v_1$。

# 四十、再遇正交

令

$$
v_1,...,v_n\in R^n是一组标准正交基。\\
\omega=c_1v_1+...+c_nv_n\\
c_iv_i=(v_i\cdot \omega)v_i\\
Thus,\omega=[v_1...v_n]\begin{bmatrix}
v_1^T\omega\\
.\\
.\\
.\\
v_n^T\omega
\end{bmatrix}
=[v_1...v_n]\begin{bmatrix}
v_1^T\\
.\\
.\\
.\\
v_n^T
\end{bmatrix}\omega=QQ^T\omega
$$

$$
b=QQ^Tb=\sum_{i\in [n]}(q_i\cdot b)q_i
$$

正交分解罢了。

令M为$e_1,...,e_n$向$v_1..v_n$的基变换矩阵。

由定义，我们也有$T_{\bar v}(v)=MT_{\bar v'}(v)$

如果$v_1,...,v_n$是标准正交的，那么M也是个标准正交阵。

因而$\omega$在$v_1,...,v_n$为一组基的坐标向量是为$(v_1\cdot\omega,...,v_n\cdot\omega)$。

由于乘上一个标准正交阵不会改变向量的模长，故

$$
||\omega||=||Q^T\omega||
$$

由于M=Q，故w的模长为上述内积之和开根。

$$
A=\sum_{i\in [r]}\sigma_iu_iv_i^T
$$

由于$\omega=\sum_{i\in[n]}c_iv_i$，故而$\sum_{i\in [n]}c_i^2=1$

故$||A\omega||^2=||(\sigma_1c_1,...,\sigma_rc_r,0,...,0)||^2=\sum_{i\in[r]}\sigma_i^2c_i^2\leq\sigma_i^2\sum_{i\in[r]}c_i^2\leq \sigma_1^2\sum_{i\in[n]}c_i^2=\sigma_1^2$

# 四十一、通过k维子空间适应数据

固定一常数$k\geq1$,对于$a_1,...,a_m\in R^n$，我们欲寻一k维子空间最小化每一个数据点到其距离的平方和。等价于，我们要最大化数据点投影在空间上的投影向量之长度。

我们令$\omega$为k维子空间W中的向量。

令$w_1,...,w_k$为$W$的一组标准正交基。令$Q=[w_1...w_k]$则$Q^TQ=I_k$,$QQ^T=w_1w_1^T+...+w_kw_k^T$

对于每一个向量$a_i$，它的投影向量可以这样计算。$p_i=Q(Q^TQ)^{-1}Q^Ta_i=\sum_{j\in[k]}(w_j\cdot a_i)w_j$

亦即，投影是在已有的基向量上的正交分解。

考虑到第三十九节提出的曾提出的矩阵A，我们可以得到：

$$
\sum_{j\in[k]}||Aw_j||^2\leq\sum_{j\in[k]}\sigma_j^2
$$

上式中去到等号，当且仅当：$\forall i\in [k],w_i=v_i$

$$
Let\ k\in[r],w\in R^n,||w||=1,w\perp v_i,\forall i\in[k-1]\\
then,||Aw||^2\leq||Av_k||^2=\sigma_k^2
$$

当$k\in[2,n]$时，可以存在这样的$w$,使得上述定理成立。

故，

$$
\sum_{j\in[k]}||Aw_j||^2\leq \sum_{j\in[k]}\sigma_j^2
$$

上式等号成立，$iff\ \forall w_i=j_i$。

引理：

$$
v在W=span({w_1,...,w_k})上的投影p=\sum_{i=1}^kw_iw_i^Tv
$$

引理：

$$
|v-p|=\sqrt{\sum_{i=k+1}^n(w_i\cdot v)^2}
$$

利用上面投影的结果。这就是v与子空间W的距离。

考虑$W$的正交补$W^\perp$,$W^\perp = span({w_{k+1},...,w_n})$

引理：

$$
|a_i-p_i|=\sqrt{|a_i|^2-|p_i|^2}
$$

定理：

$$
A=
\begin{bmatrix}
a_1^T\\
.\\
.\\
.\\
a_m^T
\end{bmatrix}\\
\sum_{j\in[k]}|Aw_j|^2\le    \sum_{j\in[k]}\sigma_j^2\\
w_1,...,w_k是W的一组orthonormal\ basis,等号成立当且仅当\forall w_i=v_i
$$

重要引理：

$$
k\in[r],w\in R^n,|w|=1.w\perp v_i,\forall i\in[k-1],Then\\
|Aw|^2\leq|Av_k|^2=\sigma_k^2
$$

引理：

$$
k\in[2,n],W\in R^n,dim(W)=k,\exist w\in W,|w|=1,w\perp v_i,\forall i\in[k-1]
$$

# 四十二、通过伪逆矩阵求方程近似解

$$
A=U\Sigma V^T\\
A^+=V\Sigma^+U^T\\
x^+=A^+b
$$

$x^+$是最小二乘解。并且，当$x!=x^+且|Ax|=|Ax^+|$时，$|x^+|<|x|$

对于一个矩阵的奇异值分解是不唯一的。因为我们可以选择不同的标准正交解。但是，伪逆矩阵一定是唯一的。

# 四十三、通过低秩矩阵进行图像压缩

$$
A=U\Sigma V^T\\
A=\sum_{i=1}^r\sigma_iu_iv_i^T
$$

我们可以取得满秩矩阵R和满秩矩阵C，使得$\Sigma$中每一个奇异值均为1。

$$
A=\sum_{i=1}^rr_ic_i^T
$$

考虑矩阵A'，其秩为k，并且其奇异值恰为前k个特征值。即：

$$
A'=\sum_{i=1}^k\sigma_iu_iv_i^T
$$

$$
||M||=\sqrt{\sum_{i\in[m],j\in[n]}M(i,j)^2}\\
||A'-A||=\min_{rank(B)\leq k}||B-A||
$$

# 四十四、又见SVD

$$
\min_{k-dimension}\sum_{i\in[m]}(the\ distance\ between\ a_i\ and \ W)^2=
\sigma_{k+1^2}+...+\sigma_{r}^2
$$

这就是根据上面得到的结论。

$$
A-A'=\sum_{i=k+1}^r\sigma_iu_iv_i^T
$$

# 四十五、内积空间和复数矩阵

对于一个线性空间$V$以及一个函数<$v_1$,$v_2$>:$V^2\to R$，共同组成了一个内积空间。

这个函数具有这些性质：

$$
<u,v>=<v,u>\\
<u+v,w>=<u,w>+<v+w>\\
<cu,v>=c<u,v>\\
<u,v>\geq 0\\
<u,v>=0\ iff\ u=0
$$

如果$V$是$R^n$，那么这样的空间称之为欧氏空间。

## Cauchy-Schawarz不等式

$$
<u,v>^2\leq<u,u><v,v>
$$

## 范数

$$
||u||=\sqrt{<u,u>}
$$

## 单位向量

$$
||u||=1\\
如果正交，则二者内积为0
$$

# 四十六、内积空间在$C$上的推广

在$C$上时，我们可以这样定义内积：

$$
<u,v>=\bar u^Tv
$$

如此这般，我们可以对内积的第一条和第三条性质作出更加通用的描述。

$$
<u,v>=\overline{<v,u>}\\
<cu,v>=\bar c<u,v>
$$

Cauchy-Schwarz Inequality still holds.

# 四十七、赫米特矩阵以及酉矩阵

$u^H=\bar u^T$。

实际上，内积$<u,v>$就是$u^Hv$。

并且，我们有：

$$
<Au,v>=<u,A^Hv>
$$

如果一个方阵是赫米特的，那么：

$$
S=S^H
$$

若一个实矩阵是赫米特的，那么当且仅当其为对称阵。

对于一个赫米特矩阵而言，它的所有特征向量均为实数。并且，如果两个特征值不同，那么它们对应的特征向量之间相互正交。

如果一个方阵所有的列向量标准正交，则我们称它是酉矩阵。

一个方阵$Q$是酉矩阵，当且仅当$QQ^H=I$，即$Q^{-1}=Q^H$

对于每一个赫米特矩阵而言，它都一定可以对角化。

# 四十八、傅里叶矩阵

$$
Let\ n\geq1,w=e^{2\pi i/n}=\cos{2\pi\over n}+i\sin{2\pi\over n}
$$

我们定义：

$$
F_n=
\begin{bmatrix}
1&1&1&...&1\\
1&w&w^2&...&w^{n-1}\\
1&w^2&w^4&...&w^{2(n-1)}\\
...\\
...\\
...\\
1&w^{n-1}&w^{2(n-1)}&...&w^{(n-1)^2}
\end{bmatrix}\\
\\
\\i.e.F_n(i,j)=w^{(i-1)(j-1)}
$$

$$
{1\over\sqrt n}F_n是一个酉矩阵。
$$

# 
