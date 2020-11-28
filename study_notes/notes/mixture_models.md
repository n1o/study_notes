# Mixture models

The simplest form of [LVM](latent_variable_models.md) is when $z_i \in \{1, \cdots,K\}$, representing a discrete latent state. We use a discrete prior $p(z_i) = Cat(\pi)$. The likelihood function we use $p(x_i,z_i = k) = p_k(x_i)$ where $p_k$ is the k'th **base distribtuion** for the observations (it can be of any type). The overall model is known as a **mixture model**, since we mix togeter the K base distributions as follows:

$$p(x_i|\theta) = \sum_{k=1}^K \pi_k p_k(x_i|\theta)$$

Which is a **convex combination** of the $p_k$'s where we are taking a weighted sum, where the **mixin weights** $\pi_k$ satisfy $0 \le \pi_k \le 1$ and $\sum_{k=1}^K \pi_k =1$. 

The following tables gives an example of different mixture models:


| Name   |      Likelihood      |  Prior |
|----------|:-------------:|------:|
| Mixture of Gaussians |  MVN | Discrete |
| Mixture of multinomials |    Prod. Discrete   |   Discrete |
| Factor analysis/ Probabilistic PCA| Prod.. Gaussian |    Prod. Gaussian |
| Probabilistic ICA | Prod. Gaussian | Prod. Laplace |
| Multinomial PCA | Prod. Discrete | Prod. Gaussian|
| Latent Dirichlet allocation | Prod. Discrete | Dirichlet|

## Examples
Some common [examples](mixture_model_examples.md) of mixture models. Like
* mixture of multinoulis
* [mixture of gaussians](gaussian_mixture_model.md)

And their application

# Parameter estimation
