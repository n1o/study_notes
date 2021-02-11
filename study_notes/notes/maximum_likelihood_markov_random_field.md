# Maximum likelihood markov random fields

We are given a dataset D and we want to estimate $\theta$ via [maximum likelihood](maximum_likelihood_learning.md). Since we work with exponential families the maximum likelihood is concave. The log likelihood is:

$$
\frac{1}{|D|} \log p(D;\theta) = \frac{1}{|D|}\sum_{x \in D}\theta^T f(x) - Z(\theta)
$$
Here we have two parts:

1. $\frac{1}{|D|}\sum_{x \in D}\theta^T f(x)$. This is the easy part since it is linear in $\theta$ and we can decompose it.

2. $\log Z(\theta) = \log \sum_x \exp(\theta^T f(x))$. This is hard to optimize, and hard to evaluate.

The gradient of the second parts is:

$$
\nabla_{\theta} \log Z(\theta) = E_{x \sim p}[f(x)]
$$

Computing the expectation requires inference with respect to $p$ which in general is intractable, thus computing the gradient is intractable.

We can compute the hessian of $\log Z(\theta)$:

$$
\nabla^2_{\theta} \log Z(\theta) = E_{x \sim p}[f(x)f(x)^T] - E_{x\sim p}[f(x)]E_{x\sim p}[f(x)]^T = \text{cov}[f(x)]
$$

The covariance matrix is always positive-definite, thus $\log Z(\theta)$ is convex (this is also known from the fact that it is an exponential family).

## Summary
Since computing the gradient is intractable the whole optimization problem is hard, even if it is convex.