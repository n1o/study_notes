# Adams Law
Is a powerful strategy for finding expectations $E[Y]$, by conditioning on an r.v $X$, that we wish we knew. First we obtain $E[Y|X]$ by treating $X$ as known and then take the expectation of $E[Y|X]$.


Let:

$$
g(x) = E[Y|X] = \sum_y P(Y=y|X=x) 
$$

Now if we take the expectation we get:

$$
E[g(x)] = \sum_x g(x)P(X = x) \\
= \sum_x \Big [ \sum_y P(Y=y| X = x) \Big]P(X =x) \\
= \sum_x \sum_y yP(X= x)P(Y = y | X = x) \\
= \sum_y y\sum_x P(X = x| Y = y) \\
= \sum_y yP(Y = y) = E[Y]
$$

Thus we derive 

$$
E[E[Y|X]] = E[g(X)] = E[Y]
$$

Thus we can view Adams Law as a more compact version of the law of total expectation.
$$
E[E[Y|X]] = E[g(X)] = \sum_x g(x)P(X=x)= \sum_x E[Y|X=x]P(X=x)
$$

## Conditional Adams law

$$
E[E[Y|X,Z]|Z] = E[Y|Z]
$$