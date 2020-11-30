# Dirac measure / Dirac delta

It is an infinitely narrow gaussian centered at an point. Mathematically:

$$
\delta_x (A) = \begin{cases}
1 & \text{ if } x \in A \\ 
0 & \text { if } x \notin A
\end{cases}
$$

Such that:

$$ \int_{-\infty}^{\infty} \delta(x)dx = 1 $$

## Usage
It can be used to select a single term from an integral:

$$ \int_{-\infty}^{\infty} f(x)\delta(x - \mu)dx = f(\mu)$$