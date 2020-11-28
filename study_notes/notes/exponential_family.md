# Exponential family
The exponential family is important because:

* It can be shown that, under certain regularity conditions, the exponential family is the only family of distributions with finite-sized sufficient statistics, meaning that we can compress the data into a fixed-sized summary without loss of information.

* The exponential family is the only family of distributions for which conjugate priors exist, which simplifies the computation of the posterior.

* The exponential family can be shown to be the family of distributions that makes the least set of assumptions subject to some user-choosen constraints

* The exponential family is at the core of generalized linear models.

* The exponential family is at the core of variational inference


## Definition 
A distribution of the form:

$$p(x|\theta) = \frac{1}{Z(\theta)} h(x) \exp{[\theta^T \phi(x)]} = h(x)\exp[\theta^T \phi(x) - A(\theta)]$$

* $Z(\theta) = \int_{X^m} h(x) \exp[\theta^T \phi(x)]dx$  (this is the partition function)
* $h(x)$ is the scaling constnat ofthen set to 1.
* $A(\theta) = \log Z(\theta)$ (log partition function or cumulant function)
* $\theta$ is called the **natural parameters** of **canonical parameters**. 
* $\phi(x) \in R^d$ is called a vector of **sufficient statistics** , if $\phi(x) =x​$ we say it is a **natural exponential family**

We can futher generalize the exponential family by writing:

$$p(x|\theta) = h(x)\exp[\eta(\theta)^T \phi(x) - A(\eta(\theta))]$$

* $\eta$ is a function that maps the parameter $\theta$ to the canonical parameter $\eta = \eta(\theta )$. 
  * If $dim(\theta) < dim(\eta(\theta))$, it is called a **curved exponential family**, which means we have more sufficient statistics than parameters. 
  * If $\eta(\theta) = \theta$ , the model is said to be in **canonical form**


### Minimal exponential distribution

If there is a unique parameter $\theta$ associated with the distribution, we can say it is unique. (The components of sufficient statistics are linearly independent)

## Examples

* [Bernoulli](bernoulli_distribution_exponential_family.md)
* [Multinoulli](multinoulli_exponential_family.md)
* [Univariate Gaussian](univariate_gaussian_exponential_family.md)
### What does not belong
* [Uniform distributiion](uniform_distribution.md) since its parameters deppend on the data
* [Student](student_t_distribution.md) since it does not have the form.

## Log partition function

An important property of the exponential family is that the derivatives of the [log partition function](log_partition_function.md) can be used to generate **cumulants** (moments) of the sufficient statistics. For this reason $A(\theta)$ is sometimes called a **cumlant function**.

## Pitman-Koopman-Darmois theorem

Under certain regularity conditions, the exponential family is the only family of distributions with [finite sufficient statistics](pitman_koopman_darmois_exponential_family_mle.md). (independent of the size of the dataset)

## [Bayesian view](exponential_family_bayesian_view.md)
The only family for which conjugate priors exists is the exponential family. Conjugate priors can simplify exact Baysian analysis.

## [Maximum entropy derivation](exponential_family_maximum_entropy.md)

The exponential family, is the distribution that makes the least number of assumptions about the data, subject to a specific set of user-specified constraints. In particular suppose all we know is the expected values of certain features or functions.

