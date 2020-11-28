# Computing the marginal likelihood (evidence)
In general we are not interested in the evidnece, and computing can be really hard. But if we use [conjugate priors](conjugate_prior.md) it is easy to compute them:

1. Let $p(\theta) = q(\theta)/Z_0$ be our prior where $q(\theta)$ is an unormalized distribution, and $Z_0$ is the normalization constant for the Prior.
2. Let $p(D|\theta) = q(D|\theta)/Z_l$ be the likelhood, where $Z_l$ contains any constant factors in the likelihood.
3. Let $p(\theta|D) = q(\theta|D) /{Z_N}$ be our posterior where $q(\theta|D) = q(D|\theta)q(\theta)$ is the unnormalized posterior:

Then we get:
$$p(\theta|D) = \frac{p(D|\theta) p(\theta)}{p(D)} $$

$$ \frac{q(\theta|D)}{Z_N} = \frac{q(D|\theta)p(\theta)}{Z_l Z_0 p(D)} $$

$$p(D) = \frac{Z_N}{Z_0 Z_l} $$

## Beta binomial model
$$ p(D) = \binom{N}{N_1} \frac{B(a + N_1, b + N_0)}{B(a,b)} $$

## Dirichlet multinomial

$$p(D) = \frac{\Gamma(\sum_k \alpha_k)}{\Gamma(N + \sum_k \alpha_K)} \prod_k \frac{\Gamma(N_k + \alpha_k)}{\Gamma(\alpha_k)}$$

## Gauss-Wishart

$$p(D) = \frac{1}{\pi^{N D/2}} (\frac{k_0}{k_N})^{D/2} \frac{|S_0|^{v_0/2}}{|S_N|^{v_N/2}} \frac{\Gamma_D (v_N /2)}{\Gamma_D (v_0 /2)} $$

# Bic approximation of marginal likelihood

Computing the marginal likelihood can be diffucult but we can apporximate it using Bayesian information criterion:

$$BIC \triangleq \log p(D|\hat{\theta}) - \frac{dof(\hat{\theta})}{2} \log N \approx \log p(D)  $$

Where:
* $dof(\hat{\theta})$ is the number of degrees of freedom in a model
* $\hat{\theta}$ is the MLE of the model.

We can see that this has the form of a penalized negative log likelihood, where the penalty depends on the model complexity.

## Effect of the prior

In general [prior](prior.md) has a little influence especially if we have a lot of data. Unfortunatelly this is not true if we talk about marginal likelihood. Since here we have to average the likelihood over all possible parameter settings as weighted by the prior.

We can avoid this problem by defining hyper priors (priors for our priors). This models our uncertainity in our prior, and it is the base for Hierarchical bayesian modelling. Here the influence of hyper priors is relativelly low, and it is common to use uninformative priors.