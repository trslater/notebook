# Möller–Trumbore

Ray–Triangle intersection algorithm.

For a triangle $ABC$, any point $P$ on or inside the triangle can be found with the following:

$$P = uA + vB + wC$$

Where $u, v, w \geq 0, u + v + w = 1$.

Sub in a equation for point on a ray and solve:

$$\begin{align*}
    E + t\mathbf{\hat{d}} &= uA + vB + (1 - u - v)C \\
    E - C &= t(-\mathbf{\hat{d}}) + u(A - C) + v(B - C) \\
    &= \begin{bmatrix}
        | & | & | \\
        -\mathbf{\hat{d}} & A - C & B - C \\
        | & | & |
    \end{bmatrix}\begin{bmatrix}
        t \\
        u \\
        v
    \end{bmatrix} \\
    \begin{bmatrix}
        t \\
        u \\
        v
    \end{bmatrix} &= \begin{bmatrix}
        | & | & | \\
        -\mathbf{\hat{d}} & A - C & B - C \\
        | & | & |
    \end{bmatrix}^{-1}(E - C)
\end{align*}$$

Just check: $t \geq 0, u, v, w \in [0, 1]$

To get intersection point, plug $t$ into ray equation:

$$R(t) = E + t\mathbf{\hat{d}}$$
