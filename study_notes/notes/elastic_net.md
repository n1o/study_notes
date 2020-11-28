
# Elastic Net (ridge and lasso combined)

Although lasso has proved to be effective as a variable selection technique, it has several problems such as the following:

* If there is a group of variables that are highly correlated, the lasso tends to select only one of them, choosen rather arbtirary.
* If $D > N$ case lasso can select at most N variables
* If $N > D$, but the variables are correlated, it has been empirically observed that the perdiction performance of ridge regression is better than that of lasso.

To overcome these shortcomming we use an approach called the **elastic net** which is a hybrid between lasso and ridge regression. 

**Objective function**

$$J(w, \lambda_1, \lambda_2) = || y - Xw||^2 + \lambda_2||w|||_2^2 + \lambda_1 ||w||_1 $$

This penalty is *strictly convex* ($\lambda_2 > 0$)  there is a unique global minimum, even if X is not full rank. Now since we have a strictly convex penalty on w will exhibit a **grouping effect**, which means that the regression coefficients o highly correlated variables tend to be equal. 

## Reduction to lasso
Elastic net problem can be reduced to a lasso problem:

This can be solved as:

$$
\hat{w} = \argmin_{w} w^T {\frac{X^TX + \lambda_2 I}{1 + \lambda_2}}w - 2y^TXw + \lambda_1||w||_1
$$

* $\frac{X^TX + \lambda_2 I}{1 + \lambda_2} = (1 - \rho)\hat{\Sigma} + \rho I$


## Bayesian view

The implicit prior used by elastic net has the form:

$$
p(w| \sigma^2) \propto \exp( - \frac{\gamma_2}{\sigma} \sum_{j=1}^D |w_j| - \frac{\gamma_2}{2\sigma^2}\sum_{j=1}^D w_j^2) 
$$

which is the product of a Gaussian and Laplace distributions. And can be written as a hierarchical prior as:

$$
w_j | \sigma^2, \tau_j^2 = N(0, \sigma^2 (\tau_j^{-2} + \gamma_2)^{-1}) \\
\tau_j^2| \gamma_1 \sim Expon(\frac{\gamma_1^2}{2})
$$

If $\gamma_2 = 0$ we reduce to lasso.