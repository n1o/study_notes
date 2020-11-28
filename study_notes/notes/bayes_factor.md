# Bayes factors

In bayes factor we compare 2 hypothesis by comparing they marginal likelihoods:

$$BF_{1,0} \triangleq  \frac{p(D|M_1)}{p(D|M_2)} = \frac{p(M_1|D)}{p(M_0|D)} / \frac{p(M_1)}{p(M_0)} $$

If we assume that $p(M_0) = p(M_1) = 0.5$ than the equation simplifies to:

$$p(M_0|D) = \frac{1}{BF_{1,0}  +1 }$$

Now we can use this ration, to say which model is better or worse, and by how much.

## Computing