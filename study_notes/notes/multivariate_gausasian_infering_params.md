# Infering the parameters of an NVM
We assume that $D = \{x_1, \cdots, x_N \}$ where $x_i \sim \mathcal{N}(\mu, \Sigma)$ observations. We may want to find:

* $P(\mu| D, \Sigma)$
* $P(\Sigma| D ,\mu)$ 
* $p(\mu, \Sigma |D)$ 

## $P(\mu|D, \Sigma)$.

### Likelihood

$$p(D|\mu) = \mathcal{N}(\bar{x}| \mu, \frac{1}{N}\Sigma) $$

### Prior
Gaussian prior is the [Conjugate prior](conjugate_prior.md) to the [Gaussian distribution](gaussian_distribution.md).

$$p(\mu) = \mathcal{N}(\mu|m_0,V_0$$

We can derive the Gaussian posterior for $\mu$:

This becomes a [linear gaussian system](linear_gaussian_systems.md)
$$p(\mu|D, \Sigma) = \mathcal{N}(\mu|m_N, V_N) $$

Where:
* $V^{-1}_N = V_0^{-1} + N \Sigma^{-1}$
* $m_N = V_N (\Sigma^{-1} (N \bar{x}) + V_0^{-1}m_0)$

## $P(\Sigma|D, \mu)$

### Likelihood:
$$ p(D| \mu, \Sigma) \propto |\Sigma|^{-\frac{N}{2}} \exp(-\frac{1}{2} tr(S_{\mu}\Sigma^{-1}))$$

### Prior
[Conjugate prior](conjugate_prior.md) is [Inverse Wishart distribution](inverse_wishart_distribution.md).

$$ P(\Sigma) = IW(\Sigma| S_0^{-1}, v_0) \propto |\Sigma|^{-(v_0 + D + 1)/2} \exp (-\frac{1}{2}  tr(S_0\Sigma^{-1}))$$
Where:
* $v_0 >  D -1$
* $S_0$ is symmetric pd matrix. 
* $S_0^{-1}$ plays the role of the prior scatter matrix
* $N_0 \triangleq v_0 + D +1$ controls the strength of the prior.

### Posterior

$$P(\Sigma| D, \mu) = IW (\Sigma| S_N, v_n) $$

Where:
* $v_N = v_0 + N$
* $S_N^{-1} = S_0 + S_{\mu}$  

Hence the posterior strength $v_N$ is the prior strength $v_0$ plus the number of observations N, and the posterior scatter matrix $S_N$ is the prior scatter matrix plus the data scatter matrix.


## $P(\mu, \Sigma| D)$


### Likelihood
$$ p(D| \mu, \Sigma) = (2\pi)^{-ND/2}|\Sigma|^{-N/2} \exp{ (-\frac{1}{2} \sum_{i=1}^N(x_i - \mu)^T \Sigma^{-1}(x_i - \mu) ) } $$

We can re express the term in the exponent using the follwing fact:

$$\sum_{i=1}^N(x_i - \mu)^T \Sigma^{-1}(x_i - \mu)  = tr(\Sigma^{-1} S_{\bar{x}}) + N (\bar{x} - \mu)^T{\Sigma^{-1}} (\bar{x} - \mu) $$

$$ p(D| \mu, \Sigma) = (2\pi)^{-ND/2}|\Sigma|^{-N/2} \exp{(\frac{N}{2} (\bar{x} - \mu)^T{\Sigma^{-1}} (\bar{x} - \mu) )} \exp{(- \frac{N}{2} (tr(\Sigma^{-1} S_{\bar{x}}))}$$

### Prior

We can use the obvious mixture prior:
$$ p(\mu, \Sigma) = \mathcal{N}(\mu| m_0, V_0) IW(\Sigma| S_0, v_0)$$

Unfortunately this is not a conjugate prior, it is a **semi-conjugat** or **conditionally conjugate**, since booth $p(\mu|\Sigma), p(\Sigma|\mu)$ are individually conjugate.

To create a conjugate prior, we need to use a prior where $\mu$ and $\Sigma$ are dependent of each other. And we will use a joint distribution of the form:

$$p(\mu, \Sigma) = p(\Sigma)p(\mu, \Sigma)$$

and it is a **Normal-inverse-wishart (NIW)** defined as:

$$NIW(\mu, \Sigma| m_0, k_0, v_0, S_0) \triangleq $$

$$ \mathcal{N}(\mu| m_0, \frac{1}{k_0}\Sigma) \times IW(\Sigma| S_0, v_0)$$

Where:
* $m_0$ is our prior mean for $\mu$
* $k_0$ is how strongly we believe in the prior of the mean
* $S_0$ is the prior for $\Sigma$
* $v_0$ is how strongly we believe in the prior for $\Sigma$


### Posterior
$$p(\mu, \Sigma | D) = NIW(\mu, \Sigma | m_N, k_N, v_N, S_N) $$

where:
* $m_N = \frac{k_0 m_0 + N \bar{x}}{k_n} = \frac{k_0}{k_0 + N }m_0 + \frac{N}{k+0 + N}\bar{x}$
* $k_n = k_0 + N$
* $v_N = v_0 + N$ 
* $S_n = S_0 + S\bar{x} + \frac{k_0 N}{k_0 + N}(\bar{x} - m_0)(\bar{x} - m_0)^T = S_0 + S\bar{x} + k_0 m_0m_0^T - k_N m_N m_N^T$
* $S \triangleq \sum_{i=1}^N x_i x_i^T$ this is the uncentered sum of squares matrix.

Here we can sea that the posterior mean is a convex combination of the prior mean and the MLE, with strength $k_0 + N$, and the posterior scatter matrix $S_N$ is the prior scater matrix $S_0$ plus the empirical scatter matrix $S_{\bar{x}}$ and an extra term due the uncertainity in the mean.

#### Posterior marginals
$$p(\Sigma | D) = IW(\Sigma | S_N , v_N)$$

The posterior marginal for $\mu$ has a multivariate Student T distribution:
$$p(\mu|D) = \mathcal{T}(\mu | m_N, \frac{1}{k_N (v_n - D + 2)S_N}, v_N - D + 1) $$

This follows the fact that the [Student distribution](student_t_distribution.md) can be represented as a scaled mixture of Gusssians.

### Posterior predictive
$$p(x| D) = \frac{p(x,D)}{p(D)} = \mathcal{T}(x| m_n \frac{k_N + 1}{k_N(v_n - D + 1)}, S_N, v_N - D  +1)$$

### Univariate case
Here we assume that $P(\mu, \sigma^2| D)$ follows an [normal inverse chi-squared](normal_inverse_chi_squared.md) distribution.
