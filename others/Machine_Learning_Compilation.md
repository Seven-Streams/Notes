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
