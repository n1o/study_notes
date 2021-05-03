# Predictive sparse decomposition

* hybrid between [sparse coding](sprase_coding.md) and parametric [autoencoder](autoencoder.md)
* the model consist of:
    * parametric encoder $f(x)$
    * decoder $g(h)$

* hidden code $h$ is found by minimizing:
$$
 ||x - g(h)||^2 + \lambda |h|_1 + \gamma ||h  - f(x)||^2
$$

* PSD is an example of learned approximate inference