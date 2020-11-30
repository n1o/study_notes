# Independence

Two events A and B are independend if $A \perp B \Leftrightarrow P(A,B) = P(A)P(B)$ or equivalently $P(A|B) = P(A)$ that means, that knowing one provides no information about the other.

## Conditional independence

$$ X \perp Y| Z \Leftrightarrow P(X,Y|Z) = P(X|Z)P(Y|Z) \\ 
\Leftrightarrow P(X|Y,Z) = P(X|Z)$$


## Conditional independence $\ne$ uncoditional independence

Example:
>Suppose that you are going to play two games of tennis against one of two identical twins. Against one of the twins, you are evenly matched, and against the other you have a 3/4 chance of winning. Suppose that you can’t tell which twin you are playing against until after the two games. So each of them is equally likely. Now if you play one game an you win, we gained aditional information that we won. The contitional probability of winning against the worst twin is higher han the conditional probability against the better one. This is an example that independence does not imply conditional independence.

## Disjoint envents

If two events are disjoiints they are **not** independent, but **totally dependent** since knowning one completely describes the other.

## Mutliple events
For $P(A,B,C)$ to be independent they have to be pairwise independent:

$$
P(A,B) = P(A)P(B) \\ 
P(B,C) = P(B)P(C) \\
P(A,C) = P(A)P(C)
$$

And together:
$$
P(A,B,C) = P(A)P(B)P(C)
$$