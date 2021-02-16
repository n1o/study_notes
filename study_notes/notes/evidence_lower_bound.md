# Evidence lower bound (ELBO

In [variational inference](variational_inference.md) we minimize [unormalized reverse KL divergence](forward_vs_reverse_kl_divergence.md).
$$
KL(q||\tilde{p})
$$
* $\tilde{p}(x) = Zp(x)$
  * $Z = p(D)$ is the normalizing constant
  * $p(x)$ is the normalized distribution


The loss functions is defined as:

$$
J(q) = \sum_x q(x) \log \frac{q(x)}{\tilde{p}(x)} \\ 
= \sum_x q(x) \log \frac{q(x)}{p(x)} - \log Z \\
= KL(q||p) - \log Z
$$


For $KL(q||p) > 0$ is always true thus we can rearrange the terms to get:  

$$
\log Z = KL(q||p) - J(q) \ge - J(q) \\
\log p(D) = KL(q||p) - J(q) \ge - J(q)

$$

$J(q)$ is a lower bound on $Z$, thus by minimizing $J(q)$ we maximize the lower bound on the log likelihood $p(D)$. This property is called the evidence lower bound (ELBO).

## EBLO
Most of the time ELBO is express as
$$
\log p(D) \ge E_{q(x)}[\log \tilde{p}(x) - \log q(x)] 
$$

The difference between $\log Z(\theta)$ and $-J(q)$ is exactly $KL(q||p)$. If we maximize the evidence-lower bound, we minimize $KL(q||p)$ by "squeezing" it between $-J(q)$ and $\log Z(\theta)$

Alternatively we can view it as [variational free energy](variational_free_energy.md).