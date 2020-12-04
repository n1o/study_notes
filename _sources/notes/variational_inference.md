# Variational inference
We try to approximate the posterior using a distribution from tractable family. 

$$
p(\theta|D) \approx q(\theta)
$$

We assume that $q$ has some free parameters that we can optimize, to make the approximation as tight as possible.

To do this we usually minimize the KL divergence:

$$
KL(p^*||q) = \sum_x p^*(x) \log \frac{p^*(x)}{q(x)}
$$
* $p^*(x)$ is our posterior distribution.

This is hard to compute since the expectation $\sum_x p^*(x)$ is not tractable. Instead we work with the **reverse KL divergence**

$$
KL(q||p^*) = \sum_x q(x) \log \frac{q(x)}{p^*(x)}
$$

If we choose $q$ right this is tractable. But evaluating $p^*(x) = p(x|D)$ pointwise is hard, since it requires to evaluate the normalization contant $Z = p(D)$. We have to use the unnormalized distribution:

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

KL divergence is nonnegative, thus $J(q)$ can be viewed as an **upper bound on the NLL(negative log likelihood)**. Alternatively we can view it as [variational free energy](variational_free_energy.md).

$$
L(q) = -J(q) = -KL(q||p^*) + \log Z \le \log Z = \log p(D)
$$

To get the thightest lowerbound we set $q = p^*$