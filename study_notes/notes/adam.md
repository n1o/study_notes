# Adam (adaptive moment estimation method )
Adapts the learning rate to each parameter. It stores booth an exponentially decaying squared gradient like RMSProp and Adadelta, but also an exponentially decaying gradient like momentum.

Initializing the gradient and squared gradient to zero introduces a bias. A bias correction step is required to alleviate the issue. (A good default settings are $s= 0.001, \gamma_s = 0.999, \gamma_v = 0.9, \epsilon = 10^{-8}$)

At each iteration of Adam we calculate the following values:

1. Biased decaying momentum $v^{(k+1)} = \gamma_v^{(k)} + (1 - \gamma) g^{(k)}$
2. Biased decaying squared gradient $s^{(k+1)} = \gamma_ss^k + (1 - \gamma_s)(g^{(k)} \odot g^{(k)})$
3. Corrected decaying momentum $\hat{v}^{(k+1)} = v^{(k)} / (1 - \gamma_v^k)$
4. Corrected decaying gradient $\hat{s}^{(k+1)} = s^{(k+1)} / (1 - \gamma_s^k)$
5. Next iterate $x^{(k+1)} = x^{(k)} - \alpha \hat{v}^{(k+1)} / (\epsilon + \sqrt{\hat{s}^{(k+1)}})$

## Algorithm 

Initialize:
$\alpha$ learning rate, $\gamma_v$ decay, $\gamma_s$ decay momentum, $\epsilon$ small value, $k = 0$ step counter, $v = 0$ first moment estimate, $s=0$ second moment estimate.

Iterate:

$g = \nabla f(x)$

$v = \gamma v * v + (1 - \gamma_v) * g$

$s = \gamma s * (1 - \gamma s) + (1 - \gamma_s)* (g \cdot g)$

$k = k +1$

$\hat{v} = v / (1 - \gamma_v^k)$

$\hat{s} = s / (1 - \gamma_s^k)$

$\text{return } x - \alpha \hat{v} / (\sqrt{\hat{s}} + \epsilon)$