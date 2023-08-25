# Derivatives

## Vector Function Derivatives

For vector-valued function:

$$\mathbf{f}(x) = \begin{bmatrix}
    f \\ g \\ h
\end{bmatrix}$$

$$\frac{d\mathbf{f}}{d x} = \begin{bmatrix}
    \frac{\partial f}{\partial x} \\
    \frac{\partial g}{\partial x} \\
    \frac{\partial h}{\partial x}
\end{bmatrix}$$

Pretty natural when you realize that $\mathbf{f}$ can be represented as a linear combination of basis vectors, where each coefficient is a scalar-by-scalar function. Then, we just apply derivative sum rule.

## Multivariate Function Derivatives

For multivariate function:

$$f(\mathbf{x}) = f(x, y, z)$$

$$\frac{d f}{d\mathbf{x}} = \begin{bmatrix}
    \frac{\partial f}{\partial x} & \frac{\partial f}{\partial y} & \frac{\partial f}{\partial z}
\end{bmatrix}$$

This is less straightforward than the vector-valued equivalent. Why is the derivative of a scalar-valued function a vector? Why is it a row vector? There are two good ways to think about this I've found:

1.  Instead of viewing it as a vector, think of it was a tuple of 1D vectors. What universe does the value of this derivative live in? The same universe as $f$. This derivative takes values in the 3D universe of $\mathbf{x}$ and converts them to the 1D universe of $f$.
2.  The other way of thinking of this is less conceptual and more pragmatic. Think about the derivative as a ratio. The top is scalar, but the bottom isn't. It's a scalar-to-vector ratio. For vectors in linear algebra, what is the analog to division? Inversion. So, the derivative can be thought of as:

    $$\frac{df}{d\mathbf{x}} = (d\mathbf{x})^{-1}df$$

    If we rearrange to solve for $df$ (a scalar):

    $$df = \frac{df}{d\mathbf{x}}d\mathbf{x}$$

    $d\mathbf{x}$ is a normal column vector, so $\frac{df}{d\mathbf{x}}$ has to be a row vector to make $df$ a scalar.

In either formulation, it says, "how do changes in each variable affect $f$, and if we apply these rates to each actual change in $\mathbf{x}$ we'll get each variables contribution to the new $f$. We just add them together to get the final result."

Think what happens when approximating:

$$\begin{align*}
    f(\mathbf{x} + \Delta\mathbf{x}) &= f(\mathbf{x}) + \frac{df}{d\mathbf{x}}\Delta\mathbf{x} \\
    &= f(\mathbf{x}) + \frac{\partial f}{\partial x}\Delta x + \frac{\partial f}{\partial y}\Delta y + \frac{\partial f}{\partial z}\Delta z
\end{align*}$$

## Multivariate Vector Function Derivatives

When combined, it is very natural to just apply either the multivariate or vector-valued derivative first and then the other:

$$\begin{align*}
    \mathbf{J} &= \frac{d\mathbf{f}}{d\mathbf{x}} \\
    &= \begin{bmatrix}
        - \frac{\partial f}{\partial\mathbf{x}} - \\
        - \frac{\partial g}{\partial\mathbf{x}} - \\
        - \frac{\partial h}{\partial\mathbf{x}} -
    \end{bmatrix} \\
    &= \begin{bmatrix}
        | & | & | \\
        \frac{\partial\mathbf{f}}{\partial x} & \frac{\partial\mathbf{f}}{\partial y} & \frac{\partial\mathbf{f}}{\partial z} \\
        | & | & |
    \end{bmatrix} \\
    &= \begin{bmatrix}
        \frac{\partial f}{\partial x} & \frac{\partial f}{\partial y} & \frac{\partial f}{\partial z} \\
        \frac{\partial g}{\partial x} & \frac{\partial g}{\partial y} & \frac{\partial g}{\partial z} \\
        \frac{\partial h}{\partial x} & \frac{\partial h}{\partial y} & \frac{\partial h}{\partial z} \\
    \end{bmatrix}
\end{align*}$$

This matrix is commonly referred to as **the Jacobian**.

## Del Operator

The del operator is a convenient notation for working with vector fields:

$$\nabla = \begin{bmatrix}
    \frac{\partial}{\partial x} \\
    \frac{\partial}{\partial y} \\
    \frac{\partial}{\partial z}
\end{bmatrix}$$

Gradient:

$$\nabla f = \begin{bmatrix}
    \frac{\partial f}{\partial x} \\
    \frac{\partial f}{\partial y} \\
    \frac{\partial f}{\partial z}
\end{bmatrix} = \left(\frac{d f}{d \mathbf{x}}\right)^T$$

Divergence:

$$\nabla \cdot \mathbf{f} = \frac{\partial f}{\partial x} + \frac{\partial g}{\partial y} + \frac{\partial h}{\partial z}$$

Curl:

$$\nabla \times \mathbf{f}$$

There's not a lot of value in expanding it out, since it is not very elegant.

Laplacian:

$$\nabla^2 = \frac{\partial^2}{\partial x^2} + \frac{\partial^2}{\partial y^2} + \frac{\partial^2}{\partial z^2}$$

The Jacobian can be written in terms of del:

$$\begin{align*}
    \left(\nabla\mathbf{f}^T\right)^T &= \left(\begin{bmatrix}
        \frac{\partial}{\partial x} \\
        \frac{\partial}{\partial y} \\
        \frac{\partial}{\partial z}
    \end{bmatrix}\begin{bmatrix}
        f & g & h
    \end{bmatrix}\right)^T \\
    &= \begin{bmatrix}
        \frac{\partial f}{\partial x} & \frac{\partial g}{\partial x} & \frac{\partial h}{\partial x} \\
        \frac{\partial f}{\partial y} & \frac{\partial g}{\partial y} & \frac{\partial h}{\partial y} \\
        \frac{\partial f}{\partial z} & \frac{\partial g}{\partial z} & \frac{\partial h}{\partial z}
    \end{bmatrix}^T \\
    &= \begin{bmatrix}
        \frac{\partial f}{\partial x} & \frac{\partial f}{\partial y} & \frac{\partial f}{\partial z} \\
        \frac{\partial g}{\partial x} & \frac{\partial g}{\partial y} & \frac{\partial g}{\partial z} \\
        \frac{\partial h}{\partial x} & \frac{\partial h}{\partial y} & \frac{\partial h}{\partial z}
    \end{bmatrix} \\
    &= \mathbf{J}
\end{align*}$$

Or:

$$\begin{align*}
    \begin{bmatrix}
        - \nabla^T f - \\
        - \nabla^T g - \\
        - \nabla^T h -
    \end{bmatrix} &= \begin{bmatrix}
        - \begin{bmatrix}
            \frac{\partial}{\partial x} & \frac{\partial}{\partial y} & \frac{\partial}{\partial z}
        \end{bmatrix}f - \\
        - \begin{bmatrix}
            \frac{\partial}{\partial x} & \frac{\partial}{\partial y} & \frac{\partial}{\partial z}
        \end{bmatrix}g - \\
        - \begin{bmatrix}
            \frac{\partial}{\partial x} & \frac{\partial}{\partial y} & \frac{\partial}{\partial z}
        \end{bmatrix}h -
    \end{bmatrix} \\
    &= \begin{bmatrix}
        - \begin{bmatrix}
            \frac{\partial f}{\partial x} & \frac{\partial f}{\partial y} & \frac{\partial f}{\partial z}
        \end{bmatrix} - \\
        - \begin{bmatrix}
            \frac{\partial g}{\partial x} & \frac{\partial g}{\partial y} & \frac{\partial g}{\partial z}
        \end{bmatrix} - \\
        - \begin{bmatrix}
            \frac{\partial h}{\partial x} & \frac{\partial h}{\partial y} & \frac{\partial h}{\partial z}
        \end{bmatrix} -
    \end{bmatrix} \\
    &= \begin{bmatrix}
        \frac{\partial f}{\partial x} & \frac{\partial f}{\partial y} & \frac{\partial f}{\partial z} \\
        \frac{\partial g}{\partial x} & \frac{\partial g}{\partial y} & \frac{\partial g}{\partial z} \\
        \frac{\partial h}{\partial x} & \frac{\partial h}{\partial y} & \frac{\partial h}{\partial z}
    \end{bmatrix} \\
    &= \mathbf{J}
\end{align*}$$
