# Algorithm

## Introduction

Turing machine is a Triple $(\Gamma,Q,\delta)$

Church-Turing Thesis: an effective method iff it's computable by a Turing machine.

Halt Problem

- Divide and Conquer

- Graphs

- Greedy

- Dynamic Programming

- Max Flow

- NP-hardness

- Advanced Problems

NP and P

NP-complete problem

Approximation Algorithms

Online Algorithm: how to evaluate:$\forall \text{ input }A(\sigma)\leq \Gamma\cdot OPT(\sigma)$

Ski-rental

## Divide and Conquer and Running Time Analysis

### Integer Multiplication

Divide a multiplication problem into two smaller problems!

#### Karatsuba Algorithm

$$

(a*10^\frac{n}{2}+b)(c*10^\frac n2+d)=ac*10^n+(ad+bc)*10^\frac n2+bd\\

=ac*10^n+((a+b)(c+d)-ac-bd)*10^\frac n2+bd
$$

Try to down the calculation!

#### Better algorithms

Toom-Cook: $O(n^{1.465})$，break it into 5 $\frac n3$-size problems

### Matrix Problems

#### Srassen's magical idea


