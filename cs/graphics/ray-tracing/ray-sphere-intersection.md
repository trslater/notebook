# Ray–Sphere Intersection

$$\begin{align*}
    r &= ||P - C|| \\
    &= ||E + t\mathbf{\hat{d}} - C|| \\
    r^2 &= ||E + t\mathbf{\hat{d}} - C||^2 \\
    &= ((E - C) + t\mathbf{\hat{d}}) \cdot ((E - C) + t\mathbf{\hat{d}}) \\
    0 &= ||E - C||^2 - r^2 + 2((E - C) \cdot \mathbf{\hat{d}})t + ||\mathbf{\hat{d}}||^2 t^2 \\
    &= ||E - C||^2 - r^2 + 2((E - C) \cdot \mathbf{\hat{d}})t + t^2, & \mathbf{\hat{d}} \text{ is a unit vector}
\end{align*}$$

Note: we have a quadratic equation in terms of $t$:

$$\begin{gather*}
    a = 1 \\
    b = (E - C) \cdot \mathbf{\hat{d}} \\
    c = ||E - C||^2 - r^2
\end{gather*}$$

$$\begin{align*}
    t &= \frac{-b \pm \sqrt{b^2 - 4ac}}{2a} \\
    &= \frac{-2(E - C) \cdot \mathbf{\hat{d}} \pm \sqrt{(2(E - C) \cdot \mathbf{\hat{d}})^2 - 4(||E - C||^2 - r^2)}}{2} \\
    &= -(E - C) \cdot \mathbf{\hat{d}} \pm \sqrt{((E - C) \cdot \mathbf{\hat{d}})^2 - ||E - C||^2 + r^2} \\
\end{align*}$$

## Improving Performance

We can pre-compute $\beta = (E - C)\cdot\mathbf{\hat{d}}$ and use it to compute the discriminant:

$$\Delta = \beta^2 - ||E - C||^2 + r^2$$

We only want real solutions, so if $\Delta < 0$, we know the ray misses.

If $\Delta = 0$ and $-\beta \geq 0$, then $t = -\beta$. This happens when the ray is tangent to the sphere.

If $\Delta > 0$, there will be two solutions: the entrance into and exit out of the sphere, but we only want the entrance, which will always be the smaller of the two, i.e., hits the object first. Since both $t$ and the radical have to be non-negative, the minus solution will always be smaller, so we don't need to worry about the plus solution.

Therefore, if $-\beta - \sqrt{\Delta} \geq 0$, then $t = -\beta - \sqrt{\Delta}$
