----
source:
- Machine Learning An Probabilistic Perspective

tags:
- Machine Learning
----

# Inference in joint Gaussian distribution
Given an joint [Guassian distribution](multivariate_gausasian.md) $p(x_1, x_2)$ we may want to compute the marginals $p(x_1)$ or conditonals $p(x_1|x_2)$:

Suppose $(x_1, x_2)$ is jointly Gaussian with parameters:

$$\mu = \begin{bmatrix} \mu_1 \\ \mu_2 \end{bmatrix}$$

$$\Sigma = \begin{bmatrix} \Sigma_{11} & \Sigma_{12} \\ \Sigma_{21} & \Sigma_{22} \end{bmatrix}$$

$$\Lambda = \Sigma^{-1} \begin{bmatrix} \Lambda_{11} & \Lambda_{12} \\ \Lambda_{21} & \Lambda_{22} \end{bmatrix}$$

## Marginals:
These marginal can be used to detect outliers.

$$ p(x_1) = \mathcal{N}(x_1 | \mu_1, \Sigma_1) $$
$$ p(x_2) = \mathcal{N}(x_2 | \mu_2, \Sigma_2) $$

## Conditionals


$$p(x_1 | x_2) = \mathcal{N}(x_1 | \mu_{1|2}, \Sigma_{1|2})$$

$$\mu_{1|2} = \mu_1 + \Sigma_{12}\Sigma^{-1}_{22}(x_2 - \mu_2) \\ = \mu_1 - \Lambda_{11}^{-1}\Lambda_{12}(x_2 - \mu_2) \\ = \Sigma_{1|2} (\Lambda_{11}\mu_{1} - \Lambda_{12}(x_2 - \mu_2)) $$

$$ \Sigma_{1|2} = \Sigma_{11} - \Sigma_{12} \Sigma_{22}^{-1} \Sigma_{21} = \Lambda_{11}^{-1}$$

**Booth the marginal and the conditional are Gaussian distributions**

## Proof:

![](../.images/gaussian_conditioning_proof.png)
