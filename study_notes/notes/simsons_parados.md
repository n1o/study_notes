# Simsons Paradox
A trend appears in several different groups of data but disappears or reverses when these groups are combined.

## Probability

We have 2 doctors A, B we can see that doctor A has a higher success probability for booth cases of surgeries, but the overal probability of sucess is higher for doctor B. More mathematically it is:

$$
P(A|B,C) < P(A|B^c, C) \\
P(A|B,C^c) < P(A| B^c , C^c)
$$

but: 
$$
P(A|B) > P(A|B^c)
$$

This can happen, and it can be proved using the law of total probability:

$$
P(A|B) = P(A|C,B)P(C|B) + P (A|C^c,B)P (C^c|B) \\
P(A|B^c) = P(A|C,B^c)P(C|B^c) + P(A|C^c, B^c)P(C^c|B^c)
$$

Where  the weights $P(C|B), P(C^c|B)$ can flip the overal balance.