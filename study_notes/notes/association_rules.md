# Association Rules
We want to find items that frequently occure together. Unfortunatelly this is not straight forward since there are noise items that are so frequently together that they disturb. To find frequent items we need to define the notion of confidence:

## Confidence
Confidence is the number of transactions where the itemset is presently divided by the total number of times the first one is present.

$$ c(X \rightarrow Y) = \frac{|T(X \text{ AND } Y )|}{T(X)} $$

Where T is a function that measures the total amount. 

This can be missleading if the total number of transactions for an given item is small. For this case we need to define:

## Support 

$$ s(X \rightarrow Y) = \frac{|T(X \text{ AND } Y )|}{T()} $$

Here $T()$ is the total amounth of transactions. In other words this is the evidence that supports the association rule $X \rightarrow Y$.


## Algorithm
1. Find pairs
2. Calculate Confidence and Support
3. Choose minimum Confidence and Support
4. Choose the pairs that remain