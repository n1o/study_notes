# Graph

A **graph** $G = (V, E)$ consists of set of **nodes** $V = \{1, \cdots, V\}$ and a set of edges $E= \{(s,t) : s,t \in V\}$. We can represent the graph by its **adjacency matrix**, $G(s,t) =1$ to denote $(x,t) \in E$, that is if $s \rightarrow t$ is an edge in the graph. We assume that $G(s,s) = 0$ that means we do not have **self loops**.

## Parent
For a directed graph, the **parents** of a node is the set of all nodes that feed into it
$$pa(s) \triangleq \{ g: G(t,s) = 1 \}$$

## Child
For a directed graph, the **child** of a node is the set of all nodes that feed out of it:
$$
ch(s) \triangleq \{t: G(s,t) = 1 \} 
$$

## Family
For a directed graph, the **family** of a node is the node and its parents
$$
fam(s) = \{ s\} \cup pa(s)
$$

## Root
For a directed graph, a **root** is a node with no parents

## Leaf
For a directed graph, a **leaf** is a node with no children

## Ancestors
For a directed graph, the **ancestors** are the parents, grandparents, etc of a node. That is the ancestor of t is the set of nodes that connect to $t$ via a trail:
$$
anc(t) \triangleq \{ s: s \rightsquigarrow  t\}
$$

## Descendants
For a directed graph, the **descendant** are the children, grand-children, etc of a node. That is, the descendants of $s$ is the set of nodes that can be reached via trails from $s$.

$$
desc(s) \triangleq \{s \rightsquigarrow t\}
$$

## Neighbors
For any graph, we define the **neighbours** of a node as the set of all immediately connected nodes,

$$
nbr(s) \triangleq \{ t: G(s,t) = 1  \vee G(t,s) = 1 \}
$$

For an undirected graph, we write $s \sim t$ to indicate that s and t are neighbours (so $(s,t) \in E$ is an edge in the graph)

## Degree
The **degree** of a node is the number of neighbours, for diirected graphs, we speed of the **in-degree** and **out-degree**, the number of parents and its children.

## Cycle or Loop
For a graph we define a **cycle** a sereis of nodes such taht we can get back to where we started by following at least two edges. If the graph is directed we may speak of directed cycles. 

## DAG
A **directed acyclic graph** is a directed graph with no directed cycles

## Topological ordering
For a DAG, a **topological ordering (total ordering)** is the numbering of nodes such that parents have lower numbers than their children.  

## Path or Trails
A path or trail $s \rightsquigarrow t$ is a series of directed edges leading from s to t. 

## Tree
An undirected tree is an undirected graph with no cycles. A directed tree is a DAG in which there are no directed cycles. If a node can have multiple parents we call it **polytree**

## Forest
A forrest is a set of trees

## Subgraph
A subgraph $G_A$ is the graph creted by using the nodes in A and their corresponding edge $G_A = (V_A, E_A)$

## Clique
For an undirected graph, a clique is a set of nodes that are all neighbours of each other. A **maximal clique** is a clique which cannot be made any larger without loosing the clique property.