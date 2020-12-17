# Hamiltonian monte carlo
Also called hybrid monte carlo since it combines MCMC and deterministic simulation

Hamiltonian monte carlo borrows an idea from physics to suppress the local random walk behaviour in Metropolis algorithm, allowing much faster progress trough the target distributions. 

For each compontent $\theta_j$ in target space, we add an momentum variable $\phi_j$. Booth $\theta_j$ and $\phi_j$ are updated together in an Metropolis algorithm, in which the jumping distribution for $\theta$ is determined by $\phi$. Each itreration of HMC has multiple steps, during which position and momentum evolves, where we move rapidly trough the space $\theta$, and we are able to turn corrners to preserve the total energy of the trajectory.

We can view the momentum as an auxiliary variable, since we are only interested in $\theta$. In HMC the posterior $p(\theta|y)$ is augumented by an independent distribution $p(\theta)$ defining:

$$p(\theta, \phi|y) = p(\phi)p(\theta|y) $$

To perform HMC we also require the gradient of $\log p (\theta|y)$

## Momentum distribution $p(\theta)$

Usualy $\phi$ is an multivariate Normal, with mean $0$ and covariance matrix set to an pre specified 'mass matrix' M (naming is due the analogy of Hamiltonian dynamics). We commonly use an diagonal M, so components of $\phi$ are independent, with $\phi_k \sim \mathcal{N}(0, M_{jj})$ . It is useful for M to roughly scale with the inverse covariance matrix of the posterior distribution $var[\theta|y]^{-1}$, this gives us an more efficient sampler, but it is not required.

## [Steps of HMC](hamiltonian_monte_carlo_steps.md)

## Restricted parameters and areas of zero posterior density

HMC works only with all positive target distributions. If we at a given state ned up in an region with negative probability we can change the sign of the momentum to bounce back to positive regions. This preserves detailed balance.. 

Another alternative is to reparametrize the model, take the log of params that are positive, sigmoid that are bounded between 0-1. However if we reparametrize we need to work out the Jacobian. 

## [Tunning parameters](hamiltonian_monte_carlo_tunning.md)

There are 3 places where we can tune HMC

1. Proposal distribution $p(\phi)$, where we can set the diagonal entries of the 'mass matrix' M
2. $\epsilon$ - scaling factor of the leap-frog steps
3. $L$ - number of leap-frog steps


### Riemanian adaptation

The mass matrix M is conform with local curvature of the log posterior density at each step. However this is inpractical in high dimensions.



## Combine HMC with other samples

If our model booth contains discrete and continuous distributions, it is common to partition the space into discrete and continuous parameters, then alternate between HMC update on continuous nad Gibbs/Metropolis on discrete 