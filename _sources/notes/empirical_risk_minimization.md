# Empirical risk minimization

In machine learning we want to reduce risk or expected generalization error. Since we do not know the true data generating distribution we cannot optimize it directly. Our best guess is to minimize the empirical risk.

$$
E_{x,y \sim \hat{p}_{\text{data}}(x,y)} [L(f(x;\theta), y)] = \frac{1}{m}\sum_{i=1}^m L(f(x^{(i)}; \theta), y^{(i)})
$$
* $\hat{p}_{\text{data}}(x,y)$ is the training data
* $m$ is the number of samples

Minimizing the average training error is known as empirical risk minimization and we hope we also minimize the generalization error. Unfortunately this will overfit.