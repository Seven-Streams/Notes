# Lec 1

由于词的数量过大，所以独热编码是不合适的。我们将词表征为一个实值多维向量，用来表征词与词之间的联系性。这被称为单词嵌入。

word2vec算法。对于每一个中心词，去预测哪些词语更有可能出现在上下文中。这一点是通过词向量的点积实现的。每个词有两个词向量，一个是作为中心词的，一个是作为非中心词的词向量。将中心词的向量与所有词作点积，并进行softmax，得到结果。在高维空间中，词会在不同的维度上相互靠近。

# Lec 2 Word Vectors, Word Senses, and Neural Network Classifiers

在词向量的基础上，我们需要考察如何得到好的词向量。所以要进行梯度下降优化。首先，将词向量初始化为接近0的随机向量。

简单的梯度下降算法显然是不合适的。因为量太大了。所以SGD常常被使用到。

神经网络在一定条件下是**反直觉的**。

在随机梯度下降的过程中，梯度更新的矩阵对象是很稀疏的。

note:大多数词向量在torch等中都表示为行向量。

为什么给一个单词对应两种不同情况下的单词向量？因为如果只有一个向量，文本窗中出现了两次这个单词，就会引入二次项，不利于优化的计算。

## skip-gram model with negative sampling

问题：在计算朴素的softmax函数时，必须要遍历词表，计算之。

这里，简单地解决方法就是把softmax换成sigmoid。并且，将损失函数的计算改为随机取样K个词。

$$
J=-\log\sigma(u_o^Tv_c)-\sum_{k\in K}\log\sigma(-u_k^Tv_c)
$$

这个损失函数在直觉上，就是用一种粗略的方法去模拟softmax进行的工作。也就是说，我们希望正确的事情，点积比较大。错误的比较小，从而等价于softmax后的结果。

## Co-occurrence vectors

共现向量是巨大而又稀疏的。

**SVD**，并且删除那些作用较小的一些奇异值，从而降低维度。也就是类似于截断SVD（也许就是？）的方法。

同类类比过程中，向量值大小方向相近。

考察词语的共现比率。

我们如何能够得到它们的共现比率，并且使之具有线性化特征？

目标：拟合$w_i\cdot w_j=\log P(i|j)$

也就是说，我们通过点积这种运算来拟合了共现概率。

Note:看到有其他采用互信息的方法进行构建的词向量(PMI),看上去更加合理。即考察：

$$
\frac{P(x,y)}{P(x)P(y)}
$$

## word vector evaluation

两种，内部的和外部的评估。

内部评估，比如考虑单词类比这种类型。

## word senses and word sense ambiguity

# Lec3: Gradients by hand and algorithmically

例子：命名实体识别(NER)

## Matrix Calculas

Jacobian矩阵。

$$
f(x)=[f_1(x_1,...,x_n),...,f_m(x_1,...,x_n)]\\
(\frac{\partial f}{\partial x})_{i j}=\frac{\partial f_i}{\partial x_j}
$$

在反向传播的过程中，根据链式法则，有很多东西，我们不必**重复计算**。

因为根据Jacobian矩阵的定义，如果我们只有一个输出，考虑对$W$进行优化，那么我们得到的Jacobian矩阵应该是一个$(1,mn)$形状的矩阵。不利于我们进行优化。所以，我们要对Jacobian矩阵进行变形。

## Backpropagation

玉川有一个不成熟的想法。在取ReLu为激活函数的时候，那些数值基本都没有更新。我们能不能改善这一点，加快模型的更新速度？

反向传播和正向传播应当有相同的时间复杂度。

自动微分：利用的就是反向传播算法。对每一个节点进行拓扑排序，之后可以得到结果。显然，我们需要先进行正向传播，才可以进行反向传播。

梯度下降不是万能的。

# Lec 4

## linguistic structure

词性，和限定词(determiners)

phrase structure grammars:最小单位由词变为了短语。

phrase的构建

constituency grammars:上下文无关的语法。就是那种短语结构的方式。句子不会影响短语本身。

dependency grammars:依存于句子结构之上的语法。

在近二十年，dependency grammars更加被使用。简单地说，他的思路就是要考察，每一个词语，有多大程度上去修饰了某一个对象。使用通用依赖关系中，我们认为介词依存于之后的中心名词，然后再次构成短语。

问题在于，短语之间的依存关系可能具有一定的歧义。

同时，自然语言中还有一个常见的语义歧义是作用范围的模糊。

依赖关系应当构成**一棵树**。

依赖关系箭头绘制是，由被依赖对象(head)指向依赖词(dependent)。

Treebanks:语法库。个人的理解，就是一个标的还不错的数据集。

依赖关系怎么判断：

- 依赖词和被依赖词本身

- 距离

- 一般依赖关系不会跨越动词或者标点

- 被依赖对象的配价（即考虑词性本身的特点。比如你不会在cat后面添加一个the之类的）

在解析过程中，我们会添加一个root标记，使得只有一个词从属于root。然后，我们不希望在处理过程中产生回环。

如果在投影弧都在句子上方，并且没有产生交叉，那么我们就称，这杨的一个句子解析是一个投影解析。

## trainstion-based dependency parser

parser由$\sigma$堆栈，右侧为顶；$\beta$队列，左侧为顶；依赖弧集合$A$，和一系列shift和reduce动作构成。

首先：

$$
\sigma=\text{root},\beta=w_1,...,w_n,A=\empty\\

$$

 然后，我们有三种动作可以选择：

1. shift:$\sigma.\text{push}(\beta.\text{pop()})$

2. Left-Arc-reduce:$A.\text{insert}(r(\sigma.\text{top}, \sigma.\text{second})),\\ \text{res}=\sigma.\text{top}\\\sigma.\text{pop}(),\sigma.\text{pop}()\\ \sigma.\text{push}(\text{res})$

3. Right-Arc-reduce:$A.\text{insert}(r(\sigma.\text{second}, \sigma.\text{top})),\sigma.\text{pop}()$

直到$\beta=\empty$

其中，二元组前者为head，后者为dependent。

我们要保证经过reduce操作后，head依旧在stack中。

# Lec 5

句法依存分析下特征的问题：稀疏和不完整性，并且计算代价高昂。

单词嵌入。

词性标签和依赖标签。

深度学习分类器是非线性的分类器。

这些是为什么要采用深度学习作词法依赖解析器的原因。

对于单词，在输入之前，我们要用独热编码，找到词及其词性的特征向量作为输入。

另一种词法依赖解析器是基于图的词法依赖解析器。也就是考虑每一对词之间，它们之间存在某一项解析关系的概率。问题在于，复杂度是二次项级别的，比较慢。

最经典的正则化显然是L2，现在暂退的使用也很多，可能是目前最好的方法。暂退的好处在于，可能L2会对不同的参数产生不同的约束强度，从而降低对某些特征的识别。

暂退可以避免特征联合效应。

使用向量，矩阵，张量，而不是循环。

单纯的线性层叠加，可以视作是一个线性变换。

$$
\text{tanh}(x)=2\text{logistic}(2x)-1\\
\text{hardtanh}(x)=x,x\in [-1, 1];-1,x<-1;1, x>1
$$

ReLU应该是目前激活函数中的首选。

参数初始化：在**几乎所有**情况下，必须要用小的随机值去初始化参数。因为如果是全零矩阵，那么就是对称的情况，学不到很特殊的内容。但偏置设置为0是无伤大雅的，可能是更好地方案。

Xavier初始化：该层的初始化方差为$\frac{2}{n_{in}+n_{out}}$

一般而言，使用SGD结果还可以。但是，需要考虑学习率。如果使用Adam，它是自适应的，效果可能更不错。

在训练过程中，尽量对训练集进行shuffle，避免使模型陷入一种周期律的幻想当中。

## Language Modeling

预测下一个单词是什么。

n-gram Language Models

非常简单。思想就是收集每一个不同大小的词块出现的概率。

我们首先进行马尔科夫假设，即假定下一个词的概率仅和之前的n-1个词语有关。

这样的问题在于，我们很多时候在数据集中找到这样的对象。所以并不是很好。一种方式是给每一个词语在该条件下添加一个增量$\delta$.而且，可能前n-1个词语的序列亦未曾出现，我们就要考虑缩短我们依赖的单词数。

RNN的好处在于，模型可以学习到序列性的信息，并且可以充分运用已有的文本。

# Lec 6

"Teacher forcing"

我们的损失计算，在每一步长中，我们只预测一个单词，并对这个单词进行惩罚。但是，如果模型选择的输出不够好，我们选择采用**语料库**中的输入继续训练。

在朴素循环神经网络中，我们不能在反向传播中即修改$W_h$

为了能从零开始生成一个句子，我们可以添加一个开始标记，将其作为第一个输入，投喂给RNN。

模型好坏的评判：困惑度(perplexity)

$$
\prod_{t=1}^T(\frac{1}{P_{LM}(x^{(t+1)}|x^{(t)},...,x^{(1)})})^{\frac{1}{T}}
$$

等价于指数形式下的交叉熵损失。

RNN可用于预测下一个词的词性，可以**识别句子的情绪**。

我们考虑一个矩阵，如果它的所有特征值都小于一，我们取其特征向量为一组基，求梯度后需要对特征值取次方，所以可能使得梯度消失。

类似的，也会有梯度爆炸的问题。所以，我们可以给梯度更新设定一个上限值。

LSTM不能完全解决梯度消失和爆炸的问题。但总体好得多。

实际上，现在LSTM也开始被Transformer取代了。

残差神经网络，也是为了解决长距离梯度消失的问题导致的。

DenseNet，HighwayNet

# Lec 7

## Pre-Neural Machine Translation

在1990~2010之间，基本是采用统计学方法。即根据大量的平行语料，计算条件概率。

如何根据平行语料去计算条件概率？我们要引入一个**对齐变量**，从而确保每一个单词（短语）二元组之间有着合理的对应关系。对齐关系可是多对多的。

机器需要学习这些对齐关系。对齐变量也是个潜在的变量。

翻译过程的选择公式：

$$
\text{argmax}_yP(x|y)P(y)
$$

其中，y是我们翻译的结果，x是待翻译的对象。这是根据贝叶斯公式导出的，等价于$P(y|x)\cdot1$

上式中，前一个条件变量由一个翻译模型控制，后一个由我们构造的一个目标语言模型控制。

在翻译过程中，我们将句子拆成一个个部件，如积木一般。然后将其都尝试一下，看看组成句子的概率是不是够高。然后，挑选较高的几组选择。

这样的模型很复杂，并且包含了很多人类智慧。

## Neural Machine Translation

seq2seq模型

包含两个RNN。一个将源句子进行编码。剩下一个则是根据中间状态，将其解码为目标语言。

在解码过程中，我们也要用teacher forcing方式进行训练。

s2s可以做很多事情。比如概括，比如对话，比如语法解析、比如代码生成等等等 。

s2s会从零开始，搭建一个句子。  它是一种条件语言模型。

多层RNN(stacked RNN)

对于编码器，2~4层为佳；对于解码器，4层更好。

如果想要更多的层数，我们需要跳过层（残差层之类）和稠密层来保证深度较高的情况下的效果。

解码的算法：第一种，贪心法。但显然不是很好。我猜可能采用束搜索之类的方法？（诶嘿，猜对了）

束搜索的停止：时间步达到上限，或者已经有一定个完成的假设答案。

显然，如果序列更长，它的得分大概是会下降的。处理这个问题的方式，是将得分对长度进行归一化。

神经网络的训练更快，更流利，对文本的运用更好，对短语相似性的利用更好。作为一个整体的神经网络系统，对这样端对端系统进行优化可能是较好的。

但问题是解释性差，不容易被控制。

使用BLEU来对机器翻译进行评分。对句子进行人工翻译，根据机器翻译和人工翻译之间的相似性评分。比如n-gram准确性，对过短的翻译给惩罚。但显然，一个句子可以有多种翻译方式，BLEU并不是非常准确。 

无人称指代时，系统会带有偏见。这样当时数据集本身所导致的。

## attention

s2s中的问题：必须将原有句子转化为一个隐状态。

解决方法：每一级RNN和当前编码器状态得到一个注意力得分，明白大概要把注意力放在哪里。

# Lec8 Self-Attention and Transformers

## Self-Attention

issue:线性交互距离可能过长。

GPU尽管可以并行计算，但在多层RNN中，有一些严格的拓扑序，影响了并行性。计算时间复杂度为$O(n)$

attention考察把每个单词的表示视作是一个询问。 所以，它可以解决长线性交互距离，和并行性计算的问题。

具体细节：将一个单词嵌入，然后和询问矩阵相乘得到询问向量，和键值矩阵相乘得到键值向量，和值矩阵相乘得到值。 

然后，计算询问和所有键值之间的相似性。

一种方式，是和所有点积，然后求softmax

 但是，这样忽略了位置的信息。所以，我们可以为每一个句中编号添加一个位置向量，用来进行指示。只需要在第一次输入时修饰这些嵌入向量以位置向量即可。 

位置向量是一个d维的向量。对于位置向量，表示方式是$p_{2n}=\cos(i/10000^{n/d}),p_{2n-1}=\sin(i/10000^{n/d})$

但是这样效果不是很好。

目前一种更可行的方式，可能是考虑一个$d\times n$的矩阵，用它来转换信息。其中，n是最长的句子。也就是说，不能有超过n的句子。（但这个问题应该不是很难解决？）

为了提高准确性，可以通过MLP和self-attention的结合。

在解码器过程中进行self-attention，我们需要保证我们不会**预知未来**。需要给那些未来的单词添加掩码。对那些未来的点积，强制计算为-INF。

## Transformers

最重要的一个差别之一：使用多头注意力层。multi-head self-attention.

首先，令$X$为序列嵌入向量的合并。

$XQ(XK)^T$实际上就是在计算得分。

我们假设有$h$个注意力头，令$Q_i,K_i,V_i\in\R^{d\times\frac{d}{h}},i\in\{1,...,h\}$

对于每一部分，我们单独地应用self-attention。输出为$\text{softmax}(XQ_iK_i^TX^T)*XV_i$

让每一部分的输出进行列连结，再乘上一个矩阵$Y\in\R^{d\times d}$，得到最后的总输出。它的想法是让每一个头关注一部分，然后共同作用得到一个结果。

scaled dot product：如果向量维数d比较多，那么点积可能会比较大，通过softmax之后，导致梯度会比较小，降低学习的效率。所以，将原有的输出改为

$$
\text{softmax}(XQ_iK_i^TX^T/\sqrt {d/h})*XV_i
$$

在Transformers架构中，经过多头注意力后，会有一个残差层，然后会进行层归一化。层归一化，指的是计算层间所有值的平均值$\mu$，计算标准偏差$\sigma$，记输入为$x$,额外三个常数$\epsilon,\gamma,\beta$,那么输出为$\frac{x-\mu}{\sqrt\sigma +\epsilon}*\gamma+\beta$

# Lec9 Pretraining

过去,将未见过的单词全部映射到UNK这个token上。

byte-pair压缩算法：可以以每一个字母为单位，作为初始值。每一次，合并语料中出现的，相邻概率最高的两个token将会被合并，直到词表规模达到我们想要的情况。会尝试选择数量最少的子词来表示一个单词。

## language modeling

通过之间说的方式进行预训练一个基本的预测模型。之后，在我们自己的问题和任务上进行微调(finetune)。留下Transformer，去掉最后一个线性层，重新训练之。

目前这种方式的优势原理还没有很好的解释。目前的说法还是非常直觉化的。

Encoder不可以直接用于语言建模。因为这会提前暴露下文。使用屏蔽的方法，去构建上下文表示，屏蔽大部分随机的单词。

## BERT

Masked LM 4 BERT：随机预测约15%的token。选择大部分进行mask操作，部分不变，部分随机替换为其他单词。

## finetune

第一种，是全盘接受网络的参数。

第二种，是对参数进行轻量级的优化。

一种方式是进行前缀微调，prefix-tuning，也就是在网络前加入一些新的前缀可学习参数。

一种方式可进行low-rank adaptation,即控制学习的内容是一个低秩的矩阵。

## encoder-decoder

Input中进行一定的mask，在输出的时候尝试输出结果。

## decoder

decoder只能看到当前的情况，不可以看到之后的信息。

# Lec10

 zero-shot and few-shot

chain-of-thought

COT比少量样本的作用大得多。

指令微调

RLHF

# Lec11 Neural Language Generation

NLU&NLG

不同NLG任务的自由度不同。非开放式生成（机器翻译之属），开放式生成（故事生成等）。

非开放式生成，一般采用encoder-decoder架构。encoder可以是一个双向LSTM，decoder可以是一个autoregressive LSTM。

开放式生成可能不太适合用这种方式去解决。开放式生成存在一定的自放大效应，即对一些token不断重复之后，导致错误结果的连续出现。从另一个方面想，这说明模型学习了这种重复。一种解决方式是禁止n-grams的短暂阻塞。更好的方式，是在函数训练阶段即降低这种情况的得分。

利用束搜索，来始终挑选概率最高的字符串作为输出并不是一个非常好的方式。因为如人类那般，生成的文本会有比较大的概率波动。一种方式是在decoder中引入一定的随机性。

策略是使用top-k sampling，选择概率最高的一部分。

更好的方式：top-p samping， 相当于根据分布，动态地调整k的值，可以设定一个概率的阈值下界。

需要注意的是，基于n-gram方式进行计算重叠度量并不是一种好的方法。

# Lec12 Question Answering

# Lec13 Coreference Resolution

  Coreference Resolution,指的是识别出段落中所有的指代。

split antecedents:比如they的指代关系。

发现指代、分配指代。

Coreference:共指，两个指代指向同一个实体。

Anaphora:回指，一个指代依赖于之前出现过的指代，二者指代对象相同。

Bridging Anaphora:一个指代依赖于之前出现过的指代，但是该指代的对象并非前一指代的对象，而是前一指代对象的某一部分或延伸附属等。

解决方法：

1、规则解析(Hobbs' naive algorithm)

基于现实知识的改进

2、指代对

3、神经网络(end-to-end)

4、BERT

# Lec14 Connections Between NLP and Linguistics

## Language Structure

grammaticality

e.g:英语中的SVO order

syntactic rules and lexicion

new word with similiar structure(phonotactics)

英语中的doer-patient结构

Multilinguality

# Lec15 Knowledges

模型会产生错误的合理回答。

原因可能是模型未见过，或少见；也有可能是因为对语气过于敏感。

传统知识图：主体、客体、关系。

entity linking 把问题中的实体连接到对应的真正实体。，也就是进行entity embedding

实体嵌入的方法有指示图嵌入(knowledge graph embedding)

词-实体共现(word-entity co-occurrence)

Transformer

KGLM:Local LG 局部的知识图。

kNN-LM：Nearest Neighbor Language Models

WKLM

How to evaluate knowledge in LM

# Lec16 Multimodality

多类型的输入

McGurk effect("ba" and "fa")

不同数据来源的信息。

Bag of visual words

skip-gram

GAN

特征化图片

Multimodal foundation models

# Lec17 Model Analysis and Explanation

模型推理不同逻辑下的问题：

1、词法分析重叠(如主动、被动间的推理关系会出错)

2、子序列(如短语修饰的名词后跟动词)

3、组成(如假设关系中的前提条件)

带有引诱物的测试集

# Lec18 The future of NLP and DL

人类语言在一定程度上具有合成性。
