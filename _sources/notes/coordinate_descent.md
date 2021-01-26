# Coordinate descent

It is quite simple, and efficient if used in the right setting. A more appropriate name would be coordinatewise minimization.

Exactly mimize alog coordinates, or blocks of variables, in a sequential fashion.\

## Coordinate wise minimum

We have a convex differentiable function $f: R^n \rightarrow R$, if we are at a point x such that $f(x)$ is minimized along each coordiate axis, the we have found a global minimizer.

Example we are a point $x_0$ on the x coordiate axis, and by moving in any direction on the x axsis we increate the function value.

## Algorithm (Cyclic coordinate descent)

This suggest that for $f(x) = g(x) + \sum_{i =1}^m h_i(x_i)$ with g convex differentiable and each $h_i$ convex, we can use coordiate descent to find a mimizer. Starting with our initial guess $x^0$ and repeat:

$$
    x_1^k = \argmin_{x_1} f(x_1, x_2^{k-1}, x_3^{k-1}, \cdots, x_n^{k-1} )\\
    x_2^k = \argmin_{x_2} f(x_1^k, x_2, x_3^{k-1}, \cdots, x_n^{k-1} ) \\
    x_3^k = \argmin_{x_3} f(x_1, x_2, x_3, \cdots, x_n^{k-1} ) \\
    \vdots \\
    x_n^k = \argmin_{x_n} f(x_1, x_2, x_3, \cdots, x_n )
$$
for $k=1,2,3,\cdots$. Afther solving for $x_j^k$ we use its new value form then on.

**Notes**

- The order of cycle through coordinates is arbitrary, can use any permutation of $\{ 1,2,\cdots, n \}$

- Can everywhere replace individual coordinates with blocks of coordinates

- "One-at-a-time" update scheme is critical, and "all-at-once" scheme does not neccesarily converge.

## Examples

### Linear regression.

$y \in R^n$ and $X \in R^{n \times p}$, with  columns $X_1, \cdots, X_p​$ consider the linear regression:

$min_{\beta} \frac{1}{2} || y - X\beta||_2^2$

We can minimize over all $\beta_i$, with all $\beta_j, j \ne i$ fixed:

$$0 = \nabla_i f(\beta) = X_i^T (X\beta - y)  = X_i^T (X_i \beta_i + X_{i-1}\beta_{i-1} - y)$$

we take:

$\beta_i = \frac{X_i^T (y - X_{-i}\beta_{-i})}{X_i^T X_i}$

Here coordinate descent repeates this update for $i = 1,2,3, \cdots, p, 1,2,3, \cdots$

### Lasso regression

$min_{\beta} \frac{1}{2} ||y - X \beta||_2^2$

The update rule for $\beta_i$

$\beta_i = S_{\lambda / || X_i||^2_2} (\frac{X_i^T(y - X_{-i}\beta_{-i})}{X_i^T X_i})$

### SVM

This can also be done check.

## Performance

Each coordinate costs $O(n)$ flops, $O(n)$ to update r, $O(n)$ to compute $X_i^Tr$



## Scalability

Since we optimize a coordinate at a time, we don't need to keep the whole in the memory.



## Optimization

### Warm start

We compute a solution across $\lambda_i > \lambda_1 > \cdots > \lambda_r$ until we arrive arrive at a $\lambda$ that is close to our lambda. Where we use the previous $\lambda_{i-1}$ as a warm start for finding $\lambda_i$. 