# Exponential family sufficient statistics
The likelihood of an [exponential family](exponential_family.md) model has the form:

$$p(D| \theta) = [\prod_{i=1}^N h(x_i)] g(\theta)^N \exp( \eta(\theta)^T [ \sum_{i=1}^N \phi(x_i)])$$

And the sufficient statistics are N (sample size) and:

$$\phi(D) = [\sum_{i=1}^N \phi_1(x_i), \cdots, \sum_{i=1}^N \phi_K(x_i)]$$

Examples of sufficient statistics

* Bernoulli $\phi= [\sum_i I(x_i =1)]$
* Gaussian $\phi = [\sum_i x_i, \sum_i x_i^2]$

## Pitman-Koopman-Darmois theorem

Under certain regularity conditions, the exponential family is the only family of distributions with finite sufficient statistics. (independent of the size of the dataset)

One of the conditions of this theorem is that the support of the distribution not be dependent on the parameter. (The distribution is unbounded)

The MLE for a canonical exponential family, for N iid data points $D = \{x_, \cdots, x_N \}$

$$ \log p(D| \theta) = \theta^T \phi(D) - NA(\theta) $$

Since $-A(\theta)$ is concave in $\theta$ and $\theta^T \phi(D)$ linear in $\theta$, we see that the log likelihood is concave and hence has a unique global maximum. To derive the maximum, we use the fact that the derivative of the log partition function yields the expected value of the sufficient statistic vector:

$$\nabla_{\theta} \log p (D|\theta) = \phi(D) - N E[\phi(X)]$$

If we set it equal to zero, we see that at the MLE, the empirical average of the sufficient statistics must equal the model's  theoretical expected sufficient statistics, i.e: $\hat{\theta}$ must satisfy:

$$E[\phi(X)] = \frac{1}{N} \sum_{i=1}^N \phi(x_i)$$

This is called moment matching.

For the Bernoulli distribution we have $\phi(X) = I(X - 1)$ then the MLE is:

$$
E[\phi(X)] = p(X = 1) 
$$