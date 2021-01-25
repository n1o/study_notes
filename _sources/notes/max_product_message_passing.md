# Max-product message passing

It a variant of [belief propagation](belief_propagation.md) used for MAP inference.

$$
\max_{x_1, \cdots, x_n} p(x_1, \cdots, x_n)
$$

We replace sums in [marginal inference](sum_product_message_passing.md) with max, to perform MAP estimation.

>Example:
>
> Given the following MRF
> $$
>Z = \sum_{x_1} \cdots \sum_{x_n} \phi(x_1)\prod_{i=2}^n \phi(x_i, x_{i-1}) \\
>= \sum_{x_n}\sum_{x_{n-1}}\phi(x_n, x_{n-1})\sum_{x_{n-2}}\phi(x_{n-1}, x_{n-2})\cdots >\sum_x \phi(x_2,x_1)\phi(x_1)
>$$
> To compute the maximum value $\tilde{p}^* of \tilde{p}(x_1,\cdots, x_n)$ we replace sum with max.
> $$ \tilde{p}^* = \max_{x_1} \cdots \max_{x_n} \phi(x_1) \prod_{i=1}^n \phi(x_1,x_{i-1}) \\ > \max_{x_n}\max_{x_{n-1}} \phi(x_n, x_{n-1})\max_{x_{n-2}}\phi(x_{n-1}, x_{n-2})\cdots \max_{x_1}\phi(x_2,x_1)\phi(x_1)$$


Here we use the same rules as with marginal inference.

If we want to calculate also the maximum value of the distribution $\arg \max_x p(x)$ we can use back-pointers during optimization. In the example above we need to keep a back-pointer to the best assignment to $x_1$ given each assignment to $x_2$, a pointer to the best assignment to $x_2$ given assignment $x_3$ and so on.