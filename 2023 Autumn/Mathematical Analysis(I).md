# 第一章 绪论

## 1.1 集合

### 朴素集合论

集合的交、补、并、差

集合运算满足交换律、结合律、分配律、对偶律

对偶律(De Morgan公式)：

$$
(A\cap B)^C = A^C\cup B^C \\
(A\cup B)^C = A^C\cap B^C
$$

笛卡尔积(Cartasian product)

$$
A\times B =\{ (a,b)|a\in A,b\in B\}
$$

闭区间和开区间

朴素集合论的问题：罗素悖论(Russell's paradox)

$$
A=\{x\in X|x\notin x\} \\
X是所有集合构成的集合。\\
问题在于，A\in A？还是A\notin A?
$$

于是，我们有ZFC公理化集合论。

### 集族

集族可以看成是集合的集合。

$$
C=\{A_\lambda|\lambda \in \Lambda,A_\lambda \subset X \}
$$

C就是X的一个集族。集族中的集合也可以正常进行交、并等。

## 1.2映射

### 映射的基本概念

原像和像的概念。

单射、满射、双射、复合映射。

双射存在逆映射。

恒等映射。

### 幂集

$$
B^A := \{f:A\rightarrow B\} \\
2^A :=\{f:A \rightarrow \{ 0,1\} \}
$$

幂集的概念，就是指这种映射规则的全体。

## 1.3集合的势

集合的势的概念

集合的势与映射的概念

$$
\exist f:A\rightarrow B为单射，则|A|\leq |B|\\
\exist f:A\rightarrow B为双射，则|A|=|B|
$$

CBS定理

$$
if |A|\leq|B| \:\ and \:\ |B|\leq |A|,then \:\ |A|=|B|
$$

阿列夫数

自然数集的势是阿列夫0。这是无穷集中最小的势。

所有势为阿列夫0的集都是可数集。

实数集是不可数的。

阿列夫1是紧接着阿列夫0之后的一个数。连续统假设认为，**R**的势为阿列夫1。

$$
|2^{N^+}|=|R|的证明
$$

对角线规则

**选择公理**：可以在无穷多个集合中，每个中选出一个元素。

## 1.4函数

函数有多种表达方式。

基本初等函数**有限次**四则运算后，得到的还是初等函数。

# 二、数列极限与实数系基本定理

## 2.1极限的基本概念和性质

### 极限的基本概念

描述数列的渐近趋势，从而得到数列极限。

极限的$\epsilon-N$语言

trick1：分块处理

### 极限的性质

数列极限的唯一性

数列极限的保序性（N足够大后，极限的大小关系与数列项的大小关系相同）

极限的有界性

极限的迫敛性

极限可以进行四则运算

### 无穷小量与无穷大量

无穷小量和无穷大量

$G-N$语言来描述无穷量

## 2.2极限的计算

### Stolz定理

要求：分母严格单调趋于无穷。或严格单调趋于0。

### 子列

$\lim_{k\rightarrow \infin}x_k = a$的充要条件为其任何一个子列都以a为极限。只要有不收敛子列，数列就不收敛。

## 2.3实数系的构造和连续性

自然数集对$+，\times$封闭

整数集对$+,-,\times$封闭

有理数集对$+,-,\times,/$封闭

对四则运算封闭的集合称为域

考虑n次多项式$P(x)$，它等于0的根就不一定在有理数集中。

实数集中为了保证表示唯一性，不允许出现9循环。

序结构的概念，最大值和最小值。

上界和下界的概念。

### 实数的确界存在定理（连续性定理）

### Dedekind分割

分割出一个左无界的开区间，那么这个开区间中所有的有理数构成的集合称为有理数集的一个分割。那么，关于实数系的序结构，可以定义为两个以实数为右界的区间的包含关系。加法的定义就成为了集合右界相加后得到的区间的右界。

## 2.4收敛数列判定准则与实数系基本定理

### 单调有界必收敛

### B-W定理（列紧性）

R中有界数列必有收敛子列，可以用二分法证明

### $e$

自然对数$e$的定义$\lim_{n \to \infin}(1+1/n)^{n}$

证明方法，首先，利用类似迫敛性的方法，用$(1+1/n)^{n} 和(1+1/n)^{n+1}$说明它最后一定在一个范围中。然后，说明其单调性，从而收敛。

$e$不是有理数的证明：从$x_n$和$e$的误差开始放缩，最后导出整数不可能与非整数相等，从而矛盾。

### 欧拉常数的概念

$\gamma = \lim_{n \to \infin}(\sum_{x = 1}^n(1/i)-ln(n))$

### Cauchy收敛准则

误差不能太大

### 闭区间套定理

### 有限覆盖定理

无数个开区间覆盖了一整个闭区间，那么我一定能够选出有限个开区间，覆盖一整个闭区间。

# 三、函数极限与连续函数

## 3.1函数极限

### 定义

在足够小的去心邻域内，距离极限值的误差足够小。

需要注意的是，函数极限描述的是**趋势**，与该点处函数值无关。

### 左右极限

计法为$\lim(x_0^+)和\lim(x_0^-)$

函数在某点处极限为a当且仅当在该点处左右极限均为a。

## 3.2函数极限的基本性质

函数极限的唯一性

函数极限的局部有界性

函数极限的局部保序性

函数极限的迫敛性

函数极限的四则运算

函数极限的复合运算

### 重要极限

$$
\lim_{x \to 0}(1+x)^{1\over x}=e\\
\lim_{x \to 0}{{ln(1+x)}\over x}=1\\
\lim_{x \to 0}{{e^x-1}\over x}=1\\
\lim_{x \to 0}{{a^x-1}\over x}=lna\\
\lim_{x \to 0}{{(1+x)^\alpha-1}\over x}=\alpha
$$

### 极限定义的扩充

自变量趋向无穷的极限

### 函数极限存在的条件

#### Henie定理

在$x_0$的某去心邻域中，任何收敛于$x_0$的数列，$\lim_{x \to x_0}f(x_0)$均为同一值。

#### Henie定理的弱形式

在$x_0$的某去心邻域中，任何收敛于$x_0$的数列，其对应的函数值极限都存在。

#### Cauchy准则

对于任意小的误差，总存在一个足够小的去心邻域，使得f(x)的值落在这个误差范围内。

#### 单调有界单侧极限存在定理

### 无穷小量和无穷大量的阶

常见等价无穷小量

高阶无穷小量

等阶无穷小量

低阶无穷小量

k阶无穷小量的含义

$$
\lim_{x \to x_0}{{\beta(x)}\over (x-x_0)^k}=A,A\in R
$$

则称$\beta(x)$为$x-x_0$的k阶无穷小量

## 3.3函数的连续性

若函数在$x_0$处有定义，并且在$x_0$处的极限等于在该处的函数值，那么就称函数在此处连续。

### 函数的间断点

可去间断点

跳跃间断点：该点处两侧极限存在，但是大小不相等。

第二类间断点：至少有一侧函数极限不存在。包括无穷间断点和振荡间断点。

### 连续函数的四则运算

在某点处连续的函数间进行四则运算后，在该点处一定仍然连续。

trick：$max\{f(x),g(x)\}={1\over 2}(f(x)+g(x)+|f(x)-g(x)|)$

### 反函数的连续性

若原函数在某区间内连续并且严格单调，那么它的反函数在对应值域区间内连续并且有相同的单调性。

### 初等函数的连续性

一切初等函数都在定义域上连续。

### 单调函数的性质

单调函数只能有跳跃间断点。并且至多只有可数个。

## 3.4闭区间上连续函数的性质

闭区间上，连续函数有界。

闭区间上，连续函数存在最值。

零点存在定理：利用闭区间套定理二分证明。

介值定理

### 函数的一致连续性

在一个区间上，对任意的误差$\epsilon$，总存在一个值，使得自变量相差不超过这个值时，函数值之差小于$\epsilon$。

### Cantor定理

如果函数在一个闭区间上连续，那么它在该闭区间上一致连续。

### 开区间函数一致连续的充要条件

在左端点处右极限存在，在右端点处左极限存在，并且函数在这个开区间上连续，那么它在这个开区间上一致连续。

# 四、一元微积分学

## 4.1微分和导数

## 可微的定义

微分，实际上是一种线性逼近。如果在$x_0$附近，有

$$
f(x_0+\Delta x)=f(x_0)+A\Delta x +o(\Delta x)
$$

那么，它就在这一点处可微。

在一点处可微，那么它一定在这点处连续。

## 可导的定义

$$
\lim_{x\to x_0}{{f(x_0+\Delta x)-f(x)}\over \Delta x} 
$$

存在，那么它在这点处可导。

一元函数中，可微和可导等价。

微分和导数有很大的联系。

## 4.2导数的计算

### 导数的四则运算

### 导数的莱布尼兹法则

### 链导法则

### 反函数求导法则

### 参数方程求导

## 4.3高阶导数和高阶微分

### 函数的高阶导数(Leibniz公式)

$$
[f(x)g(x)]^{n}=\sum_{k=0}^nC_n^kf^{n-k}(x)g^k(x)
$$

复合函数求导得到的情况依旧符合链导法则。同时，其系数分布与二项式系数相同。

### 4.4微分中值定理

### 极值点的引入和驻点

### 罗尔中值定理

### 拉格朗日中值定理

若函数连续可导，在区间导数恒为0，那么它是常值函数。

若两函数连续可导，在区间导数始终相等，那么两函数的差为常数。

### 柯西中值定理

### 导数的介值性

## 4.5洛必达法则

$0\over 0$型或$* \over \infin$型

洛必达法则由微分中值定理推导。

每次运用洛必达，需要判断使用条件。

### 4.6泰勒公式

n次泰勒多项式

### Peano余项

是一个高阶无穷小量。只能在趋向时使用。

### Lagrange余项

$$
R_n(x:x_0)={{f^{n+1}(\xi)}\over (n+1)!}(x-x_0)^{n+1} 
$$

### Cauchy余项

$$
R_n(x:x_0)={f^{n+1}(\xi)\over n!}(x-\xi)^n(x-x_0)
$$

如果我们令$x-x_0$为$h$，那么我们可以将三种余项分别写为

$$
o(h^n)\\
{f^{n+1}(x+\theta h)\over (n+1)!}h^{n+1}\\
{f^{n+1}(x+\theta h)\over n!}[(1-\theta)h]^nh
$$

泰勒公式具有唯一性。

复合函数也可以有这样的泰勒公式。

可以用待定系数法求反函数的泰勒展开。

## 4.6微分学的一些应用

### 一阶导与单调性

### 一些重要不等式

伯努利不等式

杨氏不等式

乔丹不等式

### 二阶导与凸性

多种不同的视角看下凸函数：

1、任意两点连线在图像的上方。

2、斜率之间的关系

$$
\forall x_1<x_2<x_3,{f(x_2)-f(x_1)\over x_2-x_1}\leq {f(x_3)-f(x_1)\over x_3-x_1}
\leq {f(x_3)-f(x_2)\over x_3-x_2}
$$

3、线性组合的观点

$$
f(\lambda x_1+(1-\lambda)x_2)\leq\lambda f(x_1)+(1-\lambda)f(x_2)
$$

如果一个函数在区间$[a,b]$下凸，那么$\forall x\in (a,b)$，$f'_+(x_0)$和$f'_-(x_0)$均存在。

需要注意的是，下凸函数的左导数和右导数不一定相等。比如绝对值函数。

如下三个命题等价：

**i)$f$在$I$上下凸。**

**ii)$f'$在$I$上单调递增。**

**iii)$\forall x_1,x_2\in I,x_1<x_2,f(x_1)+f'(x_1)(x_2-x_1)\leq f(x_2)$**

### 从凹凸性的角度看不等式

**杨氏不等式**

因为：$ln(x)$是一个上凸函数，所以我们可以很容易得到这个不等式，即

$$
\lambda f(a)+(1-\lambda)f(b)\leq ln(\lambda a+(1-\lambda)b)
$$

**琴生不等式**

对于下凸函数，我们有：

$$
\forall x_1,x_2,...,x_n\in I,\forall \lambda_1,\lambda_2,...,\lambda_n>0\\
且\sum_{i=1}^n\lambda_i=1\\
f(\sum_{i=1}^n(\lambda_ix_i))\leq \sum_{i=1}^n\lambda_if(x_i)
$$

实际上，这可以看做是一种凸函数加权的组合。

用数学归纳法可以很容易证明。

### 利用Taylor公式的逼近来计算极限

### 极值点的充分条件

### 导数与极值点

若$f(x)$直到$n$阶可导，且$f'(x_0)=f^{2}(x_0)=...=f^{n-1}(x_0)=0,f^n(x_0)\not= 0$

若$n$为奇数，那么$x_0$一定不是极值点。

若$n$为偶数，那么$x_0$一定是极值点。

这个定理的思考方式可以认为是Taylor公式展开后，其行为类似于对应阶幂函数的行为。

### Lipshitz函数

$$
\exist L>0,s.t\:\ \forall x_1,x_2\in I \\
|f(x_1)-f(x_2)|\leq L|x_1-x_2|
$$

# 第五章、不定积分（反导数）

## 5.1不定积分的意义

## 原函数的定义

原函数的导数为目标函数。

如果一个函数在区间$I$上是连续函数，那么一定存在这样的原函数。

如果$F_1,F_2$均为一个函数的原函数，那么它们之间一定只有常数的区别。

求不定积分和求导互为逆运算。

## 双曲函数的引入

## 5.2一些求解不定积分的方法

不定积分和求导相同，具有线性性。

### 换元积分法

分为第一换元积分法和第二换元积分法。

第一换元积分法为：

$$
\int f(g(x))g'(x)dx=\int f(t)dt=F(t)+c=F(g(x))+c
$$

第二换元积分法为：

$$
\int f(x)dx=\int f(\phi(t))\phi'(t)dt=G(t)+c=G(\phi^{-1}(x))+c
$$

### 分部积分法

$$
\int f(x)g'(x)dx=f(x)g(x)-\int g(x)f'(x)dx
$$

## 5.3几类特殊的初等函数的不定积分

### 有理函数的不定积分

代数基本定理：考虑到对于一个多项式方程，如果有复根，那么共轭复根也是它的根。所以，在实数范围内，每一项均可分解到不超过二次。

所以，在求有理函数的不定积分时，首先将假分式化为真分式。然后，就可以化为形如

$$
\int{1\over (x-a)^n}dx和\int{Bx+C\over (x^2+px+q)^n}dx的组合。
$$

第一个积分很容易计算。第二个则有：

$$
\int{Bx+C\over (x^2+px+q)^n}dx\\
let\:\ u=x+{p\over 2},a=\sqrt[]{q-{p^2\over 4}}\\
=\int{Bu+C-{Bp\over 2}\over({u^2+a^2})^n}du\\
=B\int{u\over{(u^2+a^2)}^n}du+(C-{Bp\over 2})\int{1\over (u^2+a^2)^n}du\\
=BIn+(C-{Bp\over 2})Jn\\
In易知。Jn可从递推公式得知。
$$

对于有理三角函数的不定积分，我们可以使用万能公式。$i.e,t=tan({x\over 2})$从而化归为有理函数的不定积分。

对于无理函数而言，通过换元，可以化归为有理不定积分。

# 六、一元积分学

## 1、定积分的概念

$$
\pi:a=x_0<x_1<...<x_n=b
$$

称为[a,b]的一个分割。

$$
||\pi||=\max_{1\leq n}\Delta x_i
$$

若

$$
\lim_{||\pi||\rightarrow0}\sum_{i=1}^nf(\xi_i)\Delta x_i
$$

存在，并且其值与$\pi,\xi$无关，那么称为这个函数Riemann可积。这个式子被称为Riemann和。

### Newton-Leibniz公式

$$
\int_a^bf(x)dx=F(x)|_a^b
$$

## 2、可积性理论

如果一个函数在一个区间上可积，那么它在这个区间上有界。

如果在一个闭区间上，函数$f$为有界实函数，则以下三个命题等价：

1、区间可积；

2、对任意$\epsilon>0$，存在一组分割，使得

$$
\sum_{i=1}^n\omega_i\Delta x_i<\epsilon
$$

3、小和的极限等于大和的极限。

任意小和都不会大于任意大和。

分割得越细，小和不减，大和不增。

在分割中加入n个新分割点，小和、大和与原来小和、大和的差不超过$n\omega||\pi||$。

在闭区间上，如果一个函数连续，或单调，或至多只有可数个间断点，那么这个函数可积。

### Lebesgue引理

$$
记\{U_\alpha,\alpha \in \Lambda\}是区间[a,b]的一个开覆盖。\\
\exist \delta>0,\forall 闭区间I\subset[a,b],若|I|<\delta,\\
则\exist \alpha \in \Lambda,s.t.\:\ I\subset U_\alpha
$$

### Lebesgue定理

$f\in R[a,b],iff\:\ f的不连续点的集合是零测集。$

有限集、可数集均为零测集。零测集的子集仍为零测集。可数个零测集的并仍为零测集。

零测集不一定是可数集。如Cantor集合。将记[0,1]为$F_0$，然后挖去这个区间的中间三分之一，记为$F_1$。之后，每次挖去每个区间的中间$1\over 3$。记Cantor set 为

$$
\cap_{i=1}^{\infin}F_i
$$

这个集合是零测度的。将其中每一个数用三进制进行表示，那么Cantor set与实数集等势。

### Lebesgue积分

从另外一种视角来考察积分。也就是横着积分。

## 3、定积分的性质

1、线性性

2、乘积可积性

3、保序性

4、绝对可积性

5、区间可加性

### 第一积分中值定理

若f，g在[a,b]上可积，并且g在[a,b]上不变号，那么$\exist \lambda \in[\inf_{[a,b]}f,\sup_{[a,b]}f],s.t.$

$$
\int_a^bf(x)g(x)dx=\lambda \int_a^bg(x)dx
$$

这就是第一积分中值定理。当g(x)=1时，有

$$
\int_a^bf(x)dx=\lambda(b-a)
$$

### 阶梯函数

一切积分都可以用阶梯函数逼近。

### 积分形式的Jensen不等式

$$
\phi \ is \ convex.\\
\phi({1\over b-a}\int_a^bf(x)dx)\leq {1\over b-a}\int_a^b\phi(f(x))dx\\
\phi({1\over b-a}\int_a^bf(x)\rho(x)dx)\leq {1\over b-a}\int_a^b\phi(f(x))\rho(x)dx
$$

## 4、微积分基本定理

### 第一微积分基本定理

$$
f\in R[a,b],\\
Def:F(x)=\int_a^xf(t)dt,x\in[a,b]\\
Then,F\in U.C[a,b]\\
{d\over dx}\int_a^xf(t)dt=f(x),并且F'(x)=f(x)
$$

### 第二微积分基本定理

类似Newton-Lebnitz?

需要注意的是，黎曼可积与是否存在原函数并非是等价的。

我们可以考察导数的介值性以及导函数的无界性找到反例。

## 5、定积分的计算

当我们计算定积分时，需要考察原函数在对应区间上的性质。比如，如果有arctan函数，而被积区间含有$\pi\over 2$。这个时候，需要将被积函数拆开来。

### 分部积分法

没什么需要注意的。与不定积分的方法类似。

### 换元积分法

$$
\int_a^bf(\phi(t))\phi'(t)dt=\int_{\phi(a)}^{\phi(b)}f(x)dx
$$

使用换元积分法，要求f在$[\phi(a),\phi(b)]$可积并有原函数，$\phi$在[a,b]可微。

### Riemann-Lebesgue引理

$$
if\ f\in R[a,b],then\\
\lim_{\lambda \to \infin}\int_a^bf(x)cos(\lambda x)dx=\lim_{\lambda \to \infin}\int_a^bf(x)sin(\lambda x)dx
=0
$$

这意味着如果一个函数的性质足够好，那么用这种足够高频率的函数复合后，它的积分值趋向于0。

### Taylor公式

Taylor公式可以通过分部积分的方式进行推导。

如果f在[a,b]上具有n阶的连续导数，并且其n+1阶导数可积，那么我们可以用积分的形式精确刻画余项。

$$
f(x)=f(x_0)+\int_{x_0}^xf'(t)dt\\
=f(x_0)-\int_{x_0}^xf'(t)d(x-t)\\
=f(x_0)-[f'(t)(x-t)|_{x_0}^x-\int_{x_0}^x(x-t)f''(t)dt]\\

$$

如此这般反复，我们可以导出余项的表达式。

$$
R_n={1\over n!}\int_{x_0}^x(x-t)^n f^{n+1}(t)dt
$$

## 6、第二积分中值定理

$$
if\ f\in R[a,b],then\\

$$

如果g在[a,b]单调递减并且始终大于0，那么$\exists \xi \in [a,b],s.t.\ \int_a^bf(x)g(x)dx=g(a)\int_a^{\xi}f(x)dx$

如果g在[a,b]单调递增并且始终大于0，那么

$\exists \xi \in [a,b],s.t. \int_a^bf(x)g(x)dx=g(b)\int_{\xi}^bf(x)dx$

如果g在[a,b]单调，那么

$\exists \xi \in [a,b],s.t. \int_a^bf(x)g(x)dx=g(a)\int_a^{\xi}f(x)dx+g(b)\int_\xi^bf(x)dx$

这些的证明方法均使用了类似于分部积分法的离散分部积分法。

## 7、补充：数列的上下极限

极限点的定义：$\exist x_{nk},s.t.\lim_{n\to \infin}x_{nk}=A\in R^+$

极限点集：$E=\{ A| \exist x_{nk},s.t.\lim_{n\to \infin}x_{nk}=A\}$

上极限的定义：$\bar\lim_{n\to \infin}x_n=\lim_{n\to \infin}\sup x_n$

下极限的定义：$\underline \lim_{n\to \infin}x_n=\lim_{n\to \infin}\inf x_n$

$\{x_n\}收敛 \leftrightarrow \bar\lim_{n\to \infin}x_n=\underline \lim_{n\to \infin}x_n $

数列极限不大于其上极限。

数列取相反后的上极限等于原有下极限的相反。

## 8、定积分的应用

对曲线长度的参数化定义：

$$
\sigma:[\alpha,\beta]\rightarrow R^n\\
t\rightarrow(x_1(t),...,x_n(t))
$$

若$x_i\in C[\alpha,\beta]$，那么$\Gamma$是连续曲线。

若$x_i$可微，那么我们称$\Gamma$是可微曲线。

若$x_i\in C^k[\alpha,\beta]$，那么我们称$\Gamma$为$C^k$曲线。

我们因此可以定义曲线的长度。

$L(\Gamma):=\int_\alpha^\beta\sqrt{\dot x_1(t)^2+...+\dot x_n(t)^2}dt$

曲线的长度与参数化的选取无关。

我们可以考虑在极坐标下的情况。这时，我们考虑微元，并且将函数的变化趋势按照径向和法向分解。于是，我们可以得到：

$$
dl=\sqrt{(dr)^2+(rd\theta)^2}\\
L(\Gamma)=\int_\alpha^\beta\sqrt{r'(\theta)^2+(r(\theta))^2}d\theta
$$

对于平面图形的面积而言，我们可以定义它的代数面积和几何面积。

对于旋转曲面的面积而言，我们可以得到：

$$
dS=2\pi y(x)\sqrt{1+y'(x)^2}dx\\
S=2\pi\int_\alpha^\beta y(x)\sqrt{1+y'(x)^2}dx
$$

现在考虑求体积。

$$
dV=S(x)dx\\
V=\int_\alpha^\beta A(x)dx
$$

如果所求对象为旋转体，那么我们可以得到:

$$
V=\int_\alpha^\beta \pi f(x)^2dx
$$

### 参数方程下的情况

$$
l: x=x(t),y=y(t),t\in[\alpha,\beta]
$$

$$
s=\sum
$$

# 第七章、广义积分

## 1、无穷积分

$$
\int_a^{\infin}f(x)dx=\lim_{a\to +\infin}\int_a^Af(x)dx
$$

对于从负无穷积到正无穷的积分，我们定义如下：

$$
\int_{-\infin}^{+\infin}f(x)dx=\int_{-\infin}^cf(x)dx+\int_c^{+\infin}f(x)dx
$$

其收敛，当且仅当后两者亦收敛。

此外，还有一种定义方式，称为Cauchy主值积分。

$$
\int_{-\infin}^{+\infin}f(x)dx=\lim_{A\to +\infin}\int_{-A}^Af(x)dx
$$

需要注意的是，两种积分定义出来的无穷积分，很可能不相等。

## 2、瑕积分

$$
设f:[a,B)\rightarrow R,\forall[a,b]\subset[a,B),f\in R[a,b]\\
\int_a^Bf(x)dx=\lim_{b\to B^-}\int_a^bf(x)dx
$$

另一侧亦同理。对于正常可积的区间，其瑕积分恰等于本身。

更一般的广义积分，可以将积分拆为若干个无穷积分与瑕积分的和。

对比Riemann积分和广义积分，广义积分依旧具有线性性、保序性、区间可加性，换元积分法和分部积分法常常适用。然而**乘积可积性与绝对可积性**则不正确。

## 3、广义积分收敛准则

### Cauchy收敛准则

$$
\int_a^{+\infin}f(x)dx收敛\leftrightarrow\: \forall \epsilon>0,\exist M,\\
\forall A_2>A_1>M,|\int_{A_1}^{A_2}f(x)dx|<\epsilon
$$

推广之，我们可以得到

$$
设f\geq0\\
\int_a^{+\infin}f(x)dx收敛\leftrightarrow \exist M>0,\forall A>a,\int_a^Af(x)dx<M
$$

我们对于广义积分的收敛性可定义为绝对收敛与条件收敛。

在$\int_a^{+\infin}f(x)dx$收敛的前提下，若$\int_a^{+\infin}|f(x)|dx$收敛，则称其为绝对收敛。反之，则呼之为条件收敛。

### 比较判别法

不失一般性，我们假设$f(x),g(x)$在$[a,+\infin)$上同号，且不变号。若$\exist c>0,\forall x\in[a,+\infin),0\leq f(x)\leq cg(x)$，倘若$\int_a^{+\infin}g(x)dx$收敛，那么$\int_a^{+\infin}f(x)dx$亦收敛。

### 又见Cauchy

$$
假设a>0,f:[a,+\infin)\to R>0,则\\
若\exist c>0,s.t.0\leq f(x)\leq{c\over x^p}，若p>1，则其收敛。反之，则发散。
$$

### Abel-Dirichlet判别法

$$
设：f,g:[a,+\infin)\to R，若下列两个条件中有一个满足：\\
(1)(Abel)\int_a^{+\infin}f(x)dx收敛，g单调且有界\\
(2)(Dirichlet)F(x)=\int_a^xf(t)dt在[a,+\infin)有界，g单调且趋于0(x\to +\infin)\\
则\int_a^{+\infin}f(x)g(x)dx收敛。
$$

对于瑕积分而言，唯一的不同恐怕就是积分上限的不同。

# 第八章 数项级数

## 1、基本概念及性质

$$
\{x_n\}是一列实数，称形式和\sum_{n=1}^{\infin}x_n为无穷级数。\\
x_n称为通项。记S_n:=\sum_{i=1}^{n}x_i为\sum_{n=1}^{\infin}x_n的部分和。\\
若\lim_{n\to \infin}S_n存在，称\sum_{n=1}^{\infin}x_n收敛。否则，称其发散。
$$

无穷级数收敛的一个必要条件为$\lim_{n\to +\infin}x_n=0$

然而，$\int_a^{+\infin}f(x)dx$收敛不可以退出$\lim_{x\to +\infin}f(x)=0$因为二者的“权重”不同。后者可以在某些点处有高峰等情况。

### Cauchy收敛准则

$$
\sum_{n_1}^{+\infin}x_n收敛\leftrightarrow \forall \epsilon>0,\exist N,\forall m>n>N\\
|\sum_{k=n+1}^mx_k|<\epsilon
$$

对于无穷级数而言，其具有线性性，满足结合律。我们称调换顺序的无穷级数为一个更序级数。更序级数与原本的无穷级数相比，不一定相等。

### Riemann定理

$$
\forall A\in R,-\infin,+\infin,\\
\exist \sum_{n=1}^{\infin}x_n的更序级数加和\sum_{n=1}^{\infin}x_n',s.t.\sum_{n=1}^{\infin}x_n'=A
$$

若原无穷级数收敛，那么其符合结合律，可以随意增加括号。

## 8.2数列的上下极限

### 极限点

$$
若\exist\lim_{k\to +\infin} \{x_{nk}\}=\xi,则称\xi是\{x_n\}的一个极限点。\\
E=\{\xi|\xi是\{x_n\}的极限点\}\\
若\{x_n\}有界，则E有界\\
令H=\sup E,h=\inf E,二者分别称为\{x_n\}的上下极限。\\
并且H=\max E,h=\min E
$$

$$
若\{x_n\}无上界，则\forall G>0,\exist n\in N^+,s.t.\ x_n>G\\

$$

一个数列的极限存在，当且仅当其上极限等于其下极限。

### 上下极限的等价描述

$$
H=\bar\lim_{n\to +\infin}x_n\leftrightarrow\\
(1)\exist N,\forall n>N,x_n<H+\epsilon\\
(2)\exist \{x_n\}中的无穷多项>H-\epsilon
$$

$$
h=\underline \lim_{n\to +\infin}x_n\leftrightarrow\\
(1)\exist N,\forall n>N,x_n>h-\epsilon\\
(2)\exist{x_n}中的无穷多项<h+\epsilon
$$

### 上下极限的四则运算性质

$$
\bar \lim_{n\to \infin}(x_n+y_n)\leq \bar \lim_{n\to \infin}x_n+\bar \lim_{n\to \infin}y_n\\
\underline \lim_{n\to \infin}(x_n+y_)\geq \underline \lim_{n\to \infin}x_n+\underline \lim_{n\to \infin}y_n
$$

上式等号可取$iff\ \lim_{n\to \infin}x_n$存在。

然右侧不可为$+\infin\ +\ -\infin$的不定型。

如果为乘法运算，那么我们需要假定$x_n,y_n$均非负。

此时，我们可以得到：

$$
\bar \lim_{n\to \infin}(x_ny_n)\leq\bar\lim_{n\to\infin}(x_n)\bar\lim_{n\to\infin}(y_n)\\
\underline\lim_{n\to\infin}(x_ny_n)\geq\underline\lim_{n\to\infin}(x_n)\underline\lim_{n\to\infin}(y_n)
$$

取等条件同上。

### 上下极限的另一种构造方式

$$
a_n:=\inf\{x_n,x_{n+1},...\}=\inf_{k\geq n}x_k\\
h^*=\lim_{n\to\infin}a_n=\sup\inf_{k\geq n}x_k\\
h^*=\underline\lim_{n\to\infin}x_n
$$

反之亦然。

## 8.3正项级数的收敛判定

### 比较判别法

$$
\sum_{n=1}^\infin x_n,\sum_{n=1}^\infin y_n均为正项级数，且\exist M>0,当n足够大时s.t.0\leq x_n\leq My_n\\
则y_n求和收敛，可知x_n求和收敛；由x_n求和发散，可知y_n求和发散。
$$

### 极限形式比较判别法

$$
\sum_{n=1}^\infin x_n,\sum_{n=1}^\infin y_n为正项级数，且\lim_{n\to \infin}{x_n\over y_n}=\lambda\geq0\\
若\lambda>0,\lambda<+\infin，则其一收敛，可知另一收敛；\\
若\lambda=0,\sum_{n=1}^\infin y_n\leq+\infin，可知另一亦收敛。\\
若\lambda=+\infin,\sum_{n=1}^\infin y_n=+\infin,可知另一亦发散。
$$

### Cauchuy判别法

$$
设x_n\geq0,\bar\lim_{n\to\infin}(x_n)^{1\over n}=\lambda\\
若\lambda<1,则收敛；若大于1，则发散；若为1，无定论。
$$

### d'Alembert判别法

$$
若\bar \lim_{n\to \infin}{x_{n+1}\over x_n}=\bar\lambda<1,则\sum_{n=1}^\infin x_n收敛。\\
若\underline\lim_{n\to \infin}{x_{n+1}\over x_n}=\underline\lambda>,则\sum_{n=1}^\infin x_n发散。
$$

### 积分判别法

$$
f:[1,+\infin)\to R\geq0,f非负且单调递减。\\
\sum_{n=1}^\infin f(x)收敛\leftrightarrow \int_1^{+\infin}f(x)dx收敛。
$$

### Rabbe判别法

$$
设x_n>0,n\in N^+,\lim_{n\to +\infin}({{x_n}\over {x_{n+1}}}-1)n=p存在，则\\
若p>1,\sum_{n=1}^\infin x_n收敛。\\
若p<1,\sum_{n=1}^\infin x_n发散。
$$

## 8.4任意项级数的收敛判定

### Leibniz级数

交错级数定义如下：

$$
\forall n\in N^+,u_n\geq0,\sum_{n=1}^\infin(-1)^nu_n
$$

形如这样的无穷级数，称之为交错级数。

在交错级数的定义上，若$u_n单调，且\lim_{n\to \infin}u_n=0$,那么称这样的级数为Leibniz级数。Leibniz级数必收敛。

### Abel-Dirichlet判别法

Abel判别法：

$$
\{x_n\}单调有界，\sum_{n=1}^\infin y_n收敛
$$

Dirichlet判别法：

$$
\{x_n\}单调趋于0，\sum_{n=1}^ky_n=Y_k有界
$$

这两者都可以推出$\sum_{n=1}^\infin x_ny_n$收敛。

### Abel变换

差分处理的办法。设

$$
a_k,b_k\in R,B_0=0\\
let\ B_n=\sum_{k=1}^\infin b_k,then\ \sum_{k=1}^pa_kb_k=\sum_{k=1}^\infin a_k(B_{k+1}-B_k)\\
then,if\ a_n单调，B_n当1\leq n\leq p时有界，则\\
|\sum_{k=1}^pa_kb_k|\leq M|a_p|+\sum_{k=1}^{p-1}|a_{k+1}-a_k|M\leq M(2|a_p|+|a_1|)
$$

### 绝对收敛与条件收敛

无穷级数在这方面的定义与广义积分相仿。

定义：

$$
\{x_n\}的正部:=x_n^+=\max\{x_n,0\}={{x_n+|x_n|}\over 2}\\
\{x_n\}的负部:=x_n^-=\max\{-x_n,0\}={{|x_n|-x_n}\over 2}
$$

则：

$$
x_n=x_n^+-x_n^-\\
|x_n|=x_n^++x_n^-
$$

故，若$\{x_n\}$绝对收敛时，其正部与负部均收敛。若$\{x_n\}$条件收敛时，一方面，其正部与负部均发散。另一方面，$\lim_{n\to \infin}\sum_{k=1}^n(x_k^+-x_k^-)$收敛。

## 8.5加法交换律

更序级数的概念在此前已然引入。

如果$\{x_n\}$绝对收敛，那么其更序级数亦收敛，且其和不变。

如果$\{x_n\}$条件收敛，根据此前已提及的Riemann定理，对$\forall A\in R || A=+\infin ||A=-\infin,\exist \sum_{k=1}^\infin x_n的一个更序级数\sum_{k=1}^\infin x_n',s.t.\sum_{k=1}^\infin x_n'=A$
