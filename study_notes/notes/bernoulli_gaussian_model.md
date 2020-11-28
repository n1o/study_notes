# Bernoulli-Gaussian Model

It is the model of the form:

$$
y_i | x_i, w, \gamma, \sigma^2 \sim N(\sum_j \gamma_j w_j x_{ij}, \sigma^2) \\
\gamma_j \sim Ber(\pi_0) \\
w_j \sim N(0, \sigma^2_w)
$$

In the signal processing literature this is called the Bernoulli-Gaussian model, although we could also call it the binary mask model, since we can think of the $\gamma_j$  variables as “masking out” the weights $w_j$ .

From this model we can derive $l_0$ regularization:

$$f(w) = ||y - Xw ||_2^2 + \lambda ||w||_0$$

This is called $l_0$ regularization, which converts the discrete optimization into a continuous one. However the $l_0$ pseudo-norm makes the objective very non smooth so it is still hard to optimize.
