# Leaky Unis

We with linear self-connection and weight near 1 on these connections. The idea is that if we calculate the running average $\mu^t$ for some value $v^{(t)}$

$$
\mu^{(t)} = \alpha \mu^{(t-1)} + (1-\alpha)v^{(t)}
$$

* $\alpha$ is a linear self connection from the past value $\mu^{(t-1)}$ to $\mu^{(t)}$. If it is near 1 than the running average remembers information about the past for a long time. If it is close to 0 the information about the past is rapidly discarted. 

This idea of discarding an keeping past is the idea behind leaky units. Where the constant $\alpha$ is either fixed or learned as a free parameter.