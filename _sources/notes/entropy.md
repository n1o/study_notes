
# Entropy
Given we have a random variable $X$ with distribution $p$, we can say that the entropy of $H(X)$ is the measure of uncertainty. 

$$H(X)  \triangleq - \sum_{x \in A_X} p(x) \log_2 p(x) \\ 
= \sum_{x \in A_X} p(x) \log_2 \frac{1}{p(x)}$$

It measures the information content of an event in **bits** (If we would use base $e$ for the logarithm, the units we would measure entropy would be **nats**). And it can be viewed as the average [information content of an outcome](./shannon_information_content.md).


## Properties

* $H(X) = 0 \iff  p(x_i) =1$ for one $i$ (in other words only one event happens all the time thus we do not gain any information if it happens).
* Always positive or zero
* Entropy is maximised if $p$ is uniform

# Joint entropy


$$
H(X,Y) = \sum_{x\in A_x, y\in A_y } p(x,y) \log \frac{1}{p(x,y)}
$$

If $p(x,y) = p(x)p(y)$ then 

$$
H(X,Y) = H(X) + H(Y)
$$

Otherwise it is:
$$
H(X,Y) = H(X) + H(Y|X)
$$

## Binary entropy function
If X a bernoulli r.v with states $X = \{0,1 \}$ with $P(X=1) = \theta$ and $P(X=0) = (1 - \theta)$ the entropy has a special form:

$$H(X) = - [p(X=1)\log_2 P(X =1) + p(X =0)\log_2(X = 0)] $$

$$H(X) = - [-\theta\log_2 \theta + (1 - \theta)\log_2 (1 - \theta)] $$

And the maximum occurs when the distribution is uniform $\theta = 0.5$