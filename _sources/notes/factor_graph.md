# Factor graph
* a way to express [undirected graphical models](markov_random_fields.md) with less ambiguity
  * from the standard notation in MRF, we do not known if the corresponding factor encompasses the whole clique or some of its parts
    * an example if we have a clique of 3 nodes, we can have a single factor for the whole clique, or we can have 3 factors for each possible pairs


* factor graph is a [bipartite graph](biparite_graph.md) and has the following nodes:
  * **circles**: which are random variables as in undirected graphs
  * **squares**: factors $\phi$ of unnormalized probability distribution

* variables and factors can be connected with undirected edges, this connection is there if a variable is a argument of a factor in the unnormalized distribution.
* there cannot be an connection 
  * variable - variable
  * factor - factor


![](../.images/machine_learning/factor_graph_v1.png)
* an classical undirected graph
* a factor graph where we have a single factor for the clique of variables a,b,c
* we have 3 factors in the clique a,b,c