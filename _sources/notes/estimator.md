# Estimator
An estimator is a statistics (we use only a sample not the whole population) that estimates some fact about the population (estimand)

> Example:
> Sample mean is is an estimator for the true mean
> $$ \bar{x} \approx \mu $$

## Desirable properties of estimators
Unfortunatelly we cannot achieve all the properties at the same time.

### Consistency
An estimator is said to be consistent if it eventually recovers the true parameter that generated the data as the sample size goes to infinity

$$\hat{\theta}(D) \rightarrow \theta^*, |D|\rightarrow \infty$$ 

(Converges in probability)

Where it can be shown that the MLE is an consistent estimator. The intuition is that we minimize $KL(p(\cdot| \theta^*)||p(\cdot| \hat{\theta}))$ which is zero if $\hat{\theta} = \theta^*$

### Ubiased estimator

The **bias** of an estimator is defined as:

$$bias(\hat{\theta}(.)) = E_{p(D|\theta^*)}[\hat{\theta}(D)- \theta_*]$$

* $\theta_*$ is the true parameter.

If bias is zero, the estimator is called **unbiased**. That means that the means of the sampling distribution is centered on the true parameter. 

We can use this fact to show that the sample variance is not an unbiased estimator for $\sigma^2$. Hence we need to use:

$$\hat{\sigma}^2_{N -1} = \frac{N}{N-1}\sigma^2$$

### Minimum variance

We can have that our estimator will be unbiased, but it will have a large variance. So it is important to have a low variance. The lower bound of the variance is given by **Cramer-Rao lower bound**.

Where MLE achieves the Cramer Rao lower bound, hence it has the smallest asymptotic variance of any unbiased estimator. MLE is **asymptotically optimal**.

###  Bias variance tradeoff

Sometimes using an unbiased estimator is not the best idea. If the correspoing risk of our estimator is the MSE. Than we can decompose it as:

$$E[(\hat{\theta} - \theta^*)^2] = var[\hat{\theta}] + bias^2(\hat{\theta})$$

This is called the **bias-variance tradeoff**. Which means that it might be wise to use a biased estimator, so long as it reduces our variance, assuming our goal is to minimize squared error.

## Sampling distribution of an extimator

In frequentist statistics, a parameter estimate $\hat{\theta}$ is computed by applying an **estimator** $\delta$ to some data D such that $\hat{\theta} = \delta(D)$. The parameter is viewed as fixed and the data as random, which is the exact opposite of the Bayesian approach.  The uncertainity in the parameter estimate can be measured by computing the **sampling distribution** of the estimator. This an be viewed as sampling different datasets $D^{(s)}$ from some true model $p(.|\theta^*)$. Now we apply the estimator $\hat{\theta}(\cdot )$ to each $D^{(s)}$ to get $\{ \hat{\theta}(D^{(s)}) \}$. As $S \rightarrow \infty$ than this set becomes the sampling distribution of our estimator.

To compute this sampling we can use [Boostrap](boostrap.md)
