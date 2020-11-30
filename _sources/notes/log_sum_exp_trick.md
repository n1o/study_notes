# Log-sum-exp trick

In generative models, we ofthen result in probabilities that are really small, and if we take products of small numbers we can fail due to numerical underflow. To calculate the probability of a given event we can take the logs when applying Bayes rule:

$$
p(y=c|x) = \frac{p(x|y=c)p(y=c)}{p(x)} \\
\log p(y=c| x)=  \log p(x|y = c) + \log p(y = c) - \log [ \sum_{'c =1}^C e^{b_{c'}} ]
$$

Here we need to evaluate:

$$\log p(x) =  \log \sum_{c'} p(y=c', x) = \log [ \sum_{'c =1}^C e^{b_{c'}} ]$$ 

We cannot add in the log domain. The trick is to factor the largest term and just represent the remaining numbers relative to that:

Example:
$$ \log (e^{-120} + e^{-121}) = \log (e^{-120} (e^0 e^{-1})) = \log(e^0 + e^{-1}) - 120 $$

In general:

$$\log \sum_c e^{b_c} = \log [ (\sum_c e^{b_c} - B) e^B ] = [ \log (\sum_c e^{b_c}) ] + B$$

where:
* $B = \max_c b_c$

**However if we do not care about the probabilities, we do not need to normalize them**.