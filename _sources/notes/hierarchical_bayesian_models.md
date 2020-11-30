# Hierarchical bayes (multi-level model)

A key requirement for computing the posterior $p(\theta| D)$is the specification of a prior $p(\theta| \eta)$, where $\eta$ is a hyper-parameter. (The bayesian way is to put priors on top of priors) In Hierarchical bayes we assume that this hyper parameter is unknown, and we model our uncertainity by putting a prior on top of this hyper parameter (Hyper prior).

We can use hierarchical modeling to enable data sharing, where we can borrow statistical strength from data rich observations.