
# Directed vs undirected graphical models

We cannot say that one is more powerfull than the other. Since there are some CI relationships that can be modeled by a DGM, but nod a UGM. An example is:

$A \rightarrow C \leftarrow B$ where $A \perp B$ but not $A \cancel{\perp} B | C$ 

$A - C -B$ where $A \perp B | C$ but $A \cancel{\perp} B$

In general the CI properties in UGMs are monotonic, in the following sense:

$$A \perp B |C \Rightarrow A \perp B | (C \cup D)​$$

But in DGMs, CI properties can be non-monotonic, since conditioning on extra variables can eliminate conditional independence due explaining away.

Some distributions can be perfectly modeled by either a DGM or a UGM; the resulting graphs are called **decomposable** or **cordal**. Roughly speaking, this means that if we collapse together all the variables in each maximal clique, to make "mega variable", the resulting graph will be a tree. 
