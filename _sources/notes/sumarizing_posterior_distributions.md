# Map estimation
It is easy to compute because in most of the times it reduces to optimizaton problems. And it is easy to interpret it in an nonbayesian seting viewing it as a regularizer.

## Drawbacks:
1. There is no measure of uncertainity. This is however true also for estimates like mean or median. 
2. Overfitting. MAP estimates do not model uncertainity so they tend to overfit.
3. Untipical point. If the mode of the distribution is an untipical point, it can be a really bad choise (or if we are in higher dimensional settings).  Mean and the median at least take into account the total mass. It fails also for skewed distributions, (Gamma distribution). which occur in Hierarchical models. 
4. Not invariant to reparametrization. Given we find $\hat{x} = argmax_x p_x(x)$ and if we transform $y = f(x)$ using a function, than in general $\hat{y} = argmax_y p_y(y)$ these two values are not  the same. **MLE** does not suffer from this. And in bayseian inference this is all right since we do change of variables we need to introduce the jacobian.
  

# Credible intervals
We define an interval that contains some % of the total mass.  This will result in a lower or upper bound or in general in a function $C(l,u)$. This can either be done numerically if we know the CDF of a function than $l = F^{-1}(\alpha/2), u =F^{-1}(1 - \alpha/2)$. If we dont know it we can draw samples using MCMC.

# Highest posterior density (HDP)
Is a set of most probable points. So each point outside this set has a lower probability density. This can be hard for multimodal distributions.