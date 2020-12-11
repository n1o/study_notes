# Sequential importance sampling

The basic idea is to approximate the belief state using a weighted set of particles. 

$$p(z_{1:t} | y_{1:t}) \approx \sum_{s=1}^S \hat{w}_t \delta_{z_{1:t}^s} (z_{1:t}) $$

* $\hat{w}_t^s$  is the normalized weight of sample s at time t.

We update this belief state using [importance sampling](importance_sampling.md). If the proposal has the form $q(z_{1:t}^s| y_{1:t})$ the importance weights are given as:

$$w_{t}^s \propto \frac{p(z_{1:t}^s|y_{1:t} )}{q(z_{1:t}^s | y_{1:t} )}$$

$\tilde{w}_t^s = \frac{w_t^s}{\sum_s, w_t^{s'}}$

We can express the numerator recursively as:

$$
p(z_{1:t}|y_{1:t}) = \frac{p(y_t| z_{1:t}, y_{1:t-1})p(z_{1:t},y_{1:t-1}))}{p(y_t| y_{1:t-1})} \\
= \frac{p(y_t| z_t)p(z_t|z_{1:t-1, y_{1:t-1}})p(z_{1:t-1},y_{1:t-1}))}{p(y_t| y_{1:t-1})} \\
\propto p(y_t|z_t)p(z_t|z_{t-1})p(z_{1:t-1}| y_{1:t-1})
$$

Here we make the usual Markov assumptions. We restrict attention to proposal densities of the form:

$$
q(z_{1:t}| y_{1:t}) = q(z_t| z_{1:t-1}, y_{1:t})q(z_{1:t-1}| y_{1:t-1})
$$

Here we can grow the trajectory by adding the new state $z_t$ to the end. Then the importance weight simplify as:

$$
w_t^s \propto \frac{p(y_t|z_t^s) p(z_t^s|z^s_{t-1})p(z_{1:t-1}^s|y_{1:t-1})}{q(z_t^s| z^s_{1:t-1}, y_{1:t})q(z^s_{1:t-1}| y_{1:t-1})} \\
= w_{t-1}^s \frac{p(y_t|z_t^s)p(z_t^s|z^s_{t-1})}{q(z_t^s|z^s_{1:t-1}, y_{1:t})}
$$
If we further assume $p(z_t| z_{1:t-1}, y_{1:t}) = p(z_t| z_{t-1}, y_t)$ we only need to keep the most recent part of the trajectory and observation sequence, hence the weight becomes:

$$
w_t^s \propto w_{t-1}^s \frac{p(y_t|z_t^s)p(z_t^s|z^s_{t-1})}{q(z_t^s|z^s_{1:t-1}, y_{1:t})}
$$

Now we can approximate the posterior filtered density as:

$$
p(z_t|y_{1:t}) \approx \sum_{s=1}^S \hat{w}_t^s \delta_{z^s_t}(z_t)
$$

As $S \rightarrow \infty$ this approaches the true posterior. 

## Algorithm
For each old sample s, propose an extension using $z_t^s \sim q(z_t | z_{t-1}^s, y_t)$, and give this new particle weight $w_t^s$. Unfortunately this algorithm does not work well, because of **degeneracy problem**.

## The degeneracy problem
The basic sequential importance sampling algorithm fails afther a few steps because most of the particles will have neglibe wight. This is called the  **degeneracy problem**, and occurs because we are sampling in a high-dimensional space (the space is growing in size over time), using a myopic proposal distribution.

We can quantify the degree of degenracy using the **effective sample size**:

$$
S_{\text{eff}} = \frac{S}{1 + \text{var}[w_t^{*s}]}
$$
* $w_t^{*s} = p(z_t^s| y_{1:t}) / q(z_t^s| z_{1:t}^s, y_t)$ is the "true weight" of the particle s.

Unfortunately we cannot compute this exactly, since we do not know the true posterior but we can approximate it:

$$
\hat{S}_{\text{eff}} = \frac{1}{\sum_{s=1}^S (w_t^s)^2}
$$

If the variance of the weights is large, then we are wasting our resources updating particles with low weight, which do not contribute much to our posterior estimate.

we have 2 possible solutions to degeneracy problem:

1. Adding a resampling step
2. Using a good proposal distribution

### Resampling step
Here we monitor the effective sampling size, and whenever it drops below a threshold, we elimite particles with low weight, and then create replicas of the surviving particles. 

### Proposal distribution

The most widely used proposal distribution is to sample from:

$$q(z_t| z_{t-1}^s, y_t) = p(z_t | z_{t-1}^s)$$

in this case the weight update simplifies to:

$$w_t^s \propto w_{t-1}^s p(y_t| z_t^s)$$

This can be thought of a “generate and test” approach: we sample values from the dynamic model, and then evaluate how good they are after we see the data. 
