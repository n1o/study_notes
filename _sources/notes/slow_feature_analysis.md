# Slow feature Analysis

* a version of [linear factor model](linear_factor_model.md) that uses information from time signals to learn invariant features
* slow feature is motivated by the slowness principle, this principle states that the most important characteristics of a scene change slowly, compared to individual measurements. (pixels change rapidly but the position only slowly)

## Problem

$$
\min_{\theta} E_l[f(x^{t+1})_i -f(x^{(t)})_i]^2 \\
\text{s.t: } \\
E_t[f(x^{(t)})]_i = 1 \\
E_t[f(x^{(t)})^2]_i = 1 \\
\forall i < j \space E_t[f(x^{(t)})_i f(x^{(t)})_j]=0
$$

The last constrain forces the features to be linearly decorelated. If it would not be present then it would capture the same feature.