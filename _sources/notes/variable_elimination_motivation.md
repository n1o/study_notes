# Variable elimination motivation

Let assume the following Bayesian network:

$$
p(x_1,\cdots, x_n) = p(x_1)\prod_{i=2}^n p(x_i|x_{i-1})
$$

If we want to find the marginal probability $p(x_n)$, the naive way is to sum over the probability of all $k^{n-1}$ assignments:

$$
p(x_n) = \sum_{x_1}\cdots \sum_{x_{n-1}} p(x_1, \cdots, x_n)
$$

unfortunately this has a runtime of $O(k^n)$ which is not trackable for high n.

If we leverage the factorization of $p$, we can push some sums inside:

$$
p(x_n) = \sum_{x_1} \cdots \sum_{x_{n-1}}p(x_1) \prod_{i=1}^n p(x_i|x_{i-1}) \\ 
= \sum_{x_{n-1}}p(x_n|x_{n-1})\sum_{x_{n-2}}p(x_{n-1}|x_{n-2})\cdots \sum_{x_1} p(x_2|x_1)p(x_1)
$$

The summing starts from $x_1$ and ends with $x_{n-1}$, therefore we first sum out $x_1$ resulting an intermediate factor:

$$
\tau(x_2) = \sum_{x_1}p(x_2|x_1)p(x_1)
$$

This takes $k^2$ since we sum over $x_1$ for each assignment to $x_2$ (we can think about this factor as a table of k values (not necessarily probabilities) for each assignment to $x_2$). Now our marginal probability becomes:

$$
p(x_n) = \sum_{x_{n-1}}p(x_n|x_{n-1})\sum_{x_{n-2}}p(x_{n-1}|x_{n-2})\cdots \sum_{x_2} p(x_3|x_2)p(x_2)\tau(x_2)
$$

We can now compute the next factor $\tau(x_3) = \sum_{x_2} p(x_3|x_2) \tau(x_2)$ and repeat until we left only with $x_n$, each step taking $O(k^2)$ time with $O(n)$ steps, therefore the inference now takes $O(nk^2)$ time.

At each step we eliminate a variable (thus the name) and replace it with a factor.