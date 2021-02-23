# Black-box variational inference

Black-box [variational inference](variational_inference.md) is a special class of [auto encoding variational inference](auto_encoding_variatonal_bayes.md) algorithms we assume that we can differentiate $q_{\phi}$ with respect to $\phi$ we can use using [gradient descent](gradient_descent.md) to maximize [ELBO](evidence_lower_bound.md).

The algorithm simultaneously performs gradient descent to update $\phi$ and $\theta$. 
* Optimizing over $\phi$ keeps the ELBO tight around $\log p(x)$
* Optimizing $\theta$ pushes the lower bound up.

## Score function gradient estimator

To perform black-box variational inference, we need to compute the gradient:

$$
\nabla_{\theta, \phi}E_{q_{\phi}(z)}[\log p_{\theta}(x,z) - \log q_{\phi}(z)]
$$

Taking the expectation with respect to q is not always possible. Thus we can make [Monte Carlo estimates](monter_carlo_estimation.md) of the gradient by sampling from $q$. 

This is easy to do for the gradient of $p$, we just swap the gradient and the expectation and estimate the following expression via Monte Carlo.

$$
E_{q_{\phi(x)}}[\nabla_{\theta} \log p_{\phi}(x,z)]
$$

Taking the gradient with respect to q is more difficult, we cannot swap the gradient and the expectation, since the expectation is being taken with respect to the distribution that we are try to differentiate.

Way can estimate the gradient a so-called score function estimator:

$$
\nabla_{\phi}E_{q_{\phi}(z)}[\log p_{\theta}(x,z) - \log p_{\phi}(z)] = E_{q_{\phi}(z)}[(\log p_{\theta}(x,z) - \log q_{\phi}(z)) \nabla_{\phi} \log q_{\phi}(z)]
$$

We place the gradient inside the expectation, and we can evaluate it using Monte Carlo. This is called the score function estimator of the gradient.

Biggest shortcoming of this estimator is that it has high variance. (High variance means that the observations are far away from the mean). In some cases the variance is so high that it cannot be used to learn many models.


## The SGVB estimator

We reformulate ELBO as:

$$
\log p(x) \ge E_{q_{\phi}(z|x)} [ \log p_{\theta}(x|z)] - KL(q_{\phi}(z|x)|| p(z))
$$

This reparametrization can be interpreted as: First, we can think of x as an observed data point. The right-hand side consists of two terms, both involve taking a sample $z \sim q(z|x)$, which can be interpret as a code describing x. Where we call q as the encoder.

* $\log p(x|z)$ is the log-likelihood of the observed x given the code z that we have sampled. This term is maximized when $p(x|z)$ assigns high probability to the original x. It is trying to reconstruct x given the code z, for that reason we call $p(x|z)$ the decoder network ad the term is called the reconstruction error.
* $KL(q_{\phi}(z|x)|| p(z))$ is the divergence between $q(z|x)$ and prior $p(z)$ (unit Normal). This forces z to look Gaussian, and we call it the regularization term. It prevents $q(z|x)$ from encoding identity mappings, and forces to learn more interesting representations.
  
The optimization objective is to fit a $q(z|x)$ that wil map x into a useful latent space z from which we are able to reconstruct x via $p(x|z)$. (this objective is reminiscent of auto-encoder neural network)