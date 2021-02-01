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

