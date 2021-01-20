# Potential Function

In [markov random fields](markov_random_fields.md) there is no topological ordering and we cannot factor $p(y)$ using [d-separation]. Instead we associate [potential functions](markov_random_fields_potential_function.md) (factors) with each maximal clique in the graph. The potential function for clique c is:

A potential function is non-negative function of its arguments. The join distribution is then defined to be proportional to the product of clique potentials.

$$\psi_c (y_c|\theta_c)$$

## Example
Lets take the following distribution: 
$$
\tilde{p}(A,B,C,D) = \phi(A,B)\phi(B,C)\phi(C,D)\phi(D,A) \\ 
p(A,B,C,D) = \frac{1}{Z}\tilde{p}(A,B,C,D) \\ 
Z = \sum_{A,B,C,D}\tilde{p}(A,B,C,D)
$$

The potential for A,B can be defined as:

$$
\phi(A,B) = \begin{cases} 
    10 & \text{ if } A = B =1 \\  
    5 & \text{ if } A = B = 0 \\ 
    1 & \text{ otherwise}
\end{cases}
$$

This differs form conditional probability (they define how one variable generates an another). Thus potential functions only indicate an level of coupling between dependent variables in a graph. 

## Linear potential functions

A general approach is to define log potentials as linear functions of the parameters:

$$\log \phi_c(y_c) \triangleq \phi_c(y_c)^T\theta_c $$

* $\phi_c(y_c)$ is a feature vector derived from the values of the variables $y_c$.

The resulting log probabilities have the form:

$$ \log p(y|\theta) = \sum_c \phi_c(y_c)^T\theta_c - \log Z(\theta) $$

These are also known as **maximum entropy** or **log linear** models. 