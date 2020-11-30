# Normal Inverse Chi Squared

Is the univariate case of [Normal-Inverse-Wishart](multivariate_gausasian_infering_params.md) and it can be used to find the distribution $p(\mu, \sigma^2| D)$ where $D=\{x_1, \cdots, x_n \}$.


## Prior Distribution

$$NI_{\mathcal{X}^2}(\mu, \sigma^2| m_0, k_0, v_0,\sigma^2) \triangleq \mathcal{N} (\mu| m_0, \sigma^2 / k_0) \mathcal{X}^2 (\sigma^2| v_0 ,\sigma^2)$$
$$\propto (\frac{1}{\sigma^2})^{(v_0 + 3)/2} \exp{ (-\frac{v_0\sigma^2_0 + k_0 (\mu - m_0)^2}{2\sigma^2})} $$

## Posterioor Distribution

$$p(\mu,\sigma^2| D) = NI_{\mathcal{X}^2}(\mu, \sigma^2| m_N, k_N, v_N, \sigma^2_N)$$

where:
* $m_N = \frac{k_0m_0 + N \bar{x}}{k_N}$
* $k_N = k_0 + N$
* $v_0 + N$
* $v_N \sigma^2_N = v_0 \sigma^2_0 + \sum_{i=1}^N (x_i - \bar{x}) + \frac{N k_0}{k_0 + N}(m_0 - \bar{x})^2$


### Posterior Marginals
$$p(\sigma^2|D) = \int p(\mu, \sigma^2|D) d\mu = X^{-1}(\sigma^2| v_N, \sigma^2_N)$$

For $\mu$ it has a [Student-T](student_t_distribution.md) distriibution 

$$
p(\mu|D) = \int p(\mu, \sigma^2) d\sigma^2  = T(\mu| m_N, \sigma^2_N/k_N, v_N)
$$

# Uninformative prior

We can choose an [uninformative prior](uninformative_prior.md):
$$
p(\mu|\sigma^2) \propto p(\mu| \sigma^2) \propto \sigma^{-2} \propto NI_{X^{2}}(\mu, \sigma^2| \mu_0 = 0, k_0 = 0, v_0 = -1, \sigma^2_0 = 0)
$$

The posterior becomes:

$$
p(\mu, \sigma^2| D) = NI_{X^{2}}(m_n = \bar{x}, k_N = N, v_N = N -1, \sigma^2_N = s^2)
$$

* $s^2 \triangleq \frac{1}{N - 1} \sum_{i=1}^N (x_i - \bar{x})^2 = \frac{N}{N- 1} \sigma^2_{mle}$ is the standard deviation. And it is an unbiased estimae of the varaince.

The marginal posterior for the mean:

$$p(\mu|D) = T(\mu| \bar{x}, \frac{s^2}{N}, N - 1)$$

The posterior variance:
$$
var[\mu|D] = \frac{s^2}{N}
$$

If we take the square rooot we get the **standard error of the mean** 

$$
\sqrt{var[\mu|D] } = \frac{s}{\sqrt{N}}
$$