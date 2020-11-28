# Binomial distribution

Describes the number of successes out of total n [Bernoulli trials](bernouli_distributioin.md) with a set probability. Where it is bounded $(0,n)$ where n is the total number of trials.

## PDF:

$$ f(x| n, p) = \binom{n}{x}p^{x}(1-p)^{n-x}$$
* n is the total number of trials
* p is the probability of success on any given trial
* $\binom{n}{p}$ is the normalizing constant, defines the total number of ways x can be drawn out of n trials 


## Integral of an binomial distribution

$$\int_{0}^1  \binom{n}{k} \theta^k (1-\theta)^{n-k}d\theta = \binom{n}{k} \frac{\Gamma(k+1)\Gamma{(n - k +1)}}{\Gamma{(n+k)}}  = \frac{1}{n+1}$$

[An alternatively this can be explained using bayes biliard](bayes_biliard.md)

## Properties 
* variance is greatest when $p=0.5$ and decreases as p gets closer to either 0 or 1.
* when n is large and p is away from 0 or 1, it approaches the normal distribution 
* wne n is large and p is small, it approaches the Poisson distribution

## Convergence to Normal distribution

Since the Binomial distribution can be viewed as a sum of i.i.d Bern(p) random variable therefore for a large n, we can use the law or large number for approximation:

$$ Y \sim Bin(n,p) \approx  N(np, np(1-p))$$

Normal distribution is continuous but the binomial is discrete thus the probability $P(Y=k)$ would be 0. For this case we need to use the continuity correction:

$$ p(Y=k) = P(k-1/2 < Y < k + 1/2) \approx \Phi(\frac{k _ 1/2 - np}{\sqrt{np(1-p)}}) - \Phi(\frac{k - 1/2 - np}{\sqrt{np(1-p)}}) $$


## Connection to Hypergeometric

We have 2 Binomial distributions with the same probability $p$

$$X \sim \text{Bin}(n,p) \\
Y \sim \text{Bin}(m, p)$$

If we assume that $X \perp Y$ and take the sum of those two random variables $X + Y = r$. Now we can condition one of the distributions on the sum:

$$P(X|X+Y) = \text{HGeom}(n,m,r) $$

An example:
We have $n$ women and $m$ men. There is a virus and the probability that a random person is infected is $p$. Thus the number of infected woman is $X\sim Bin(n,p)$ and the number of infected men is $Y\sim Bin(m,p)$. Now we pick a random sample from the population and we want to know what is the probability that a sample size of x of woman is infected.


# Conjugacy
The conjugate prior for $p$ in $Bin(n,p)$ is the beta distribution $p \sim Beta(a,b)$ thus:

$$
p \sim Beta(a,b) \\
X \sim Bin(n,p) \\
p|X \sim Beta(a + k, b+n - k)
$$