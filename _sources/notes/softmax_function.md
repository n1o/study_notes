# Softmax function

Softmax is the convex relaxation of the max function. 

$$S(\eta)_c = \frac{e^{\eta_c}}{\sum_{c' = 1}^C e^{\eta_{c'}}}$$

## Temperature
We can augument it using a temperature constant T.

If $T \rightarrow 0$
$$ \mathcal{S}(\eta / T)_c = \begin{cases}
    1.0 & \text{ if } c = \arg\max_{c'}\eta_{c'} \\
    0.0  & \text{ otherwise }
\end{cases} $$

Essentially the lower the temperature the more the time the distribution spends in the most probable state. As the temperature increases it spends more time uniformly.