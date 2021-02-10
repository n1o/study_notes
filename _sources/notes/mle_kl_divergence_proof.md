We use the [empirical distribution](empirical_distribution.md) to prove this. The empirical distribution is defined as

$$
\tilde{p}(x) = \frac{1}{N} \sum_{i=1}^N\delta(x, \bar{x}_i)
$$

Thus the probability of a data point x is proportional to the number of times it is found in the training data D.

The KL divergence between our model $p(x|w)$ and the empirical density $\tilde{p}$ is defined as:

$$
D_{KL}(\tilde{p}(x)|| p(x|w)) = \sum_x \tilde{p}\log \frac{\tilde{p}(x)}{p(x|w)}=
\sum_x \tilde{p}\log \tilde{p}(x) - \sum_x \tilde{p}(x) \log p(x|w)
$$

We can ignore $\sum_x \tilde{p}\log \tilde{p}(x) = -H(\tilde{p}(x))$, our minimization becomes:

$$
\min_w D_{KL}(\tilde{p}(x)||p(x|w)) = \min_w - \sum_x \tilde{p}(x) \log p(x|w)
$$

We can turn this into a maximization:

$$
\max_w - D_{KL}(\tilde{p}(x)||p(x|w)) = \max_w \sum_x \tilde{p}(x) \log p(x|w)
$$

And plug in the definition of the empirical distribution $\tilde{p}$

$$
\max_w \sum_x \frac{1}{N} \sum_{i=1}^N \delta(x,x_i) \log p(x|w)
$$

We swap the sums, and $\delta(x,x_i)$ is nonzero only when $x = \bar{x}_i$, the optimization reduces to:

$$
\max_w \frac{1}{N} \sum_{i=1}^N \log p(\tilde{x}_i|w)
$$
