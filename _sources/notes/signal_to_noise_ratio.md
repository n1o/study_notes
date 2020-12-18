# Signal to noise ratio

Given a Linear Gaussian system:

$$x \sim \mathcal{N}(\mu_0, \Sigma_0)$$

System
$$y = x  + \epsilon$$

where 

$$\epsilon \sim \mathcal{N}(0, \Sigma_y)$$

is the noise term:

Then the signal to noise ratio is:

$$
SNR \triangleq \frac{E[x^2]}{E[\epsilon^2]} = \frac{
\Sigma_0 + \mu_0^2}{
\Sigma_y}
$$