# Softmax function

Softmax is the convex relaxation of the max function. 

$$\text{softmax}(\eta)_c = \frac{\exp(\eta_c)}{\sum_{c' = 1}^C \exp(\eta_{c'})}$$

If we take the log of the softmax function we get

$$
\log \text{softmax}(z)_i = z_i - \log \sum_j \exp(z_j)
$$

* $\log \sum \exp(z_j)$ can be viewed as an approx to $\max z_j$ this approximation states that $\exp(z_k)$ is insignificant for any $z_k$ other than $\max_j z_j$

In the log version $z_i$ directly contributes to the loss function it is hard for it to saturate. It saturates only if there is an extreme difference between input values.

It is invariant to adding a scalar to each of the inputs

$$
\text{softmax}(z) = \text{softmax}(z + c) 
$$

because of this we an derive an numerically stable softmax variant:
$$
\text{softmax}(z) = \text{softmax}(z  - \max_i z_i) 
$$


## Temperature
We can augument it using a temperature constant T.

If $T \rightarrow 0$
$$ \text{softmax}(\eta / T)_c = \begin{cases}
    1.0 & \text{ if } c = \arg\max_{c'}\eta_{c'} \\
    0.0  & \text{ otherwise }
\end{cases} $$

Essentially the lower the temperature the more the time the distribution spends in the most probable state. As the temperature increases it spends more time uniformly.