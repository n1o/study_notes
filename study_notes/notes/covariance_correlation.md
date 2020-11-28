# Covariance
Is a single number sumary of the joint distribution of two random variables, which measures their linear dependence. In human language it measures how much two random variables go up or down together. 

## Equation:
$$cov(X,Y)= E[(X - E[X])(Y - E[Y])] = E[XY] - E[X]E[Y] $$

## Properties
If two random variables are independent then they are uncorelated. **However this is not true for the converse**

1. $cov(X,X) = var(X)$
2. $cov(X,Y) = cov(Y,X)$
3. $cov(X,c) = 0$ for any constant c
4. $cov(aX, Y) = a cov(X,Y)$ for any constant a
5. $cov(X + Y, Z) = cov(X,Z) + cov(Y,Z)$
6. $var(X + Y) = var(X) + var(Y) + 2 cov(X,Y)$

## Covariance Matrix

Now **covariance matrix** defines the pairwise covariances between multiple random variables:

$$
Cov[X,Y] = \begin{bmatrix}
    Var[X] & Cov[X,Y] \\ Cov[Y,X] & Var[Y] 
\end{bmatrix}
$$

This matrix is symmetric and positive definite. 

# Correlation (Pearsons correlation coefficient)


$$Cor[X,Y] \triangleq \frac{Cov[X,Y]}{\sqrt{ Var[X] Var[Y]}}$$

Thus we can define the **correlation matrix** as:

$$
Cor[X,Y] = \begin{bmatrix}
    1 & Cov[X,Y] \\ Cov[Y,X] & 1
\end{bmatrix}
$$

Here the entries on the main diagonal are $1$ and the rest is $-1 \le Cor[X,Y] \le 1$. We can view **corrleation** as the degree of linearity, and if $Y = aX + b$ then $corr[X,Y] =1$.

If X and Y are independent then their correlation is 0 (**The converse does not hold**) 