# Learning for LG-SSM

If we use SSM for time series forecasting or physical state estimation problems, than the observation matrix $C​$ and the transition matrix $A​$ are both known and fixed by definition of the model. Hence we need to learn the covariance matrix $Q​$ and $R​$. (The initial state estimate $\mu_0​$ is ofthen less important, since it get "washed away" by the data afther a few steps.)

Now we show a method how to estimate $Q,R​$ offline, but it can be done also online.

## Identifiability and numerical stability

In the more general setting, where the hidden states have no pre-specified meaning, we need to learn $A$ and $C$. However, in this case we can set $Q = I$ without loss of generality, since an abitrary covariance matrix can be learned by appropriatly modifying $A$, we also require $R$ to be diagonal without loss of generaility. Doing this reduces the number of ree parameters and improves numerical stability. We also need to contrain the eigen values of the dynamics matrix A. We require them to be $\lambda_i < 1$. This by itself would leave, that with large $t$ we would return to the origin ($E[z_t] =0$), but since we add noise, the state becomes nonzero, so the model do not degenerate. 


## Training the model

**Fully observed data**

It simplifies to solving A by solving a least squares problem $J(A) = \sum_{t=1}^2 (z_t - Az_{t-1})$, and similarly for C. And estimate the system noise variance Q from the residuals in predicting $z_t$ from $z_{t-1}$, and estimate the noise variance R from the residuals in predicting $y_t$ from $z_t$.

**Bayesian methods**

* Variational Bayes EM
* Block Gibbs 
