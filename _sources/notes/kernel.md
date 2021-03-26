# Kernel function

We define a **kernel function** to be a real-values function of two arguments 

$$
    \mathcal{k}(x, x') \in R \\
    x,x' \in \mathcal{X}
$$

Typically the function is symmetric, and non-negative, so it can be interpreted as a measure of similarity. (But this is not required)

## RBF (Gaussian) Kernel 
Also known as **squared exponential kernel** (SE). We can view it as template matching where x associated with y becomes a template for y. If a test point $x'$ is close to x in euclidean distance the Gaussian kernel has a large response indicating $x$ and $x'$ are similar putting large weights on the association to training label $y$.

$$
\mathcal{k}(x, x') = \exp(- \frac{1}{2}(x - x')^T\Sigma^{-1}(x - x'))
$$

In case that $\Sigma$ is diagonal we can simplify

$$
\mathcal{k}(x, x') = \exp(- \frac{1}{2}\sum_{j=1}^D \frac{1}{\sigma^2_j}(x_j - x_j')^2)
$$

* $\sigma_j$ can be interpreted as defining the **characteristic length scale** of dimension j. If $\sigma_j = \infty$, the corresponding dimension is ignored, hence this is known as the **ARD kernel**. 

If $\Sigma$ is spehrical, we get the isotropic kernel. (This is an example of a **radial basis function**, since it is only a function of $||x - x'||$)

$$
\mathcal{k}(x, x') = \exp(- \frac{||x - x'||^2}{2\sigma^2})
$$

* $\sigma^2$ is known as the bandwidth

## Cosine similarity
$$
\mathcal{x_i, x_{i'}} = \frac{x_i^Tx_{i'}}{||x_i||_2 ||x_{i'}||_2}
$$

Here we measure the cosine of the angle between two vectors. This is bounded to be within 0 and 1.

We can extend this to [compare documents](tf_idf_kernel.md).


## [Mercer kernels](mercer_kernel.md)
Sometimes kernel function have to be positive definite.

## Linear kernels

$$
\mathcal{k}(x, x') = \phi(x)^T\phi(x') \\ 
\phi(x) = x \\
\mathcal{k}(x, x') = x^Tx'
$$

This kernel is especially usefull if the data is high dimensional. In such case, the decision boundary is likely to be represented by a linear combination of the original features. 

## Matern kernels
Commonly used in Gaussian processes regression and has the form:

$$
\mathcal{r} = \frac{2^{1 - v}}{\Gamma(v)} (\frac{\sqrt{2v}r}{l})^v K_v(\frac{\sqrt{2v}r}{l})
$$
* $r = ||x - x,||$

* $v > 0$
* $l > 0$

* $K_v$ is a modified Bessel function

As we take $v \rightarrow \infty$ this approaches the SE kernel. If $v = 1/2$ the kernel simplifies to 

$\mathcal{k}(r) = \exp(-r /l)$

If $D=1$, and we use this kernel to define a Gaussian process, we get the **Ornstein-Uhlenbeck process**, which describes the velocity of a praticle undergoing Brownian motion. 