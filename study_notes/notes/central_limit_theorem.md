# Central Limit Theorem

The basic ida that if we have i.i.d random variables $X_1, \cdots, X_n$ where each of those random variables $E[X_i] = \mu, var(X_i) = \sigma$. Than if we take a the sum of those n i.i.d r.v's $S_n = X_1 + \cdots X_n$ than we get a new distribution where:

$$E[S_n] = n E[X_i] $$

$$ var(S_n) = n \sigma^2 $$

We can visualize this as a flat distribution. 

![Central Limit theorem](resources/E4418488A50A21A4D9D832904A6D6052.png)

Now we can push this futher to standardise this distribution to get a new distribution:

$$ Z_n = \frac{S_n - n \mu}{ \sqrt{n}\sigma}$$

This distribution now has:

$E[Z_n] = 0$
$var(Z_n) = 1$

and if $n \rightarrow \infty$ than the CDF of $Z_n$ converges to the standard normal CDF. Or more simply $Z_n \sim N(0,1)$