# Gibbs sampling
Can be viewed as [MCMC](markov_chain_monte_carlo_inference.md) analog of [coordinate descent](coordinate_descent.md). It is also known as **Guauber dynamics** or **heat bath** method or **aternating conditional sampler**.

## Basic idea
The basic idea behind Gibbs sampling is that we sample each variable in turn, conditioned on the values of all the other variables in the distribution. That is given a joint sample $x^s$ of all the variables, we generate a new sample $x^{s+1}$ by sampling each component in turn, based on the most recent values of the other variables:

An example for a joint distribution $p(x_1, x_2, x_3)$ we sample:

$$
    x_1^{s+1} \sim p(x_1| x_2^s, x_3^s)\\
    x_2^{s+1} \sim p(x_2| x_1^{s+1}, x_3^s) \\
    x_3^{s+1} \sim p(x_3| x_1^{s+1}, x_2^{s+1})
$$

We can generalize this to D variables. If $x_i$ is visible we do not need to sample it since it is already known. The expression $p(x_i|x_{-i})$ is called the **full conditional** for variable i. In general $x_i$ may only depend on some of the other variables. If we represent $p(x)$ as a graphical model, we can infer the dependencies by looking at *i'ts Markov blanket*. 

In general we need to throw away the initial samples until the Markov chain has **burned in**, or entered its stationary distribution.

## Collapsed Gibbs sampling

In some cases, we can analyticaly integrate out some of the unknown quantities, and just sample the rest. This is called **collapsed Gibbs sampler**, and it tends to be much more efficient, since it is sampling in a lower dimensional space. 

Example:

Suppose we sample $z$ and we integrate out $\theta$. Thus $\theta$ parameters do not participate in the Markov chain; consequently we can draw conditionally independent samples $\theta^s \sim p(\theta|z^s, D)$, which has much lower variance than sample drawn from the joint state space. This process is callled [Rao-Blackwellisation](rao_blackwell.md)

## Imputation posterior (IP ) algorithm

The Imputation Posterior or IP algorithm is a special case of Gibbs sampling in which we group the variables into two classes: hidden variables $z$ and parameters $\theta$. This should sound familiar: it is basically an MCMC version of EM, where the E step gets replaced by the I step, and the M step gets replaced the P step. This is an example of a more general strategy called data augmentation, whereby we introduce auxiliary variables in order to simplify the posterior computations (here the computation of $p(\theta|D)$).

## Blocking Gibbs sampling

Gibbs sampling can be quite slow, since it updates only one variable at a time. (called **single site updating**). If the variables are highly correlated, it will take a long time to move away from the current state. In some cases we can sample groups of variables at a time. This is called **blocking Gibbs sampling** or **blocked Gibbs sampling**. Using this we can achieve bigger moves through the state space.