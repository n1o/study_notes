# Robust linear regression

Normaly we assume that a [linear model](linear_regression.md) is of a form:

$$p(y|x, \theta) = \mathcal{N}(y| w^Tx, \sigma^2)$$

However this setting is sensitive to outliers. If we would like to make it more robust, we have to change the likelihood distribution, to a heavy tailed distribution. 

We can use [Laplace distribution](laplace_distribution.md):

$$p(y|x,w,b) = Lap(y|w^Tx, b) \propto \exp(-\frac{1}{b}| y - w^Tx|) $$

Here the robustness arises from the use of $|y - w^Tx|$ istead of $(y - w^Tx)^2$.  If we assume that $b$ is fixed, our NNL becomes

$l(w) = \sum_i |r_i(w)|$

where

* $r_i \triangleq y_i - w^Tx_i$

Unfortunatelly this is a nonlinear objective function, which is hard to optimize. We can convert the NNL to a linear objective function using the **split variable** trick:

$$r_i \triangleq r^+_i - r^{-}_i$$

We get the following contrained optimization problem

$$min_{w,r^+,r^-} \sum_i(r_i^+ + r^-_i)$$ 

st:

$$ r_i^+ \ge 0, r_i^- \ge 0, w^Tx_i + r_i^+ + r_i^- = y_i $$

This is a [linear programm](linear_programming.md) which we can convert to standard form:

$$
\min_{\theta} f^T\theta \space \text{ s.t: } \space A\theta \le b, A_{eq}\theta = b_{eq}, 1 \le \theta \le u
$$
* $\theta = (w, r^+, r^-)$
* $f = [0,1,1]$
* $A = []$
* $b = []$
* $A_{eq} = [X, I,I]$


Alternativelly we can choose to minimize the **Hubert loss**. 

$$L_H(r, \delta) = \begin{cases} r^2/2 & \text{ if } |r| \le \delta \\ \delta|r| - \delta^2/2 & \text{ if } |r| > \delta \end{cases} $$

This is equivalent to $l_2$ for errors that are smaller than $\delta$ and $l_1$ for larger errors. Advantage of this method is that it is differentiable. And we can use [Quasi-newton](quasi_newton.md) instead of LP. (Faster)  
