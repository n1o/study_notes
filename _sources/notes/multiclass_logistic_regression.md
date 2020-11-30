# Multi-class Logistic Regression
Generalizes [logistic regression](logistic_regression.md) into multiple mutually exclusive classes.

It is also knwon as **multinomial logistic regression** or **maximum entropy classifier**.

## Model

$$p(y =c|x ,w)= \frac{\exp(w^T_c x)}{\sum_{'c = 1}^C \exp(w^T_{c'}w)} $$

We can introduce the following notation:

$\mu_i = p(y_i = c| x_i, W) = \mathcal{S}(\eta_i)_c$

* $\eta_i = W^Tx_i$ is a $C \times 1$ vector.
* $y_{ic} = I(y_i =c)$ is a one-of-C encoding of $y_i$
* $\mathcal{S}$ is the [softmax function](softmax_function.md)


The negative Log likelihood is:

$$NLL(w) = - \sum_{i=1}^N[(\sum_{c=1}^Cy_{ic}w^T_cx_i) - \log (\sum_{c'=1}^C \exp(w_{c'}^T x_i))] $$