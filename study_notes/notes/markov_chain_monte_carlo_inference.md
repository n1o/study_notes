# Markov chain Monte Carlo (MCMC) inference
In general classic [Monte Carlo methods](monte_carlo_inference.md) do not work well in high dimension space. MCMC are more efficient. 

The basic idea of MCMC is to construct a Markov chain on the state pace $X$ whose stationary distribution is the target density $p^*(x)$ of interest. That is, we perform random walk on the state space  X is proportional ot $p^*(x)$. By drawing **correlated** samples $x_0, x_1, \cdots$, from the chain, we can perform Monte Carlo integration with respect to $p^*$.

## Commong algorithms
* [Gibs Sampling](gibs_sampling.md)
* Metropolis hastings
* Hamiltonian monte carlo

## Speed and accuracy of MCMC

We start MCMC from an arbitrary initial state. If we see enough samples, only than has the chain "forgotten" where it has started from will the samples be comming from the chain's stationary distribution. Samples collected before the chain has reached its stationary distribution do not come from $p^*$, and are usually thrown away. The initial period, whose samples will be ignored, is called **burn-in phase**.

Unfortunatelly diagnose when a chain has burned in is difficult, and it is one of the fundamental weaknesses of MCMC. 

## [Mixing rates of Markov chains](markov_chain_monte_carlo_convergence.md)
The amount of time it takes for a Markov chain to converge to the stationary distribution, and forget its initial state, is called the **mixing time**. 

## [Accuracy of MCMC](markov_chain_monte_carlo_accuracy.md)
Samples produces by MCMC are autocorrelated, and this reduces their information content relative to independent or perfect samples. Thus we need to estimate how accurate the samples are.

## How many chains

In practice it is common to run a medium number of chains (~3) of medium lenght (~ 100k steps), and take samples from each afther discarting the first half of the samples. If we initialize at a local mode, we may be able to keep more samples, sometimes we can keep all of them. 