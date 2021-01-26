# Junction tree algorithm

Here we want to perform inference on a graph. In most cases this is not tractable. Thus we try to massage the graph into something that resembles a tree, and run message passing on this graph. We can view it as a generalization of  [belief propagation](belief_propagation.md) to graphs. 

## High level overview
We partition the graph into clusters of variables, variables inside a cluster are tightly coupled; however interactions among clusters have a tree structure. (clusters are influenced only by its neighbors). If the cluster-level problem can be solved exactly, we have a globally tractable solution.

## [Example](junction_tree_example.md)

## OLD!

## Crating a junction tree
The basic idea of JTA is:

First we run the [variable elimination](variable_elimination.md) algorithm "symbolically", adding fill-in edges as we go, according to a given elimination ordering. The resulting graph will be a [chordal graph](chordal_graph.md).

Having this chordal graph, we can extract its maximal cliques. In general finding max cliques is computationally hard, but for this special graph it can be done efficiently.

> Example:
> ![](../.images/machine_learning/junction_tree_algorithm.png)

It turns out that the cliques of a chordal graph can be arranged into a special kind of tree known as **junction tree** (on the picture it is on the bottom). This enjoys the **running intersecion property** (RIP), which means that any subset of nodes containing a given variable forms a connected component. 

In the example we can see that node I occurs in the two adjacent three nodes, so they can share information about this variable. This holds for all the other variables.

We can show that if a tree satisfies the running intersection property, then applying BP to this tree will return the exact values of $p(x_c|v)$ for each node c in the tree. From this we can extract the node and edge marginal $p(x_t|v)$ and $p(x_s,x_t|v)$ from the original model by marginalizing the clique distribution. 

## Message passing on a junction tree
If we have created an junction tree, we can use it for inference. The process is similar to belief propagation on a tree. There are 2 version:

* sum-product form also known as **Shafer-Shenoy** algorithm
* belief updating form also known as **Hugin**

## Computational complexity of JTA
If all nodes are discrete with K states each, it is clear that the JTA takes

$$O(|C|K^{w+1})$$

*  $|C|$ is the number of cliques
*  $w$ is the size of the largest clique -1 


Unfortunately choosing a triangulation to minimize the tree width is NP hard. Unfortunately JTA does not work with continuous variables, except they are jointly Gaussian.

## Limitations
Does not work with continuous variables, unless we have joint Gaussian distributions.