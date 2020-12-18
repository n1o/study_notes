# Model Averaging
Instead of choosing a single model from a set of candidate models, model averaging is about getting one meta-model by averaging separate models. Where we use the marginal posterior probability:

$$ p(\theta| y) = \sum_{k=1}^K p(\theta | y, M_k) p(M_k| y) $$

## The good part
Models with more parameters tend to have larger penalization than models with fewer parameters. The intuitive reason is that the larger the number of parameters the more spread the prior with respect to the likelihood.
## The bad parts

Computing the integral $p(y|M_k) = \int_{\theta_k} p(y| \theta_k, M_k)p(\theta_k, M_k) d \theta_k$ is rather hard. 

## The ugly parts

The marginal likelihood depends **sensitively** on the specified prior $p(\theta_k | M_k)$ for each model. In human language the prior won't really affect the value of $\theta_k$ but it will hugely affect the value of $p(\theta_k | M_k)$.

## Occam's razor
We prefer the simpler hypothesis over the more complicated one. (A theory with mathematical beauty is more likely to be correct than an ugly one that fits some experimental data.(Paul Dirac))
