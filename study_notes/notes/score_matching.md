# Score Matching
* it is a way to avoid computing the [partition function](partition_function.md) (or its derivatives) for probabilistic models
* derivatives of a log density wtr to its arguments $\nabla_x \log p(x)$ are called the **score**

* the idea is that we minimize the square difference between derivatives of models log density wtr to the input and the derivatives of the data log density wtr to the input

$$
L(x,\theta) = \frac{1}{2}||\nabla_x \log p_{\text{model}} (x;\theta), - \nabla_x \log p(x)||_2^2 \\
J(\theta)  = \frac{1}{2}E_{p_{\text{data}}(x)}L(x, \theta) \\
\theta^* = \min_{\theta}J(\theta)
$$

* here we need to know $p_{\text{data}}$, but we can substitute it with:

    $$
    \hat{L}(x, theta) \sum_{j=1}^n(\frac{\partial^2}{\partial x^2_j} \log p_{\text{model}}(x;\theta) + \frac{1}{2} (\frac{\partial}{\partial x_j} \log p_{\text{model}}(x;\theta))^2 )
    $$
  * n is the dimensionality of x

* score matching is only applicable to continuous x
* we need to be able to evaluate $\tilde{p}$ and its derivatives
* we cannot use it in deep models