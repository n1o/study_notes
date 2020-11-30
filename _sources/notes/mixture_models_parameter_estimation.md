# Parameter estimation for mixture models
In LVM are hiddner variables $z_i$ which is unobserved. Hence the posterior no longer factorize. Hence computing MAP or ML is compilcated. 

## Unidentifiability

The posterior may have multiple modes, and hence it does not have a unique MLE, we say that the parameter is not **identifiable**. 

Unidentifiability can cause a problem for Bayesian inference. If we draw samples from the posterior $\theta^{(s)} \sim p(\theta|D)$ and the posterior has multiple modes, the average $\bar{\theta} = \frac{1}{S} \sum_{s=1}^S \theta^{(s)}$ is meaning less.

There are a couple of solution to **Unidentifiability**

1. Use MCMC
2. Use approximate MAP estimation. 

# EM
An common approach is to use the [EM algorithm](em_algorithm.md) the algorithm iterates between 2 steps:

* E step, Inferring the missing values given the parameters
* M step optimizing the parameters given the "filled in" data
