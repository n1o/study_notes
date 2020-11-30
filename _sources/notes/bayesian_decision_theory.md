# Bayeisan decision theory 

It is a way to connect our belief into actions that are optimal. We can formalize this problem as a game against nature. In this game nature pics a state $y \in Y$, unknow to us, and then generates an observation $x \in X$,which we get to see. Now we have to make a decision to choose an action a from some action space $\mathcal{A}$.  Then we measure our [loss $L(y,a)$](common_bayesian_loss_functions.md), which measures how compatible our cation a is with natures hidden state y. 

Our goal is to minimize this loss over all states, this is done by minimizng the expected loss:

$$ \delta(x) = \arg_{a \in \mathcal{A}} \min E[L(y,a)]$$  

Instead of loss function we can define a **utility function**

$$U(y,a) = -L(y,a)$$

Than we want to maximize the expected utility:

$$ \delta(x) = \arg_{a \in \mathcal{A}} \max E[U(y,a)] $$

This is also called the **maximum utlity principle**, or simply **rational behaviour**

In a bayesian setting if we talk about expected loss, we mean **posterior expected loss**

$$p(a|x) \triangleq E_{p(y|x)}[L(y,a)] = \sum_x L(y,a)p(y|x) $$

Hence the **Bayesian estimator** is:

$$\delta(x) = \arg_{a \in \mathcal{A}} \min p(a|x)$$

In classificatin setings we may care about [false positive false negative tradeoff](false_positive_negative_tradeoff.md)
