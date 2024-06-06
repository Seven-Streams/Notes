# Lec 1

回答四个问题：什么是数学证明？数学证明为什么对？可证明有边界吗？电脑可以找到证明吗？

数学证明：基于一阶逻辑的证明。

数学证明为什么对：在正式证明体系中，正确和可证等价。**（哥德尔完备性定理）**

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

# Lec 9

我们的目标，是去掉符号集可数的限制。

对于contain witness这一部分，我们可以扩充符号集，也就是将$\exist x\varphi\implies\varphi_{\frac{c}{x}}$中的$c$加入之，构成一新的符号集$S',s.t.\text{cons}(\Phi),\text{cons}(\Psi)\Phi\sub\Psi\sub L^{S'}$这一扩充的过程可以无限地进行下去。

对于一个consistent的$\Phi$，取出其中所有的存在性命题，改写成contain witness的命题。那么，这二者的并也是consistent的。我们只要说明每一个有限的$\Phi_i$与其对应的存在性命题的交是consistent的即可。对于剩下的常量解释，我们不用在意。根据一致性引理可得。

我们构造符号集$S_0\sub...S_n\sub...$，对应之可数公式集为$\Phi_i$,定义$S,\Phi$分别为其无穷并。我们定义，$S_{i+1}$为$S_i$与其contain witness公式之并。我们定义，$\Psi_{i+1}$为$\Psi_i$及其contain witness的并。

之后，我们应用Zorn引理。说明在consistent的公式集中，一定有一个最大的公式集。从而，这说明了它是完全否定的。因为它既consistent，并且最大。

从而，我们说明了完备性。

# Lec 10

Löwenheim-Skolem定理：

$$
\Phi\sub L^S,\Phi\text{ is at most countable and satisfiable.}\\
\exist\mathfrak{I}=(\mathfrak{A},\beta),s.t.\\
A\text{ is at most countable,}\mathfrak{I}\vDash\Phi
$$

这一点可以利用项结构进行说明。

如果去掉$\Phi\text{ is at most countable}$，我们可以得到Downward Löwenheim-Skolem定理，区别在于将$A\text{ is at most countable}$改为$|A|\leq|T^S|\leq|L^S|$

因此，对于$\Phi_{\R}=\{\varphi\in L^S_0|(\R,+,\cdot,<,0,1)\vDash\varphi\}$

我们可以挑出一个可数的S-结构，从而使得$\mathfrak{A}\vDash\Phi_\R$

紧致性：

$$
\Phi\vDash\varphi\iff\exist\text{ finite }\Phi_0\sub\Phi,\Phi_0\vDash\varphi\\
\text{sat}(\Phi)\iff\forall\text{ finite }\Phi_0\sub\Phi,\text{sat}(\Phi)
$$

我们定义：

$$
\text{Mod}(\varphi):=\{\mathfrak{I}|\mathfrak{I}\vDash\varphi\}\\
\text{Mod}(\Phi)=\{\mathfrak{I}|\mathfrak{I}\vDash\Phi\}=\cap_{\psi\in\Phi}\text{Mod}(\psi)
$$

紧致性与下面的说法等价：

$$
\text{Mod}(\varphi)\sub\cup_{\psi\in\Phi}\iff\exist\text{ finite }\Phi_0\sub\Phi,\text{Mod}(\varphi)\sub\cup_{\psi\in\Phi_0}\text{Mod}(\psi)
$$

定理：

$$
\Phi\sub L^s ,\forall n\in\N,\exist\mathfrak{I}_n=(\mathfrak{A}_n,\beta_n),
|A_n|\geq n,\mathfrak{I}_n\vDash\Phi,\text{then}\\
\exist \text{ infinite } A,\mathfrak{I}\vDash\Phi
$$

Upward Löwenheim-Skolem定理:

$$
\Phi\sub L^s,\text{assume }\mathfrak{I}\vDash\Phi,A\text{ is infinite.}\\
\forall\ B,\exist\  \mathfrak{I}',|A'|>|B|,\mathfrak{I}'\vDash\Phi
$$

因此，对于：

$\Phi_{\N}=\{\varphi\in L^S_0|(\N,+,\cdot,<,0,1)\vDash\varphi\}$，那么存在一个不可数的S-结构$\mathfrak{A}$,$\mathfrak{A}\vDash\Phi_\N$

# Lec 11

在下文中，所有的$\mathcal{A}$表示一个有限的字母表，$W\sub \mathcal{A}^*$,

我们称一个过程是$W$的判定过程，如果对于每一个输入$w\in\mathcal{A^*}$,输出为$w'\in\mathcal{A}$。$w\in W\implies w'=\square,w\not\in W,w'\neq\square$

我们称$W$是可判定的，如果存在一个$W$的判定过程。

我们称一个过程是$W$的枚举过程，当这个过程没有任何输入的情况下，可以除数所有$W$中的word，可以有重复。

我们称$W$是可枚举的，如果存在一个$W$的枚举过程。

lemma:$A^*$是可枚举的。$\{\varphi\in L_0^{S_\infin}|\vDash\varphi\}$也是可枚举的。这是前一个引理显然的推论。

可枚举集一定存在一种枚举方式，使得每个元素恰出现一次。

每一个可判定集合都是可枚举的。

一个集合是可判定的，当且仅当其和其补集都是可枚举的。

寄存器机模型：字母表为$\mathcal{A},|\mathcal{A}|=r$,共有$m$个可以存储字的寄存器。我们定义五种运算：

- 加法：在一个寄存器的最后加上一个符号。

- 减法：在一个寄存器的最后减去一个**特定**符号。如果其末尾非此符号，则不操作。

- 条件判断语句：根据寄存器对象为空或者末尾的符号，跳转到不同标签的语句。

- 打印：打印0号寄存器中的内容。

- 停机：停机。

我们称一个程序是寄存器程序，当且仅当：其为有限的上述语句之组合。并且，每一行之语句有与其自然数序相同的标签。跳转语句跳转的范围必须在出现的标签中。停机语句应当是最后一行。

我们记$w\to\text{halt}$表示输入为$w$的情况下，最终会停机。$w\to\infin$表示输入为$w$

的情况下，最终不会停机。$w\to w'$表示最终会停机，并且输出有且仅有$w'$。

将之前可判定性迁移至此处，则可得到R-可判定性。即$w\to\square$和$w\to w',w'\neq\square$

可枚举性，即是$w=\square$的情况，要求输出了每一个元素。

# Lec 12

$F:\mathcal{A}^*\to\mathcal{B}^*$,我们称一个程序可以计算$F$当对任意的$w\in\mathcal{A}^*$,$P:w\to F(w)$

这个程序定义在$\mathcal{A}\cup\mathcal{B}$上。

对于每一个程序，我们显然可以对每一个语句进行编码，从而得到某个唯一编码。然后，我们将这些程序的编码按照字典序进行排序，那么我们就可以得到一个序结构。我们定义$w_P$为某个程序的编码，其由$n$个$a_0$组成，$n$为其在排序中的序号。$a_0$为域中任意一元素。那么，存在映射$P\to w_p,\Pi=\{w_P|P\text{ is a program over }\mathcal{A}\}$

前者通常被称作哥德尔配数。

$\Pi$是可判定的。

对于一个固定的字母表$\mathcal{A}$，但是$\Pi'_{\text{halt}}=\{w_P|P:w_P\to\text{halt},w_P\in\Pi\},\\ \Pi_{\text{halt}}=\{w_P|P:\square\to\text{halt},w_P\in\Pi\}$

均不可判定。

这两个问题是在可枚举范围内，在规约意义下最困难的问题。二者可以互相规约。对于前者的证明，可以使用反证法。假设存在判定程序$P$，我们可以考虑一个程序和$P$几乎一致，但在输出时进行判断。如果$P$将输出$\square$，则不停机，否则停机。

若$W_A\sub A^*,W_B\sub B^*,\text{if } \exist F,\text{s.t.}, w\in W_A\iff F(w)\in W_B$

那么，$W_A$就可规约到$W_B$。并且，如果$W_B$可判定，那么$W_A$一定可判定。

对于所有的$L_0^{S\infin}$，它们显然是可枚举的。如果我们想要说明一阶逻辑的不可判定性，我们只需要将$\Pi_{\text{halt}}$规约到$L_0^{S\infin}$中valid公式的集合。即可说明不可判定性。

首先，我们规定字母表$\mathcal{A}=\{|\}$

对于每一个程序，假设使用了$n+1$个寄存器，那么我们可以用一个$n+2$元组来表征程序当前的状态。第一个位置表示将要运行哪一行程序。第$k$个位置表征第$k-1$个寄存器中，存放了多少个$|$。

我们定义$S=\{R,<,f,c\}\sub S^\infin$

我们定义$\mathfrak{A}_P:A_P=\N,<=<^\N,f(x)=x+^\N1^\N,c=0^\N$

$R^{\mathfrak{A}_P}$为一个$n+2$元关系符。其即表征了某个元组是否是某个程序可以到达的状态。

首先，我们需要一个合适的$\psi_P$，其需要满足：

$\mathfrak{A}_P\vDash\psi_P\\ \forall\mathfrak{A},\mathfrak{A}\vDash \psi_P\implies\mathfrak{A}\vDash R\bar L\bar m_0...\bar m_n$

首先，我们需要一个“头”，它表征我们构建$\varphi_P$所需要的一些性质。即$<$是一个序结构，$c$是序结构中的最小元素，$x< fx$，$x<y\to (fx<y\vee fx\equiv y)$

这些记为$\psi_0$

那么，$\psi_P=\psi_0\wedge R\bar0\bar0...\bar0\wedge\psi_{\alpha_0}\wedge...\wedge\psi_{\alpha_{k-1}}$

$\psi_\alpha$表征的，就是在任意的输入下，如果$L$为将执行的语句，那么寄存器中的内容将发生的变化，以及将要执行的语句之间的跳转。

我们定义$\varphi_p=\psi_P\to\exist y_0...\exist y_n R\bar k y_0...y_n$

$\bar k$即表征将要执行停机语句。从而，我们得到了一个在停机程序和valid公式之间的规约。说明一阶逻辑中，valid公式具有不可判定性。

# Lec 13

我们称$T\sub L_0^S$是一个理论，如果：$\text{sat}(T);\forall\varphi\in L_0^S,T\vDash\varphi,\ then\ \varphi\in T$

第二点，就是在说这个集合具有封闭性。

我们记$\text{Th}(\mathfrak{A})=\{\varphi\in L_0^S|\mathfrak{A}\vDash\varphi\}$

我们记$\mathfrak{N}=(\N,+,\cdot,0,1),\text{Th}(\mathfrak{N})$称为初等算术。

我们定义$T^\vDash=\{\varphi\in L_0^S|T\vDash\varphi\}$

存在以下三条等价关系。$T^\vDash$是理论，$\text{sat}(T),T^\vDash\neq L_0^S$

我们定义$\Phi_{PA}$由一系列$S_{ar}$句子组成。$S_{ar}=\{+,\cdot,0,1\}$

$$
\forall x\ \neg x+1\equiv 0\\
\forall x\ x +0\equiv x\\
\forall x\ x\cdot0\equiv0\\
\forall x\forall y(x + 1\equiv y + 1\implies x\equiv y)\\
\forall x\forall y\ x +(y + 1)\equiv (x+y)+1\\
\forall x\forall y\ x\cdot(y + 1\equiv)\equiv x\cdot y +x\\
\text{free}(\varphi)\sub\{x_1,...,x_n,y\}\\
\forall x_1 ...\forall x_n((\varphi_{0\over y}\wedge\forall y(\varphi\implies \varphi_{y +1\over y}))
\implies\forall y\varphi)
$$

说人话，就是存在最小的，加法的单位元。存在数乘中的零映射。

后继相等，可以推出前驱相等。加法具有交换律。乘法具有分配律。具有起点为0的数学归纳法。

我们称$T$是R-axiomatizable当存在R-decidable$\Phi\sub L_0^S,T=\Phi^\vDash$

也就是说，这个公式集可以被一个可判定的集合所公理化。

我们称$T$是有限axiomatizable的，如果存在有限的$\Phi\sub L_0^S,T=\Phi^\vDash$

每一个R-axiomatizable的理论，都是R-enumerable的。

可被公理化，不一定可被判定。比如valid的公式。

我们称一个理论$T\sub L_0^S$是完备的，如果对于任何的公式$\varphi$，要么$\varphi\in T$,要么$\neg\varphi\in T$

对于一个S-结构$\mathfrak{A}$，$\text{Th}(\mathfrak{A})$一定是完备的。

每一个完备的可被公理化的理论，一定是可判定的；每一个完备的可枚举的理论，一定是可判定的。

为了说明算术的不可判定性，我们需要进行规约。

我们考虑一个公式，$\Chi_P(x_0,...,x_n,z,y_0,...,y_n)$,我们需要说明对于任何的初始状态$(0,l_0,...,l_n)$和任意一个有限步内可达状态$(L,m_0,...,m_n)$，能够有$\mathfrak{N}\vDash\Chi_P[l_0,...,l_n,L,m_0,...,m_n]$

定义$\varphi_P=\exist y_0...\exist y_n\Chi_P(0,...,0,\bar k,y_0,...,y_n)$

其中，$\bar k$定义为$1+1+...+1=k^\N$

如果能够说明算术公理的不可判定性，那么$\text{Th}(\mathfrak{N})$不可被公理化和枚举。从而有$\Phi_{PA}^\vDash\subsetneq\text{Th}(\mathfrak{N})$

我们在构建公式的一个瓶颈是，我们并不预先知道到达一个状态之前，我们走了多少步。

我们用一个自然数序列来刻画每个状态。假设花费了s步到达某一状态，那么我们用一个$(s+1)*(n+1)$的序列来刻画之。前$n+1$个数显然在表征初始状态。对于所有比s小的数，我们都可以通过程序转移到后一状态。

哥德尔$\beta$函数：对于每一个长度为$r$的序列，存在$t,p\in\N,\forall\ i\leq r,\beta(t,p,i)=a_i$

$\mathfrak{N}\vDash\varphi_\beta[t,q,i,a]\iff\beta(t,q,i)=a$

# Lec 14

$\beta$函数：

首先，我们对$p$提出要求，要求其比$r$和所有的$a_i$都要来得大。这一步的目的是为了构建出一个真正的$p$进制数。随后，我们构造出一个$t$，即：

$$
1\cdot p^0+a_0\cdot p^1+...+(r+1)\cdot p^{2r}+a_r\cdot p^{2r+1}
$$

也就是说，我们构造出了一个$p$进制的数。其中，自然数的额外引入用于确定位置。

$\text{claim:}i\leq r,a\in\N,a=a_i\iff\exist b_0,b_1,b_2\in\N,s.t\\ t= b_0+b_1((i+1)+a\cdot p+b_2\cdot p^2)\\ a<p\\ b_0<b_1\\ \exist m\in \N, s.t.\ b_1=p^{2m}$

左推右是平凡的。

右推左的话，由最后一条，我们可以向第一条中回代。由于$i+1$的定位作用和第二，第三条所保证下的$p$进制数的特点，可以得到这一结论。

如果$\mathscr{R}\sub\N^r$是一个可判定的关系，那么就存在一个$L^{S_{ar}}$公式$\varphi(v_0,...,v_{r-1})\in \N,s.t.$

$\mathscr{R}\in\N^r,(l_0,...,l_{r-1})\in\mathscr{R}\iff\mathfrak{N}\vDash\varphi(\bar l_0,...,\bar l_{r-1})$

如果$f:\N^r\to\N$是一个可计算函数，那么类似地，有：

$$
f(l_0,...,l_{r-1})=l_r\iff\mathfrak{N}\vDash\varphi(\bar l_0,...,\bar l_{r-1},\bar v_r)
$$

并且，因此会有：

$$
\mathfrak{N}\vDash\exist^{=1}v_r\varphi(\bar l_0,...,\bar l_{r-1},v_r)
$$

其中，$\exist^{=1}x\theta(x)$表示$\exist x(\theta(x)\wedge \forall y(\theta(y)\implies y\equiv x))$

说人话，就是唯一存在。

当$\Phi\sub L_0^{S_{ar}}$时，若$r\geq 1$我们对于可表示性做出如下定义：

$\mathscr{R}\sub\N^r$在$\Phi$可被表示，如果存在$\varphi(v_0,...,v_{r-1})$使得：

$$
(n_0,...,n_{r-1})\in\mathscr{R}\implies \Phi\vdash\varphi(\bar n_0,...,\bar n_{r-1})\\
(n_0,...,n_{r-1})\not\in\mathscr{R}\implies\Phi\vdash\neg\varphi(\bar n_0,...,\bar n_{r-1})
$$

$f:\N^r\to\N$在$\Phi$可被表示，也是类似的，即：

$$
(n_0,...,n_{r-1})= n_r\implies \Phi\vdash\varphi(\bar n_0,...,\bar n_{r-1},\bar n_r)\\
(n_0,...,n_{r-1})\not= n_r\implies\Phi\vdash\neg\varphi(\bar n_0,...,\bar n_{r-1},\bar n_r)\\

\Phi\vdash\exist^{=1}v_r\varphi(\bar n_0,...,\bar n_{r-1},v_r)
$$

如果$\Phi$是inconsistent的，那么天然地，每一个关系和函数都是可表示的。

$\Phi\sub\Phi'\sub L_0^{S_{ar}}$,那么在$\Phi$中可表示的，天然在$\Phi'$中可以表示。

如果$\text{cons}(\Phi)$，如果$\Phi$是可判定的，那么$\Phi$可表示的所有关系是可判定的，所有函数是可计算的。

我们称$\Phi$是允许表示的，如果所有可判定的关系和可计算的函数都是可表示的。

$\text{Th}(\mathfrak{N})$和$\Phi_{PA}$都是允许表示的。

不动点定理：假设$\Phi$是允许表示的。那么$\forall\psi\in L_1^{S_{ar}}$，存在$S_{ar}-sentece\ \varphi,s.t.$

$$
\Phi\vdash\varphi\iff\psi(\overline{[\varphi]})
$$

$\overline{[\varphi]})$表示这个公式在一个有效的无重复枚举过程中的枚举序。

证明较为复杂。定义一个二元函数$F$有：

$F(n,m)=[\varphi_n(\bar m)],\varphi_n\in L_1^{S_{ar}}-L_0^{S_{ar}};0,otherwise$

这个函数是可计算的。并且有$F([\varphi],m)=[\varphi(\bar m)]$

考虑到$\Phi$是允许表示的，那么就应该有一个公式$\varphi_F(x,y,z)$用来判断$F(n,m)$是否为$l$，并且有着存在唯一性。

我们定义$\beta(v_0):=\forall x(\varphi_F(v_0,v_0,x)\implies \psi(x))$

接下来，我们记$\varphi=\beta(\bar n),n=[\beta]$

那么，$F(n,n)=F([\beta],n)=[\beta(\bar n)]=[\varphi]$

所以$\Phi\vdash \varphi_F(\bar n,\bar n,\overline{[\varphi]})$

所以，$\Phi\cup\{\varphi\}\vdash\psi(\overline{[\varphi]})$

反向，可以由唯一性和$\psi(\overline{[\varphi]})$共同取得。从而得证。

# Lec 15

定义：

$$
\Phi^\vdash=\{\varphi\in L^{S_{ar}}|\Phi\vdash\varphi\}
$$

我们称$\Phi^\vdash$为可表示的，如果：

$$
\{[\varphi]\in\N|\varphi\in\Phi^\vdash\}=\{[\varphi]|\varphi\in L^{S_{ar}},\Phi\vdash\varphi\}
$$

在$\Phi$中是可表示的。

引理：倘$\Phi\sub L^{S_{ar}}$是consistent的且允许表示，$\Phi^\vdash$在$\Phi$中不可表示。

证明：假设上述说法不成立。则，对于每一个$\varphi$，都应当有一个$\chi(v_0)$,从而来刻画这种属性。由于consistent，可得：

$$
\Phi\not\vdash\varphi\iff\neg\chi(\overline{[\varphi]})
$$

但是，由于$\Phi$允许表示，所以，由不动点定理，可得:

$$
\exist\varphi,s.t.\Phi\vdash\varphi\iff\neg\chi(\overline{[\varphi]})
$$

因为，右边也是个$L_1^{S_{ar}}$.

是故，自然可得$\Phi^{\vDash}$亦不可于$\Phi$中得以表示。$\text{Th}(\mathfrak{N})$亦不可于$\text{Th}(\mathfrak{N})$中被表示（这是废话）。

从而，可得哥德尔第一不完备定理：$\Phi$consistent且允许表示，一定会有些sentence$\varphi$，既不可得到$\Phi\vdash\varphi$且不可得到$\Phi\not\vdash\varphi$
