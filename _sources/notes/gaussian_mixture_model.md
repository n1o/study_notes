# Mixture of Gaussians

The most widely used [mixture model](mixture_models.md) is the **mixture of Gaussians** also known as **Gaussian mixture model (GMM)**. In this model each base distribution is a mixture of multivariate Gaussians with mean $\mu_k$ and covariance matrix $\Sigma_k$.

$$
p(x) = p(x|z)p(z) \\
p(x_i|\theta) = \sum_{k=1}^K \pi_k \mathcal{N}(x_i| \mu_k, \Sigma_k)
$$

* $\pi_k = p(z=k)$
* $\sum_k \pi_k = 1$ are the mixture weights

Here we assume that our observed data is comprised of K cluster with proportions specified by $\pi_1, \cdots, \pi_k$, where each cluster is a Gaussian.

![](../.images/machine_learning/gaussian_mixture_example.png)

## EM
One way to fit Gaussian mixture model is to use [EM](em_algorithm.md)

We assume a known number of K mixture components:

$$
Q(\theta|\theta^{(t -1)} ) \triangleq E[\sum_i \log p(x_i, z_i |\theta)] \\
= \sum_i E[\log [\prod_{k =1}^K (\pi_k  p(x_i | \theta_k))^{I(z_i = k)}]] \\ 
= \sum_i \sum_k E[I(z_i = k| x_i ,\theta^{t - 1})]\log [\pi_k p(x_i|\theta_k)] \\ 
= \sum_i \sum_k r_{ik} \log \pi_k + \sum_i \sum_k r_{ik} \log p(x_i|\theta_k)
$$

* $r_{ik} = p(z_i = k| x_i, \theta^{(t-1)})$ is the responsibility that cluster k takes from data point i.

## E step

This is the same for all mixture models

$$
r_{ik} = \frac{\pi_k p(x_i| \theta_k^{(t - 1)}) }{\sum_{k'} \pi_{k'}p(x_i| \theta^{(t-1)}_{k'}) }
$$

## M step

We need to optimize Q with respect to $\pi$, $\mu$ and $\Sigma$

$$
\pi_k = \frac{1}{N} \sum_{i}r_{ik} = \frac{r_k}{N}
$$

* $r_k = \sum_i r_{ik}$ the number of points asigned to cluster k


For $\mu_k, \Sigma_k$ we simplify Q and leave only the parts it depends on

$$
l(\mu_, \Sigma_k) = \sum_k \sum_i r_{ik} \log p(x_i|\theta_i)  \\ 
= - \frac{1}{2} \sum_i r_{ik} [\log |\Sigma_k| + (x_i - \mu_k)^T \Sigma_k^{-1}(x_i - \mu_i)]
$$

This is just the weighted MLE of an NVM

$$
\mu_k = \frac{\sum_i r_{ik} x_i}{r_{k}} \\
\Sigma_k = \frac{\sum_{i} r_{ik} (x_i - \mu_k)(x_i - \mu_k)^T}{r_k} = \frac{\sum_i r_{ik} x_ix_i^T}{r_k} - \mu_k \mu_k^T
$$

This is intuitive the mean of cluster $k$ is just the weighted average of all points assigned to cluster k, and the covariance is proportional to the weighted empirical scatter matrix.

Now we set $\theta^k = (\pi_k, \mu_k, \Sigma_k)$ for $k = 1 : K$ and go to the next E step.
