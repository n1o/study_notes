
# Bayesian t-test
We want to test the hypothesis that $\mu \ne \mu_0$ foro some known value $\mu_0$ (ofthen 0), given values $x_i \sim N(\mu, \sigma^2)$. This is called a **two-sided one sample t-test**. We perform this test by checking if $\mu_0 \in I_{0.95}(\mu|D)$. If not than we can be 95% sure that $\mu \ne \mu_0$. A more common scenario is when we want to test if two paried samples have the same mean. 

$$y_i \sim N(\mu_1, \sigma^2) \\ z_i \sim N(\mu_2, \sigma^2)$$ 

We want to determine if $\mu = \mu_1 - \mu_2 \ge 0$ using $x_i = y_i - z_i$

This can be evaluted as:

$$
p(\mu \ge \mu_0|D) = \int_{\mu_0}^{\infty}p(\mu|D)du
$$

This is called **one sided paired t-test**.

To find $p(\mu|D)$ we specify an uninformative prior the [posterior marginal](normal_inverse_chi_squared.md) on $\mu$  is T distributed:

$$
p(\mu|D) = T(\mu| \bar{x}, \frac{s^2}{N}, N - 1)
$$

Now we define the *t-statistics* as:

$$
t \triangleq \frac{\bar{x} - \mu_0}{s/\sqrt{N}}
$$

* $s/\sqrt{N}$ is the standard error of the mean

Thus the posterior:
$$
p(\mu|D) = 1 - F_{N-1}(t)
$$

* $F_v(t)$ is the CDF of the standard [Student t distribution](student_t_distribution.md) $T(0,1,v)$
  
## Connection to frequentist
Using uninformative prior gives us the same result as using frequentist methods. 

**Frequentist**
$$\frac{\mu - \bar{x}}{\sqrt{s/N}}| D \sim t_{N-1}$$

**Bayesian**
The sampling distribution of the MLE:

$$
\frac{\mu - \bar{X}}{\sqrt{s/N}}| \mu \sim t_{N-1}
$$

The reason is that the Student T distribution is symmetric in its first two arguments

$$
T(\bar{x}| \mu , \sigma^2, v) = T(\mu| \bar{x}, \sigma^2, v)
$$

The results are similar but have different interpretation. In the Bayesian approach $\mu$ is unknown and $\bar{x}$ is fixed. In frequentist $\bar{X}$ is unkown and $\mu$ is fixed.