# Rao Blackwell theorem
It is a way to improve the efficiency of initial estimators.

> Theorem:
> Suppose $g(X)$ is an unbiased estimator of a scalar parametric function $h(\theta)$ and $T_i(X); i = 1,2,\cdots p$ are jointly sufficient for $(\theta)$; then there exists an estimator $u(T)$, depending on the data only through the sufficient statistics, such that 
> $$E[u(T)] = h(\theta) \\ \text{Var}[u(T)] \le \text{Var}[g(X)]$$

Improvement in efficiency is obtained by taking the statistic’s conditional expectation with respect to a [sufficient statistic](sufficient_statistics.md) (assuming one exists). In other words, a statistic is “sufficient” if it retains all of the information about the population that was contained in the original data points.

## Context of random vriables
Let $z$ and $\theta$ be dependent random variables, and $f(z, \theta)$ be some scalar function. Then:

$$ var_{z,\theta} [f(z, \theta)] \ge var_z [E_{\theta}[f(z,\theta)|z]] $$

This theorem guarantees that the variance of the estimate is create by analyticially integrating out $\theta$ will always be lower (or rather never by higher) than the variance of direct [MCMC](markov_chain_monte_carlo_inference.md) estimate.
