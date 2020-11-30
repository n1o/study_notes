# Kalman filtering algorithm

The **Kalman filtering** is an algorithm for exact Bayesian filtering for [linear-Gaussian state space models](state_space_model.md). Where we are interested in the marginal posterior at time t:

$$p(z_t| y_{1:t}, u_{1:t}) = N(z_t| \mu_t, \Sigma_t)$$

Since everything is Gaussian we can perfrom the predict and update step in closed form, and the resulting algorithm is the analog of the [HMM](hidden_markov_models.md) filter.

# Prediction step
$$
p(z_t| y_{1:t-1}, u_{1:t}) = \int \mathcal{N}(A_tz_{t-1} + B_t u_t, Q_t)\mathcal{N}(z_{t-1}|\mu_{t-1}, \sigma_{t-1})dz_{t-1} \\ 
= \mathcal{N}(z_t| \mu_{t|t-1}, \Sigma_{t|t-1}) \\
\mu_{t|t-1} = A_t\mu_{t-1} + B_t u_t \\
\Sigma_{t|t-1} = A_t\Sigma_{t-1}A_t^T + Q_t
$$
# Measurement step

We compute using Bayes rule:

$$p(z_t| y_t, y_{1:t-1}, u_{1:t}) \propto p(y_t|z_t, u_t)p(z_t| y_{1:t-1}, u_{1:t}) $$

This is just the product of the prediction step and the actual observation.

This is given by:
$$
    p(z_t|y_{1:t}, u_t) = \mathcal{N}(z_t|\mu_t, \Sigma_t) \\ 
    \mu_t = \mu_{t|t-1}+ K_t r_t \\
    \Sigma_t = (I - K_tC_t) \Sigma_{t|t-1}
$$

* $r_t$ is the **residual** or **inovation**, given by the difference between our predicted observation and the actual observation:

$$
    r_t = y_t - \hat{y}_t \\
    \hat{y}_t = E[y_t| y_{1:t-1}, u_{1:t}] = C_t \mu_{t|t-1} + D_t u_t
$$

* $K_t$ is the **Kalman gain matrix** given by:

$$K_t \triangleq \Sigma_{t|t-1}C_t^T S_t^{-1}$$

$$
    S_t = cov[r_t| y_{1:t-1}, \mu_{t:1}] \\ 
    = E[(C_tz_t + \delta_t - \hat{y}_t)(C_tz_t + \delta_t - \hat{y}_t)^T| y_{1:t-1}, u_{1:t}] \\ 
    = C_t\Sigma_{t|t-1}C_t^T + R_t
$$

* $\delta_t \sim N(0, R_t)$ is the observation noise term which is independent of all other noise sources. 

We can also use the matrix inversion lehma, and we can express the Kalman gain matrix as:

$$
K = \Sigma_{t|t-1}C^T (C \Sigma_{t|t-1}C^T + R)^{-1} = (\Sigma^{-1}_{t|t-1} + C^TCR)^{-1}C^TR^{-1}
$$

Lets dig into the mean update:

$$
\mu_t = \mu_{t|t-1} + K_tr_t
$$

This says that the new mean is the old mean plus a correction factor ($K_t$ times the error signal $r_t$). The amount of weight placed on the error signal depends on the Kalman gain matrix. If $C_t = I$ then $K_t = \Sigma_{t| t-1} S_t^{-1}$, wich is the ration between the covariance of the prior and the covariance of the measurement error. If we have a strong prior $|K_t|$ will be small and we will place little weight on the correction term, and vice versa.

# Posterior predictive

The one step-ahead posterior preditive density for the observations can be computed as follows:

$$
p(y_t| y_{1:t-1}, \mu_{1:t}) =  \int \mathcal{N}(y_t| Cz_t,R)\mathcal{N}(z_t| \mu_{t|t-1A}, \Sigma_{t|t-1})dz_t \\ 
= \mathcal{N}(y_t|C\mu_{t|t-1}, C \Sigma_{t|t-1}C^T + R)
$$

# Computational issues
There is an matrix inversion which takes $O(|y_t|^3)$ and a matrix-matrix multiply to compute $\Sigma_t$ which takes $O(|z_t|^2)$