# Motion in plane
We extend the [one dimensional motion](one_dimensional_motion.md) into two dimensions. This generalizes than into tree dimensions.

![](../.images/physics/two_dimensional_motion.png)

The vector $\vec{r}$ is the **position vector** (x,v coordinates). If we want to measure the distance a particle has traveled whe take its magnitude:

$$
r = ||r||_2
$$

This can be viewed as displacement. We can now calculate the average velocity by:

$$
v_{av} = \frac{\Delta r}{\Delta t} \\
v_{av,x} = \frac{\Delta x}{\Delta t} \\
v_{av,y} = \frac{\Delta y}{\Delta t}
$$

This is a vector, and it has the same direction as $\Delta \vec{r}$ and the magnitude equal to the magnitude of $\Delta \vec{r}$ divided by $\Delta r$. And its compontets are the average velocity along each axes.

The magnitude $\Delta \vec{r}$ is allways a straing line distance between two points, regardle of the actal path.

## Instananeous velocity
Here ve just take the limit:

$$
\vec{v} = \lim_{\Delta t \rightarrow 0} \frac{\Delta \vec{r}}{\Delta t} \\
v_x = \lim_{\Delta t \rightarrow 0} \frac{\Delta x}{\Delta t} \\
v_y =\lim_{\Delta t \rightarrow 0} \frac{\Delta y}{\Delta t} 
$$

Here $\Delta \vec{r}$ becomes tagent to the curve of the trajector. 

The instantenous speed is just the magnitude of the instataneous velocity.

$$
|\vec{v}| = \sqrt{v_x^2 + v_y^2}
$$

We can express the angle in which an object is traveling as:

$$
\theta = \tan^{-1} \frac{u_y}{u_x}
$$