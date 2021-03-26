# Estimator

Given $m$ i.i.d points $\{x^{(1()}, \cdots, x^{(m)} \}$ a point estimator is any function of the data (sample):

$$
\hat{\theta}_m = g(x^{(1)}, \cdots, x^{(m)})
$$

A good estimator is a function whose output is close to the true underlying population parameter $\theta$.

> Example:
> Sample mean is is an estimator for the true mean
> $$ \bar{x} \approx \mu $$

## Bias of an estimator

$$
\text{bias}(\hat{\theta}_m) = E[\hat{\theta}_m] - \theta
$$

* $\theta$ is the true value of the population
* $E[\hat{\theta}_m]$ we take the expectation over the data

### Unbiased estimator

$$\text{bias}(\hat{\theta}_m) = 0$$ 

In this case $E[\hat{\theta}_m] = \theta$ on average the point estimate is equal to the population parameter.

### Asymptotically unbiased
$$\lim_{m \rightarrow \infty} \text{bias}(\hat{\theta}_m) =0$$ 

In this case $\lim_{m \rightarrow \infty} E[\hat{\theta}_m] = \theta$, the estimator in the limit is equal to the population parameter.

## Variance of an estimator (standard error)
We are interested how the estimator changes for different samples. 

$$
\text{var}(\hat{\theta}) \\
\text{SE}(\hat{\theta}) = \sqrt{\text{var}(\hat{\theta})}
$$

In general we prefer estimators with low variance. The lower bound of the variance is given by **Cramer-Rao lower bound**. The [maximum likelihood](maximum_likelihood_learning.md) has asymptotically zero variance.

The standard error for the sample mean is defined:
$$
\text{SE}(\hat{\mu}_n) = \sqrt{\text{var}[\frac{1}{m} \sum_{i=1}^m x^{(i)}]} = \frac{\sigma}{\sqrt{m}}
$$

* $\sigma$ is the true standard deviation we can approximate it using an biased estimation $\sqrt{\tilde{\delta}^2}$ with is the square root of the unbiased estimate for the sample variance.

We can use [central limit theorem](central_limit_theorem.md) to construct an 95% confidence interval around the mean. 

$$
(\hat{\mu}_m - 1.96 \text{SE}(\hat{\mu}_m), \hat{\mu}_m + 1.96 \text{SE}(\hat{\mu}_m)
$$

This is useful in machine learning, we can build confidence interval around errors from training or testing.

## Consistent estimators
We study the behavior of the estimator as the sample size increases. We prefer the following behavior:

$$
p \lim_{m \rightarrow \infty} \hat{\theta}_m = \theta \\
p(|\hat{\theta}_m - \theta| \ge \epsilon) \rightarrow 0 \text{ as } m \rightarrow \infty
$$

* $p \lim$ is convergence in probability
##  Bias variance tradeoff

Sometimes using an unbiased estimator is not the best idea. If the corresponding risk of our estimator is the MSE. Than we can decompose it as:

$$E[(\hat{\theta} - \theta^*)^2] = var[\hat{\theta}] + bias^2(\hat{\theta})$$

This is called the **bias-variance tradeoff**. Which means that it might be wise to use a biased estimator, so long as it reduces our variance, assuming our goal is to minimize squared error.

## Sampling distribution of an estimator

In frequentist statistics, a parameter estimate $\hat{\theta}$ is computed by applying an **estimator** $\delta$ to some data D such that $\hat{\theta} = \delta(D)$. The parameter is viewed as fixed and the data as random, which is the exact opposite of the Bayesian approach.  The uncertainity in the parameter estimate can be measured by computing the **sampling distribution** of the estimator. This an be viewed as sampling different datasets $D^{(s)}$ from some true model $p(.|\theta^*)$. Now we apply the estimator $\hat{\theta}(\cdot )$ to each $D^{(s)}$ to get $\{ \hat{\theta}(D^{(s)}) \}$. As $S \rightarrow \infty$ than this set becomes the sampling distribution of our estimator.

To compute this sampling we can use [Boostrap](boostrap.md)

## Statistical efficiency of an estimator
An estimator can obtain lower generalization error for a fixed number of samples or require fewer samples to reach a fixed level of generalization error.