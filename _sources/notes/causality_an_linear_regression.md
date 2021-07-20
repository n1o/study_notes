# Causality linear Regression

* in an ideal world we could observe booth potential outcomes and estimate the individual treatment effect:

$$
Y_i = Y_{i1} - Y_{i0} \\
Y_i = Y_{0i} + T_i(Y_{1i} - Y_{0i}) \\
= Y_{0i}(1 - T_i) + T_i Y_{1i}
$$

* instead we estimate the [average causal effect](causality_intro.md) (ATE)
  $$
    ATE = E[Y_1 - Y_0]
    $$
  * here the treatment effect is a constant
    $$
    Y_{1i} = Y_{0i} + k
    $$
  * if k is positive we can say, the treatment on average has a positive effect (Some people may respond badly)

* we can use linear regression to estimate the average treatment effect $k$

## Example:
* we want to examine what effect online classes have on exam scores: 
$$
\text{exam}_i = \beta_0 + k \times \text{online}_i + \mu_i
$$

* this regression recovers:
  * $E[Y|Y=0] = \beta_0$
  * $E[Y|Y=1] = \beta_0 + k$
  * $k$ = ATE


## Regression theory for Causality

* if we have a single regression variable $T$ (randomly assigned)

$$
y_i = \beta_0 + kT_i
$$
  * $k  = \frac{cov(Y,T)}{Y}$

* for multiple regression
    $$
    y_i = \beta_0 + k T_i + \beta_1 x_{1i} + \cdots \beta_k x_{ki} 
    $$
  * $k = \frac{cov(Y, \tilde{T})}{\tilde{T}}$
  * $\tilde{T}$ is the residual from a regression of all the other covariates $x_{1i}, \cdots, x_{ki}$ on $T_i$
* coefficient of a multivariate regression is the bivariate coefficent of the same regression after accounting for the effect of other variables in the model or k is the biavariate coeffcient of T after having used all other variables predicting it
* **intuition**
  * if we can predict T using other variables than T is not random
  * by controlling other variables we can make T good as random
  * to do it we use other variables to predict it and then we use the residuals $\tilde{T}$ of the prediciton
    * $\tilde{T}$ by definition cannot be predicted by other variables $X$ that are used to predict T
    * $\tilde{T}$ is a version of T that is not associated with any variable $X$

## Omitted variable of Confounding Bias

* in most cases we fail to control on some variable that is important, in some cases it is not possible to measure it
* to better understanding we assume the following true model:

$$
\text{wage}_i \alpha + k \times \text{edu}_i A_i' \beta_i
$$
* $A$ is an additional ability factors
* if we ommit ability from the model, the estimate for $k$ beocmes:

    $$
    \frac{cov(wage, educ)}{var(educ)} = k + \beta' \delta_{ability}
    $$
  * $\delta_{ability}$ is the coefficient from regression of A on Education
  * we got an extra term $\beta' \delta_A$, which is the impact of the ommited A on Wage, \beta times the inpact of the ommited on the included educ
* the bias term is zero if the ommited variable has no impact on the dependent variable Y (we do not control on variables that are irrelevan )
* the bias term is zero if the ommited term has no impact on the treatment variable (if everything that imacts education is included, there is no way to estimate the impact of education is mixed with correlation form education on something else that also impacts wage)
* there is no ommited variable bias if we include all confounding variables in the model
* causal graphs are an excelent way to depict our understanding of the worls and understanding the confounding bias

![](../.images/machine_learning/causal_graphs_understanding.png)

* causal inference with non-random observations data should be taken with a grain of salt