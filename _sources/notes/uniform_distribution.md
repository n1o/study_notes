
# Uniform distribution 
The uniform distribution describes a square distribution with a specific range

$$ 
    U(x|a,b) = \begin{cases}
    \frac{1}{b-a} && \text{ for } a \le x \le b \\
    0 &&     \text{ otherwise }
\end{cases} $$

## Applications
It is as common vague prior distribution for precision (variance) in Bayesian modelling


# Universality
If we can sample from an uniform distribution we can sample from any continuous distribution. This comes from the fact that the CDF of any continuous distribution bound between 

$$\lim_{x \rightarrow -\infty}F(x) = 0; \lim_{x \rightarrow \infty} F(x) =1$$

Thus this holds:

$$
F(X) \sim Unif(0,1)
$$

Thus if the CDF is a one-to-one function than if we can perform:

$$
U \sim Unif(0,1) \\
X = F^{-1}(U)
$$

Now X is a random variables with CDF F. 

This an be proven:
Let:

$$U \sim Unif(0,1) \\ X = F^{-1}(U)$$

Than:

$$
P(X \le x ) = P(F^{-1}(X) \le x) = P(U \le F(x)) = F(x)
$$

And we can prove it backwards:
$$
Y = F(X)
$$

Since $F$ is a CDF than Y is bound $y \in (0,1)$ thus:

$$
P(Y \le y) = P(F(X) \le y) = P(X \le F^{-1}(y)) = F(F^{-1}(y)) = y
$$