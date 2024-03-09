# Lec 1

回答四个问题：什么是数学证明？数学证明为什么对？可证明有边界吗？电脑可以找到证明吗？

数学证明：基于一阶逻辑的证明。

数学证明为什么对：在正式证明体系中，可对和可证等价。**（哥德尔完备性定理）**

证明有边界吗：在有可行性的证明系统中，有真的数学陈述不可证。**（哥德尔第一不完备性定理）**

电脑可以找到证明吗：图灵停机问题。

令$\phi_{P,x}$表示为$x$在$P$上运行会停机。那么，构造程序$H$，假设它可以判断出$\phi_{P,x}$为可以停机，那么就一直运行；反之，则停机。那么，把$H$作为$H$的输入，无法判断它会不会停机。

定义：字母表(alphabet)是一个**非空**的符号集。

定义：由字母表中的符号组成的一个有限符号序列是一个字(word)。我们定义这个字的长度就是符号的个数。如果字的长度是0，那么我们定义这样的字为$\epsilon$,称为**空字**。$A^i$ 代表$A$这个字母表中长度为i的字组成的集合。 $A^*$代表$A$字母表中可以组成的字的集合。$A^*$是可数的。

一阶逻辑由如下的符号组成。

1、变元。

2、否，且，或，蕴含，当且仅当。

3、任意，存在。

4、相等。

5、括号。

6、n元关系符，n元函数符，常元。n不能取0。

前五种称为逻辑符号。

定义：每一个变元都是S项，每一个常元都是S项。如果$t_1,...,t_n$都是S项，而$f$是一个n元函数符，那么$ft_1...t_n$也是一个S项。所有S项组成的集合就是$T^S$。

定义：

1、若$t_1,t_2$是S项，那么$t_1\equiv t_2$是S公式。

2、若$t_1,...,t_n$是S项，R是一个n元关系符，那么$Rt_1...t_n$是S公式。

3、如果$\phi$是S公式，那么$\neg\phi$也是S公式。

4、如果$\phi,\psi$都是S公式，那么$(\phi*\psi),*\in\{\vee, \wedge,\to\iff\}$都是S公式。

5、如果$\phi$是S公式，x为变元，那么$\forall x\phi$和$\exist x\phi$也都是S公式。

所有的S公式组成的集合就是$L^S$

# Lec 2

$\exist\ \forall\ \neg$的作用域会尽可能短。

对于所有的S项，我们定义变元为：

$$
var(x)=\{x\}\\
var(c)=\{c\}\\
var(ft_1...t_n)=\cup_{i\in[n]}var(t_i)
$$

从而，我们可以得到自由变元：

$$
free(t_1\equiv t_2)=var(t_1)\cup var(t_2)\\
free(Rt_1...t_n)=\cup_{i\in[n]}var(t_i)\\
free(\neg\varphi)=free(\varphi)\\
free(\varphi * \psi)=free(\varphi)\cup free(\psi)\\
free(\forall x\varphi)=free(\varphi)-\{x\}\\
free(\exist x\varphi)=free(\varphi)-\{x\}
$$

我们定义，如果一个S公式中，自由变元的集合为空集，那么这是个S句子。

我们定义：

$$
L_n^S=\{\varphi|\varphi\ is\ an\ S-formula\ with\ free(\varphi)\sub \{v_0,...,v_{n-1}\}\}
$$

当$n=0$时，其为所有S-句子的集合。

我们定义，所有可能出现的元素为$A$，我们的演算将基于此进行。

$A\not =\empty$

接下来，我们需要定义出一种映射关系$\mathfrak{a}$，即：

$\forall R\in S,\mathfrak{a}(R)\sub A^n$

$\forall f\in S,\mathfrak{a}(f):A^n\to A$

$\forall c\in S,\mathfrak{a}(c)\in A$

有了这两种定义，我们可以定义出S-结构，$\mathfrak{A}=(A,\mathfrak{a})$

接下来，我们需要定义一种赋值操作，使得每一个自由变元在演算开始前，都是有值的，也就是：

$$
\beta:\{v_i|i\in \N\}\to A
$$

从而，我们可以定义出什么是S-解释，即$\mathfrak{I}=(\mathfrak{A},\beta)$

我们定义另一种赋值的操作：$\beta_{a\over x}(y)=a,if\ x=y;=\beta(y),otherwise$

从而，我们可以定义出满足关系，即：

$$
\mathfrak{I}|=\varphi\\

$$

我们先定义什么是解释：

$$
\mathfrak{I}(x)=\beta(x)\\
\mathfrak{I}(c)=c^{\mathfrak{A}}\\
\mathfrak{I}(ft_1...t_n)=f^{\mathfrak{A}}(\mathfrak{I}(t_1),...\mathfrak{I}(t_n))
$$

我们从而可以定义：

$$
\mathfrak{I}|=t_1\equiv t_2\ if\ \mathfrak{I}(t_1)=\mathfrak{I}(t_2)\\
\mathfrak{I}|=Rt_1...t_n\ if\ (\mathfrak{I}(t_1),...,\mathfrak{I}(t_n))\in R^{\mathfrak{A}}\\
\mathfrak{I}|=\neg\varphi\ if \mathfrak{I}|\neq \varphi\\
$$

或、和、蕴含、当且仅当同理。当为蕴含时，需要注意，如果前提不对，那怎么都对。

$$
\mathfrak{I}|=\forall x\varphi\ if\ for\ all\ a\in A,\mathfrak{I}_{a\over x}|=\varphi\\
\mathfrak{I}|=\exist x\varphi\ if\ for\ some\ a\in A,\mathfrak{I}_{a\over x}|=\varphi
$$

满足了以上的关系，我们就称：$\mathfrak{I}|=\varphi$

# Lec 3

$\Phi$是S-公式的集合，$\varphi$是一个S-公式，那么$\varphi$是$\Phi$的结果，记作$\Phi|=\varphi$，当且仅当对于任意的解释，存在$\mathfrak{I}|=\Phi\implies\mathfrak{I}|=\varphi$

倘若$\Phi$中仅有一个元素$\psi$，那么我们可以用$\psi|=\varphi$来代替之。

一个S-公式是系统认可的(valid)，当且仅当$\empty|=\varphi$，记作$|=\varphi$

一个公式是可满足的，如果存在一个解释，使得$\mathfrak{I}|=\varphi$

$\Phi|=\varphi$当且仅当$\Phi\cup\{\neg\varphi\}$不是可满足的。这是反证法的本质。

我们称两个公式是逻辑等价的，当且仅当$\varphi|=\psi$且$\psi|=\varphi$

通过逻辑等价，我们可以将一个公式化为与之逻辑等价，并且不含有$\wedge,\implies,\iff,\forall$的形式。

一致性引理：考虑两种解释，假如它们的universe都是A，并且每个在$S=S_1\cap S_2$的符号的解释都相同，那么，所有的S-项都有相同的解释。并且，当一个公式在两种解释下，自由变元赋值相同的情况下，该公式在解释1下成立，等价于该公式在解释2下成立。
