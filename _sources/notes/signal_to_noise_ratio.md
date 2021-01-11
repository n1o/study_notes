# Signal to noise ratio
Compares the level of a desired signal to the level of background noise. A ratio higher than 1:1 indicates more signal than noise. 

Given a Linear Gaussian system:

$$x \sim \mathcal{N}(\mu_0, \Sigma_0)$$

System
$$y = x  + \epsilon$$

where 

$$\epsilon \sim \mathcal{N}(0, \Sigma_y)$$

is the noise term:

Then the signal to noise ratio is:

$$
SNR \triangleq \frac{E[X^2]}{E[\epsilon^2]} = \frac{
\Sigma_0 + \mu_0^2}{
\Sigma_y}
$$