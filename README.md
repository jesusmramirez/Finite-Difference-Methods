Partial Differencial Equation:

Backward difference in time:
\begin{align*}
\frac{\partial V}{\partial V} = \frac{V_{i,j} - V_{i,j - 1}}{\delta t}
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

\begin{align*}
\frac{f_{i,j} - f_{i,j - 1}}{dt} + rS_i\frac{f_{i + 1,j} - f_{i - 1,j}}{2dS} + \frac{1}{2}\sigma^2 S_i^2\frac{f_{i + 1,j} - 2f_{i,j} + f_{i - 1,j}}{dS^2} - rf_{i,j} = 0
\end{align*}

Implicit Scheme

\begin{align*}
\frac{f_{i,j + 1} - f_{i,j}}{dt} + rS_i\frac{f_{i + 1,j} - f_{i - 1,j}}{2dS} + \frac{1}{2}\sigma^2 S_i^2\frac{f_{i + 1,j} - 2f_{i,j} + f_{i - 1,j}}{dS^2} - rf_{i,j} = 0
\end{align*}

The \textbf{Crank-Nicolson} scheme is basically the average of the explicit and implicit methods. Before to compute the average we lead the explicit equation one-period-ahead. Besides, we will assume that $S_i = S_b + idS$

Putting the $j+1$ terms in the left hand side of the equation, and multiplying by $dt$:
\begin{align*}
-a_i f_{i - 1,j} + (1 + b_i)f_{i,j} - c_i f_{i + 1,j} = a_i f_{i - 1,j + 1}  + (1 -  b_i) f_{i,j + 1} + c_i f_{i + 1,j + 1}
\end{align*}

where
\begin{align*}
a_i &= \frac{1}{4}(\sigma^2 k_i^2 - rk_i)dt \\
b_i &= \frac{1}{2}(\sigma^2 k_i^2 + r)dt\\
c_i &= \frac{1}{4}(\sigma^2 k_i^2 + rk_i)dt 
\end{align*}

\noindent In matrix form:
\begin{align*}
CU_{j} + g_{j}= DU_{j + 1} + h_{j + 1}
\end{align*}
where
\begin{align*}
C =
  \begin{bmatrix}
    (1+b_1) & -c_1  &  \cdots & 0 & 0 \\
    -a_2 & (1+b_1)  &  \cdots & 0 & 0 \\    
    \vdots & \vdots  & \ddots  & \vdots & \vdots\\    
    0 & 0 & \cdots  & (1 + b_{N-2}) & -c_{N-2}\\
    0 & 0 & \cdots  & -a_{N-1} & (1 + b_{N-1})    
  \end{bmatrix}  
\end{align*}
\begin{align*}
D =
  \begin{bmatrix}
    (1-b_1) & c_1  &  \cdots & 0 & 0 \\
    a_2 & (1-b_1)  &  \cdots & 0 & 0 \\    
    \vdots & \vdots  & \ddots  & \vdots & \vdots\\    
    0 & 0 & \cdots  & (1 - b_{N-2}) & c_{N-2}\\
    0 & 0 & \cdots  & a_{N-1} & (1 - b_{N-1})    
  \end{bmatrix}  
\end{align*}
\begin{align*}
U_j = 
\begin{bmatrix}
    f_{1,j}\\
    f_{2,j} \\
    \vdots \\    
    f_{N - 2, j} \\
    f_{N - 1, j}    
  \end{bmatrix}
, g_j = 
\begin{bmatrix}
    -a_0 f_{0,j}\\
    0 \\
    \vdots \\    
    0 \\
    -c_{N-1} f_{N, j}    
  \end{bmatrix}
  , h_{j + 1} = 
\begin{bmatrix}
    a_0 f_{0,j + 1}\\
    0 \\
    \vdots \\    
    0 \\
    c_{N-1} f_{N, j + 1}    
  \end{bmatrix}
\end{align*}
