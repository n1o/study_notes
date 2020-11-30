
# Probability

**Sample space**

Sample space $\Omega$ defines all the outcomes of a random experiment. 

**Event space**
Set of events F denotes all the possible outcomes of an experiment, thus it is a subset of $\Omega$

**Probability measure**

Is a function $P: F \rightarrow R$ which satisfies the following properties:

* $P(A) \ge 0, \forall A \in F$
* If $A_1, A_2, \cdots$ are disjoint then $P(\cup_i A_i) = \sum_i P(A_i)$
* $P(\Omega) = 1$

There three are the **Axioms of probability** from these three we can deriive others:

* $0 \le P(a) \le 1$
* $P(A \cap B) \le \min(P(A), P(B))$
* Union bound $P(A \cup B) \le P(A) + P(B)$
* $P(\Omega - A) = 1 - P(A)$
* [Law of total probility](law_of_total_probability.md)
  
In general this function takes an event from the sample space and asigns it to the real line.

# Joint probability
The join probability of event A and B as:
$$
P(A,B) = P(A \cap B) 
$$

## Marginalization:
We sum over all the possible states of one event:
$$P(A) = \sum_b P(A,B=b)$$

This is also known as the [law of total probability](law_of_total_probability.md).

# Conditional probability

Let B an event with non-zero probability. The conditional probability of any event A given B is defined as 

$$
P(A|B) = \frac{P(A \cap B)}{P(B)}
$$

In other words it is the probability measure of the event A after observing the occurrence of event B.


# Union of mutliple events
Given event A and B the probabiility that A or B will happen is:

$$
P(A \cup B) = P(A) + P(B) - P(A \cap B)
$$

or

$$P(A \cup B) = P(A) + P(B)$$ 

If they are mutualy exclusive. 

In case we have more than 2 events we follow the [inclusion exclusion rule](probability_inclusion_exclusion.md)