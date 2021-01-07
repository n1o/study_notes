# Parametrization of Markov Random Fields

Unfortunately representing joint distributions in Undirected graphical models is less natural than in DGM.

## The Hammersley-Clifford theorem

Since there is no topological ordering associated with an undirected graph, we can't use the chain rule to represent $p(y)$. So instead of associating CPDs with each node, we associate **potential functions** or **factors** with each maximal clieque in the graph. We will denote this potential function for clique c as 

$$\psi_c (y_c|\theta_c)$$

A potential function is non-negative function of its arguments. The join distribution is then defined to be proportional to the product of clique potentials. 

More formaly this is called the *Hammersley-Clifford* theorem

*A positive distribution $p(y) > 0$ satisfies the CI properties of an undirected graph G iff p can be represented as a product of factors, one per maximal clique, i.e.,*

$$p(y|\theta) =  \frac{1}{Z(\theta)} \prod_{c \in C}  \psi_c(y_c|\theta) $$

*where C is the set of all the (maximal) cliques of G and $Z(\theta)$ is the **partition function** given by* 

$$Z(\theta) \triangleq \sum_x \prod_{c \in C} \psi_c (y_c|\theta_c) $$

*this partition function is what ensures the overall distribution sums to 1*

> Example
>
> ![](../.images/machine_learning/markov_random_fields_parametrization.png)
> $$ p(y|\theta) = \frac{1}{Z(\theta)} \psi_{123}(y_1, y_2, y_3)\psi_{234}(y_2, y_3, y_4) \phi_{35}(y_3,y_5) \\ Z(\theta) = \sum_y \psi_{123}(y_1, y_2, y_3)\psi_{234}(y_2, y_3, y_4) \phi_{35}(y_3,y_5)$$


There is a deep connection between UGMs and statistical physics. We can convert the **Gibs distribution**:
$$
p(y|\theta) = \frac{1}{Z(\theta)}\exp(- \sum_c E[y_c|\theta_c])
$$
* $E[y_c] > 0$ is the energy function associated with the variables in clique c

We can convert it to an UGM:

$$
\psi_c(y_c|\theta) = \exp(-E[y_c|\theta_c])
$$

This forms the base of **energy based models**. Here high probability states correspond to low energy configurations.

## Representing potential functions

If the variables are discrete, we can represent the potential function or energy functions as tables of number just as with CPT. However, potentials are not probabilities. They rather represent the "compatibility" between the different assignments to the potential. 

A general approach is to define log potentials as linear functions of the parameters:

$$\log \psi_c(y_c) \triangleq \phi_c(y_c)^T\theta_c $$

* $\phi_c(y_c)$ is a feature vector derived from the values of the variables $y_c$.

The resulting log probabilities have the form:

$$ \log p(y|\theta) = \sum_c \phi_c(y_c)^T\theta_c - \log Z(\theta) $$

These are also known as **maximum entropy** or **log linear** models. 