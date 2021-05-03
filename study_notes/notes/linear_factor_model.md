# Linear factor model

Linear factor model can be viewed as the following data generating process:

1. Sample explanatory factor h
$$
h \sim p(h) \\
p(h) = \prod_i p(h_i)
$$

2. Observations are sampled from:
$$
x = Wh + b + \text{noise}
$$