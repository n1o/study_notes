# State space models (SSM)

Is just an [hidden markov model](hidden_markov_models.md), except the hidden states are continuous:

$$z_t = g(u_t, z_{t-1}, \epsilon_t)$$ 
$$y_t = h(z_t, u_t, \delta_t)$$

* $z_t$ is the hidden state
* $u_t$ is an optional input or control signal
* $y_t$ is the observation
* $g$ is the **transition model**
* $h$ is the **observation model**
* $\epsilon_t$ is the system noise at time t
* $\delta_t$ is the observation noise at time t.

Our goal is to recursively estimate the belief state:

$$p(z_t| y_{1:t}, u_{1:t}, \theta)$$

## Linear-Gaussian SSM (LG-SSM) (Linear dynamical system (LDS))
$$
    z_t = A_tz_{t-1} + B_t u_t + \epsilon_t \\
    y_t = C_t z_t + D_tu_t + \delta_t \\
    \epsilon_t \sim N(0, Q_t) \\
    \delta_t \sim N(0, R_t)
$$

1. The transition model is a linear function
2. The observation model is a linear function
3. The system noise is Gaussian:
4. The observation noise is Gaussian


If all the parameters $\theta_t = (A_t, B_t, C_t, D_t, Q_t, R_t)$ are independent of time, the model is called **stationary**.

LG-SSM supports exact inference. The initial belief state is a Gaussian:

$$p(z_1) = N(\mu_{1|0}, \Sigma_{1|0})$$

All subsequent belief states are also Gaussian:

$$p(z_t| y_{1:t}) = N(\mu_{t|t}, \Sigma_{t|t})$$

[Kalman filtering](kalman_filtering.md) algorithm can compute this quantities efficiently.

## Application of SSM

1. Object tracking
2. Robotic slam (Essentially this is the base for robotic vacuums)
3. Time-series forecasting: Here we can show that the popular ARMA model can be viewed as a form of SSM.

## Non-Linear and non-Gaussian SSM

A lot of models are not linear, or the noise is non-Gaussian. Hence the posterior is no longer Gaussian. So we have to approximate 
$p(Y)$