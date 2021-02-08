# Forward vs reverse KL divergence

[KL divergence](kl_divergence.md) is not symmetric in its arguments, minimizing $K(q||p)$ wtr $q$ will give different behavior than minimizing $KL(p||q)$.

## Reverse $KL(q||p)$  (I-projection, information projection)

By definition we have:

$$KL(q||p) = \sum_x q(x) \ln \frac{q(x)}{p(x)} $$

This is infinite if $p(x) = 0$ and $q(x) \ge 0$. Thus if $p(x) = 0$ we must ensure $q(x) = 0$. We say that the reverse KL is **zero forcing for q.**  Hence **q will typically under-estimatethe support of p**.

## Forward $KL(p||q)$ (M-projection, moment projection) 

$$K(p||q) = \sum_x p(x) \ln \frac{p(x)}{q(x)} $$

This is inifinite if $q(x) = 0$ and $p(x) > 0$. So if $p(x) > 0$ we must ensure that $q(x) > 0$. We say that the forward KL is **zero avoiding for q**. Hence **q will typically over-estimate the support of p**.

> ![](../.images/machine_learning/kldiv.png)
> a) KL(p||q)
> b,cc) KL(q||p)
> 
> We can see that KL(p||q) overestimates but KL(q||p) chooses only one mode 
## Alpha divergence

Ofthen if we minimize $K(q||p)$ where $q$ is factorized, the result in an approximation that is overconfident. 

We can create a family of divergence measures indexed by a parameter $\alpha \in R$. By defining the **alpha divergence** as follows:

$$
D_{\alpha}(p||q) = \frac{4}{1 - \alpha^2}(1 - \int p(x)^{(1+\alpha)/2} q(x)^{(1- \alpha)/2})dx
$$

This measure satisfies $D_{\alpha}(p||q) = 0 \iff p = q$, but it is not symmetric, hence it is not a metric. $KL(p||q)$ correspondes to the limit $\alpha \rightarrow 1$, whereas $KL(q||p)$ corresponds to $\alpha \rightarrow -1$. When $\alpha = 0$, we get a symmetric divergence measure that linearly related to the **Hellinger distance** defined by:

$$
D_H (p||q) = \int (p(x)^{1/2} - q(x)^{1/2})^2 dx
$$

* $\sqrt{D_H (p||q)}$ is a valid distance metric. 

