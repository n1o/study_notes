# Energy based models

* many theoretical results about [undirected graphical models](markov_random_fields.md) depend on the assumption that 
    $$
    \forall x, \space \tilde{p}(x) > 0
    $$
    this can be enforced by using an energy based model
    $$
    \tilde {p}(x) = \exp \{ -E(x) \}
    $$
    * $E(x)$ is the energy function, the $-$ sign optional and it can be absorbed inside $E(x)$ but it is common to have it, to have notational parity with statistical physics 
    * $\exp(z)$ is always positive thus no energy function will result in zero probability for any state 

* they are simpler to learn than general undirected graphical models, we do not need to constrain clique potentials, because of this we can use unconstrained optimization
*  for most models it is enough to compute the unnormalized $\tilde{p}_{\text{model}}$ 
*  in most cases we have latent variables $h$ in the model, if we take the negative log we get the **free energy** form
    $$
    F(x) = - \log \sum_h \exp \{-E(x,h) \}
    $$