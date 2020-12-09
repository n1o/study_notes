# Variational free energy

We can express [variational inference](variational_inference.md) alternatively as:

$$
J(q) = KL(q||\tilde{p}) = E_q[\log q(x)] = E_q[-\log \tilde{p}(x)] = -H(q) + E_q[E(x)]
$$
* $E[x] = - \log \tilde{p}(x)$
* $\tilde{p} = Zp^*(x)$ is the unnormalized posterior distribution

The equation is the expected energy minus the entropy of the system.
In statistical physics $J(q)$ is called the **variational free energy (Helmholtz free energy)**. It is called free because the variable x is free to vary, rather than being fixed. The variational free energy is a function of a distribution q, whereas the regular energy is a function of the state vector x. 

Alternatively it can be written as:

$$
J(q) = E_q(\log q(x) - \log p(x)p(D|x)) \\
= E_q[\log q(x) - \log p(x) = \log p(D|x)] \\
= E_q[-\log p(D|x)] + KL(q(x) || p(x))
$$

This is the expected NLL, plus a penalty term that measures how far the approximate posterior is from the exact prior.