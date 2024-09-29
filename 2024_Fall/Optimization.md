# Optimization

## Lec 2

Weierstrass极值定理：

$$
S\ \text{is compact},f:S\to\R\text{ is continuous on }S,f \text{ is bounded and has both}\\
\text{min and max values.}
$$

方向导数：

$$
\nabla_vf(x_0)=\lim_{h\to 0}\frac{f(x_0+hv)-f(x_0)}{h}
$$

偏导数就是取单位向量。

可微：

$$
\lim_{x\to x_0}\frac{||f(x)-f(x_0)-J(x-x_0)||}{||x-x_0||}=0
$$

其中，$\text{d}f(x_0)=J,\nabla f(x_0)=J^T$

一般地，有：

$$
\nabla_vf(x_0)=\nabla f(x_0)^Tv
$$

一阶必要条件：

$$
f\text{ is diffenrential, }\text{for any feasible direction }v,\nabla_v f(x^*)\geq 0
$$

如果$x^*$是个内点，那么上式应为$\nabla f(x^*)=0$

Schwarz's theorem：

$$
f:\Omega\subset\R^n\to\R,x\in\Omega \text{ s.t }B(x,\varepsilon)\sub\Omega,f\text{ has continuous }\frac{\partial^2f}{\partial x_ix_j}\\
\text{forall }i,j,\text{then }\frac{\partial^2f}{\partial x_ix_j}=\frac{\partial^2f}{\partial x_jx_i}
$$

二阶必要条件：

$$
f\text{ is twice continuously differentiable, }\forall v\in\R^n\\
v^T\nabla^2f(x^*)v\geq 0
$$

Sylvester's criterion:

- $A$ 是正定的，等价于所有顺序主子式大于零。

- $A$ 是半正定的，等价于所有主子式不小于零。

- 如果所有顺序主子式大于零，且$\text{det}(A)\geq0$，那么$A$ 是半正定的。

二阶充分条件：

$$
f:\R^n\to\R\text{ is a twice continuously differentiable function, }\\
\nabla f(x^*)=0,\nabla^2f(x^*)>0
$$
