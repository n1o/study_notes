# Causality Matching
* if $(T_0,T_1) \perp T |X$ we can use [regression](causality_an_linear_regression.md) to find [ATE](causality_intro.md) while controlling for X
* the behind regression is
  * if we have only binary variables regression will partition the data into dummy cells and compute the mean different between the control and treatment in each cell
  * combines each cell outcome weighted by the cells variance in the treatment groups, with more weights for higher variance

* linear regression puts more weight to higher variance which in some cases may not be what we want

## Subclassiffication estimator
* to perform causal inference we need to make treatment and control comparable ($Y_0, Y_1 \perp T|X$), or we can say that we compare treatment and control within a small sub group where X is the same

$$
\text{ATE} = \int E[Y|X,T=1] - E[Y|X, Y=0]dP(x) \\
\hat{\text{ATE}} = \sum_{i=1}^k (\hat{Y}_{k1} - \hat{Y}_{k0})\frac{N_k}{N}
$$
* thus we compute the difference in means over the distribution of features X.
* this will fail in high dimension since some groups may not contain observations for booth treatment and control group

## Matching Estimator
* we match every treated with a similar untreated unit
* in most cases we measure similarity using a distance metric like euclidean norm $||X_i-X_j||$ which require to standardize the features for good performance

$$
\hat{\text{ATE}} = \frac{1}{N} \sum_{i=1}^N(2T_i -1)(Y_i - Y_{jm}(i))
$$
* $Y_{jm}(i)$ is the closes sample to unit i from the oposite group
* $2T_i$ is required since we match booth ways, treated -> control, control -> treated

### Matching Bias
* $\hat{\text{ATE}}$ is biased
* lets look at the ATE estimator
    $$
    \hat{\text{ATET}} = \frac{1}{N_1} \sum (Y_i - Y_j(i))
    $$
  * $N1$ is the number of treated individuals
  * $Y_j(i)$  is the untreated match for i
* $\hat{\text{ATET}}$ is also biased, and we have to unbias it
* to understand the source of bias we look at:
    $$
    \sqrt{N_1} (\hat{\text{ATET}} - ATET)
    $$
  * given the [central limit theorem](central_limit_theorem.md) this should converge to a zero mean gaussian
    * however this is not guaranteed to happend since:
        $$
        E[\sqrt{N_1} (\hat{\text{ATET}} - ATET)] = E[\sqrt{N_1} (\mu_0(x_i) - \mu_0(x_j(i)))]
        $$
        * $\mu_0 = E[Y|X=x,T=0]$ mean outcome of the untreated given X
        * $\mu_0(x_i)$ outcome Y of undreated unit i, thus it is the counterfactual outcome $Y_0$ for unit i
        * $\mu_0(x_j(i)$ is the outcome Y of the match for unit i, this is the facutal outcome since $j$ is from the untreated group
        * $\mu_0(x_i) - \mu_0(x_j(i))$ this in most cases wont be zero since the two are similar but different in most cases
        * if $\sqrt{N_1}$ grows faster than $\mu_0(x_i) - \mu_0(x_j(i))$ decreases than the expectation wont converge to zero

* to correct for bias we compute:

$$
\hat{\text{ATET}} = \frac{1}{N_1} \sum((Y_i - Y_j(i)) - (\hat{\mu}_0(x_i) - \hat{\mu}_0(x_j(i))))
$$
* $\hat{\mu}_0(x)$ is the estimate for $E[Y|X,T=0]$ like a linear regression fitted only on the untreated sample.

* to debias ATE we follow the same reasoning:

$$
\hat{\text{ATE}} = \frac{1}{N} \sum_{i=1}^N(2T_i -1)(Y_i - Y_{jm}(i)) - (\hat{\mu}(x_i) - \hat{\mu}_{j}(x_i))
$$

* $\hat{\mu}$ is the debiasing term fitted for the treated
* $\hat{\mu}_j$ is the debiasing term fitted for the untreated