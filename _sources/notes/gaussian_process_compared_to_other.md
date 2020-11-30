# Comparing gaussian processes to other models

## Lienar regression Models
If we have a bayesian linear regression for D-dimensional features, with prior weights $p(w) = \mathcal{N}(0, \Sigma)$ the posterior can be expressed as:

$$
p(f_*| x_*, X, y) = \mathcal{N}(\mu, \sigma^2) \\
\mu = \frac{1}{\sigma^2_y}x_*^TA^{-1}X^Ty \\
\sigma^2 = x_*^TA^{-1}x_*
$$

* $A = \sigma_y^{}-2X^TX+\Sigma^{-1}$

It can be shown that this equals to an GP with covariacne function $\mathcal{k}(x,x')= x^T\Sigma x'$. Howerever this is an degenerate covariacne fuction since it has at most D non-zero eigen values. Thus this model can represent only an limited number of functions.

## Neural networks

Given a neural network:

$$
p(y|x,\theta) = \mathcal{N}(y| f(x;\theta), \sigma^2) \\
f(x) = b + \sum_{j=1}^H v_j g(x; \mu_j)
$$
* $b$ bias
* $v_j$ is the output weight from hidden unit j to response $y$
* $u_j$ are the inputs weights to unit $j$ from input $x$ 
* $g$ is the hidden unit activation function (any smooth function)

If we assume the following priors:

$$
b \sim \mathcal{N}(0, \sigma^2_b) \\
v \sim \prod_j \mathcal{N}(v_j|0, \sigma^2_w) \\ 
u \sim \prod_j p(u_j)
$$

We denote all the weigths by $\theta$ we have:
$$ 
E_{\theta}[f(x)] = 0 \\
E_{\theta}[f(x)f(x')] = \sigma^2_b + \sum_j \sigma^2_v E_v[g(x; u_j)g(x'; u_j)] \\
= \sigma^2_b + H \sigma^2_v E_v[g(x;u)g(x';u)]
$$

In the limit as the number of hidden units $H \rightarrow \infty$ we get a Gaussian process.