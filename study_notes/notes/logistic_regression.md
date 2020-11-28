# Logistic regression
It can be viewed as a binary classification model defied as:

$$ p(y|x,w) = Ber(y| sigm(w^Tx))$$

Now we can threshold $p(y|x,w) = 0.5$ to classify $y=1$, if we do this we get a linear decision boundary. 

We can interpret logistic regression in therms of **log ods** $LO \triangleq \log \frac{p(y=1| x)}{p(y=0| x)}$. If this is a linear function than we can interpert the coefficients as the increase in $e^w$. 

Example:

If we want to model the relationship between smoking a cigarete and gettng lung cancer. If our weight on smoking cigarete is $w=1.3$, than we can say that by smoking a cigarete the probability of getting cancer increases by $e^{1.3}$

## MLE
The negative log likelihood  is given by:

$$ NLL(w) = - \sum_{i =1}^N[y_i \log \mu_i + (1 - y_i)\log(1 - \mu_i)]$$

* $\mu_i = sigm(w^Tx_i)$


This is alsocalled the **cross-entropy error** function. Unfortunately there is no closed form for finding the MLE of this function. We need to use optimization algorithms to find its minimum. The MLE is not well defined if the two classes are linearly separable. If this happens $w$ becomes large and the sigmoid becomes a step function.

## Gradient
We can use any [first order method](first_order_methods.md) like gradient descent:
$$g = \frac{d}{dw} NLL(w) = \sum_i (\mu_i - y_i)x_i = X^T(\mu - y)$$

## Hessian
We can use any [second order method](second_order_methods.md) like Newtons.
$$H = \frac{d}{dw} g(w)^T = \sum_i (\nabla_w \mu_i)x_i^T = \sum_i \mu_i( 1 - \mu_i)x_i x_i^T = XS^TX$$

* $S \triangleq diag(\mu_i (1 - \mu_i))$
* $H$ is positive definite, hence NLL is convex and has a unique global minimum.


## L2 regularization

As with [linear regression](linear_regression.md) we can put a Gaussian prior onto our weights in logistic regression. Now our Gradient and Hessian becomes:

*  $f'(w)= NLL(w) + \lambda w^Tw$
* $g'(w) = g(w) + \lambda w$
* $H'(w) = H(w)  + \lambda I$

## [Multi class logistic regression](multiclass_logistic_regression.md)
We can extend logistic regression to multiclass classification.

##  Bayesian Logistic regression

Unfortunatly there is no closed formula to compute the posterior distribution for logistic regression. We have to approximate it instead.

## Gaussian approximation with prior

We perform [Gaussian Approximation](gaussian_approximation.md) of the posterior. First we put an Gaussian prior $p(w) = N(w| 0, V_0)$ the posteriior becomes:

$$
p(w|D) = N(w| \hat{w}, H^{-1})
$$

* $\hat{w} = \arg \min_w E(w)$
* $E(w) = -(\log p (D|w) + \log p(w))$
* $H = |\nabla^2E(w)|_{\hat{w}}$


