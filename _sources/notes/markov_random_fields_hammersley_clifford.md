# Hammersley-Clifford

*A positive distribution $p(y) > 0$ satisfies the CI properties of an undirected graph G iff p can be represented as a product of factors, one per maximal clique, i.e.,*

$$p(y|\theta) =  \frac{1}{Z(\theta)} \prod_{c \in C}  \psi_c(y_c|\theta) $$

*where C is the set of all the (maximal) cliques of G and $Z(\theta)$ is the **partition function** given by* 

$$Z(\theta) \triangleq \sum_x \prod_{c \in C} \psi_c (y_c|\theta_c) $$

*this partition function is what ensures the overall distribution sums to 1*

> Example
>
> ![](../.images/machine_learning/markov_random_fields_parametrization.png)
> $$ p(y|\theta) = \frac{1}{Z(\theta)} \psi_{123}(y_1, y_2, y_3)\psi_{234}(y_2, y_3, y_4) \phi_{35}(y_3,y_5) \\ Z(\theta) = \sum_y \psi_{123}(y_1, y_2, y_3)\psi_{234}(y_2, y_3, y_4) \phi_{35}(y_3,y_5)$$
