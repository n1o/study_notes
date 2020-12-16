# Marko chain monte carlo convergence
The amount of time it takes for a Markov chain to converge to the stationary distribution, and forget its initial state, is called the **mixing time**. More formaly, the mixing time from state $x_0$ is the minimal time such that, for any constant $\epsilon > 0$, we have:

$$
\tau_{\epsilon}(x_0) = \min \{ t: || \delta_{x_0}(x)T^t - p^*||_1 \le \epsilon \}
$$

* $\delta_{x_0} (x)$ is the distribution with all its mass at state $x_0$
* $T$ si the transition matrix of the chain
* $\delta_{x_0} (x)T^t$ is the distribution afther t steps

The mixing time of the chain is defined as:

$$\tau_{\epsilon} \triangleq \max_{x_0} \tau_{\epsilon} (x_0)$$

The mixing time is determined by the eigengap $\gamma = \lambda_1 - \lambda_2$, which is the difference between the first and second eigen value of the transition matrix. Then:

$$\tau_{\epsilon} \le O(\frac{1}{\gamma} \log \frac{n}{\epsilon}) $$

* $n$ is the number of states

Unfortunately computing the transition matrix can be hard to do, especially for high dimensional and/or continuous state spaces, it is useful to find other ways to estimate the mixing time.

Anternativelly we can examine the geometry of the state space. From this we can define the **conductance** $\theta$ of a chain as the minimum probability, over all subsets of states, of transitioning from that set to its complement:

$$
\phi = \min_{s: 0 \le p^*(S) \le 0.5} \frac{\sum_{x in S, x' \in S^c} T(x \rightarrow x')}{p^*(S)}
$$
* $\tau_{\epsilon} \le O(\frac{1}{\sigma^2} \log \frac{n}{\epsilon})$

In general chain that have low conductance have high mixin time. <span style="color:red">For example, distributions with well-separate modes usually have high mixing times</span>

## Practical convergence diagnostics
Computing the mixing time of a chain is in general quite difficult, since the transition matrix is usually very hard to compute. In practice we use various heuristics, where these methods do not diagnose convergence, but rather non-convergence, since diagnosinc convergence is computationally intractable. 

One of the simples approaches to assesing when a method has converged is to run multiple chains from very different **overdispersed** starting points, and to plot the samples from some variables of interest. This is called **trace plot**. If the chain has mixed, it should have "forgotten" where it started from, so the trace plots should converge to the same distribution, thus they should overlap.

## Estimated potential scale reduction (EPSR)

(Gelman and Rubin 1992)

An quantitative measure of convergence. The basic idea is to compare variance of a quantitiy within each chain to its variance across chains. 

Suppose we collect S samples (afther burn-in) from each C chains of D variables $x_{isc} , i = 1:D, s = 1:S, c = 1:C$. Let $y_{sc}$ be a scalar quantity of interest derived from $X_{1:D,s,c}$ (e.g $y_{sc} = x_{isc}$ for some choosen i). 

We define the within-seqence mean and overall mean as:

$$
\bar{y}_{.c} = \frac{1}{S}\sum_{s=1}^S y_{sc} \\
\bar{y}_{..} = \frac{1}{C} \sum_{c=1}^C \bar{y}_{.c}
$$

We define the between-sequence and within sequence variance as:

$$
B = \frac{S}{C-1} \sum_{c=1}^C(\bar{y}_{.c} - \bar{C}_{..})^2 \\
W = \frac{1}{C} \sum_{c=1}^C [\frac{1}{S-1} \sum_{s=1}^S(y_{sc} - \bar{y}_{.c})^2]
$$

We can now construct the two estimates of variance of y. The first estimate is $W$: this should underestimate $var[y]$ if the chain have not ranged over the full posterior. The second estimate is:

$$
\hat{V} = \frac{S-1}{S}W + \frac{1}{S}B
$$

This is an estimate of $var[y]$ that is unbiased under stationarity, but is an overestimate if the starting poins where overdisperse. From this we can define the **EPSR** diagnostic statistics:

$$\hat{R} = \triangleq \sqrt{\frac{\hat{V}}{W}} $$

This quantity measures the degree to which the posterior variance would decrease if we where to continue sampling in the $S \rightarrow \infty$ limit. If $\hat{R} \approx 1$ for any given quantity, than the estimate is reliable (or at least not unrealiable).
