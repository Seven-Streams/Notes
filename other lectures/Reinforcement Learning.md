# 第一章 初探强化学习

强化学习，解决的是序贯决策的问题。目标是要找到一个最优的占用度量。占用度量，可以理解为在不同情况下，采取不同策略的概率分布模型。

# 第二章 多臂老虎机(MAB)问题

有一台老虎机，其有k根拉杆，每根拉杆对应不同的奖励概率分布。如何在操作T次拉杆后，获得尽量高的奖励呢？ 

我们引入懊悔(regret)这一概念来刻画拉动一根拉杆的期望奖励和最优拉杆期望之间的差距，定义为二者之差。我们的目标，就是要最小化懊悔。显然，我们需要不断拉一根拉杆，才能对它产生的值有一个大概的估计。我们使用增量式估计来更新，而非重新计算。递推的复杂度更低。

操作实际上可以分为两种类型：探索和利用。

## $\epsilon-$贪婪算法

每次有$1-\epsilon$的概率拉下期望奖励最大的拉杆，否则，就随机选择一根拉杆。$\epsilon$可以设置为随着时间下降。

## 上置信界算法

显然，如果我们对一根拉杆测试较多，那么它的确认度较高，我们更会相信目前的结果是可靠的。原理依靠于霍夫丁不等式，即：

$$
P(E[X]\geq\bar x_n+u)\leq e^{-2nu^2}
$$

我们假设这是第t次操作，拉下的是k号拉杆，那么不确定度为$\hat U(a_t)=\sqrt{\frac{-\log p}{2N(a_t)}}=\sqrt{\frac{-\log p}{2N(k)}}$

根据霍夫丁不等式，$Q(a_t)<\hat Q(a_t)+\hat U(a_t)$成立的概率至少为$1-p$

实际上，在具体操作过程中，我们分母会加2处理，避免出现除0错。同时，可以设置p依旧随时间衰减。由此可见，两种方法的idea还是比较接近的。一般而言。为了更好地控制，我们可以选择$\max[\hat Q(a)+c\cdot \hat U(a)]$的那根拉杆。

## 汤普森采样算法

我们采用贝塔分布来给每一个选择的概率进行建模。我们根据目前已经建模的情况，进行一次随机采样。然后，我们选择采样结果最高的那一个。

# 第三章 马尔可夫决策过程

## 马尔可夫过程

随机过程(sticgastuc process)是我们研究的对象。如果一个状态转移的过程中，下一状态仅取决于当前状态，那么就称这个过程具有马尔可夫性质。

我们称具有马尔可夫性质的随机过程为马尔可夫过程，用$<\mathcal{S},\mathcal{P}>$来描述马尔可夫过程。其中，$\mathcal{S}$是状态集，$\mathcal{P}$是状态转移矩阵，有$\mathcal{P}_{ij}=P(s_j|s_i)$

根据状态转移矩阵，我们可以轻松地画出状态之间的转移关系。

## 马尔可夫奖励过程

在马尔可夫过程的基础上，加上奖励函数$r$和折扣因子$\gamma$,即得到马尔可夫奖励过程，记作$<\mathcal{S},\mathcal{P},r,\gamma>$

$r(s)$表示转移为该状态时可以获得的奖励的期望。$\gamma$是为了控制短期影响和长期影响之间的权重关系。

假设我们考察从$t$时刻到最后的最后，定义$R_t$为第$t$时刻的可以获得的奖励，那么我们定义回报为：

$$
G_t=\sum_{k=0}^\infin \gamma^k R_{t+k}
$$

我们定义，一个状态的期望回报称为这个状态的价值。

由于这是一个马尔可夫过程，所以我们有：

$$
V(s)=E[G_t|S_t=s]\\
=E[R_t+\gamma G_{t+1}|S_t=s]\\
=E[R_t+\gamma V(S_{t+1})|S_t=s]
$$

所以，我们有：

$$
V(s)=r(s)+\gamma\sum_{s'\in \mathcal{S}}P(s'|s)V(s')
$$

这就是贝尔曼方程。如果我们将每个状态的奖励和回报都写作列向量，那么，我们可以得到：

$$
V=R+\gamma PV\\
V=(I-\gamma P)^{-1}R
$$

这个方法很好。但是它的复杂度是$O(|S|^3)$，这是不可接受的。

## 马尔可夫决策过程

在马尔可夫奖励过程的基础上，加上一个外来的“智能体”(agent)，可以对当前的状态做出影响，就得到了马尔可夫决策过程，记作$<\mathcal{S},\mathcal{A},P,r,\gamma>$，其中$\mathcal{A}$为所有动作的集合。此后，我们采用状态转移函数，而非状态转移矩阵来描述这一过程。因为自变量增多了。

我们定义智能体的策略为$\pi(a|s)=P(A_t=a|S_t=s)$

类似地扩充，我们紧接着定义$V^\pi(s)=E_\pi[G_t|S_t=s]$

因为我们的选择还与动作有关，所以我们额外定义一个动作价值函数$Q^\pi(s,a)=E_\pi[G_t|S_t=s,A_t=a]$

二者之间存在着这样的联系：$V^\pi(s)=\sum_{a\in\mathcal{A}}\pi(a|s)Q^\pi(s,a)$

$Q^\pi(s,a)=r(s,a)+\gamma\sum_{s'\in\mathcal{S}}P(s'|s,a)V^\pi(s')$

这两个式子是符合直觉的。

对于二者分别取期望，可以得到贝尔曼期望方程：

$$
Q^\pi(s,a)=r(s,a)+\gamma\sum_{s'\in\mathcal{S}}P(s'|s,a)\sum_{a'\in\mathcal{A}}\pi(a'|s')Q^\pi(s',a')\\
V^\pi(s)=\sum_{a\in\mathcal{A}}\pi(a|s)(r(s,a)+\gamma\sum_{s'\in\mathcal{S}}P(s'|s,a)V^\pi(s')
$$

仔细看看这两个式子，还是可以理解其朴素的意图的。

### 蒙特卡罗方法

通过模拟爆算，近似地试探出每个状态的价值函数。我们采样很多条序列。在一个序列计算结束后，我们根据每个状态经过时之总回报进行平均处理，得到一个对状态价值的估计。在大量采样之后，我们在对每条序列中某一个状态的价值进行平均取样。根据大数定律，这样会趋近于$V^\pi(s)$。

## 占用度量

因为不同的策略，会使得agent访问到不同的概率分布的状态，所以我们需要考察在某一策略下的状态访问分布。我们定义$P_t^\pi(s)$表示策略$\pi$使得$t$时刻状态为$s$的概率。下式中的$1-\gamma$用于归一化概率。初始状态分布记为$v_0(s)$

$$
v^\pi(s)=(1-\gamma)\sum_{t=0}^\infin\gamma^t P_t^\pi(s)\\
v^\pi(s')=(1-\gamma)v_0(s')+\gamma\int P(s'|s,a)\pi(a|s)v^\pi(s)dsda
$$

这里需要稍体察其用意。

定义占用度量为

$$
\rho^\pi(s,a)=(1-\gamma)\sum_{t=0}^\infin\gamma^t P_t^\pi(s)\pi(a|s)
$$

这可以用来表征一个状态-动作对被访问到的概率。二者之间存在这样的关系

$$
\rho^\pi(s,a)=v^\pi(s)\pi(a|s)
$$

Theorem1：二者的占用度量相等，当且仅当策略相同。

Theorem2：给定一可行的占用度量，可生成其的唯一策略是$\pi_\rho={\rho(s,a)\over \sum_{a'}\rho(s,a')}$

也就是说，这可以认为是个不动点？

## 最优策略

这是强化学习的目标。一个策略是最优策略，当且仅当在任意状态下，它都不比其他策略差，那么它就是最优策略。我们可以定义一系列最优函数：

$$
V^*(s)=\max_\pi V^\pi(s)\\
Q^*(s,a)=\max_\pi Q^\pi(s,a)\\
Q^*(s,a)=r(s,a)+\gamma\sum_{s'\in\mathcal{S}}P(s'|s,a)V^*(s')\\
V^*(s)=\max_{a\in\mathcal{A}}Q^*(s,a)
$$

第三式的产生，是由最优性保证的。

根据二者之间的关系，我们可以得到贝尔曼最优方程：

$$
V^*(s)=\max_{a\in\mathcal{A}}\{r(s,a)+\gamma\sum_{s'\in\mathcal{S}}P(s'|s,a)V^*(s')\}\\
Q^*(s,a)=r(s,a)+\gamma\sum_{s'\in\mathcal{S}}P(s'|s,a)\max_{a'\in\mathcal{A}}Q^*(s',a')
$$

# 第四章 动态规划算法

主要有两种基于动态规划的强化学习算法：策略迭代(policy iteration)和价值迭代(value iteration)。策略迭代由策略评估(policy evaluation)和策略提升(policy improvement)两部分共同构成。

## 悬崖漫步环境

策略评估：用上一轮得到的结果来更新每一个策略的状态价值函数。即

$$
V^{k+1}(s)=\sum_{a\in\mathcal{A}}\pi(a|s)(r(s,a)+\gamma\sum_{s'\in\mathcal{S}}P(s'|s,a)V^k(s'))
$$

测试轮数足够多的话，会有$V^k(s)\approx V^\pi(s)$

策略提升：在测试的过程中，对策略本身进行改进。想法是如果进行了足够次数的测试后，如果有：

$$
Q^\pi(s,\pi'(s))\geq V^\pi(s)
$$

对任意$s$恒成立，那么

$$
V^{\pi '}(s)\geq V^\pi
$$

此为策略提升定理。这一点从直觉上去考虑是成立的。

策略迭代的过程，就是测试、策略评估、策略提升依次进行的过程。

价值迭代也是类似的过程。即

$$
V^{k+1}(s)=\max_{a\in\mathcal{A}}\{r(s,a)+\gamma\sum_{s'\in\mathcal{S}}P(s'|s,a)V^k(s')\}
$$

# 第五章 时序差分算法

$$
V(s_t)\leftarrow V(s_t)+\alpha[G_t-V(s_t)]
$$

这是蒙特卡洛算法中对状态价值函数的更新。由于我们需要$G_t$,所以必须要计算完整个序列才能进行改动。为了在更新过程中，就可以对其进行改动，我们可以这样处理：

$$
V(s_t)\leftarrow V(s_t)+\alpha[r_t+\gamma V(s_{t+1})-V(s_t)]
$$

我们称$r_t+\gamma V(s_{t+1})-V(s_t)$为**时序差分误差**。