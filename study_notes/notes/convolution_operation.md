# Convolution operation

$$
s(t) = \int x(a) w(t-a)da \\ 
s(t) = \sum_{a=-\infty}^ tx(a) w(t-a) \\ 
s(t) = (x * w)(t)
$$

* $w$ is a valid probability density
* in the discrete case in general we do not need the infinite sum since in most cases we have only finite number of elements.

> Example
> $x(a)$ measures a position, this measurement in noisy, and we take multiple measurements to reduce the noise. $w(a)$ is a weighted average operation that puts more weight on recent measurements.

