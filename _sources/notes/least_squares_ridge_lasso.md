# Comparing OLS with Ridge and Lasso

If we assume that $X$ is orthonormal $X^TX = I$ we can express RSS as:

$$
RSS(w) = ||y - Xw||^2 = y^Ty + w^TX^TXw - 2w^TXy \\
= const + \sum_k w_k^2 - 2\sum_k \sum_i w_kx_{ik}y_i
$$

It factorizes into a sum of terms, one per dimension.

## OLS solution is given:

$$
\hat{w}_k^{OLS} = x_{:k}^Ty
$$

This is just an orthogonal projection of feature k onto the response vector.

## Ridge

$$
\hat{w}_k^{RIDGE} = \frac{\hat{w}_k^{OLS}}{ 1 + \lambda}
$$

## LASSO
$$
\hat{w}_k^{LASSO} = sing(\hat{w}_k^{OLS}) (|\hat{w}_k^{OLS}| - \frac{\lambda}{2})
$$
