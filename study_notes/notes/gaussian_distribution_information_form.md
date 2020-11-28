# Information norm
The from $x \sim \mathcal{N}(\mu, \Sigma)$, where $\mu, \Sigma$ are the **moment parameters** of the [gaussian distribution](multivariate_gausasian.md). But we can reexpress them in therms of **canonnical parameters** or **natural parameters**. 

$$\Lambda = \Sigma^{-1}, \xi=\Sigma^{-1}\mu$$

Which can be converted back to moment parameters using:

$$\mu = \Lambda^{-1}\xi, \Sigma = \Lambda^{-1}$$

If we use the canonical parameters we can rewrite the NVM in **information form**:

$$\mathcal{N}_C(x| \xi, \Lambda) = (2\pi)^{-D/2} |\Lambda|^{1/2} \exp{ [- \frac{1}{2} (x^T \Lambda x + \xi^T \Lambda^{-1} \xi - 2x^T\xi )]} $$
* $N_c$ denotes information form


In this form we can express the [marginalization and conditioning](joint_gaussian_inference.md) formulas as:

$$p(x_2) = \mathcal{N}_c (x_2| \xi_2 - \Lambda_{21}\Lambda^{-1} \xi_1, \Lambda_{22} - \Lambda_{21}\Lambda^{-1}_{11}\Lambda_{12}) $$

$$p(x_1|x_2) = \mathcal{N}_c(x_1| \xi_1 - \Lambda_{12}x_2, \Lambda_{11}) $$

Here we can see that the conditioning is easier in information form.

Also information form makes it easier to multiply two Gaussians:

$$\mathcal{N}_c(\xi_f, \lambda_f)\mathcal{N}_c(\xi_f, \lambda_f) = \mathcal{N}_c(\xi_f + \xi_g, \lambda_f + \lambda_g) $$


In moment from this is much messier:

$$ \mathcal{N}(\mu_f, \sigma^2_f)\mathcal{N}(\mu_f, \sigma^2_f) = \mathcal{N}(\frac{\mu_f \sigma^2g + \mu_g \sigma^2f}{\sigma^2_g + \sigma^2_g}, \frac{\sigma^2_f \sigma^2_g}{\sigma^2_g + \sigma^2_f} )$$