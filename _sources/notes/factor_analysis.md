# Factor analysis (FA)

One problem with [mixture models](mixture_models.md) is that they use only a single latent variable to generate the obervations. One observation can come from one of K prototypes. Since the prototypes are mutually exclusive the model is limited in its representational power.

Alternatively we can use an vector valued latent variable $z_i \in R^L$ and use an Gaussian prior:

$$
p(z_i) = N(z_i| \mu_0, \Sigma_0)
$$

If the observations $x_i$ is are also continuous $x_i \in R^D$ we may use a Guassian for the likelihood. And as in [linear regression](linear_regression.md) we assume that the mean is a linear function of the hidden inputs:

$$
p(x_i|z_i, \theta) = N(Wz_i + \mu , \Psi))
$$

* $W_{D \times L}$ is a **factor loading matrix** 

* $\Psi_{D \times D}$ covariance matrix, and we force it to be diagonal hence it will force $z_i$ to explain the correlation instead of covariance.

The overal model is called **Factor analysis**

![](../.images/machine_learning/factor_analysis.png)

## FA as a low rank parametrization of MVN

Factor analysis can be thought as a way of specifying a joint density model on x using a small number of parameters.

$$ p(x_i| \theta) = \int N(x_i| Wz_i + \mu, \Psi)N(z_i|\mu_o, \Sigma_0)dz_i \\ 
= N(x_i| W\mu_0 + \mu, \Psi + W \Sigma_0 W^T)
$$


* $\mu_0 = 0$ can be set without loss of generality since we can absorb $W\mu_0$ into $\mu$
* $\Sigma_0= I$ can be set without loss of generality, since we can emulate a correlated prior by defining a new weight matrix $\tilde{W} =W \Sigma_0^{-1/2}$

The covariance:

$$
cov[x|\theta] = \tilde{W}^T + E[\epsilon \epsilon^T] = (W \Sigma_0^{-1/2}) \Sigma_0(W \Sigma_0^{-1/2})^T + \Psi = W^TW + \Psi
$$

Thus FA approximates the covariance matrix of visible vector using a low-rank decomposition:

$$
C \triangleq cov[x] = WW^T + \Psi
$$

This parametrization is more efficient uses only $O(LD)$ parameters instead of the full Gaussian covariance $O(D^2)$.

## Inference of latent factors

We ofthen hope that the latent factors will reveal something interesting about the data. To do that we need to compute the posterior over the latent factors:


$$ p(z_i|x_i, \theta) = N(z_i| m_i, \Sigma_i) \\ 
\Sigma_i \triangleq (\Sigma_0^{-1} + W^T \Psi^{-1}W)^{-1} \\
m_i \triangleq \Sigma_i (W^T \Psi^{-1}(x_i - \mu) + \Sigma_0^{-1}\mu_0)
$$


* $\Sigma_i$ is actually independent of $i$ so we drop the subscript, computing reqires $O(L^3 + L^2D)$ time
* $m_i$ are called the latent **scores** or latent **factors** computing requires $O(L^2 + LD)$ time

# Unidentifiability

Similar to mixture mudels FA are also [unidentifable](factor_analysis_unidentifiability.md).