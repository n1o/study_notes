# Variational inference
We try to approximate the posterior using a distribution from tractable family. 

$$
p(\theta|D) \approx q(\theta)
$$

We assume that $q$ has some free parameters that we can optimize,   make the approximation as tight as possible.

To do this we usually minimize the KL divergence:

$$
KL(p^*||q) = \sum_x p^*(x) \log \frac{p^*(x)}{q(x)}
$$
* $p^*(x)$ is our posterior distribution.

This is hard to compute since the expectation $\sum_x p^*(x)$ is not tractable. Instead we work with the [reverse KL divergence](forward_vs_reverse_kl_divergence.md)

$$
KL(q||p^*) = \sum_x q(x) \log \frac{q(x)}{p^*(x)}
$$

If we choose $q$ right this is tractable. But evaluating $p^*(x) = p(x|D)$ point-wise is hard, since it requires to evaluate the normalization constant $Z = p(D)$. We have to use the un-normalized distribution:

$$
\tilde{p}(x) = p^*(x)Z
$$

The objective function becomes:

$$
J(q) = KL(q||\tilde{p}) \\ 
= \sum_x q(x) \log \frac{q(x)}{Zp^*(x)} \\ 
= \sum_x q(x) \log \frac{q(x)}{p^*(x)} - log Z \\
= KL(q||p^*) - \log Z
$$

Here Z is an constant, thus by minimizing $J(q)$ we will force q to become close to $p^*$. 

KL divergence is nonnegative, thus $J(q)$ can be viewed as an **upper bound on the NLL(negative log likelihood)**. 

$$
L(q) = -J(q) = -KL(q||p^*) + \log Z \le \log Z = \log p(D) \\
\log p(D) = KL(q||p) - J(q) \\
\log p(D) \ge -J(q) \\
$$

By minimizing $J(q)$ we essentially maximize the lower-bound of the log likelihood $\log p(D)$. Because of this $-J(q)$ is called the variational lower bound or [evidence lower bound (ELBO)](evidence_lower_bound.md).

## [Mean field method](mean_field_method.md)
One of the most popular variational inference methods. It assumes that the posterior is fully factorized approximation of the form:

$$q(x) = \prod_{i=1} ^D q_i(x)$$

Our goal is to solve this optimization problem:

$$min_{q_1, \cdots, q_D } KL(q||p) $$