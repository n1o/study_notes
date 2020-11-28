# Dirichlet Multinomial model

Here we generalize the notion of a coin flip where only 2 possible outcomes are possible, to the notion of a K sided die roll.

## Likelihood
If we observe N die rolls $D = \{ x_1, x_2, \cdots, x_N\}$, where $x_i \in \{1,2, \cdots, K \}$ we assume the data is i.i.d, the likelihood has the form:

$$p(D|\theta) = \prod^K_{k=1}  \theta_K^{N_k}$$

where:
* $N_K = \sum_{i=1}^N I(y_1 = k)$ is the number of times event k occured. (this is the sufficient statistics). Here we do not really care about the multinomial coeficient since it is an irrelevant constant factor.

## Prior
We need to put a prior on the parameter $\theta$ which is a K dimensional probability distribution. We use a Dirichlet distribution, which has support over all K dimensional probability simplex. And it is a conjugate prior to a multinomial distribution.

$$ Dir(\theta| \alpha) = \frac{1}{B(\alpha)} \prod_{k=1}^K \theta_k^{\alpha_k - 1}I(x \in S_k) $$

## Posterior 

$$ p(\theta| D) \propto p(D| \theta)p(\theta) \\
\propto \prod^K_{k=1}  \theta_K^{N_k} \theta_k^{\alpha_k - 1} = \prod_{k=1}^K \theta_k^{\alpha_k + N_k -1} \\ = Dir(\theta| \alpha_1 + N_1, \cdots, \alpha_k + N_K)$$

## MAP
The MAP estimate is:

$$\hat{\theta_k} = \frac{N_K + \alpha_k - 1}{N - \alpha_0 - K} $$

which is just the **mode of a dirichlet distribution**

and if we set $\alpha_k =1$ than we recover the MLE. (Empirical fraction of times face k shows up)

## Posterior predictive distribution

$$P(X = j |D) = \int p(X = j| \theta)p(\theta| D) d\theta \\
=\int p(X = j| \theta_j) [\int p (\theta_{-j}, \theta_j | D) d\theta_{-j}]d\theta_j \\ 
=\int \theta_j p(\theta_j| D)d\theta_j = E[\theta_j|D] = \frac{\alpha_j + N_j}{\alpha_0 + N}
$$