# Univariate Gaussian exponential distribution

$$
N(x| \mu, \sigma^2) = \frac{1}{Z(\theta)} \exp(\theta^T \phi(x))
$$

* $\theta =  \begin{pmatrix} \mu / \sigma^2 \\ -\frac{1}{2 \sigma^2} \end{pmatrix}$
* $\phi(x) = \begin{pmatrix} x \\ x^2 \end{pmatrix}$
* $Z(\mu, \sigma^2) = \sqrt{2\pi} \sigma \exp{|\frac{\mu^2}{2\sigma^2}|}$
* $A(\theta) = \frac{- \theta^2_1}{4 \theta_2} - \frac{1}{2} \log (-2 \theta_2) - \frac{1}{2} \log(2\pi)$