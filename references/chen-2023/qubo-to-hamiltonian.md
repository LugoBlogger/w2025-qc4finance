$$
\rule{19cm}{1pt}
$$

From the QUBO objective function
$$
\begin{align*}
  &\min_{\mathbf{x}} \gamma \mathbf{x}^\mathsf{T} \mathbf{\sigma} \mathbf{x} 
    - \mathbf{\mu}^\mathsf{T} \mathbf{x}
    + P(\mathbf{1}^\mathsf{T} \mathbf{x} - B)^2  \\
  &\quad= \min_{x_k \in \{0, 1\}}
    \gamma \sum_{i=1}^n \sum_{j=1}^n x_i \sigma_{ij} x_j  
      - \sum_{i=1}^n \mu_i x_i
      + P \left(\sum_{i=1}^n x_i - B\right)^2
\end{align*}
$$



because covariance matrix $\mathbf{\sigma}$ is symmetric 
$(\sigma_{ij} = \sigma_{ji})$, we can decompose the sum for lower and 
upper triangular of matrix $\mathbf{\sigma}$ and its diagonal terms
$$
\begin{align*}
  &= \min_{x_k \in \{0, 1\}}
    2 \gamma \sum_{i=1}^n \sum_{j=i+1}^n x_i \sigma_{ij} x_j  
      + \gamma\sum_{i=1}^n x_i \sigma_{ii} x_i
      - \sum_{i=1}^n \mu_i x_i
      + P \left(\sum_{i=1}^n x_i - B\right)^2
\end{align*}
$$

Use the substitution $x_i = (1 - z_i)/2$ 
$$
\begin{align*}
  &= \min_{z_k \in \{-1, 1\}}
    2 \gamma \sum_{i} \sum_{j>i} 
      \left(\frac{1 - z_i}{2}\right) \sigma_{ij} \left(\frac{1 - z_j}{2}\right)
      + \gamma\sum_{i} \sigma_{ii} \left(\frac{1 - z_i}{2}\right)^2
      - \sum_{i} \mu_i \left(\frac{1 - z_i}{2}\right)
      + P \left(\sum_{i} \left(\frac{1 - z_i}{2}\right) - B\right)^2 \\
  &= \min_{z_k \in \{-1, 1\}}
    \frac{\gamma}{2} \sum_{i} \sum_{j>i} 
      \sigma_{ij} (1 - z_i - z_j + z_i z_j)
      + \frac{\gamma}{4}\sum_{i} \sigma_{ii} (1 - 2z_i + z_i^2)
      - \frac{1}{2}\sum_{i} \mu_i (1 - z_i)
      + P \left(\frac{n}{2} -\frac{1}{2}\sum_{i}z_i - B\right)^2 \\
  &= \min_{z_k \in \{-1, 1\}}
    \frac{\gamma}{2} \sum_{i} \sum_{j>i} 
      \sigma_{ij} (1 - z_i - z_j + z_i z_j)
      + \frac{\gamma}{4}\sum_{i} \sigma_{ii} (1 - 2z_i + z_i^2)
      - \frac{1}{2}\sum_{i} \mu_i (1 - z_i)
      + \frac{P}{4} \left(n -\sum_{i}z_i - 2B\right)^2 
\end{align*}
$$

Since $\sigma_{ij} = \sigma_{ji}$, we have
$$
\begin{align*}
  \sum_i \sum_{j>i} \sigma_{ij} (- z_i - z_j) 
    &= \frac{1}{2} \sum_i \sum_{j\neq i} \sigma_{ij}(-z_i - z_j) \\
    &= \frac{1}{2} \left( \sum_i \sum_{j\neq i} \sigma_{ij}(-z_i) 
      + \sum_i \sum_{j \neq i} \sigma_{ij}(-z_j)\right) \\
    &= \frac{1}{2} \left( \sum_i \sum_{j\neq i} \sigma_{ij}(-z_i) 
      + \sum_i \sum_{j \neq i} \sigma_{ji}(-z_j)\right) \\
    &= \frac{1}{2} \left( \sum_i \sum_{j\neq i} \sigma_{ij}(-z_i) 
      + \sum_j \sum_{i \neq j} \sigma_{ji}(-z_j)\right) \\
    &= \frac{1}{2} \left( \sum_i \sum_{j\neq i} \sigma_{ij}(-z_i) 
      + \sum_i \sum_{j \neq i} \sigma_{ij}(-z_i)\right) \\
    &= \frac{1}{2} \left( 2 \sum_i \sum_{j\neq i} \sigma_{ij}(-z_i) 
      \right) \\
    &= \sum_i \sum_{j\neq i} \sigma_{ij} (-z_i) 
\end{align*}
$$
in the above calculation, we flip twice (due to the symmetry) 
the dummy indices $i$ and $j$ in the second summation.
With the properties that $z_i^2 = 1$, we can simplify the last term
$$
\begin{align*}
  \left(n - \sum_i z_i - 2B\right)^2
    &= \left(-\sum_i z_i + \left(n - 2B\right)\right)^2 \\
    &= \left(\sum_i z_i\right)^2 
      -  2 \left(n - 2B\right) \sum_{i} z_i
      + \left(n - 2B\right)^2 \\
    &= \sum_i \sum_j z_i z_j 
      -  2 \left(n - 2B\right) \sum_{i} z_i
      + \left(n - 2B\right)^2 \\
    &= 2\sum_i \sum_{j > i} z_i z_j  + \sum_i z_i^2
      -  2 \left(n - 2B\right) \sum_{i} z_i
      + \left(n - 2B\right)^2 \\
    &= 2\sum_i \sum_{j > i} z_i z_j  + n 
      -  2 \left(n - 2B\right) \sum_{i} z_i
      + \left(n - 2B\right)^2 \\
    &= 2\sum_i \sum_{j > i} z_i z_j 
      -  2 \left(n - 2B\right) \sum_{i} z_i
      + n + \left(n - 2B\right)^2 
\end{align*}
$$

Finaly we have
$$
\begin{align*}
&= \min_{z_k \in \{-1, 1\}}
  \frac{\gamma}{2} \sum_{i} \sum_{j>i} \sigma_{ij} 
    - \frac{\gamma}{2} \sum_i \sum_{j\neq i} \sigma_{ij} z_i 
    + \frac{\gamma}{2} \sum_i \sum_{j>i}  \sigma_{ij} z_i z_j \\
    &\qquad\qquad + \frac{\gamma}{4}\sum_{i} \sigma_{ii} 
    - \frac{\gamma}{2} \sum_{i} \sigma_{ii} z_i 
    + \frac{\gamma}{4} \sum_{i} \sigma_{ii} z_i^2 \\
    &\qquad\qquad
    - \frac{1}{2}\sum_{i} \mu_i + \frac{1}{2}\sum_{i} \mu_i z_i \\
    &\qquad\qquad
    + \frac{P}{2}\sum_i \sum_{j > i} z_i z_j 
      -  \frac{P}{2}\left(n - 2B\right) \sum_{i} z_i
      + \frac{P}{4} \left( n + \left(n - 2B\right)^2\right) \\
\end{align*}
$$

Rearranging based on the quadratic, linear, and constant terms
$$
\begin{align*}
&= \min_{z_k \in \{-1, 1\}}
    \frac{\gamma}{2} \sum_i \sum_{j>i}  \sigma_{ij} z_i z_j 
    + \frac{P}{2}\sum_i \sum_{j > i} z_i z_j \\
    &\qquad\qquad - \frac{\gamma}{2} \sum_i \sum_{j\neq i} \sigma_{ij} z_i  
    - \frac{\gamma}{2} \sum_{i} \sigma_{ii} z_i 
    + \frac{1}{2}\sum_{i} \mu_i z_i 
    -  \frac{P}{2}\left(n - 2B\right) \sum_{i} z_i \\
    &\qquad\qquad+ \frac{\gamma}{2} \sum_{i} \sum_{j>i} \sigma_{ij}
      + \frac{\gamma}{4}\sum_{i} \sigma_{ii} 
      + \frac{\gamma}{4} \sum_{i} \sigma_{ii} z_i^2 \\
    &\qquad\qquad
    - \frac{1}{2}\sum_{i} \mu_i 
      + \frac{P}{4} \left( n + \left(n - 2B\right)^2\right) \\
&= \min_{z_k \in \{-1, 1\}}
    \sum_i \sum_{j>i} \frac{(\gamma \sigma_{ij} + P)}{2}  z_i z_j  \\
    &\qquad\qquad - \frac{\gamma}{2} \sum_i \sum_{j\neq i} \sigma_{ij} z_i  
    - \frac{\gamma}{2} \sum_{i} \sigma_{ii} z_i 
    + \frac{1}{2}\sum_{i} \mu_i z_i 
    -  \frac{P}{2}\left(n - 2B\right) \sum_{i} z_i \\
    &\qquad\qquad+ \frac{\gamma}{2} \sum_{i} \sum_{j>i} \sigma_{ij}
      + \frac{\gamma}{4}\sum_{i} \sigma_{ii} 
      + \frac{\gamma}{4} \sum_{i} \sigma_{ii} z_i^2 \\
    &\qquad\qquad
    - \frac{1}{2}\sum_{i} \mu_i 
      + \frac{P}{4} \left( n + \left(n - 2B\right)^2\right) \\
&= \min_{z_k \in \{-1, 1\}}
    \sum_i \sum_{j>i} \frac{(\gamma \sigma_{ij} + P)}{2}  z_i z_j  \\
    &\qquad\qquad + \sum_i \left(
      -\frac{\gamma}{2}\sum_{j} \sigma_{ij}   + \frac{\mu_i}{2} 
      -\frac{P}{2}\left(n - 2B\right) \right)z_i \\
    &\qquad\qquad+ \frac{\gamma}{4} \left(2\sum_{i} \sum_{j>i} \sigma_{ij}
      + \sum_{i} \sigma_{ii} \right) 
      + \frac{\gamma}{4} \sum_{i} \sigma_{ii} z_i^2 \\
    &\qquad\qquad
    - \frac{1}{2}\sum_{i} \mu_i 
      + \frac{P}{4} \left( n + \left(n - 2B\right)^2\right) \\
&= \min_{z_k \in \{-1, 1\}}
    \sum_i \sum_{j>i} \frac{(\gamma \sigma_{ij} + P)}{2}  z_i z_j  \\
    &\qquad\qquad + \sum_i \left(
      -\frac{\gamma}{2}\sum_{j} \sigma_{ij}   + \frac{\mu_i}{2} 
      -\frac{P}{2}\left(n - 2B\right) \right)z_i \\
    &\qquad\qquad+ \frac{\gamma}{4} \sum_{i} \sum_{j} \sigma_{ij}
      + \frac{\gamma}{4} \sum_{i} \sigma_{ii} \\
    &\qquad\qquad
    - \frac{1}{2}\sum_{i} \mu_i 
      + \frac{P}{4} \left( n + \left(n - 2B\right)^2\right) \\
\end{align*}
$$