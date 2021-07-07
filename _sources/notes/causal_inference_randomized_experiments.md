# Randomized experiments
* we can transform [association into causation](causality_intro.md) if there is no bias. 
  * without bias the treatment and control groups are equal before treatment
  * without bias we can say that the untreated is qual to the counterfactual of the treated

* randomized trials annihilate bias since we randomly assign to control and treatment groups
    $$
    (Y_0,Y_1) \perp T
    $$
    * the  potential outcomes are independent of the treatment, thus knowing who is treated or not is independent of the treatment effect
    * the only difference between the groups is the treatment
    * $E[Y_0|T=1] = E[T_0|T=0] =E[Y_0]$

* randomized trials are powerful and reliable, but hard to achieve or expensive
  * most of causal inference is about identifying the treatment assignment mechanism, by identifying the treatment assignment we can give an more convicting causal answer