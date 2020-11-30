# Ridge regression (Penalized least squares)

The MLE can easily overfit, since it tries to fit the data as best as possible, thus it results in complex functions. Example of ordinary least squares up to a 14 degree polynomial:

![](../.images/ridge_regression_example.png)

We get the following weights:
```
6.560, -36.934, -109.255, 543.452, 1022.561, -3046.224, -3768.013, 8524.540, 6607.897, -12640.058, -5530.188, 9479.730, 1774.639, -2821.526
```

Here we that we have many large positive and negative numbers. They balace each out thus resulting in a wiggly curve, that nearly perfectly interpolates the data. However this is guaranteed to overfit. To reduce overfitting we have to encourage these parameters to be small. A simple way of doing this is to put a Gaussian prior on our parameter estimation:

$$p(w) = \prod_j  \mathcal{N}(w_k | 0, \tau^2)$$

* $1/\tau^2$ control the strenght of the prior.

If we put this together than we have the corresponding MAP estimation problem:

$$\arg \max_w \sum_i^N \log \mathcal{N}(y_i| w_0 + w^Tx_i, \sigma^2) + \sum_i^D \log \mathcal{N}(w_j| 0, \tau^2)$$
Or equivalently we can express it as a minimization problem, where our loss function is:

$$J(w) = \frac{1}{N} \sum_i^N (y_i - (w_0 + w^Tx_i)^2) + \lambda ||w||_2^2 $$

* $\lambda \triangleq \sigma^2 / \tau^2$ is the complexity penalty.
* $||w||_2^2 = \sum_jw^2_j$ is the squared two-norm

Hence our estimate for $w$ is:

$$\hat{w}_{ridge} = (\lambda I_D + X^TX)^{-1}X^Ty $$

* $\lambda$ constrols the complexity choosen in cross-validation.

* we do not need to penalyze $w_0$ since it just affect the height of the function it do not contribute to complexity. 
* by penalizing the sum of magnitues of the weights, we ensure the function is simple (*w = 0 corresponds to a straight line, which is the simplest possible model*). 

* This naive way is not [numerically stable](numerically_stable_ridge_regression.md)