# The EM Algorithm

Widely used algorithm for learning directed [latent-variable graphical models](latent_variable_models.md) of the form 

$$p(x,z|\theta)$$
* $z$ are latent variables
* $\theta$ are model parameters

Since the latent variables are unobserved, they pose a challenge for optimization.

The idea behind EM is that:
1. If the latent variables where fully observed, we could optimize the log-likelihood exactly using previously seen closed form solution for $p(x,z)$
2. Knowing the parameters, we can often efficiently compute the posterior $p(z|x,\theta)$ (for some models this is not true)

The Algorithm works in two steps
1. Given an estimate $\theta^t$ of the parameters compute $p(z|x)$ and use to "hallucinate" values for z.
2. Find a new $\theta_{t+1}$ by optimizing the resulting tractable objective.

Hallucinating data means that it computes the mean expected log likelihood:

$$
E_{z \sim p(z|x)} \log p(x,z|\theta)
$$

If z is not too high dimensional we can compute this expectation. And since this expectation is outside the log, we can decompose it into a sum of log conditional probability distributions, that can be optimized independently.

## Formal Algorithm
For a dataset D we initialize $\theta_0$ to some random value and for $t=1,2,\cdots,$ we repeat until converged.

* **E-step**: For each $x \in D$, compute the posterior $p(z|x,\theta)$
* **M-step**: Compute the new parameters via:
  $$ \theta_{t+1} = \arg \max_{\theta} \sum_{x \in D} E_{z \sim p(z|x_t, \theta_t)} \log p(x,z|\theta) $$

##  Detailed overview

Let $x_i$ be visible or observed variable in case i, and let $z_i$ be the hidden or missing variables. The goal is to maximize the log likelihood function of the observed data:

$$l(\theta) = \sum_{i=1}^N \sum_{i=1}^N \log p(x_i | \theta) = \sum_{i=1}^N \log [ \sum_{z_i} p(x_i, z_i | \theta)] $$

This is hard to optimize since we cannot push the log inside the sum.

The EM gets arround the problem as follows. Define the **complete data log likelihood** to be:

$$ l_c(\theta) \triangleq \sum_{i=1}^N \log p(x_i, z_i | \theta)$$

This cannot be computed, since $z_i$ is unknown. So let us define the **expected complete data log likelihood** as follows:

$$Q(\theta, \theta^{t -1}) = E[l_c (\theta)| D, \theta^{t -1}]$$

where t is the current iteration number. Q is called the **auxiliary function**. The expectation is taken wrt the old parameters, $\theta^{t -1}$, and the observed D. The goal of the **E step** is to compute $Q(\theta, \theta^{t -1})$, or rather, the terms inside of it which the MLE depends onl these are known as the **expected sufficient statistics (ESS)**. In the **M step**, we optimize the Q function wrt $\theta$:

$$ \theta^t = \arg \max_{\theta} Q(\theta, \theta^{t-1}) $$

To perform MAP estimation we modify the M step as follows:

$$ \theta^t = \arg \max_{\theta} Q(\theta, \theta^{t-1}) + \log p(\theta) $$

The E step retains unchanged. The EM algorithm monotonically increases the log likelihood of the observed data. 

## Theory
[EM monotonically decreases](em_theory.md) the observed data log likelihood until it reaches a local maximum.

## Applications
We can apply it to [latent variable models](latent_variable_models.md) like:

* [Gaussian mixture model](gaussian_mixture_model.md)

## [Connection to Variational Inference](em_as_variational_inference.md)
We can understand the behavior of EM by casting it in the framework of [variational inference](variational_inference.md).

## Properties

* The marginal likelihood increases after each EM cycle
* The marginal likelihood is an upper-bounded by its true global maximum, and it increases at every step, EM must eventually convergence.

Unfortunately here we optimize an non-convex objective, thus may not find an global optimum. In practice we tend to have multiple restarts of the algorithms, and find the best solution.