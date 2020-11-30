# Shannon infromation content of an outcome
It is measured in bits:

$$h(x) = \log \frac{1}{p(x)}$$

An example would be a game of submarine on a $8 \times 8$ board. (Total 64 spaces). The probability that we would sink a submarine on the first hit is $\frac{1}{64}$ if it would happen we would get $\log_2 \frac{1}{1/64} = \log_2 64 = 6$ bits

No lets imagine we hit the submarine on the $49$th hit. In this case only 16 squares are left so we gain $\log_2 16 = 4 \text{ bits}$

Now if we sum up all the previous entropies $\log_2 \frac{64}{63} + \log_2 \frac{63}{62} + \cdots + \log_2 \frac{17}{16} + \log_2 \frac{16}{1} = 6 \text{ bits}$

Where $\log_2 \frac{64}{63}$ is the number of bits recevied afther we missed the first shot, (Probability of not hitting anything is $63/64$)  $\log_2 \frac{63}{62}$ is the number of bits received afther we missed the second shot ($62/63$)

From this example we can see that no matter in what sequence we arrive at the result, but we receive the same number of bits. In this case we can see that Shannons information connect is a sensible measure of information content. And it can be intimately connected to the size of a file that encodes the outcomes of a random experiment. 


