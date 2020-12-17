# Hamiltonian Monte Carlo Tunning parameters

There are 3 places where we can tune HMC

1. Proposal distribution $p(\phi)$, where we can set the diagonal entries of the 'mass matrix' M
2. $\epsilon$ - scaling factor of the leap-frog steps
3. $L$ - number of leap-frog steps

If we perform adaptive tunning of these parameter we need to split into a warmup stage, where alter the parameters and fixed, where the parameters are fixed, and from which we keep samplers for inference.

## How to set HMC

1. M should be a crude scale of the target distribution. But by default we can use the identity matrix.
2. Set $\epsilon L = 1$. With an default $\epsilon = 0.1, L = 10$.
3. The target acceptance we should aim for $65%$. If it is lower then we should lower $\epsilon$ and  increase L, and vice versa

### Locally adaptive HMC

For dificult problems, it would be desirable for the tunning parameters to wary as the algorithm moves trough the posterior distribution, with the mass matrix M scaling the local curvature of the log density, the step size $\epsilon$ getting smaller in areas of high curvature, and $L$ large enough to move far trough the posterior, without truning arround. These requriements fuel more complicated algorithms but they are more efficient. Examples:

### No U-turn sampler

Here we adapt L at each step instead of running it for a fixed length. The trajectory at each iteration continues until it turns arround (until the dot product between the momentum variable $\phi$ and the distance traveled from the position $\theta$ at the start it not negative) . However this alone is not enough, since ti does not guarantee that we will statisfy detailed balance equation, and we need to alow for moving tovard and backward along the trajectory. This procedure also adaptively tunes the mass matrix M and $\epsilon$ during warm up phase, but it is fixed after. 

No U-turn sampler has difficulties exploring distributions with very short-tails or very long-tails. It fails to transition from center to the tails. 