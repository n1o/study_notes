# Non-Linear, non-Gaussian SSMs

Unfortunately many models are non linear. Objets do not move in straight lines. And non-Gaussian noise is also very common, due to outliers, or when we infer parameters for GLMs instead of just linear regression. For these methods we no longer can get a closed solution, we need to use *approximate inference*. 

Let $X$ be a random variable that has Gaussian distribution, and let $f$ be a nonlinear function hence, $Y = f(X)$ is no longer Gaussian.

There are 2 ways how to approximate $p(Y)$.

1. Perfrom a first-order approximation of $f$
2. Use exact $f$, but project $f(x) $ onto the space of Gaussians by moment matching. 

## Extended Kalman Filter (EKF)

Here we focus on nonlinear models, but we assume that the noise is Gaussian we have a model:

$$
z_t = g(u_t, z_{t-1}) + \mathcal{N}(0, Q_t) \\ 
y_t = h(z_t) + \mathcal{N}(0,R_t)
$$

* $g$ is the transition model, is nonlinear but differentiable
* $h$ is the observation model, is nonlinear but differentiable

The extended **Kalman filter** or EKF can be applied to nonlinear Gaussian dynamical systems of this form. The basic idea is to linearize $g$ and $h$ about the previous state estimate using a first order Taylor series expansion, and then to apply the standard Kalman filter equations. Thus we approximate the stationary non-linear dynamical system with a non-stationary linear dynamical system. 

## Unscented Kalman filter

It is a better version of EKF. The key intuition is that it is easier to approximate a Gaussian than to approximate a function. So instead of perfroming a linear approximation to the function, and passing a Gaussian through it, instead pass a deterministically chosen set of points, known as **sigma points**, through the function, and fit a Gaussian to the resulting trasformed points. This is known as the [unscented transform](unsented_transoform.md). 

The UKF performs the unscented transfrom twice, once to approximate passing throught the system model g, and one to approximate passing through the measurement model h.

## Assumed density filtering (ADF)

Perfroms exact update step, but approximate the posterior by a distribution of certain convenient form (such as Gaussian). Here we make the approximation better by minimizing the KL divergence. 
