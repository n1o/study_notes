# 0-1 Loss
Is common in binary classification.

$$L(y,a) = I(y \ne a) = \begin{cases} 0 && \text{ if } a = y \\ 1 && \text{ if } a \ne y \end{cases}$$

The posterior expected loss is given as:

$$p(a|x) = p(a \ne y|x) = 1 - p(y|x) $$

And the action that minimizes the expected loss is the posterior mode or MAP estimation:

$$y^*(x) = \arg \max_{y \in Y}p(y|x)$$

# Rejection option

In some cases when there is large uncertainity about $p(y|x)$ we may choose to reject action, in which we refuse to classify the example as any of the specified classes, and we just say that we dont know. This is usefull in risk averse domains. 

We can choose one of the C classes $a \in \{ 1, \cdots, C\}$, or we can choose $a = C+ 1$ is we want to reject the action.

Loss function:

$$ L(y =j, a =i) = \begin{cases} 0 && \text{ if i = j and } i,j \in \{ 1, \cdots, C\} \\ \lambda_r && \text{ if i = C + 1}  \\ \lambda_s &&  \text{ otherwise } \end{cases} $$

Where:

* $\lambda_r$is the cost of recet action
* $\lambda_l$ is the cost of substituion error 

We can devise a shortcut that we pick the reject action if the most probable class has the probability below $1 - \lambda_r / \lambda_l$

# $l_2$ loss

It is alos known as the **quadratic loss** and we use it for continuous variables.

$$L(y,a) = ( y - a)^2$$

Where our posterior expected loss is:

$$p(a|x)= E[(y -a)^2 |x]$$

Here the optimal value to pic is the posterior mean (minimizes the posterior mean) independently of the prior.

# $l_1$ loss

The quadratic loss penalizes deviations from the truth quadratically, thus is sensitive to outliers. A more robus alternative is the $l_1$ loss. 

Loss function:

$$L(y,a)= |y -a|$$

This is minimized if we pick the posterior median.