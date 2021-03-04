# Empirical Distribution

Given a set of data $D = \{ x_1, \cdots, x_n \}$, we define the empirical distribution (empirical measure) as:

$$ p_{\text{emp}} (A) \triangleq \frac{1}{N} \sum_{i=1}^N \delta_{x_i}(A)$$

Where:
* $\delta_{x_i}(A)$ is the [Dirac delta](dirac_measure.md), defined by:

We could also associate weights with each sample:

$$ p(x) = \sum_{i=1}^N w_i \delta_{x_i}(x) $$

where $\sum_i w_i = 1$ and $0 \le w_i \le 1$. 

The Dirac delta is necessary only for continuous variables.
# Empirical CDF

We have $X_1, \cdots, X_n \sim F$ where F is an arbitrary CDF. We use the empirical CDF to approximate F.

$$\hat{F}(x) = \frac{\sum_j^n I(X_j \le x)}{n}$$

* $\sum_j^n I(X_j \le x)$ counts the number of elements less than x.
  
By the [Strong Law of Large number](law_of_large_numbers.md) the empirical CDF converges to the real CDF: $n \rightarrow \infty \Leftrightarrow \hat{F}_n(x) \rightarrow F(x)$