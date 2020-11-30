# Posterior distribution

The posterior distribution is the prior distribution afther observing some data. Or it is the likelihood times prior normalized.

$$
p(\theta|D) =  \frac{p(D|\theta)p(\theta)}{p(D)}
$$

## Enough data
In the limit as we have enough data $p(\theta|D)$ becomes peaked at a single point, MAP estimate $\hat{\theta}^{MAP} = \argmax_{\theta}p(\theta|D)$

$$
p(\theta|D) \rightarrow \delta_{\hat{\theta}^{MAP}}(\theta)
$$

* $\delta$ is the [dirac measure](./dirac_measure.md).

## MAP -> MLE
We can express MAP as:

$$\hat{\theta}^{MAP} =\argmax_{\theta} p(D|\theta)p(\theta) = \argmax_{\theta} [\log p(D|\theta) + \log p(\theta)]$$

The likelihood is the only part that depends on the sample size, the prior stays constant, as we get more and more data **MAP** converges **maximum likelihood estimate (MLE)**.

$$
\hat{\theta}^{mle} \triangleq \argmax_{\theta} p(D|\theta) = \argmax_{\theta} \log p(D|\theta)
$$

In other words if we get enough data the **data overwhelms the prior** thus MAP estimate converges to towards MLE.

# Sumarizing the posterior distribution
Th posterior distribution summarized everything we know about a set of unkonw variables. But sometimes we need to derive some [point estimates](sumarizing_posterior_distributions.md) or other quantities. 
