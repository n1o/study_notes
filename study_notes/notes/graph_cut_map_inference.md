# Graph cut MAP inference PGM
Map inference on a particular class of MRFs to the [min-cut problem](graph_cut.md). 

Lets suppose we have an [MRF](markov_random_fields.md) over binary variables with pairwise factors with edge energies (negative log-edge factors) have the form

$$
E_{uv} (x_u, x_v) = \begin{cases}
    0 & \text{ if } & x_u = x_v \\
    \lambda_{uv} & \text{ if } & x_u \ne x_v
\end{cases}
$$

* $\lambda_{u,v} \ge 0$ cost that penalizes edge mismatches

Each node $u$ has a unary potential described by an energy function $E_u(x_u)$. The full distribution is:

$$
p(x) = \frac{1}{Z} \exp [ -\sum_u E_u(x_u) - \sum_{u,v \in E} E_{uv}(x_u,x_v)]
$$

The MAP inference is equivalent to minimizing the energy:

$$
\max_x p(x) = \min_x [\sum_u E_u(x_u) + \sum_{u,v\ in E} E_{u,v}(x_u, x_v)]
$$

For each node u, we can normalize energies such that $E_u \ge 0$, and either $E_u(0)=0$ or $E_u(1)=0$. We replace $E_u$ with $E_u' = E_u - \min E_u$ (this is equivalent to multiplying the unnormalized probability distribution by a nonnegative constant $e^{\min E_u}$). This wont change the probability distribution.

We can formulate energy minimization in this type of model as min-cut problem in an augmented graph $G'$.

$G'$ is constructed by adding special source sing nodes $s,t$ to our PGM graph, node s is connected to nodes u with $E_u(0) =0$ by an edge with weights $E_u(1)$, the node $t$ is connected to nodes $v$ with $E_v(1)=0$ by an edge with weights $E_v(0)$. At last all the edges of the original graph get $E_{uv}$ as their weight.

By construction the cost of minimal cut in this graph equal the minimum energy in the model. In particular, all nodes on the s side of the cut receive an assignment of 0, and all nodes on the t side receive an assignment of 1. The edges between the nodes that disagree are precisely the one in the minimal cut.

## Linear Programming
We can find MAP in a pairwise MRF using [Integer linear programming](linear_programming.md). We start by introducing two types of indicator variables:

* $\mu_i(x_i)$ for each $i \in V$ and state $x_i$
* $\mu_{ij}(x_i, x_j)$ for each edge $(i,j) in E$ and pair of states $x_i,x_j$

The MAP objective has the form:

$$
\max_{\mu} \sum_{i \in V}\sum_{x_i} \theta_i(x_i)\mu_i(x_i) + \sum_{i,j\in E}\sum_{x_i,x_j} \theta_{ij}(x_i,x_j)\mu_{ij}(x_i, x_j)
$$

We introduce the following constraints:

$$
\mu_i(x_i) \in \{0,1\}; \space\forall i, x_i \\
\sum_{x_i}\mu_i(x_i) = 1; \space \forall i \\
\mu_{ij}(x_i,x_j) \in \{ 0,1\}; \space \forall i, j \in E, x_i,x_j \\
\sum_{x_i,x_j}\mu_{ij}(x_i,x_j) = 1; \space \forall i, j \in E \\
\sum_{x_i}\mu_{ij}(x_i,x_j) = \mu_j(x_j); \space \forall i, j \in E, x_j \\
\sum_{x_j}\mu_{ij}(x_i,x_j) = \mu_i(x_i); \space \forall i, j \in E, x_i
$$

Where we have to relax the constraints $x \in \{ 0,1\}$ to $0 \le x \le 1$ and use an LP solver. This solution is only an approximation. For a special case of tree-structured graphs, is however optimal.

## Dual decomposition
Lets assume we have the following MRF

$$
\max_x \sum_{i \in V} \theta_i(x_i) + \sum_{f \in F}\theta_f(x_f)
$$ 

* F are factors (Edge potentials in an pairwise MRF)

This objective is difficult to optimize because the potentials are coupled. Lets consider an alternative objective:

$$
\sum_{i \in V}\max_{x_i} \theta_i(x_i) + \sum_{f \in F} \max_{x^f} \theta_f(x^f)
$$

This is easy to optimize, but produces only an upper bound to the true MAP. To make this relaxation tight we have to introduce constraints that encourage consistency between the potentials:

$$
x_i^f - x_i = 0; \space \forall f, \forall i \in f
$$

The idea of dual decomposition is to find an middle ground between these two objectives.

To do this we form the following Lagrangian:

$$
L(\delta, x^f,x) = \sum_{i \in V} \theta_i(x_i) + \sum_{f \in F}\theta_f(x^f) + \sum_{f \in F} \sum_{i \in f} \sum_{x'_i} \delta_{fi}(x'i)(I_{x'_i = x_i - I_{x'_i=x_i^f}})
$$

* $\delta$ Lagrange multipliers

The Lagrangian is an upper bound on $p^*$ (optimal solution)

$$
L(\delta) = \max_{x^f,x} L(\delta, x^f, x) \ge p^*; \space \forall \delta
$$

To get an thigh bound we optimize $L(\delta)$ over $\delta$. Thus if we find an optimal $\delta^*$ we have:

$$
L(\delta^*) = p^*
$$

To get $L(\theta)$ we re-parametrize the Lagrangian as:

$$
L(\theta) = \sum_{i \in V} \max_{x_i} (\theta_i(x_i) + \sum_{f:i \in f}\delta_{fi}(x_i)) + \sum_{f \in F} \max_{x^f} (\theta_f(x^g) + \sum_{i \in f}\delta_{fi}(x_i)) \\
= \sum_{i \in V}\max_{x_i}\theta_i^{-\delta}(x_i) + \sum_{f\in F}\max_{x^f}\theta_f^{-\delta}(x^f)
$$

We want to find $\bar{x}$ such that $\bar{x_i} \in \arg \max_{x_i} \theta^{-\bar{\delta}}(x_i)$ and  $\bar{x_f} \in \arg \max_{x_f} \theta^{-\bar{\delta}}(x^f)$, than we have:

$$
L(\bar{\delta}) = \sum_{i \in V}\theta_i^{-\bar{\delta}} (\bar{x}_i) + \sum_{f \in F}(\bar{x}^f) = \sum_{i \in V} \theta_i(\bar{x_i}) + \sum_{f\in F}\theta_f(\bar{x}^f)
$$

The first equation hold by definition of $L(\delta)$ the second holds because Lagrange multipliers cancel when $x$ and $x^f$ agree.

By definition of $p^*$ we have that:

$$
\sum_{i \in V} \theta_i(\bar{x}_i) + \sum_{f \in F} \theta_f(\bar{x}^f) \le p^* \le L(\delta) 
$$

Which implies that $L(\bar{\delta}) = p^*$

Thus we can find $p^*$ by finding a $\delta$ at which the local sub-problems agree with each other. (This is common in practice)

### How to compute $L(\delta)$
* Subgradient descent
* Block coordinate descent

### Recovering MAP assignment

If $x, x^f$ agree on the factors for some $\delta$ we have an optimal solution. If they do nto agree, than finding MAP is NP-hard.
## Local search
We start with an arbitrary assignment and perform moves on the joint assignment that locally increase the probability. Hwe have no guarantees, however we can use prior knowledge to find effective moves, in practices this performs well.

## Branch and bound
We perform exhaustive search over the space of assignments, while pruning branches that can be provably shown not to contain MAP assignments. 

## Simulated annealing
Here we sample from 

$$p_t(x) \propto \exp(\frac{1}{t} \sum_{x \in C} \theta_c(x_c))$$

* $t$ is the temperature 
  * $t \rightarrow \infty$ than $p_t$ is close to unniform
  * $t \rightarrow 0$ than $p_t$ places more weight on $\arg \max_x \sum_{x\in C} \theta_c(x_c)$ (this is what we are interested in) 

We start with high t, and gradually decrease it. If the cooling rate is sufficiently slow, we are guaranteed to find the mode of our distribution. In practice finding this rate is hard.