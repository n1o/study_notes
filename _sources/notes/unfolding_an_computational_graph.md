# Unfolding an Computational Graph

[Computational graph](automatic_differentiation.md) formalizes the set of computations that are involved in mapping inputs and parameters to outputs and the loss. We can unfold an [recursive or recurrent](recurrent_neural_networks.md) computation to a chain of events. Unfolding results in sharing parameters across a deep network structure.

Lets consider a dynamic system:

$$
s^{(t)} = f(s^{(s-t)}; \theta)
$$

* $s^{(t)}$ is the state of the system

This system is recurrent since the definition of state $s$ at time $t$ refers back to the same definition at time $t-1$. For a finite time step $\tau$ we can unfold by applying the definition $\tau -1$ times:

> Example $\tau = 3$
> $$
s^{(3)} = f(s^{(2)}; \theta) \\ 
s^{(3)} = f(f(s^{(1)}; \theta); \theta)
$$

Unfolding is only repeatedly applying the definition until it does not involve recurrence.

![](../.images/machine_learning/computation_unfolding.png)