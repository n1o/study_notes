# Log partition function

An important property of the [exponential family](exponential_family.md) is that the derivatives of the log partition function can be used to generate **cumulants** of the sufficient statistics. For this reason $A(\theta)$ is sometimes called a **cumlant function**.

## First derivative

$$
\frac{dA}{d\theta} = \frac{d}{d\theta} (\log \int \exp (\theta \phi(x))h(x)dx) \\ 
= \frac{ \frac{d}{d\theta} \int \exp(\theta \phi(x)) h(x) dx }{ \int \exp(\theta \phi(x)) h(x) dx } \\ 
= \frac{\int \phi(x) \exp(\theta \phi (x) h(x) dx)}{\exp(A(\theta))} \\
= \int \phi (x) \exp(\theta \phi(x) - A(\theta)) h(x) dx \\
= \int \phi(x) p(x) dx = E[\phi(x)]
$$

* $p(x) = \exp(\theta \phi(x) - A(\theta))h(x)$

## Second derivative

$$
\frac{d^2 A}{d\theta^2} = \int \phi(x) \exp(\theta \phi(x) - A(\theta)) h(x)(\phi(x) - A'(\theta))dx \\
= \int \phi(x)p(x) (\phi(x) - A'(\theta))dx  \\
= \int \phi^2(x) p(x)dx - A'(\theta) \int \phi(x)p(x)dx \\
= E[\phi^2(x)] - E[\phi(x)]^2 = Var[\phi(x)]
$$

* $p(x) = \exp(\theta \phi(x) - A(\theta))h(x)$


For the multivariate case we get:

$$\nabla^2 A(\theta) = cov[\phi(x)]$$

Hence the covariance is always positive definite, $A(\theta)$ is convex. 