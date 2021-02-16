# Variational auto-encoder

It is an popular instantiation of [auto encoding variational bayes](auto_encoding_variatonal_bayes.md). Where we combine:

1. [Autoencoding ELBO reformulation](auto_encoding_variatonal_bayes.md)
2. [Black box variational inference approach](black_box_variational_inference.md)
3. [Reparametrization based low variance gradient estimator](#reparametrization-based-low-variance-gradient-estimator)

This algorithm is applicable to any deep generative model $p_{\theta}$ with latent variables that is differentiable in $\theta$. The model $p$ is parametrized as:

$$
p(x|z) = N(x| \vec{\mu}(z), \text{diag}(\vec{\sigma}(z))^2) \\
p(z) = N(z| 0, I)
$$

* $\vec{\mu}(z), \vec{\sigma}(z))$  are parametrized neural networks

The model for $q$ is:

$$
q(z|x) = N(z| \vec{\mu}(z), \text{diag}(\vec{\sigma}(z))^2))
$$

Similarly we have neural networks for $\mu, \sigma$.

These choices for $p$ and $q$ alow simplify the auto-encoding ELBO. We can now use a closed form expression to compute the regularization term and use Monte-Carlo estimates for the reconstruction term.

We may interpret the variational autoencoder as a [directed](directed_graphical_models.md) [latent-variable](latent_variable_models.md) probabilistic [graphical model](graphical_models.md). We may also view it as a particular objective for training an auto-encoder neural network; unlike previous approaches, this objective derives reconstruction and regularization terms from a more principled, Bayesian perspective.

## Reparametrization based low variance gradient estimator

Under certain conditions we may express the distribution $q_{\phi}(z|x)$ in a two step generative process:

1. Sample a noise variable $\epsilon$ like a standard normal N(0,1)
   $\epsilon \sim p(\epsilon)$
2. Apply deterministic transformation $g_{\phi}(\epsilon, x)$ that maps the random noise into a more complex distribution.
   $$z = g_{\phi}(\epsilon, x)$$

For many interesting classes of $q_{\phi}$, it is possible to choose a $g_{\phi}(\epsilon,x)$ such that $z = g_{\phi}(\epsilon,x)$ will be distributed acording to $q_{\phi}(z|x)$.

Gaussian random variables provide the simplest example of the reparametrization trick.

$$
z = g_{\mu, \sigma}(\epsilon) = \mu + \epsilon \cdot \sigma
$$

* $\epsilon \sim N(0,1)$
* z is also gaussian

We can express the gradient of an expectation with respect to $q(z)$ (for any f) as:

$$
\nabla_{\phi}E_{z \sim q_{\phi}}[f(x,z)] = \nabla_{\phi}E_{\epsilon \sim p(\epsilon}[f(x, g_{\phi}(\epsilon, x))] = E_{\epsilon \sim p(e)}[\nabla_{\phi}f(x, g_{\phi}(\epsilon, x))]
$$

The gradient is now inside the expectation, so we may take Monte Carlo samples to estimate the right-hand term. This approach has much lower variance than score function estimator and helps us to learn models that we otherwise could not.
