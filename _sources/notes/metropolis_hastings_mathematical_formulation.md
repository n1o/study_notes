# Metropolis Hastings mathematical formulation

Let [$]s = (s_1, s_2, \cdots, s_M)[/$] be a desired stationary distribution on the state space [$]\{1,2, \cdots, M \}[/$]. Assumre that [$]s_i \ge 0[/$] for all i. (If this is not true we can delete any state i from the chain). Suppose that [$]P = (p_{ij})[/$] is the transition matrix form a Markov chain on state space [$]\{1,2, \cdots, M \}[/$] . Tis makes P a Markov chain that we know to run but does not have the desired stationary distribution.

We use Metripolis-Hastings to modify P to construct a Markov chain [$]X_0, X_1, \cdots [/$] with stationary distribution s. Here P is the proposal distribution, and choosing the right proposal distribution is extremely important since it can make an enormous differencei n how fast the chain converges. 

Start at any state [$]X_0[/$] (we can randomly choose form the original chain), and suppose the new chain is currently at [$]X_n[/$] to make one move of the new chain we do:

1. If [$]X_n = i[/$], propose a new state j using the transition probabilities in the ith row of the original transition matrix P.
2. Compute the acceptance probability: [$]a_{ij} = min(\frac{s_j p_{ji}}{s_i p_{ij}}, 1)[/$]
3. Flip a coin that lands Heads with probaiblity [$]a_{ij}[/$]
4. If the coin land Heads, accept the proposal [$]X_{n+1} = j[/$]. Otherwise reject the proposal [$]X_{n+1} = i[/$].

This is pracital since the normalization constants cancels out [$]\frac{s_i}{s_j}[/$]. 