# Latent Variable Models

Here we assume that observed variables are correlated because they arise form a hidden common "cause". Model with hidden variables are known as **latent variable models (LVM)**.
Our goal is to find the following joint distribution:

$$
p(x,z) = p(x|z)p(z)
$$

* x is observed
* z is unobserved

In general LVM are harder to fit, than models with no latent variables.  However they have significant advantages:

1. They often have fewer parameters than models that directly represent correlation in the visible space
2. The hidden variables in an LVMM can serve as **bottleneck**, which computes a compressed representation of the data. 

Since latent variables can be used to explain the data generation process in general we are interested to find out something about $p(z| x)$. To find out something about our hidden variables given the observed ones. 

## Learning

When we train an LVM model our goal si to maximize the marginal-log likelihood:

$$
\log p(D) = \sum_{x \in D} \log p(x) = \sum_{x \in D} \log [\sum_{z} p(x|z)p(z)]
$$

This optimization is difficult because of the summation inside the log cannot be decomposed into sum of log factors. 

If we look closer at a data point x:

$$
p(x) = \sum_z p(x|z)p(z)
$$

It is mixture of distributions $p(x|z)$ with weights $p(z)$. If we assume that a single $p(x|z)$ is from an [exponential family](exponential_family.md) it has a concave log-likelihood, but the log of a weighted mixture of such distribution is no longer concave. Thus our goal is non-convex and we have to use approximate learning algorithms.

* [Expectation maximization](em_algorithm.md)