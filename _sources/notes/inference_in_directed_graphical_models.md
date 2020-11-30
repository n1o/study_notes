# Inference

[Graphical model](directed_graphical_models.md) provides an compact way to define joint probability distriubions, where we use these distributions to perfrom **probabilistic inference**. 

In general  we have a set of correlated random variables with joint distribution $p(x_{1:V}| \theta)$. (Where we assume $\theta$ is known). Where some of those variables are observed, **visible variables** $x_v$, and unobserved, **hidden variables**, $x_h$. Now we want to compute the posterior:

$$p(x_h|x_v, \theta) = \frac{p(x_h, x_v| \theta)}{p(x_v|\theta)} = \frac{p(x_h, x_v|\theta)}{\sum_{x_h'} p(x'_h, x_v|\theta)}$$

Here we condition on the data by **clamping** the visible variables to their observed values $x_v$ and normalizing to go from $p(x_h, x_v)$ to $p(x_h|x_v)$. And the normalization constnat $p(x_v|\theta)$ is the likelihood of the data called **probability of the evidence**
