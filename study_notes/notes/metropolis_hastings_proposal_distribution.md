# Metropolis hastings proposal distribution
For a given target distribution $p^*$, a proposal distribution $q$ is valled or admissible, if it gives a non-zero probability of moving to the states, that have non-zero probability in the target:

$$supp(p^*) \sube \cup_x supp(q(.|x))$$

> **Example**

> A Gaussian distribution has non-zero probability density on the entire state space, and hence is a valid proposal for any continuous state space.



In practice it is important that the proposal spreads its probability mass just the right way. If to many proposals are rejected that it will be likely that a chain will stick in the same state for a wery long time. On other hand if a lot of proposals are accepted than we jump arround a lot and we may fail to draw relevant samples. *Advantage of using Gibbs sampling is that we do not need to tune the proposal distribution*. 

For a Gaussian kernel, the optimal acceptance rate is between 25-40%, which theory suggests is optimal.

### Gaussian proposals:

If we have a continuous space, the Hessian $H$ at a local mode $\hat{w}$ can be used to define the covariance of a Gaussian proposal. This approach has the advantage that the Hessian models the local curvature and lenght scales of each dimension; this approach therefore avoids some of the slow mixing behaviour of Gibbs sampling. 

Here we have 2 approaches:

1. Independende proposals $q(x'|x) = N(w'| \hat{w}, H^{-1})$
2. Random walk proposals $q(x'|x) = N(w'| \hat{w}, s^2H^{-1})$, here $s^2$ is a scale factor choose to facilitate rapid mixin. 

### Mixture proposals

If there are several proposals that might be useful, we can combine them using a **mixture proposal**, which is a convex combination of the base proposals:

$$q(x',x) = \sum_{k=1}^K w_kq_k(x'|x)$$

- $w_k$ are mixing weights where $w_k > 0$ 

As long individualy each $q_k$ is valid than the overall mixture is valid. 

### Data driven 

The most efficient proposals depend not just on the previous hidden state, but also the visible data, they have the form $q(x'|x,D)$. This is called **data-driven MCMC**. To create such proposals, one can sample $(x,D)$ pairs from the forwards model and then train a discriminative classifier to predict $p(x|f(D))$, where $f(D)$ are some features extracted fromthe visible data.

### Adaptive MCMC

Here we change the parameters of the proposal as the algorithm is running to increase efficiency. This is called **adaptive MCMC**. This allows one to start with a broad covariance, allowing large moves through space until a mode is found, followd by a narrowing of the covariance to ensure carefull exploration of the region arround the mode.

Here we have to be careful not to violate the Markov property; thus the parameters of the proposal should not depend on the entire history of the chain. It turns out that a sufficient condition to ensure this is that the adaptation is "faded out" gradually over time. 

### Initialization and mode hopping

It is necessary to start MCMC in an initial state space that has non-zero probability. If the model has deterministic constraints, finding such a legal configuration may be hard. It is therefore common to initialize MCMC methods at a local mode, found using optimizer.

In some domains (especially with discrete state space) it is more effective to use of computation to perfrom multiple restarts o an optimizer, and to average those modes, rather than exploring similar points arround a local mode.

However in continuous space, the mode constrains neglible volume, so it is necessary to locally explore arround each mode, in order to visit enough posterior probability mass. 
