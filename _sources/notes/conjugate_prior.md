# Conjugate prior

Finding the posterior

$$p(\theta|D) =  \frac{p(D|\theta)p(\theta)}{p(D)}$$

The true chalange is solving the following integral:

$$
p(D) = \int_{\theta}p(D|\theta)p(\theta)
$$

In most cases there is no closed form solution to it, unless we choose an specific prior for a specific likelihood. If we choose an **conjugate prior** to an likelihood, than the posterior will be the **same distribution as the prior**.

For a prior to be conjugate it has to be **proportional to the likelihood**.

## Beta binomial model

In the [beta binomial](./beta_binomial.md) model wee choose an beta prior to a binomial likelihood, the posterior distribution than becomes a beta distribution. It can be used for  modeling binary outcomes.

## Dirichlet Multinomial
In the [dirichlet multinomial](./dirichlet_multinomial.md) we choose dirichlet prior to an multinomial distribution. It generalizes the beta binomial model for multiclass classification.

## [Sufficient statistics](./sufficient_statistics.md)
//TODO Sufficient statistics