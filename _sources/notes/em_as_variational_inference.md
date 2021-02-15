# EM as variational inference

Lets consider the posterior inference problem for $p(z|x)$, where $x$ is held fixed as evidence. We can apply [variational inference](variational_inference.md) framework by taking $p(x,z)$ to be unnormalized, in this case $p(x)$ will be the normalization constant.

The goal of VI is maximize the evidence lower bound (ELBO) over q:

$$
L(p,q)= E_{q(z)}[\log p(x,z|\theta) - \log q(z)]
$$

ELBO satisfies the equation:

$$
\log p(x|\theta) = KL(q(z|| p(z|x,\theta))) + L(p,q)
$$

Hence $L(p,q)$ is maximized when $q = p(z|x)$, in this case the KL term is zero and the lower bound is tight: $\log p(x|\theta) = L(p,q)$

We can view EM as iteratively optimizing the ELBO over $q$ (at the E step) and $\theta$ (at the M step).

We start at some $\theta_t$, we compute the posterior $p(z|x,\theta)$ at the E step.

## Algorithm
We start at some $\theta_t$ at the E-step we compute the posterior $p(z|x,\theta)$. We evaluate the ELBO for $q=p(z|x,\theta)$, this makes the ELBO tight:

$$
\log p(x|\theta_t) = E_{p(z|x,\theta_t)}\log p(x,z|\theta_t) - E_{p(z|x,\theta_t)}\log p(z|x,\theta_t)
$$

Next we optimize the ELBO over p by holding q fixed. We solve:

$$
\theta_{t+1} = \arg \max_{\theta} E_{p(z|x, \theta_t)} \log p(x,z|\theta) - E_{p(z|x,\theta_t)}\log p(z|x, \theta_t)
$$

This step is precisely the optimization problem solved at the M step of EM.

Solving this problem increases the ELBO. However, since we fixed $q$ to $\log p(z|x,\theta_t)$, the ELBO evaluated at the new $\theta_{t+1}$ is no longer tight. But since the ELBO was equal to $p(x|\theta_t)$ before optimization, we know that the true log-likelihood $\log p(x|\theta_{t+1})$ must have increase.

By repeatably computing $p(z|x, \theta_{t+1})$ (The E-step), plugging $p(z|x,\theta_{t+1})$ into ELBO (this makes the ELBO tight), and maximizing the resulting expression over $\theta$. Every step increases the marginal likelihood $p(x|\theta_t)$.