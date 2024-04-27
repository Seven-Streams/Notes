# Lec 1

样本空间(sample space)：某次实验(experiment)中可能出现的所有结果的集合。

事件(event)：是样本空间的一个子集。

**直觉不一定可靠。** 概率论中可能出现不少反直觉的内容。

概率的朴素定义： 

$$
P(A)={\frac{|\text{favorable outcomes}|}{|\text{possible outcomes}|}}
$$

这样做的要求是：每个结果是等可能发生的，并且样本空间大小**有限**。

计数：

假设进行了$r$次独立实验，每次的结果为$n_i$,那么总共的结果数应当有$\prod_{i=1}^rn_i$

 抽样(sampling)：是否可重？是否考虑顺序？

# Lec 2

插板法

story proof

$$
\tbinom{n}{k}=\tbinom{n}{n-k}\\
n\tbinom{n-1}{k-1}=k\tbinom{n}{k}\\
\tbinom{m+n}{k}=\sum_{j=0}^k\tbinom{m}{j}\tbinom{n}{k-j}
$$

第二个公式：“先选成员，再选谁女装”和“先选谁女装，再选剩下的成员”

第三个等式称为Vander恒等式。

概率空间(probability space)包含两部分：$S,P$，$S$是样本空间，$P$是一个函数，其定义为$S$，输入为事件$A\sub S$，$P(A)\in[0,1]$

$P$应当有$P(\empty)=0,P(S)=1,P(\cup_{n=1}^\infin A_n)=\sum_{n=1}^\infin P(A_n),A_i\cup A_j=\empty,i\neq j$

# Lec 3

抽屉原理：物体多于抽屉数，必有一个抽屉中有不止一个物体。

生日问题

一些简单的结论：

$$
P(A^C)=1-P(A)\\
A\sub B\implies P(A)\leq P(B)\\
P(A\cup B)=P(A)+P(B)-P(A\cap B)\\
P(A\cup B\cup C)=P(A)+P(B)+P(C)-\\ P(A\cap B)-P(A\cap C)-P(B\cap C)
+P(A\cap B\cap C)
$$

更多的交时亦是如此。正负轮替着出现。
