# Trees
A tree is an abstract data type that stores elements hierarchically. Each element with expect the top element has an parent, and zero or more children. The top element of a tree is called the root of the tree. 

## Definition
Let tree T be a set of nodes storing elements, such that the nodes have a parent-child relationship that satisfies the following properties.
1. If T is nonempty, it has a special node called the root of T, that has no parent
2. Each node of T different from the root has a parent node w; every node with parent w is a child of w. 

## Other Relationships

1. If two or more nodes that share the same parent are siblings. 
2. A node that does not have a child is external (Also known as leaves)
3. A node is internal if it has one or more children
4. Ancestor is a node that is above a node v. 
5. Descendant is a node that is below a node v. 
6. Edge of a tree is a pair of nodes $(u,v)$ such that u is the parent of v, or vice versa. 
7. Path is a sentence of nodes each connected by an each. 
8. An tree is order if there is an meaningful linear order among children of each node. So we can identify a child that is first, second and so on.


## ADT
We use a concept of position as an abstraction fo a node of a tree. An element is stored at each position and positions satisfy parent-child relationships that define the tree structure. Position has a single method:

* p.element() to retrieve the element under this position

Methods on a tree are:


| Operation        | Description |
| ------------- |:-------------|
| T.root()     | Returns the position of the root element      |
| T.is_root(p)       | Returns true if the position p is the root element of T       |
| T.parent(p)       | Returns the position of parent of p     |
| T.num_children(p) | Returns the number of children of position p        |
| T.children(p)       |  Generate an iteration of children of position p      |
| T.is_leaf(p) | Returns True if position p does not contain any children |
| len(T) | Returns the number of positions (elements) that are contained in the tree T |
| T.is_empty()| Return True if three T does not contain any possitions |
| T.positions()| Generate an iteration of all positions of the tree T |
| iter(T) | Generate an iteration of all elements stored within tree T|