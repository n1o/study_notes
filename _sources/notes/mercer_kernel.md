# Mercer (positive definite kernels)

Some methods require that the kernel function satisfy the requirements that the **Gram matrix**:

$$
K = \begin{pmatrix}
    \mathcal{k}(x_1, x_1) & \cdots & \mathcal{k}(x_1, x_N) \\
    & \vdots & \\
    \mathcal{k}(x_N, x_1) & \cdots & \mathcal{k}(x_N, x_N)
\end{pmatrix}
$$

Is positive definite for any set of inputs $\{ x_i\}_{i=1}^N$. We call such a kernel a **Mercer kernel** of **positive definite kernel**.

Importance of this theorem is that, we can perform eigen value decomposition on the Gram matrix to get:

$$
K = U^T \Lambda U \\ 
k_{ij}= (\Lambda^{1/2} U_{:,i})^T(\Lambda^{1/2} U_{:,j})
$$

We can define $\phi(x_i) = \Lambda^{1/2}U_{:,i}$ than:

$$k_{ij} = \phi(x_i)^T(x_j)$$ 

Entries in the kernel matrix can be computed by performing an inner product of some feature vectors that are implicitly defined by the eigenvectors U.

In general if the kernel is Mercer, then there exists a function $\phi$ mapping $x \in \mathcal{X}$ to $R^D$ such that:

$$\mathcal{k}(x,x') = \phi(x)^T\phi(x')$$

* $\phi$ depends on the eigen functions of $\mathcal{k}$ (so D is a potentionally infinte dimension space). 

In general, establishing that a kernel is a Mercer kernel is difficult, and requires techniques from functional analysis. However, one can show that it is possible to build up new Mercer kernels from simpler ones using a set of standard rules. For example if $\mathcal{k_1}$ and $\mathcal{k_2}$ are booth Mercer so is $\mathcal{k}(x,x') = \mathcal{k}_1(x,x') + \mathcal{k}_2(x,x')$.