# Independence Map of a Graph

Given a graph G. We define its I Map as:

$$
I(G) = \{ (X|Y | Z): X,Y \text{ are d-separated given Z}\}
$$

(set of variables that are [d-separated](d-separation.md) in G).

If we define $p$ that factorizes over $G$, then $I(G) \subseteq I(p)$. Than we say that G is an I**Independence map (I-map)** for p. In other words, if all the independencies in G are sound, variables that are d-separated in G are truly independent in p. (The converse is not true, a distribution that factorize over G, do not have to capture the independencies in G).


Constructing an I-Map to a graph G is simple, but we are more interested in finding *minimal* I-map of G. This is an I-Map where we remove a single edge from G, it will no longer be an I-Map. This can be achieved by:

> Start with a fully connected G and  remove edges until  Gis no longer an I -map. One way to do this is by following the natural topological ordering of the graph, and removing node ancestors until this is no longer possible.

However often we are interested in *perfect* map of G, $I(p) = I(G)$. Unfortunately this may not exists, since some probability distribution $p$ may not be encoded by directed graphs.


## I-equivalents

We may ask wne are two graphs G, and G' equivalent, I(G) = G(G'), (the encode the same dependencies). This can be achieved by looking at their **skeleton**. 

> Skeleton: we drop the directionality of the arrows to get an undirected Graph.

> Example
>![](../.images/machine_learning/3node-bayesnets.png)
> a,b are symmetric and the directionality of the arrows is not important. In fact a,b,c encode the same dependencies. We can change the direction of the arrows as long as we don't turn them into a V-structure. In d we have a v structure, we cannot change any arrows, thus d is the only way to describe $X \cancel{\perp} Y | Z$.

** G,G', I(G) = I(G') are I-equivalent if they have the same skeleton, and the same v-structures.