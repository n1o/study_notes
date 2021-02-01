# Graph cut

A graph cut of an undirected graph $G = (V,E)$ is a partition of V into 2 disjoint sets $V_s$ and $V_t$. When each edge $(v_1,v_2) \in E$ is associated with an nonnegative cost $\text{cost}(v_1,v_2)$ the cost cost of a graph cut is the sum of the costs of the edges that cross between the two partitions:

$$
\text{cost}(V_s,V_t) = \sum_{v_1 \in V_s, v_2 \in V_t} \text{cost}(v_1, v_2)
$$

## Min-cut
The min cut problem is to find the partition $V_s, V_t$ that minimizes the cost of the graph cut. 

The fastest algorithms run take $O(|E||V|\log |V|)$ or $O(|V|^3)$
