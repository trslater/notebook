# Objects

## Ray

$$R(t) = E + t\mathbf{\hat{d}}$$

## Plane

$$\mathbf{\hat{n}}, P_0$$

Or

$$\mathbf{\hat{n}}, d$$

$P_0$ and $d$ are related as follows:

$$P_0 = \left(-\frac{d}{a}, 0, 0\right) = \left(0, -\frac{d}{b}, 0\right) = \left(0, 0, -\frac{d}{c}\right)$$

This tells us where on the $x$, $y$, and $z$ axes the plane intersects.

There are two main formulations:

$$0 = \mathbf{\hat{n}} \cdot (P - P_0)$$

$$0 = ax + by + cz + d$$

These are really the same:

$$\begin{align*}
    0 &= \mathbf{\hat{n}} \cdot (P - P_0) \\
    &= \mathbf{\hat{n}} \cdot P - \mathbf{\hat{n}} \cdot P_0 \\
    &= (a, b, c) \cdot (x, y, z) - (a, b, c) \cdot \left(-\frac{d}{a}, 0, 0\right) \\
    &= ax + by + cz - ((-d) + 0 + 0) \\
    &= ax + by + cz + d
\end{align*}$$

## Sphere

$$||P - C|| = r$$

## Parallelogram

$$P = A + u(B - A) + v(C - A), \quad u,v \in [0, 1]$$

## Triangle

Same as parallelogram with an additional constraint:

$$(u + v) \in [0, 1]$$
