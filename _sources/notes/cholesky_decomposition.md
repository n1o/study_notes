# Cholesky Decomposition
Useful if we want to decomposie a positive-definite Hermetian matrix into 2 parts. First is a lower triangular matrix and the second is its conjugate transpose.

$A = L L^T$


## Calculating the inverse
We can use this decomposition to calculate the inverse:

$A^{-1} = (L^{-1})^T (L^{-1})$

It is easier to calculate the inverse of a triangular matrix and in general it provides more stable solutions that direct inverting.

More here:
http://www.mcs.csueastbay.edu/~malek/TeX/Triangle.pdf