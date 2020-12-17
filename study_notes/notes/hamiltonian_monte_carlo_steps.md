# Steps of HMC iteration

1. The iteration begins by setting $\phi$ with a random draw form $\theta \sim N(0, M)$

2. The main part of HMC iteration is a simultaneous update of $(\theta, \phi)$, conducted via discrete mimicing physical dynamics. This involves L 'leapfrog steps', each scaled by a factor $\epsilon$. In leapfrog steps, booth $\theta$ and $\phi$ are changed, each in relation to the other. 

   Each of the L leapfrog steps procede as follows:

   1. Use the gradient of the log posterior density of $\theta$ to make an half step of $\phi$

      $$ \phi \leftarrow \phi + \frac{1}{2} \epsilon \frac{d \log p(\theta|y)}{d \theta} $$ 

   2. Use the momentum vector $\phi$ to update the 'position' vector $\theta$

      $$\theta \leftarrow \theta + \epsilon M^{-1}\phi $$

      * $\epsilon$ can be used as an tuning parameter

   3. Again use the gradient of $\theta$ to half update $\psi$

      $$\phi \leftarrow \phi + \frac{1}{2} \epsilon \frac{d \log p(\theta|y)}{d \theta}$$ 

   This algorithm is called leap-frog, which splits the momentum update into half steps, is a discrete approximation to physical Hamiltonian dynamics in which booth position and momentum evovle in continuous space. 

   In the limit $\epsilon \rightarrow 0$, leapfrog preserves $p(\theta, \phi | y)$. The intuition is:

   * If $\frac{d \log p(\theta|y)}{d \theta}$ is zero, than we in a flat region and $\theta$ will scate along with constant velocity
   * If $\frac{d \log p(\theta|y)}{d \theta}$ is negative, than the momentum will decrease until it stops and turns the other direction
   * If $\frac{d \log p(\theta|y)}{d \theta}$ is positive, then we gain momentum until we pass the mode and start to slow down. 

3. Unfortunately for finite $\epsilon$, leapfrog wont approximate the trajectory perfectly, but with an error $\delta$ . Fortunately this error with L steps is not $L\delta$ but it is wawing back and fort. For correcting this error we require an accept/reject step. 

   Label $\theta^{t-1}, \phi^{t-1}$ as the values at the start of the leap-forg step $\theta^*, \phi^*$ afther L leap frog steps. The acccept reject step:

    $$r = \frac{p(\theta^*| y)p(\phi^*)}{p(\theta^{t-1}|y)p(\phi^{t-1})} $$

4. Set

   $$ \theta^t = \begin{cases} \theta^* && \text{ with probability } \min(r,1) \\ \theta^{t-1} && \text { otherwise } \end{cases}$$

   We do not need to set $\phi^t$ since at step 1 we set it to a new value