# Reinforcement Learning

## Lec 1

强化学习是一种在交互过程中**试错**迭代的技术。

- 预测型任务

- 决策型任务

动态环境：环境有可转移的状态，并且有多步决策。

强化学习一般针对于动态黑盒的环境。

序贯决策（动态环境）

### 定义

在交互中学习来实现目标

- 感知：感知环境的状态

- 动作：采取行为来影响状态或者达到目标

- 目标：奖励函数最大化

在每一步，智能体获得观察 $O_t$，执行动作$A_t$，获得奖励$R_t$，环境获得动作$A_t$, 给出奖励 $R_t$，给出新的观察 $O_{t+1}$

在 RL 中， 我们在做 $\max_{\theta}E_{(s,a)\sim\rho^{\pi_0}}[r(s,a)]$

强化学习实际上可以看做是在优化数据集！

### RL 系统中的要素

- 历史(history): $H_t$, 观察、动作、奖励的序列

- 状态(state): $S_t, S_t=f(H_t)$, 用来确定接下来会发生的事情

- 策略(policy): 状态到动作的一个映射。
  
  - 确定性策略(deterministic policy), $a=\pi(s)$
  
  - 随机策略(stochastic policy), $\pi(a|s)=P(A_t=a|S_t=s)$

- 奖励(reward): $R_t$ 和 $r(s,a)$，一个用于定义强化学习目标的标量

- 模型(model): 用于模拟环境的行为。用于预测下一个状态和立即奖励。

强化学习的目标：$\max_{\pi}E_{\pi,\text{Env}}[\sum_{t=0}^T\gamma^tr(s_t,a_t)]$, 其中 $\gamma\in[0,1]$, 为一个衰减因子。也就是在 $T$ 步的情况下，效果还不错。 

为什么是指数？这样可以保证当两个序列函数值不同时，在序列最前面插入一个 $x$,结果依然保序。

价值：一个标量，用于定义长期来说什么是“好”的。

$Q_{\pi}(s,a)= r(s)+\gamma\sum_{s'\in S}P_{sa}(s')\sum_{a'\in A}\pi(a'|s')Q(s',a')$

一般而言，就是基于 $Q$ 改进 $\pi$，再重算 $Q$

### RL 的方法分类

- 基于价值

- 基于策略

- Actor-Critic

深度强化学习

## Lec 2 探索与利用

决策可能会造成 bias, 因此我们需要有一定的数据量

- Exploitation: 执行能够获得已知最优收益的决策。

- Exploration: 尝试更多可能的决策，但不一定最优。

### 多臂老虎机(MAB)

问题：如何估计每个拉杆的收益？

显然该取平均值。使用**增量方式**而不是直接算，可以降低其复杂度。

问题：我们应该怎么选择策略？

`Regret` 函数：计算决策和最优决策的收益差。从而有：$\sigma_R=\mathbb{E}_{a\sim\pi}[\sum_{t=1}^TQ(a_t^i)]$

如果一直探索新决策，那么 regret 会线性增大；如果一直不探索新决策，只要不是最优解，那么 regret 也会线性递增。

目前证明了，$\lim_{T\to\infin}\sigma_R\ge k\log T,k$ 为与模型有关常量。

目前，最常采取的策略为 $\epsilon-\text{greedy}$ 策略。有$ 1-\epsilon$ 概率选择利用，有小概率进行探索。它的 regret 也是线性增大的。但只是增长率小一些。

为了把 regret 增长为次线性的，因此可以把 $\epsilon$ 随着时间增长而缩小。其增长率可以成为 $\log T$ 级别的增长。

乐观初始化方法：给每一个 arm 给一个很高的初始化值。从而鼓励多探索每一个选择。由于增量式蒙特卡洛方式进行了更新，所以也确实有可能陷入局部最优解。

基于不确定性测度(UCB)：不确定性越大的价值，那么越具有探索的价值，有可能是更好地策略。因此，我们可以考虑在选择 action 的时候，不仅考虑价值，也考虑不确定性和信息量增益等等。这一点基于 Hoeffding 不等式。

Thompson Sampling 方法：根据每个动作可能成为最优概率来选择动作。直接根据当前每个动作的价值概率分布来建模，然后采样它的对应价值。然后选择价值最大的方法。

多臂老虎机可以看作是一种无状态(state-less)的强化学习

## Lec 3 马尔科夫决策过程(MDP)

随机过程：事件随时间演化的过程。

Markov Process: 具有马尔科夫性质的随机过程。我们称一个状态是马尔科夫的，当且仅当$\mathbb{P}[S_{t+1}|S_t]=\mathbb{P}[S_{t+1}|S_1,...,S_t]$

要求：$[a_1,a_2,...]<[b_1,b_2,...]\iff [r,a_1,a_2,...]<[r,b_1,b_2]$ 那么必须是指数衰减。

MDP: 可以用一个五元组来表示。$(S,A,\{P_{sa}\},\gamma,r)$

占用度量(occupancy measure): $\rho^{\pi}(s,a)=\mathbb{E}[\sum_{t=0}^T\gamma^tP(S_t=s,A_t=a)|\pi],\forall s\in S,a\in A$

用来表征我们有多大程度上忙于某个状态和动作。

在 MDP 中，我们有这两个定理：

Thm1: $\rho^{\pi_1}=\rho^{\pi_2}\iff \pi_1=\pi_2$

Thm2: 给定一个占用度量$\rho$，那么能够生成这个占用度量的唯一策略是$\pi_\rho=\frac{\rho(s,a)}{\sum_{a'}\rho^{\pi}(s,a')}$

从而，我们可以定义一个策略的累计奖励，即：$V(\pi)=\mathbb{E}_\pi[{r(s,a)]}$

MDP 中的目标：$\argmax_{\pi}\rho^\pi(s,a)r(s,a)$

### 策略评估(policy evaluation)和策略提升(policy improvement)

对于每一个状态，我们定义$V^{\pi}(s)=E_{a\sim\pi(s)}[Q^{\pi}(s,a)]$，这是状态的价值。

相关地，对于每一个动作，我们也可以相互地定义$Q^{\pi}(s,a)=r(s,a)+\gamma\sum_{s'\in S}P_{s\pi(s)}(s')V^{\pi}(s')$

如果对于任何一个状态 s, 有$Q^{\pi}(s,\pi'(s))\geq V^{\pi}(s)$， 那么，我们称 $\pi'$ 是 $\pi$ 的策略提升(policy improvement)。也就是说，考虑一种策略，它在当前状态下与原策略不同，后续却完全相同，但是奖励却更高（或不变）了，那么自然就是策略的一种提升。

这是因为通过上面的策略，可以导出$V^{\pi'}(s)\geq V^{\pi}(s)$(策略提升定理，Policy Improvement Theorem)

## Lec 4 动态规划

### 策略迭代

1. 随机初始化策略

2. 重复下列两步至收敛

3. 计算 $V=V^\pi$

4. 对每个状态，更新对应的$\pi(s)=\argmax_{a\in A}Q(s,a)$

这样做的问题在于，第三步是比较耗时的。

### 价值迭代

1. 对每个状态 s, 初始化 $V(s)=0$

2. 重复对每个状态，更新$V(s)=r(s)+\max_{a\in A}\gamma\sum_{s'\in S}P_{sa}(s')V(s')$

最优价值函数： $V^*(s)=\max_\pi V^\pi(s)$

最优策略就可以是：$\pi^*(s)=\argmax_{a\in A}\sum_{s'\in S}P_{sa}(s')V^*(s')$

价值迭代是一种贪心的更新方式。对于空间较小的 MDP，策略迭代收敛速度快；但 MDP 空间较大且没有状态转移循环，那么采用价值迭代。

### MDP 环境未知的处理

- 状态转移未给出

- 奖励函数未明确给定

先从数据中学习一个 MDP 模型。奖励函数定成每一个状态的期望奖励。从而算法也是相对比较明确的。

1. 随机化 $\pi$

2. 重复这 4 步至收敛：在 MDP 中执行 $\pi$

3. 用 MDP 中的累积经验更新对 $P_{sa}$ 和 $R$ 的估计

4. 计算新的函数 $V$\

5. 贪心地更新 $\pi$

还有一方式是不学习 MDP，直接从经验中直接学习价值函数和策略。

## Lec 5 值函数估计

### 无模型强化学习(model-free RL)

不去计算 $P_{sa},r$，而是直接利用一系列经验得到 $V^\pi(s)$

### 蒙特卡洛方法(Monte-Carlo methods)

在该方法中，我们也就是使用经验均值去代替了期望的均值。

实现：$V(s_t)\leftarrow V(s_t)+\alpha(g_t-V(s_t))$

它的缺点在于必须对数据采样完全。

### 重要性采样(important sampling)

$$
\mathbb{E}_{x\sim p}[f(x)]=\mathbb{E}_{x\sim q}[\frac{p(x)}{q(x)}f(x)]
$$

如果我们采用策略$\mu$产生的累积奖励去评估策略$\pi$,那么我们需要给累积奖励进行 **加权** 来降低偏差，即 $g^{\pi/\mu}_t=\prod_{i=t}^T\frac{\pi(a_t|s_t)}{\mu(a_t|
s_t)}g_t$

从而，更新实现为：$V(s_t)\leftarrow V(s_t)+\alpha(g^{\pi/\mu}_t-V(s_t))$

### 时序差分(temporal diffrence)

实现为：$V(s_t)\leftarrow V(s_t)+\alpha(\frac{\pi(a_t|s_t)}{\mu(a_t|
s_t)}(r_t+\gamma V(s_{t+1})-V(s_t))$

它的方差比 MC 方法联合重要性采样的方差更小。并且只需要进行一次的修正。这是因为排除了连乘的过大影响。

### 时序差分学习(temporal diffrence learning)

这种方法可以直接从经验的片段中进行学习，而不用像  MC 方法那样。实现为 $V(s_t)\leftarrow V(s_t)+\alpha(r_t+\gamma V(s_{t+1})-V(s_t))$ 

问题在于，它基于函数去更新函数本身，存在 bias！

它是出让了 bias 换取较小的 variance.

并且它的好处在于不一定要采样到最后。

MC 一般在快速采样下使用。但是 TDL 对于初始值更加敏感。

### 多步时序差分学习

也就是把原来的 $(r_t+\gamma V(s_{t+1}))$ 替换为了 $g_t^{(n)}=\sum_{i=t}^{n-1}\gamma^{i-t}r_t+\gamma^nV(s_{t+n})$

## Lec 6 无模型控制方法

基于 $V$ 函数，那么我们需要知道环境模型。但如果我们基于 $Q$ 函数，这就方便了。

### SARSA

对于每个状态，考虑一个五元组 $(s,a,r,s',a')$

从而可以有：$Q(s,a)=Q(s,a)+\alpha(r+\gamma Q(s',a')-Q(s,a))$

同样也可以使用 $\varepsilon-$ greedy 策略来做进一步更新。即一步的 TDL 方法再联合上这一方法。

在线策略时序差分控制(on-policy TD control): 使用当前策略进行动作采样。五元组中的两个动作都是根据当前策略进行选择的。

### Q 学习算法及其收敛性

是一种离线策略的更新方法。

首先，离线更便宜，更方便做。并且拓宽了可学习的数据量。

可以吸收旧策略中的经验。

特点：基于 $(s_t,a_t,r_t,s_{t+1})$四元组进行学习。不用 important sampling. $Q(s_t,a_t)\leftarrow Q(s_t,a_t)+\alpha(r_t+\max_{a'_{t+1}}\gamma Q(s_{t+1},a'_{t+1})-Q(s_t,a_t))$

它的想法：不再在新的状态下根据老的策略去计算。直接根据最高的 value 进行计算。采样的行为也不要和现在的行为差距太远。比如采取几步前产生的采样策略 Q-learning 一定可以收敛到最优函数。

悬崖漫步环境，发现 Q-learning 比 Sarsa 要差一些。 Q-learning 会考虑在悬崖边散步，因为它不会考虑那种损失很大的情况！

### 多步自助法

多步时序差分学习，实际上就是把奖励值改为多步。定义一个对应的累计奖励。 

使用多步的原因：一些稀疏奖励模型下不太容易得到奖励。可以更新到更多的状态对。

多步树回溯算法(N-step tree backup algorithm): 根据每一个分支是否已经被采样过的情况，进行计算。

## Lec 7 规划与学习

### 模型(model)

给定一个状态，模型能够预测下一个状态和奖励的分布 $p(s',r|s,a)$

模型可以分成分布模型和样本模型两种。模型可以用于模拟经验数据。

### 规划(planning)

也就是根据输入的模型，输出一个策略的过程。可以分成针对状态空间的规划，和根据规划空间的规划。

通过模型进行采样，得到模拟的数据。然后通过模拟的数据去更新值函数，从而改进策略。

世界模型

规划和学习的区别就在于经验是真实的还是模拟得到的。

### Q-planing

重复以下步骤：

1. 随机选择一个状态 $s\in S,a\in A$

2. 把 $s,a$ 输入采样模型，得到采样的奖励 $r$ 以及下一个状态 $s'$

3. 对四元组 $(s,a,r,s')$ 进行 Q-learning

### Dyna-Q 算法

根据真实经验，既更新值函数和策略，也强化模型。

重复以下步骤：

1. $s\leftarrow$ 当前状态

2. $a\leftarrow \epsilon-greedy(s,Q)$

3. 执行 $a$, 得到 $r,s'$

4. $Q(s,a)\leftarrow Q(s,a)+\alpha[r+\gamma\max_{a'}Q(s',a')-Q(s,a)]$

5. $Model(s,a)\leftarrow r,s'$

6. 重复根据模型执行 $Q$ 算法

问题：如何和环境采样？

均匀采样？不是很合适。

**优先级采样**。如果有的状态更新值很多，那么我们更应该在这部分去采样。 

选择期望更新还是采样更新？

期望更新更准确无偏。但是计算量大，需要分布模型。采样更新就很方便。

### 实时动态规划(RTDP)

规划只基于当前的状态。

Rollout 算法：从当前状态进行 MCL。 

## Lec 8 参数化值函数和策略

问题在于：如果我们的状态表非常大，为了维护每一个 $Q(s,a)$ 的开销就会很恐怖。

两种解决方式：

- 离散化或者分桶

- 参数化

分桶的好处：操作简单高效。

缺点：可能过于简单了。

第二种方式：构建一个可学习的函数来近似值函数，即：

$V_\theta(s)\simeq V^\pi(s),Q_\theta(s,a)\simeq Q^\pi(s,a)$

let $J(\theta)=\mathbb{E}_\pi[\frac12(V^\pi(s)-V_\theta(s))^2]$ 尽量小。这就转化为一个优化问题了。对于 $Q$ 函数，也是类似的。

### DQN 算法

 在第 i 轮上，对待当前的网络参数值，我们有：$L_i(\theta_i)=\mathbb{E}_{(s,a,r,s')\sim U(D)}[(r+\gamma\max_{a'}Q(s',a';\theta_i^-)-Q(s,a;\theta_i))^2]$

其中， $\theta_i$ 是在该轮迭代中将要更新的参数。 $\theta_i^-$ 是目标网络参数，其在 $\theta_i$ 每次更新 $C$ 步之后才更新。

这样做的好处，是可以一次性更新多个状态的估值。

### 策略梯度

将策略也跟着策略化： $\pi_\theta(a|s)=P(a|s;\theta)$

基于策略的 RL : 更容易收敛，大空间更有效，并且可以得到随机策略；缺点是容易被局部最优误导，方差比较大。

### 似然比（Likelihood Ratio）

利用下式，对策略的价值期望进行改写。

$$
\frac{\partial\pi_\theta(a|s)}{\partial\theta}=\pi_\theta(a|s)\frac{1}{
    \pi_\theta(a|s)}\frac{\partial\pi_\theta(a|s)}{\partial\theta}
=\pi_\theta(a|s)\frac{\partial\log\pi_\theta(a|s)}{\partial\theta}
$$

### 策略梯度定理

对于可微的策略 $\pi_\theta(a|s)$,有 $\frac{\partial J(\theta)}{\partial\theta}=\mathbb{E}_{\pi\theta}[\frac{\partial\log\pi_\theta(a|s)}{\partial\theta}Q^{\pi\theta}(s,a)]$

蒙特卡洛策略梯度 选择多条轨迹进行采样，用其平均值来得到一个经验的值。

### Softmax 随机策略

即：$\pi_\theta(a|s)=\frac{e^{f_\theta(s,a)}}{\sum_{a'}e^{f_\theta(s,a')}}$

## actor-critic

使用两个模块来做拟合。actor 和 critic 可以有着不同的损失函数。 

critic:尽量准确估计动作价值：$Q_\Phi(s,a)\simeq r(s,a)+\gamma\mathbb{E}_{s'\sim p(s'|s,a),a'\sim\pi_\theta(a'|s)}[Q_\Phi(s',a')]$

$J(\theta)=\mathbb{E}_{s\sim p,\pi_\theta}[\pi_\theta(a|s)Q_\Phi(s,a)]$

## Advantageous Actor-Critic

定义优势函数为 $A^\pi(s,a)=Q^\pi(s,a)-V^\pi(s)$

它的想法是进一步减去一个基线函数的值，这样可以出现负值。从而可以提高效率，降低方差。

## Lec 9 深度强化学习价值方法

### DQN

- 经验回放

- 双网络结构

经验回放：要尽量保证采样出的数据的多样性。

双网络结构，即前文中的 $Q$ 和 $Q^-$

### Double DQN

Q-learning 中存在过高估计。解决方式是使用两套独立的参数。一套用来采取行动，一套用来实际优化。即采用的 action 为 $\argmax_{a\in A}Q'(s,a)$

，但优化的和估值的才是 $Q$

### Dueling DQN

即：

$$
V^\pi(s)=\mathbb{E}_{a\sim\pi(s)}[Q^\pi(s,a)]\\
A^\pi(s,a)=Q^\pi(s,a)-V^\pi(s)\\
Q^\pi(s,a)=\mathbb{E}[R_t|s_t=s,a_t=a,\pi]
$$

通过这样的方式，把$Q$ 拆成两个部分$A$ 和 $V$。想法是网络模拟在 0 附近的值比较好。一般初始化的时候，也是初始化 weight 在 0 附近比较好。

$Q(s,a,\theta,\alpha,\beta)=V(s;\theta,\beta)+A(s,a;\theta,\alpha)-\frac{1}{|A|}\sum_{a'}A(s,a';\theta,\alpha)$

它更容易处理和动作关联比较小的状态的情况。

Double DQN: 解耦合了行动的选择和价值的估计。

Dueling DQN: 把 $Q$ 函数用多个模块进行模拟，精细化捕捉。

Q-learning 系列都是基于价值的 RL 方法。

### 确定性策略

$\pi(s;\theta)=\argmax_aQ_\theta(s,a)$ ：问题在于是不可微的。

同样，定义函数 $J(\pi_\theta)=\mathbb{E}_{s\sim\rho^\pi}[Q^w(s,a)]$

从而：$\nabla_\theta J(\pi_\theta)=\mathbb{E}_{s\sim\rho^\pi}[\nabla_\theta\pi_\theta(s)\nabla_a Q^w(s,a)|a=\pi_\theta(s)]$

### Twin Delayed DDPG(TD3)

一次跑两组初始化不同的参数 $Q$，挑损失函数值更小的做为学习目标。但两个在同时学习。并且，对于策略的输出 action 概率增加一个高斯噪声函数，从而减少过高估计。

## Lec 10 深度强化学习策略方法

对于随机的策略，则采样到每一个行动的概率有:$\pi_\theta(a|s)=\frac{e^{f_\theta(s,a)}}{\sum_{a'}e^{f_\theta(s,a')}}$

### A3C

AC 和 A2C 算法都是在寻找策略的提升点。

A3C: 异步(Asynchronous) A2C

这样做的原因是因为 Actor 需要大量的数据。有很多个 worker 和环境进行交互。然后每个 worker 计算出一个梯度。把梯度传回给 global worker 进行更新。

### TRPO

 策略梯度的问题：步长难以确定。

使用老策略抽样状态，但是对 action 进行重要性采样。

保证策略改进的单调性

### PPO(Proximal Policy Optimization)

进一步的改进 TRPO, 不需要重要性采样。

优势函数也进行时序差分。

把 KL 散度因子加入到损失函数中，并且自适应地调整其重要性的因子。

### Lec 11 基于模型的深度强化学习

DRL: low data efficiency

data $\to$ model $\to$ train

Model-based RL: may no need more real data once the model is learnt!

But there will be model compunding error.

off-policy methods are instable and require many datas.

This lecture focuses on blackbox model. 

- how to train the deep model

- the inaccurancy?

- How to use it effectively?

- data effeciency?

### Model Predicted Control

Generate a series of chains of actions on the models. Choose the first action of the best one. 

However, if the action sequences are randomly sampled, there will be higher variance and may not sample the high reward actions.

A refinement is Cross Entropy Method(CEM), sampling actions from a distribution closer to the high-reward actions sampled before, but leads to a larger variance.

### Probabilistic Ensembles with Trajectory Sampling(PETS)

uncertainty can be divided into two parts:

- epistemic uncertainty(some data is missing!)

- aleatoric uncertainty(datas are uncertain!)

PETS:  From (s,a) pair sampled before,  generating mean and covarience to generate $P$. i.e. we build a better model.

It's a way to build model.

### MBPO

When to trust our models?

model-based policy optimization

use the branch rollout to optimize the model.

### Bidirectional Model

This method is to reduce compounding error. 

To the past and the future can reduce the error. 

The biggest problem is the gap between our model and the real model.

**AMPO**

### Lec 12 Imitation Learning

If there isn't a reward?

The easiest policy is behavior cloning, i.e. according to what do humans do and take actions.

How to define loss functions?

- Behavior Cloning(BC)

- Inverse Reinforcement Learning(IRL)

- Generative Adversarial Imitation Learning(GAIL)

BC is very easy, but can leads to catastrophic error.

expert advise $\to$ reward

## Lec 13 Offline RL

The problem is that some data will never appear.

AWR

MOReL
