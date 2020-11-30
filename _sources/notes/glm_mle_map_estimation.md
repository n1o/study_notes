# MLE and MAP estimation for Generalized linear Models
An appealing properties of [GLM](generalized_linear_model.md) is that they can be fit using exactly the same methods that we used to fit logistic regression.  The log likelihood can be expresed in the following form:

$$l(w) = \log p(D|w) = \frac{1}{\sigma^2}\sum_{i=1}^N l_i$$

* $l_i \triangleq \theta_i y_i - A(\theta_i)$

We can compute the gradient using chain rule

$$
\frac{d l_i}{d w_j} = \frac{d l_i}{d \theta_i} \frac{d \theta_i}{d \mu_i} \frac{d \mu_i}{d \eta_i} \frac{d \eta_i}{d w_j} \\
= (y_i - A'(\theta_i)) \frac{d \theta_i}{d\mu_i} \frac{d \mu_i}{d \eta_i}x_{ij} \\ 
= (y_i - \mu_i) \frac{d\theta_i}{d\mu_i} \frac{d \mu_i}{d \eta_i} x_{ij}
$$

If we use a canonical link, $\theta_i = \eta_i$ this simplifies to 

$$\nabla_w l(w) = \frac{1}{\sigma^2}[\sum_{i=1}^N(y_i - \mu_i)x_i]$$

which is the sum of the input vectors, weighted by the errors.

Thus we can use gradient descent to fit any GLM.