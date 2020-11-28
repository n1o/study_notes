# Maximum entropy derivation

The exponential family, is the distribution that makes the least number of assumptions about the data, subject to a specific set of user-specified constraints. In particular suppose all we know is the expected values of certain features or functions:

$$ \sum_x f_k(x)p(x) = F_x $$

* $F_x$ is known constant

* $f_k(x)$ is an arbitrary function


The principle of maximum **entropy** or **maxent** says we should pick the distribution with maximum entropy (closest to uniform), subject to the constraints that the moments of the distribution match the empirical moments of the specified functions

To maximize the entropy subject to the constrain, and the constraints that $p(x) \ge 0$ and $\sum_x p(x) = 1$ we need to use Lagrange multipliers. The Lagrangian is given by:

$$J(p, \lambda) =  - \sum_x p(x) \log p(x) - \lambda_0 (1 - \sum_x p(x)) + \sum_k \lambda_k (F_k - \sum_x p(x) f_k(x))$$

We treat p as fixed length vector (since we assume that x is discrete) then we have:

$$\frac{\partial J}{\partial p(x)} = -1 - \log p(x) - \lambda_0 -  \sum_k \lambda_k f_k(x)$$

If we wet this to 0 we get:

$$p(x) = \frac{1}{Z} \exp(- \sum_k \lambda_k f_k(x)) $$

* $Z - e^{1 + \lambda_0}$

Since $p(x)$ is a probability distribution it has to sum up to 1.

$$1 = \sum_x p(x) = \frac{1}{Z} \sum_x \exp{(- \sum_k \lambda_k f_k(x))} $$

Hence the normalization constant becomes:

$Z = \sum_x \exp(- \sum_k \lambda_k f_k(x))$

Thus the maxnet distribution $p(x)$ is of the form of the exponential familuy, also known as **Gibbs distribution**.
