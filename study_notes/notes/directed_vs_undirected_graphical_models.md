
# Directed vs undirected graphical models

We cannot say that one is more powerful than the other. Since there are some CI relationships that can be modeled by a DGM, but nod a UGM. An example is:

$A \rightarrow C \leftarrow B$ where $A \perp B$ but not $A \cancel{\perp} B | C$ 

$A - C -B$ where $A \perp B | C$ but $A \cancel{\perp} B$

In general the CI properties in UGMs are monotonic, in the following sense:

$$A \perp B |C \Rightarrow A \perp B | (C \cup D)​$$

But in DGMs, CI properties can be non-monotonic, since conditioning on extra variables can eliminate conditional independence due explaining away.

Some distributions can be perfectly modeled by either a DGM or a UGM; the resulting graphs are called **decomposable** or **cordal**. Roughly speaking, this means that if we collapse together all the variables in each maximal clique, to make "mega variable", the resulting graph will be a tree. 

## Advantages of UGM vs DGM
1. UGMs are symmetric and are more natural for certain domains, such as spatial or relational data, where there is no clear causal relationship.
2. [Conditional random fields](conditional_random_fields.md) work better than discriminative DGMs

## Disadvantages of UGM vs DGM
1. Parameters are less interpretable and less modular
2. Parameter estimation is more expensive. Computing the normalization constant Z in general is NP hard.

## Rule of Thumb 
Use [Bayesian networks](directed_graphical_models.md) whenever possible, switch to [MRF](markov_random_fields.md) when there is no natural way to model the problem with directed graph.