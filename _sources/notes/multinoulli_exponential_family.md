# Multinoulli exponential family
$$Cat(x| \theta) = \exp{(\theta^T\phi(x) - A(\theta))}$$

* $\theta = [\log \frac{\mu_1}{\mu_K}, \cdots, \log \frac{\mu_{K-1}}{\mu_K} ]$

* $\phi(x) = [I(x=1), \cdots, I(x = K -1)]$


We can recover the mean from the canonical parameter:

$\mu_k = \frac{e^{\theta_k}}{ 1 + \sum_{j=1}^{K-1} e^{\theta_j}}$

From this we can find:

$\mu_K = \frac{1}{\sum_{j=1}^{K-1}e^{\theta_j}}$

Hence:

$A(\theta) = \log(1 + \sum_{k=1}^{K-1} e^{\theta_k})$

If we define $\theta_k = 0$ we can write $\mu = S(\theta)$ and $A(\theta) = \log \sum_{k=1}^K e^{\theta_k}$ where $S $ is the softmax function. 