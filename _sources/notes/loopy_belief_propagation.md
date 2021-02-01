# Loopy belief propagation (LPB)

For many graphs it is hard to find a good [junction tree](junction_tree_algorithm.md), in some cases, we may not need an exact solution and we are satisfied with a quick approximation.

Loopy belief propagation (LBP) is a technique for performing approximate inference on complex (non-tree structured) graphs. 

## Pairwise models
Lets assume we have a pairwise [MRF](markov_random_fields.md). The idea of LBP is to disregard loops in the graph and perform message passing. Given an ordering on the edges, for each time $t$ we iterate over a pair of adjacent variables $x_i,x_j$ in that order we perform the update:

$$
m_{i\rightarrow j}^{t+1} = \sum_{x_i}\phi(x_i)\phi(x_i,x_j)\prod_{l \in N(i)\backslash j} m_{l\rightarrow i}^t (x_i)
$$

We perform these updates for a fixed number of steps (or until converged, since the messages do not change). 

## Properties
Heuristics shows this works well in practice, but it may not converge. It will probably converge on trees and on graphs with at most one cycle. If the method does not converge, its beliefs may not necessarily equal the true marginals (but in practices they will be close).