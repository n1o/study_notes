
# Bridge regression

Generalization of $l_1$ [regularization](l1_regularization.md).

$$\hat{w} = NNL(w) + \lambda \sum_j|w_j|^b $$

* $b \ge 0$

This corresponds to MAP estimation using **exponential pover distribution**

$$
ExpPower(w| \mu, a,b) = \frac{b}{1a\Gamma(1 + 1/b)} \exp{ - \frac{|x - \mu|^b}{a}}
$$

If:
* $b = 2$ we get an gaussian with $a = \sigma \sqrt{2}$ correspoding to ridge regression
* $b=1$ we get the Laplace distribution corresponding to lasso
* $b =0$ we get $l_0$ regression.