# Learning in conditional random fields

A [conditional random field](conditional_random_fields.md) is a probability distribution of the form:

$$
p(y|x) = \frac{1}{Z(x;\varphi) }\prod_{c \in C} \phi_c (y_c, x; \varphi) \\ 
Z(x,\varphi) = \sum_{y_1, \cdots, y_n} \prod_{c \in C} \phi_c (y_c, x; \varphi)
$$

* $Z(x,\varphi)$ is the partition function. 

Hear each function depends on $x$ in addition of $y$, where $x$ are fixed and we get a distribution only over $y$.

Similarly as with [learning markov random fields](learning_markov_random_fields.md) we re-parametrize $p$

$$
p(y|x) = \frac{\exp{\theta^T f(x,y)}}{Z(x,\theta)}
$$

* $f(y,x)$ is a vector of indicator functions
* $\theta$ is a re-parametrization of the model parameters

The log likelihood for dataset D is:

$$
\frac{1}{|D|} \log p(D;\theta) = \frac{1}{D} \sum_{x,y\in D} \theta^Tf(x,y) - \frac{1}{|D|} \sum_{x\in D}\log Z(x,\theta)
$$

The gradient of this likelihood is:

$$
\frac{1}{|D|} \sum_{x,y \in D} f(x,y) - \frac{1}{|D|} \sum_{x \in D} E_{y \sim p(y|x)}[f(x,y)]
$$

And the hessian is just the covariance matrix:

$$
\text{cov}_{y \sim p(y|x) [f(x,y)]}
$$

Unfortunately the gradient requires one inference per training data point x,y in order to compute:

$$
\sum_{x,y \in D} \log Z(x,\theta)
$$

This makes CRF more expensive in learning than MRF. 

In practice there are more popular objective functions for training CRF called "max-margin" loss which generalizes the objective for training [SVM](support_vector_machines.md). Models using this loss are called [structured support vector machines](structured_support_vector_machines.md).