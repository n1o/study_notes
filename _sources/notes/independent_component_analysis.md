# Independent component Analysis (ICA)

Consider the following situation. You are in a crowded room and many people are speaking. Your ears essentially act as two microphones, which are listening to a linear combination of the different speech signals in the room. Your goal is to deconvolve the mixed signals into their constituent parts. This is known as the cocktail party problem , and is an example of blind signal separation  (BSS), or blind source separation , where “blind” means we know “nothing” about the source of the signals.  Besides the obvious applications to acoustic signal processing, this problem also arises when analysing EEG and MEG signals, financial data, and any other dataset (not necessarily temporal) where latent sources or factors get mixed together in a linear way.

We can formatize this as follows.

Let $x_t \in R^D$ be the observed signal at the sensors at time t, and $z_t \in R^L$ be the vector of the source signals. We assume: 

$$x_t = Wz_t + \epsilon_t $$

* $W_{D\times L}$ called the **mixin matrix** and if $D = L$ (number of sources = number of sensors) than it is a square matrix. We do not require to W be orthogonal.
* $\epsilon_t \sim N(0, \Psi)$  $\Psi$ is the noise lefvel an we ofthen assume $|\Psi| = 0$

Here we assume that each observation is independent at each time point. (we do not model temporal correlation). 

The goal is to infer the source singal:

$$ p(z_t | x_t, \theta)$$

This setting is similar to PCA, a distinction is that we relax the assumption $p(z_t)$ to be any *non-Gaussian* distribution. And without loss of generality we constrain the variance of the source distribution to be 1. This resulting model is called **independent component analysis (ICA)**. 

We assume that

$$
p(z_t) \sim Laplace(\mu, b)
$$

The reason the Gaussian distribution is disallowed as a source prior in ICA is that it does not permit unique recovery of the sources.  This is because the PCA likelihood is invariant to any orthogonal transformation of the sources $z_t$  and mixing matrix $W$ . PCA can recover the best linear subspace in which the signals lie, but cannot uniquely recover the signals themselves.