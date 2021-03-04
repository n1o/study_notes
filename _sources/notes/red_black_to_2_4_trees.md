# [Red-black tree](red_black_trees.md) to [2-4 tree](2_4_trees.md)

If we merge every red node $w$ into its parent, storing entry from $w$ at its parent, and with children of w becoming ordered children of the parent we get a (2,4) tree. 

![](../.images/algorithms/red_black_trees_2_4_trees.png)

**2,4 to red-black**
We have to perform the following transformations:
1. If w is a 2-node, then keep the (black) children of w as is
2. If w is a 3-node then create a new red node y, given $w$'s last two (black) children of y, and make the first children of w and y to be two children of w. 
3. If w is a 4-node, then create two new red nodes of y and z, give w's first two (black) children to y, give w's last two (black) children to z, and make y and z be the two children of w. 

![](../.images/algorithms/red_black_trees_2_4_trees_nodes.png)