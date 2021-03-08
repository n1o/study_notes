# Numeric computation

## Poor conditioning for matrix Inversion
Lets define the following function:

$$
f(x) = A^{-1}x \\ 
A \in R^{n \times n}
$$

* A is square thus it has eigenvalue decomposition

The conditioning number of the matrix is the magnitude of the largest and smallest eigenvalue

$$
\max_{i,j} |\frac{\lambda_i}{\lambda_j}|
$$

If the conditioning number is large, the matrix is sensitive to error in input. Poor conditioned matrices multiply pre-existing errors, and errors will be compounded further by numerical errors in inversion.