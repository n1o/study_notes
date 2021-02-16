# Auto-encoding variational Bayes
Based on [variational inference](variational_inference.md). The main idea is to minimize the [evidence lower bound (ELBO)](evidence_lower_bound.md).

$$
L(p_{\theta},q_{\phi}) = E_{q_{\phi}(z|x)}[\log p_{\theta}(x,z) - \log p_{\phi}(z|x)]
$$

Over the space of all $q_{\phi}$. The ELBO satisfies the equation:

$$
\log p_{\theta}(x) = KL(q_{\phi}(z|x)||p(z|x)) + L(p_{\theta},q_{\phi})
$$

ELBO satisfies:

$$
\log p_{\theta}(x) = KL(q_{\phi}(z|x)||p(z|x)) + L(p_{\theta},q_{\phi})
$$

X is fixed thus we can define $q(z|x)$ to be conditioned on x. This means that we choose a different $q(z)$ for every x, which will produce a better posterior approximation that always choosing the same $q(z)$.

To optimize $p(z|x)$ we could use [mean field method](mean_field_method.md), but the accuracy is insufficient. The assumption that q is fully factored is too strong, and the [coordinate descent](coordinate_descent.md) is to simple.

## [Black Box Variational inference](black_box_variational_inference.md)
We try to build general approaches to optimize q that works for large classes of q. 