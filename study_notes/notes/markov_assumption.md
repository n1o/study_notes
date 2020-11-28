# Markov assumption

A key to efficiency is represent large [joint distributions](probability_independence.md) is to make some assumptions about conditional independence. 

$$X \perp Y |Z \Leftrightarrow p(X,Y|X) = p(X|Z)p(Y|Z)  $$

Hence X and Y are conditionaly independent if the conditional joint can be written as the product of conditional marginals.

We can use conditional indpendence to express the **markov assumption**, "future data is independent of the past given the present" $x_{t+1} \perp x_{1:t-1}| x_t$. 

$$p(x_{1:V}) = p(x_1) \prod_{t = 1}^Vp(x_t|x_{t-1})$$

This is also called a **Markov chain**. They can be characterized by an initial distribution over states $p(x_t = i)$ plus a **state transition matrix** $p(x_t= j | x_{t-1} = i )$