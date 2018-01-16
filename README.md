Partial Differencial Equation:

Backward difference in time:
\begin{align*}
\frac{\partial f}{\partial t} = \frac{f_{i,j} - f_{i,j - 1}}{dt}
\end{align*}

Forward difference in time:
\begin{align*}
\frac{\partial f}{\partial t} = \frac{f_{i,j + 1} - f_{i,j}}{dt}
\end{align*}

Central difference in $S$:
\begin{align*}
\frac{\partial f}{\partial S} &= \frac{f_{i + 1,j} - f_{i - 1,j}}{2dS}
\end{align*}

Central difference in $S^2$:
\begin{align*}
\frac{\partial^2 f}{\partial S^2} &= \frac{f_{i + 1,j} - 2f_{i,j} + f_{i - 1,j}}{dS^2}
\end{align*}

Explicit Scheme

