# Gaussian mixture model EM

We apply [EM](em_algorithm.md) to [GMM](gaussian_mixture_model.md).Lets assume we have dataset D.

**At the  E-Step** we compute the posterior for each data point x as:

$$
p(z|x,\theta_t) = \frac{p(z,x|\theta_t)}{p(x|\theta_t)} = \frac{p(x|z,\theta_t)p(z|\theta_t)}{\sum_{k=1}^K p(x|z,\theta_t)p(z|\theta_t)}
$$

* each $p(x|z_k,\theta_k)p(z_k|\theta_k)$ is simply the probability that x originates form component k given the current set of parameters $\theta$.

In the model $z$ is an indicator variable that chooses a component for $x$. The result of E step is a K-dimensional vector (components sum to 1) that specifies a "soft" assignment to components. 

**At the M-step** we optimize the expected log-likelihood of our model

$$
\theta_{t+1} = \arg \max_{\theta} \sum_{x \in D} E_{x \sim p(z|x,t)}\log p(x,z|\theta) \\
= \arg \max_{\theta} \sum_{x=1}^K \sum_{x \in D} p(z_k|x,\theta_t) \log p(x|z_k, \theta) + \sum_{k=1}^K \sum_{x \in D} p(z_k|x,\theta_t) \log p(z_k|\theta) 
$$

We can optimize each term separately. 

First we start with

$$
p(x|z_k,\theta) = N(x|\mu_k,\Sigma_k)
$$

Here we have to find $\mu_k, \Sigma_k$ to maximize:

$$
\sum_{x \in D} p(z_k|x_t, \theta_t) \log p(x|z_k,\theta) = c_k \cdot E_{x \sim Q_k(x)}\log p(x|z_k,\theta)
$$

* $c_k = \sum_{x \in D} p(z_k|x,\theta_t)$ is a constant independent of $\theta$ 
* $Q_k(x) = \frac{p(z_k|x, \theta_t)}{\sum_{x \in D}p(z_k|x, \theta_t)}$ is a probability distribution defined over D 

$E_{x \sim Q_k(x)} \log p(x|z_k,\theta)$ is optimized when $p(x|z_k,\theta) = Q_k(x)$. Since $p(x|z_k,\theta)=N(x|\mu_k,\Sigma_k)$ are in the exponential family, they are entirely described by its sufficient statistics. Thus

$$
\mu_k = \mu_{Q_k} = \sum_{x \in D} \frac{p(z_k|x,\theta_t)}{\sum_{x \in D}p(z_k|x,\theta_t)} x \\
\Sigma_k = \Sigma_{Q_k} = \sum_{x \in D} \frac{p(z_k|x, \theta_t)}{\sum_{x \in D} p(z_k|x,\theta_t) }(x - \mu_{Q_k})(x - \mu_{Q_k})^T
$$


These values are just the mean and variance of the data, weighted by their cluster affinities. 

At last we find the class priors:

$$
\pi_k = \frac{1}{|D|}\sum_{x \in D} p(z_k|x, \theta_t)
$$