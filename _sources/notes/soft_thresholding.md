# Soft threhsolding
The following function

$$
soft(x; \gamma) = \begin{cases}
    x - \gamma & \text{ if } x > \gamma \\
    0 & \text{ if } x = \gamma \\ 
    x + \gamma & \text{ if } x < -\gamma
\end{cases}
$$

![](../.images/machine_learning/soft_tresholding.png)

* left softthresholding
* right hard thresholding