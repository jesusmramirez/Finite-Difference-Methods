The Black-Scholes-Merton partial differential equation (PDE):
\begin{align*}
\frac{\partial V}{\partial t} + rS\frac{\partial V}{\partial S} + \frac{1}{2} \sigma^2 S^2 \frac{\partial^2 V}{\partial S^2} - rV = 0
\end{align*}

Before to approximate this PDE using finite difference methods, we know that partial derivatives can be approximate using either backward or forward differences. For our purposes, we will use the following approximations:

Backward difference in $t$:
\begin{align*}
\frac{\partial V}{\partial t} = \frac{V_{i,j} - V_{i,j - 1}}{\delta t}
\end{align*}

Forward difference in $t$:
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

Explicit Scheme:

We use the backward difference in $t$ and the central differences in $S$ and $S^2$

\begin{align*}
\frac{V_{i,j} - V_{i,j - 1}}{\delta t} + rS_i\frac{V_{i + 1,j} - V_{i - 1,j}}{2\delta S} + \frac{1}{2}\sigma^2 S_i^2\frac{V_{i + 1,j} - 2V_{i,j} + V_{i - 1,j}}{\delta S^2} - rV_{i,j} = 0
\end{align*}

Implicit Scheme:

We change the backward difference in $t$ by its forward difference

\begin{align*}
\frac{V_{i,j + 1} - V_{i,j}}{\delta t} + rS_i\frac{V_{i + 1,j} - v_{i - 1,j}}{2\delta S} + \frac{1}{2}\sigma^2 S_i^2\frac{V_{i + 1,j} - 2V_{i,j} + V_{i - 1,j}}{\delta S^2} - rV_{i,j} = 0
\end{align*}

Crank-Nicolson scheme:

This scheme is basically an average of both the explicit and implicit schemes. Before we compute the average we have to lead the explicit equation one-period-ahead. After some simplification we get:
\begin{align*}
-a_i V_{i - 1,j} + (1 + b_i)V_{i,j} - c_i V_{i + 1,j} = a_i V_{i - 1,j + 1}  + (1 -  b_i) V_{i,j + 1} + c_i V_{i + 1,j + 1}
\end{align*}

where
\begin{align*}
a_i &= \frac{1}{4} \frac{\delta t}{\delta S}(\frac{\sigma^2 S_i^2}{\delta S} - rS_i)dt \newline
b_i &= \frac{1}{2} \frac{\delta t}{\delta S}(\sigma^2 S_i^2 + r)dt \newline
c_i &= \frac{1}{4} \frac{\delta t}{\delta S}(\frac{\sigma^2 S_i^2}{\delta S} + rS_i)dt 
\end{align*}
