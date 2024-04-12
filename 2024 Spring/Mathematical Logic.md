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
\mathfrak{I}\vDash \varphi\\

$$

我们先定义什么是解释：

$$
\mathfrak{I}(x)=\beta(x)\\
\mathfrak{I}(c)=c^{\mathfrak{A}}\\
\mathfrak{I}(ft_1...t_n)=f^{\mathfrak{A}}(\mathfrak{I}(t_1),...\mathfrak{I}(t_n))
$$

我们从而可以定义：

$$
\mathfrak{I}\vDash t_1\equiv t_2\ if\ \mathfrak{I}(t_1)=\mathfrak{I}(t_2)\\
\mathfrak{I}\vDash Rt_1...t_n\ if\ (\mathfrak{I}(t_1),...,\mathfrak{I}(t_n))\in R^{\mathfrak{A}}\\
\mathfrak{I}\vDash \neg\varphi\ if\ \mathfrak{I}|\neq \varphi\\
$$

或、和、蕴含、当且仅当同理。当为蕴含时，需要注意，如果前提不对，那怎么都对。

$$
\mathfrak{I}\vDash \forall x\varphi\ if\ for\ all\ a\in A,\mathfrak{I}_{a\over x}\vDash \varphi\\
\mathfrak{I}\vDash \exist x\varphi\ if\ for\ some\ a\in A,\mathfrak{I}_{a\over x}\vDash \varphi
$$

满足了以上的关系，我们就称：$\mathfrak{I}\vDash \varphi$

# Lec 3

$\Phi$是S-公式的集合，$\varphi$是一个S-公式，那么$\varphi$是$\Phi$的结果，记作$\Phi\vDash \varphi$，当且仅当对于任意的解释，存在$\mathfrak{I}\vDash \Phi\implies\mathfrak{I}\vDash \varphi$

倘若$\Phi$中仅有一个元素$\psi$，那么我们可以用$\psi\vDash \varphi$来代替之。

一个S-公式是系统认可的(valid)，当且仅当$\empty\vDash \varphi$，记作$\vDash \varphi$

一个公式是可满足的，如果存在一个解释，使得$\mathfrak{I}\vDash \varphi$

$\Phi\vDash \varphi$当且仅当$\Phi\cup\{\neg\varphi\}$不是可满足的。这是反证法的本质。

我们称两个公式是逻辑等价的，当且仅当$\varphi\vDash \psi$且$\psi\vDash \varphi$

通过逻辑等价，我们可以将一个公式化为与之逻辑等价，并且不含有$\wedge,\implies,\iff,\forall$的形式。

Coincidence引理：考虑两种解释，假如它们的universe都是A，并且每个在$S=S_1\cap S_2$的符号的解释都相同，那么，所有的S-项都有相同的解释。并且，当一个公式在两种解释下，自由变元赋值相同的情况下，该公式在解释1下成立，等价于该公式在解释2下成立。

# Lec 4

我们称从$\pi:\mathfrak{A}\to\mathfrak{B}$是一个同构映射，当：

$\pi$是一个双射。

对于所有的n元关系$R\in S,a_0,...,a_{n-1}\in A$，有$(a_0,...,a_{n-1})\in R^\mathfrak{A}\iff (\pi(a_0),...,\pi(a_{n-1}))\in R^\mathfrak{B}$

对于所有的n元函数$f\in S,a_0,...,a_{n-1}\in A$,有

$\pi(f^\mathfrak{A}(a_0,...,a_{n-1}))=f^\mathfrak{B}(\pi(a_0),...,\pi(a_{n-1}))$

对于所有的常元，我们有$\pi(c^\mathfrak{A})=c^\mathfrak{B}$

我们可以称$\mathfrak{A},\mathfrak{B}$同构，记作$\mathfrak{A}\cong\mathfrak{B}$

同构关系具有：结构与自身同构，交换性，传递性。

如果$\mathfrak{A}\cong\mathfrak{B}$,则$\mathfrak{A}\vDash \varphi\iff\mathfrak{B}\vDash \varphi$

也就是说，在一阶逻辑语言下，同构的两个结构不可区分。

为了证明这一点，我们先证明对于所有的S-公式，在赋值满足一定映射的情况下，在两个结构中成立，即$(\mathfrak{A},\beta)\vDash \varphi\iff(\mathfrak{B},\beta^\pi)\vDash \varphi$。然后，我们证明所有的项之间有：$\pi(\mathfrak{I}(t))=\mathfrak{I}^\pi(t)$然后，使用归纳假设的方法，得出公式的不可区分性。

我们记$t{t_0,...,t_r\over x_0,...,x_r}$为$t$的一个替换，指将下面的每一个变量替换为上面的对应项。对于公式，我们可以类似地定义之。不过，当对带有$\exist$的公式进行定义时，我们需要考虑非自由变元的问题。我们在替换时，去掉那些不需替换、或是如换的情况。比如$\varphi=\exist x\psi$在进行替换时，我们应当“顺便”把$x$换为一个从未使用过的名字。为了使流程规范化，我们定义将这个非自有变元替换为第一个没有在公式和将替换出的项中出现的变元。如果这个变元本身，并未在替换中的项出现，那么我们不需要对原有变元进行重命名。

# Lec 5

替换引理：

$$
\mathfrak{I}(t{t_0,...,t_r\over x_0,...,x_r})=\mathfrak{I}{\mathfrak{I}(t_0)
,...,\mathfrak{I}(t_r)\over x_0,...,x_r}(t)\\

\mathfrak{I}\vDash \varphi{t_0,...,t_r\over x_0,...,x_r}\iff \mathfrak{I}{\mathfrak{I}(t_0)
,...,\mathfrak{I}(t_r)\over x_0,...,x_r}\vDash \varphi
$$

接下来，为了回答证明为什么对的问题，我们需要引入演绎计算的概念。

$$
\varphi_1...\varphi_n\varphi
$$

除去最后一项，我们称之为前项，即antecedent，最后一项则是后项，称为succedent。如果演算中可以导出序列$\Gamma\varphi$,那么我们可以记作$\vdash \Gamma\varphi$，我们称$\Gamma\varphi$是可导出的。

我们称一个公式$\varphi$是可从公式集$\Phi$导出的，记作$\Phi\vdash \varphi$，当$\vdash \varphi_1...\varphi_n\varphi$

如果一个序列$\Gamma\varphi$是对的，当$\{\psi|\psi\ is\ a\ member\ of\ \Gamma\}\vDash \varphi$

演绎计算具有这些规则：

1、前项$\Gamma\in\Gamma'$

$$
\Gamma\ \varphi\\
----\\
\Gamma'\ \varphi
$$

2、分类讨论

$$
\Gamma\ \psi\ \varphi\\
\Gamma\ \neg\psi\ \varphi\\
----\\
\gamma\ \varphi
$$

3、矛盾

$$
\Gamma\ \neg\varphi\ \psi\\
\Gamma\ \neg\varphi\ \neg\psi\\
----\\
\Gamma\ \varphi
$$

4、前项引入$\vee$

$$
\Gamma\ \varphi\ \chi\\
\Gamma\ \psi\ \chi\\
----\\
\Gamma\ (\varphi\vee\psi)\ \chi
$$

5、后项引入$\vee$

$$
\Gamma\ \varphi\\
----\\
\Gamma\ (\varphi\vee\psi)
$$

且

$$
\Gamma\ \varphi\\
----\\
\Gamma\ (\psi\vee\varphi)
$$

6、前项引入$\exist$

$$
\Gamma\ \varphi_{y\over x}\ \psi\\
----\\
\Gamma\ \exist x\varphi\ \psi
$$

要求是$y\not\in free(\Gamma\cup\{\exist x\varphi,\psi\})$

7、后项引入$\exist$

$$
\Gamma\ \varphi_{t\over x}\\
----\\
\Gamma\ \exist x\varphi
$$

8、相等

$$
----\\
t\equiv t
$$

9、替换

$$
\Gamma\ \varphi_{t\over x}\\
----\\
\Gamma\ t\equiv t'\ \varphi_{t'\over x}
$$

我们可以导出一些规则。

1、排中律：$\vdash (\varphi\vee\neg\varphi)$

2、西边的太阳定律：

$$
\Gamma\ \psi\\
\Gamma\ \neg\psi\\
----\\
\Gamma\ \varphi
$$

3、链式法则：

$$
\Gamma\ \varphi\\
\Gamma\ \varphi\ \psi\\
----\\
\Gamma\ \psi
$$

$\Phi\vdash \varphi\iff \exist finite\ \Phi_0\sub \Phi,s.t.\Phi_0\vdash \varphi$

Soundness：$\Phi\vdash \varphi\implies\Phi\vDash \varphi$

# Lec 6

我们称$\Phi$是consistent的，记作$cons(\Phi)$，如果没有$\varphi,s.t.\ \Phi\vdash \varphi,and\ \Phi\vdash \neg\varphi$

反之，则称为inconsistent。如果一个结构是inconsistent的，当且仅当对于任意的$\varphi,\Phi\vdash \varphi$

如果一个$\varphi$是consistent的，当且仅当$\exist\varphi,s.t.\Phi\not\vdash\varphi$

$\Phi$是consistent的，当且仅当$\forall$有限的$\Phi_0\sub\Phi$是consistent的。

每一个可满足的$\Phi$是consistent的。

$\Phi\vdash \varphi\iff \Phi\cup\{\neg\varphi\}$是inconsistent的。

$\Phi\vdash \neg\varphi\iff\Phi\cup\{\varphi\}$是inconsistent的。

如果$\Phi$是consistent的，那么$\Phi\cup\{\varphi\}$和$\Phi\cup\{\neg\varphi\}$中至少有一个成立。

Completeness：$\Phi\vDash \varphi\implies\Phi\vdash \varphi$

为了说明这一点，我们可以考虑其逆否命题：$\Phi\not\vdash\varphi\implies\Phi|\neq\varphi$

也就是$\Phi\cup\{\neg\varphi\}$是consistent的$\implies\Phi\cup\{\neg\varphi\}$是可满足的。

Henkin's定理。

为了证明上述结论，我们先引入等价项的概念。$t_1,t_2\in T^S,\Phi\vdash t_1\equiv t_2$那么，记作$t_1$~$t_2$

~是一种等价关系，若$t_1$~$t_1'$,...$t_n$~$t_n'$，那么$ft_1...t_n$~$ft_1'...t_n'$

$\Phi\vdash Rt_1...t_n\iff\Phi\vdash Rt_1'...t_n'$

对于每一个项，我们用其等价项中的一个来代表它，记作$\bar t$

我们为$\Phi$创建一个项结构，记作$\mathfrak{T}^\Phi$

这个结构的universe就是$\{\bar t|t\in T^S\}$

$(\bar t_1,...,\bar t_n)\in R^{\mathfrak{T}^\Phi}$当$\Phi\vdash Rt_1...t_n$

$f^{\mathfrak{T}^\Phi}(\bar t_1,...,\bar t_n)=\overline{ft_1...t_n}$

$c^{\mathfrak{T}^\Phi}=\bar c$

$\beta^\Phi(v_i)=\bar v_i$

$\mathfrak{I}^\Phi=(\mathfrak{T}^\Phi,\beta^\Phi)$

# Lec 7

在这之后，我们需要说明我们创造出的这个结构是良定义的。对于原子公式，这一点是显然的。为了去掉原子性，我们需要一些新的工具。

**完全否定(negation complete)**：$\Phi\vdash\varphi\ or\ \Phi\vdash\neg\varphi$

**包含可成立的证据(contain witnesses)**：$\Phi\vdash(\exist x\varphi\implies\varphi_{\frac{t}{x}})$

如果$\Phi$是negation complete，contain witnesses， consistent，那么我们有下面的这些结论：

$$
\Phi\vdash\varphi\iff\Phi\not\vdash\neg\varphi\\
\Phi\vdash(\varphi\vee\psi)\iff\Phi\vdash\varphi\ or\ \Phi\vdash\psi\\
\Phi\vdash\exist x\varphi\iff\exist t\in T^s\ s.t.\ \Phi\vdash\varphi_{\frac{t}{x}}
$$

对于第一条的证明，是显然的。对于第二条的证明，我们不妨先假设一个不可证出，然后就能导出另一个可证出。对于第三点，使用Modus ponens(肯定前件）即可。

之后，我们可以引出Henkin‘s Theorem：$\frak{I}^\Phi\vDash\varphi\iff\Phi\vdash\varphi$

如果是原子公式，那么是显然的。对于$\neg,\vee$的处理通过之前的假设就可以得到。对于$\exist$，我们可以对公式的深度进行归纳，即connective rank，然后再进行类似结构归纳的操作。

# Lec 8

如果符号集是至多可数的，令$\Phi\sub L^S$

定义：$\text{free}(\Phi)=\cup_{\varphi\in\Phi}\text{free}(\varphi)$

我们需要说明两个引理：

$\text{free}(\Phi)$如果是有限的，那么存在一个consistent的$\Psi,\Phi\sub\Psi\sub L^S,\Psi$contain witnesses。

$\Psi$是consistent的，那么存在一个$\Theta\in L^S,s.t.\Theta$是完全否定的。

因此，我们得到一个推论：只要$\text{free}(\Phi)$是有限的，一定可以找到一个我们所希望的$\Theta$,从而$\Phi$是satisfiable的。

证明第一点，我们可以把所有存在性的句子都拿出来，它们必然是可数多个，从而进行判断。我们通过归纳法和演绎计算，证明每一个$\Phi_i$都应该是contain witness的。

证明第二点，我们考虑每一个公式，如果它证不出来，那么就加入$\Theta_n$中并成为$\Theta_{n+1}$，最后取并即可。

最后，我们的想法，就是把有限变元这个条件给去掉。为了做到这一点，我们可以对公式中的每一个变元用一个常量进行替换，并且保证对这个常量的解释与对原有变元的赋值相同。通过替换引理和一致性引理可以证明。
