Partial Differencial Equation:

Backward difference in time:
\begin{align*}
\frac{\partial V}{\partial V} = \frac{V_{i,j} - V_{i,j - 1}}{\delta t}
\end{align*}

Forward difference in time:
\begin{align*}
\frac{\partial V}{\partial t} = \frac{V_{i,j + 1} - V_{i,j}}{dt}
\end{align*}

Central difference in $S$:
\begin{align*}
\frac{\partial V}{\partial S} &= \frac{V_{i + 1,j} - V_{i - 1,j}}{2dS}
\end{align*}

Central difference in $S^2$:
\begin{align*}
\frac{\partial^2 V}{\partial S^2} &= \frac{V_{i + 1,j} - 2V_{i,j} + V_{i - 1,j}}{dS^2}
\end{align*}

Explicit Scheme

