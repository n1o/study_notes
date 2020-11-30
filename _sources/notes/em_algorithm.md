# The EM Alogirthm

Iterative algorithm with closed-form updates at each step. Exploits the fact that if the data were fully observed, then the ML/MAP estimate would be easy to compute. The algorithm iterates between 2 steps.

* E step, Inferring the missing values given the parameters

* M step optimizing the parameters given the "filled in" data

##  Basic idea

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

The E step retains unchanged. The EM algorithm monotonicaly increases the log likelihood of the observed data. 

# Theory
[EM monotonically decreases](em_theory.md) the observed data log likelihood until it reaches a local maximum.

# Applications

* [Gaussian mixture model](gaussian_mixture_model.md)

