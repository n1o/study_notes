# Gaussian Process

We assume that $y_i = f(x)$ is an unkown function which can be corrupted by noise. The optimal approach is to infer a distribution over functions given the data $p(f|X,y)$ and then use this to make predictions given new inputs.

$$
p(y_*|x_*, X, y) = \int_p(y_*| f, x_*)p(f|X,y)df
$$

In this appoach we do not assume any parametric form for the function $f$, but we perform Bayesian inference over functions themselves. 

A **Gaussian Process** GP defines a prior over functions, which can be converted into a posterior over functions once we have seen some data. This may seem difficult, but it is enough to be able to define a distribution over the function’s values at a finite, but arbitrary, set of points, say $x_1, \cdots, x_N$. Where *GP* assumes that $p(f(x_1), \cdots, f(x_N))$ is jointly Gaussian with some mean $\mu(x)$ and covariance $\Sigma(x), \Sigma_{ij} = k(x_i, x_j)$ where $k$ is a positive definite kernel function. The key idea is that $x_i$ and $x_j$ are deemed by the kernel to be similar, then we expect the ouptut of the function at those points to be similar too. 

Gaussian processes for regression can be done in close form in $O(N^3)$ time (there are setting where it can be faster).  And for **classification** setting we must use **approximation**. (Gaussian approximation, since the posterior is no longer Gaussian)

Gaussian processes can be tought of as a Bayesian alternative to kernel methods, although those methods are sparser and therefore faster, but they do not give well-calibrated probabilistic output. 