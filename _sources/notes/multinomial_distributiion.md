# Multinomial
Generailizes a [Binomial distribution](binomial_distribution.md). Instead of flipping coins we can view this as rolling a K sided die. 

We define $x = (x_1, \cdots, x_K)$ be a random vector, where $x_j$ is the number of times side j of the die occurs. Then x has the following pmf:

$$X \sim Mu(n, \theta) \triangleq \binom{n}{x_1 \cdots x_K} \prod_{j=1} ^K \theta_j^{x_j}$$

* $\binom{n}{x_1 \cdots x_K}$ is the [multinomial coefficient](multinomial_coeffiicient.md)
* $\theta = {\theta_1, \cdots, \theta_K}$ is a probability simplex, where each entry denotes the probability that a dies turns up with face $k$.

## Multinoulli (Categorical)

Is a special case of Multinomial:
$$ Cat(x| \theta) \triangleq Mu(x| 1, \theta) = \prod_{j=1} ^K \theta_j^{x_j} $$

This can be also viewed as **One-Hot** encoding.