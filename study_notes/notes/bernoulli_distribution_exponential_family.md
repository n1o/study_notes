# Bernoulli distribution exponential family
$$Ber(x|\mu) = (1 - \mu) \exp[ x \log (\frac{\mu}{ 1 - \mu})] $$

* $\phi(x) = x$
* $\theta = \log (\frac{\mu}{1 - \mu})$ this is the log odds ratio
* $Z = 1 / (1 - \mu)$

We can recover the mean parameter $\mu$ form the canonical form using:

$\mu = sigm(\theta) = \frac{1}{1 + e^{-\theta}}$

