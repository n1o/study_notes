# Probit regression

Is an [generalized linear model](generalized_linear_model.md) where we assume that our inverse link function is the [CDF](cumulative_distribution_function.md) of a [Normal distribution](gaussian_distribution.md).

$$g^{-1}(\eta) = \Phi(\eta)$$ 

* $\Phi$ is the standard normal CDF

## MLE

We can use [gradient descent](gradient_descent.md) to find MLE. Let $\mu_i = w^Tx_i$ and $\tilde{y}_i \in \{ -1, +1 \}$ the gradient of the log likelihood is:

$$g_i \triangleq \frac{d}{d w} \log p(\tilde{y}_i| w^Tx_i) = \frac{\mu_i}{dw} \frac{d}{\mu_i} \log p(\tilde{y}_i| w^Tx_i) = x_i \frac{\tilde{y}_i \phi(\mu_i)}{\Phi(\tilde{y}\mu_i)}$$
* $\phi$ is the standard normal PDF
* $\Phi$ is the standard normal CDF


## MAP

We put a Gaussian prior $p(w) = N(0, V_0)$ the penalized gradient becomes:

$$
\sum_i g_i + 2V_0^{-1}w
$$

## Latent variable interpretation
Let us associate each item $x_i$ with two latent utilities $u_{0i}, u_{1i}$ corresponding to possible choises of $y_i = 0$ and $y_i = 1$. We assume that the observed choise is whichever action has larger utility. 

$$u_{0i} \triangleq w^T_0 x_i + \delta_{0i} \\
u_{1i}  \triangleq w_1^Tx_i + \delta_{1i} \\
y_i = I(u_{1i} > u_{0i})$$

* $\delta$'s  are error terms, representing all the other factors that might be relevant in decision making that we have choosen not to model. And they have Gaussian distribution

This representation is called a **random utility model(RUM)**

Since only the difference in utilities matter we define

$$z_i = u_{1i} - u_{0i} + \epsilon_i$$

* $z_i \triangleq w^Tx_i + \epsilon_i$

* $\epsilon_i = \delta_{1i} - \delta_{0i},\epsilon_i \sim \mathcal{N}(0,1)$

This makes

$$y_i = 1 = I(z_i \ge 0)$$

We call this the difference RUM or **dRUM** model.


Now if we marginalize $z_i$ we recover the probit model:

$$
p(y_i =1 | x_i, w) = \int I(z_i \ge 0) N(z_i | w^Tx, 1)dz_i \\
= p(w^Tx_i + \epsilon \ge 0) = p(\epsilon \ge - w^Tx_i) \\
= 1 - \Phi(-w^Tx_i) = \phi(w^Tx_i)
$$

## Extension
### Ordinal probit regression
Here the response variables are ordinal, they take C discrete values which can be ordered in some way (low, medium, high)

### Multinomial probit model
The response variable can take on C unordered categorical values,

