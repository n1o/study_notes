
# Monte Carlo approximation
Computing distributions of a function of an rv using just change of variables can be challenging. There is an alternative way. First we generate S samples from the distribution $x_1, \cdots, x_S$. Given these samples we can approximate the distribution of $f(X)$, using the empirical distribution of $\{f(x_i) \}_{s=1}^S$. Hence we can use Monte Carlo to approximate expected value's of functions of random variables. 

## Mean
To compute a mean we just have to calculate the arithmetic mean of the function applied to the samples:

$$ E[f(X)] = \int f(x)p(x)dx \approx \frac{1}{S} \sum_{s=1}^S f(x_s)$$

where:
* $x_s \sim p(X)$

If we wary $f()$ we can approximate quantities of interest as:
* $\bar{X} = \frac{1}{S} \sum_{s=1} x_s \rightarrow E[X]$
* $\frac{1}{S} \sum_{s =1 }^S (x_s - \bar{x})^2 \rightarrow var[S]$
* $\frac{1}{S} \# \{x_s \le c \} \rightarrow P(X \le c)$
* $median\{x_1, \cdots, x_S\} \rightarrow median(S)$

## Accuracy of MC estimates
As we draw more and more samples, the accuracy increases. If we denote the true mean $\mu = E[f(x)]$, and the estimate from MC $\bar{\mu}$ we can show:

$$ (\bar{\mu} - \mu) \rightarrow N(0, \frac{\sigma^2}{S}) $$

where:
* $\sigma^2 = var[f(x)]$ this is still unknonw but we can use MC to estimate.

This is a consequence of the central limit theorem.

Now we can calculate error bars on the mean using:
$P \{ \mu - 1.96 \frac{\hat{\sigma}}{\sqrt{S}} \le \hat{\mu} \le \mu + 1.96 \frac{\hat{\sigma}}{\sqrt{S}} \}$

Here:
* $\frac{\hat{\sigma}}{\sqrt{S}}$ is called the numerical (empirical)  **standard error** and is an estimate of our uncertainity about our estimate $\mu$. Now if we want our estimate to be within $\epsilon$ we need to draw at least $1.96 \sqrt{\sigma ^2 / S} \le \epsilon$ samples.







