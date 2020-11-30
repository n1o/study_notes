# Law of large numbers

Describe the behaviour of the **sample mean of i.i.d. r.v.s as the sample size grows**. 

If we have a sequence of i.i.d. r.v.s  $X_1, X_2, \cdots$ with finite mean $\mu$ and variance $\sigma^2$. 

The sample mean of this of this sequence is:

$$E[\bar{X}_n] = \frac{1}{n} E(X_1 + \cdots + X_n) = \mu$$

And the variance:

$$Var(\bar{X}_n) =  Var(\frac{X_1 + \cdots + X_n}{n}) = \frac{1}{n^2}Var(X_1 + \cdots + X_n)  = \frac{\sigma^2}{n}$$

## Strong law of large number:
In the limit $n \rightarrow \infty$ the sample mean converges $E[\bar{X}_n] \rightarrow \mu$

## Weak law of large numbers:
States that we can make the difference between the sample mean and  the true mean as small as we want if we allow n to grow. $P (|E[\bar{X}_n] - \mu| < \epsilon )$ with $\epsilon$ sufficiently small.



