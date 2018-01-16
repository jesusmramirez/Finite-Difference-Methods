Partial Differencial Equation:
\begin{align*}
\frac{\partial V}{\partial V} + rS\frac{\partial V}{\partial S} + \frac{1}{2} \sigma^2 S^2 \frac{\partial^2 V}{\partial S^2} - rV = 0
\end{align*}

Backward difference in time:
\begin{align*}
\frac{\partial V}{\partial t} = \frac{V_{i,j} - V_{i,j - 1}}{\delta t}
\end{align*}

Forward difference in time:
\begin{align*}
\frac{\partial V}{\partial t} = \frac{V_{i,j + 1} - V_{i,j}}{\delta t}
\end{align*}

Central difference in $S$:
\begin{align*}
\frac{\partial V}{\partial S} &= \frac{V_{i + 1,j} - V_{i - 1,j}}{2\delta S}
\end{align*}

Central difference in $S^2$:
\begin{align*}
\frac{\partial^2 V}{\partial S^2} &= \frac{V_{i + 1,j} - 2V_{i,j} + V_{i - 1,j}}{\delta S^2}
\end{align*}

Explicit Scheme
We use the backward difference in $t$ and the central differences in $S$ and $S^2$

\begin{align*}
\frac{V_{i,j} - V_{i,j - 1}}{\delta t} + rS_i\frac{V_{i + 1,j} - V_{i - 1,j}}{2\delta S} + \frac{1}{2}\sigma^2 S_i^2\frac{V_{i + 1,j} - 2V_{i,j} + V_{i - 1,j}}{\delta S^2} - rV_{i,j} = 0
\end{align*}

Implicit Scheme
We change the backward difference in $t$ by its forward difference

\begin{align*}
\frac{V_{i,j + 1} - V_{i,j}}{\delta t} + rS_i\frac{V_{i + 1,j} - v_{i - 1,j}}{2\delta S} + \frac{1}{2}\sigma^2 S_i^2\frac{V_{i + 1,j} - 2V_{i,j} + V_{i - 1,j}}{\delta S^2} - rV_{i,j} = 0
\end{align*}

The Crank-Nicolson scheme is basically the average of the explicit and implicit schemes. Before to compute the average we lead the explicit equation one-period-ahead. After some simplification we get
\begin{align*}
-a_i V_{i - 1,j} + (1 + b_i)V_{i,j} - c_i V_{i + 1,j} = a_i V_{i - 1,j + 1}  + (1 -  b_i) V_{i,j + 1} + c_i V_{i + 1,j + 1}
\end{align*}

where
\begin{align*}
a_i &= \frac{1}{4}(\sigma^2 k_i^2 - rk_i)dt \n
b_i &= \frac{1}{2}(\sigma^2 k_i^2 + r)dt \n
c_i &= \frac{1}{4}(\sigma^2 k_i^2 + rk_i)dt 
\end{align*}

In matrix form:
\begin{align*}
CU_{j} + g_{j}= DU_{j + 1} + h_{j + 1}
\end{align*}
