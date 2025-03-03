# CS2916 LLMs

## Lec1

### 引言

- Generative Pretraining(vectors)

- Prompting Engineering

数据标注 $\to$ 数据合成

### NLP 基础

Challenges:

- 多义性(ambigious)

- 递归性(recursive)

- 结构复杂性(complex)

Tasks:

- Text to Label

- Text-Span to Label(A union of text and a span)

- Text-Text to Label

- Text to Labels

- Text to Text

- Text to Tree

- **Word Prediction**

Feature $\to$ Architecture $\to$ Objective $\to$ Prompt

## Lec 2

Fine-tuning 

Prompting

ML is to find a mapping!

Three Concepts of ML:

- Model

- Learning Policy

- Optimization(SGD is often used in LLMs)

self-supervised training

GD vs SGD

training set, validation set, test set

SGD and batch GD

Optimization and Normalization(decay, SGD, early stopping)

Some h-paras:

- gradient_accumulation

- weight_decay

- warmup_ratio

MLPs

LLMs automatically extract features!

### NN and DL

The Bitter Lesson

Activation Functions

ReLU, tanh,  Sigmoid

gradient vanish

h-paras, learning paras, status values

inductive bias

No-Free-Lunch-Law

## Lec 3

RNN: difficult to be parallelled, and the long-distance dependencies are difficult to be catched.

Gradient boom: use gradient clipping to ensure the gradient is in a proper range.

LSTM

BERT

ResNet

Highway Network

CNN  kernel, step, padding, 

Narrow CNN, Equal CNN and Wide CNN.

Multi-kernel CNN

Pooling, max pooling may be the most common one.

Pooling is a **great** way to reduce dimensions.

LM

We use $\prod_{i=1}^nP(\omega_i|w_1,w_2,...)$ to judge whether a model performs well or not.

## Lec 4

### NMT

encoder-decoder model

When decoding, the output token will be re-input in the model.

seq2seq: input tokens as a sequence, and the outputs are in a sequence too.

Attention and RNN

LSTM: Consider the situation that a key word is in the middle of the setence.

gradient vanishing and gradient exploding: the problem of long-term dependency

A easy way is to  use a max-pooling to the all $h$ in the models.

Attention Mechanism: the key point is that it build a direct connection between the input and the output.

RNN with attention:  $s_i=f(s_{i-1},y_{i-1},c_i)$, where $c_i = \sum_{j=1}^N\alpha_{ij}h_j$, $y_{i-1}$ is the last output token, and $s_{i-1}$ is the last value.

Self-attention: attention embedded in encoder-encoder, which can be seen LSTM with a better output way: use a weight matrix to measure the significance of the all tokens. Multi-head self-attention.

Further more, we don't use RNN, and add positional embedding code.

### Transformer

QKV

$$
\text{Attention}(Q,K,V)=\text{softmax}(\frac{QK^T}{\sqrt {d_k}})V
$$

In transformer, we will let $\text{head\ numbers} \times \text{head\ dimension} = \text{input dimension}$, which is helpful for calculation: since we'll use many layers of Transformer, we want lwt the input and the output have the same dimension, which does coding a favor.

Position Encoding: use cos and sin. However, as for as I know, RoPE is much more common today.

### Decoder-Only LLMs

When decoder, is self-regressive.

GPT-3

SFT(supervised fine-tuning), RLHF(reinforce learning)

Use human data to build a reward model. PPO

language generation

in-context learning

world knowledge

SFT: answer the question;generlization; code generation; CoT.
