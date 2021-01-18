# Uniform circular motion
We move in a circle with constant speed. Thus there is acceleration that is perpendicular to the path (If it would be along than we would increase the speed).

![](../.images/physics/circular_motion.png)

The velocity at each point changes, while the acceleration always points towards the Origin of the circle. The magnitude of the change of velocity is defined as:

$$
|\Delta \vec{v}| = \frac{v_1}{R}\Delta s
$$

From this we can calculate the average acceleration:

$$
a_{av} = \frac{|\Delta \vec{v}|}{\Delta t} = \frac{v_1}{R}\frac{\Delta s}{\Delta t}
$$

The instantaneous acceleration is:

$$
a = \lim_{\Delta t \rightarrow 0} 
 \frac{v_1}{R}\frac{\Delta s}{\Delta t} =  \frac{v_1}{R} \lim_{\Delta t \rightarrow 0} \frac{\Delta s}{\Delta t}
$$

The limit of $\frac{\Delta s}{\Delta t}$ is the speed $v_1$ at point A, which is constant at every point on the path. This makes:

$$
\lim_{\Delta t \rightarrow 0} \frac{\Delta s}{\Delta t} = v
$$

And the acceleration is:
$$
a_{rad} = \frac{v^2}{R}
$$

> This acceleration is **radial** (points always to the center of the circle, and perpendicular to the objects velocity)
> It is proportional to the square of speed $a_{rad}\propto v^2$ and inversely proportional to the radius $a_{rad} \propto \frac{1}{R}$