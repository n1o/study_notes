# Gaussian distribution
It makes only two assumptions about a distribution, that it has a mean and variance.

$$f(x, \mu, \sigma) = \frac{1}{\sigma \sqrt{2 \pi}} e^{- (\frac{x - \mu}{2\sigma})^2} $$

* $\mu$ determines the center o the distribution
* $\sigma^2$ determines the variance
* $\sigma \sqrt{2\pi}$ is the normalization 


## Properties
* mean and variance are independent
* symmetrical $p(x) = p(-x)$ *unbounded
* Governed by the central limit theorem, where average tend to converge to a central limit.
* Symmetry for tail areas for CDF: $\Phi(z) = 1 -\Phi(-z)$
* Symmetry of $X, -X$. If $X \sim N(\mu, \sigma)$ than $-X \sim N(\mu, \sigma)$

## Moments

### Mean
$E[X] = \mu$

### Variance

$var[X] = \sigma^2$

## Standard normal
Gaussian that has zero mean an unit variance.
$X \sim N(0,1)$

## Degenerate

In the limit 
$$ \lim_{\sigma^2 \rightarrow 0} N(x| \mu, \sigma^2)= \delta(x - \mu) $$

* $\sigma$ is the [dirac delta](dirac_measure.md)

## Pecission parametrization
We can parametrize the Gaussian by its precision instead of variance. Precision is given by $\lambda = 1 / \sigma^2$. This means the higher the precission the tighter the distribution. 

$$
N(x;\mu, \Lambda) =  \sqrt{\frac{\text{det}(\Lambda)}{2 \pi}} \exp{(-\frac{1}{2}(x - \mu)^T\Lambda (x - \mu))}
$$

This may be practical since we do not need to invert the Covariance matrix.

## Multivariate
An [n dimensional Gaussian](multivariate_gausasian.md) is parametrized by a mean vector $\mu$ and covariance matrix $\Sigma$ or precision matrix $\Lambda$.

$$N(x| \mu, \Sigma) \triangleq \frac{1}{(2\pi)^{D/2} |\Sigma|^{1/2}} \exp {[- \frac{1}{2}(x - \mu)^T \Sigma^{-1} (x - \mu)]}$$

## CDF
We integrate the pdf:
$$\Phi(x; \mu, \sigma^2) = \int_{-\infty}^x N(x| \mu, \sigma^2)dx $$

This unfortunately has no closed form, so it is built into most software packages. 

## Usage
Many common biological measurements can be occasionally approximately described by a Gaussian, especially if the samples are very large, of if we are dealing with an average count. 

Many common statistical procedures have been derived where de assume that the distribution from which the data has arose is Normal. Specially, inference and hypothesis testing from simple parametric tests like OLS regression, ANOVA, assume that the residuals are Normal distributed with mean of zero. The reliability of these test depend on the degree of conformity to this assumption of normality.

## Isotropic Gaussian
A Gaussian where covariance matrix is just a scalar times the identity matrix.

$$\Sigma = \sigma I$$