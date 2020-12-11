# Monte carlo inference

An alternative approach to perfrom [Bayesian inference](bayesian_statistics.md), where the algorithms are based on the idea of Monte Carlo approximation. The idea is simple, generate some (unweighted) samples from the posterior

$$x^s \sim p(x|D)$$

and use these to compute any quantity of interest:
*  $p(x_1|D)$ posterior marginal
*  $p(x_1 - x_2|D)$ posterior of the difference of two quantities
*  $p(y|D)$  posterior predictive

All these quantities can be [approximated](monter_carlo_estimation.md) by $E[f|D] \approx \frac{1}{S} \sum_{x=1}^S f(x^s)$ for some suitable function f. 

## [Rejection Sampling](rejection_sampling.md)

## Importance Sampling