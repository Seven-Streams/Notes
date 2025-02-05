# Machine Learning Compilation

## Lec 1

### Why MLC?

For applications, we need a broad coverage.

At now, we may need run our model on many different systems.

#### Machine Learning Deployment Problem

The problem is the gap between intelligent applications and deployment environments.

The environments are much more diverse now. We must consider the hardware, OS and so on.

To solve the problem, we start to consider MLC.

### What's MLC?

MLC is the procession that transform the development form(pytorch e.g.) to the deployment form(API interface ...).

### MLC Goal

- Integration and Dependency Minimization

- Leverage Hadrware Native Acceleration

- Optimization in General

### Some remarks

MLC may not involve code generation.

Deployment form may also need training.

### Reason to study MLC

- Build ML Demplyment Solution

- In-depth Understanding of Existing Frameworks

- Builld Software Stack for Emerging Hardware

- Have fun

### Key Elements in MLC

Tensor and Tensor functions

**Kernel Fusion**(算子融合) to reuduce the calculation time.

Abstraction and Implementation

Higher abstracion is implemented by lower abstracion

The implementation of a higher abstraction can be seen as a lower abstraction, which leads to more chance to optimize.

## Lec 2 Tensor Program Abstraction

### Primitive Tensor Function

Primitive tensor functions can be seen as the single units of computational operation.

e.g. torch.add is a primitive tensor function.

Problem: How to implement a primitive tensor function?

#### some feasible approches

- remap to library calls(e.g. cuda)

- fine grained program transformation

### Tensor Program Abstraction

#### Key Elements of a Tensor Program

- **buffers** to holds data

- **Loop nests** to compute

- **Computations**

#### Why TPA?

Carefully design -> better performance.

- Loop Splitting

- Loop Reordering

- Thread Binding

primitive tensor functions usually don't allocate memory to save time.

## Lec 3

In numpy, `a @ b` = `np.matmul(a, b)`

low-level numpy:

- use a loop instead of array functions when necessarey

- explicitly allocate arrays via numpy.empty and pass them around

`np.testing.assert_allclose(A: np.ndarray, B:np.ndarray, rtol: float32)` is used to check whether the values of two ndarray are the same.

In matmul, spatial axis will appear in the output as an axis, while reduce axis will disappear. These information sometimes can help do optimization.

TensorIR

## Lec 4

The view of computational graph

`call_tir` : used for purify functions

destination pass: destination will be seen as a para provided for functions.

pure function and side effectful

`dataflow()`: used to indicate the codes of a computational graph

## Lec 5

Problem:Sometimes we can't determine which factor is proper.

Solution:Use a stochastic method.

Idea: Only focus on the most important part.

## Lec 6

tensor expression

how to optimize models from pytorch

torchfx module

## Lec 7

Some global memory may be used by several threads. A solution is to read these data once, and transport them in shared memory.(cooperative fetching)

## Lec 8

specialized hardware

- special store

- special operator(tensor intrinsic)

- some copy

tensorization

# 
