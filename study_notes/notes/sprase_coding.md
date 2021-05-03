# Sparse coding
* [linear factor model](linear_factor_model.md) that has been studied as unsupervised feature learning and extraction
* we assume that linear factors have Gaussian noise with isotropic precision $\beta$

$$
p(x|h) = N(x; Wh + b , \frac{1}{\beta}I)
$$

$p(h)$ is strongly peak at 0 like a Laplace, Student or Cauchy. 

The encoder is an optimization problem defined as:

$$
h^* = f(x) = \argmax_h p(h|x) \\ 
\argmax_h \log p(h|x) \\
= \argmin_h \lambda ||h||_1 + \beta ||x - Wh||^2_2
$$

In training we alternate between minimizing $h$ and $W$, which booth are convex.