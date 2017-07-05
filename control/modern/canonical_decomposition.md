# 正準分解（canonical decomposition）

ある任意のシステムが与えられたとき、可制御性と可観測性の概念に基づいていくつかのサブシステムに分割する事ができ、これを**カルマンの正準分解**という。

## 定理

$$
\begin{eqnarray}
\dot{x} &=& Ax + Bu \\
y &=& Cx
\end{eqnarray}
$$

は適当な同値変換を用いて

$$
\begin{eqnarray}
\dot{\bar{x}} &=& F\bar{x} + Gu \\
y &=& H\bar{x} \\
F &=& \begin{bmatrix}
F^{aa} & F^{ab} & F^{ac} & F^{ad} \\
0 & F^{bb} & 0 & F^{bd} \\
0 & 0 & F^{cc} & F^{cd} \\
0 & 0 & 0 & F^{dd}
\end{bmatrix} \\
G &=& \begin{bmatrix}
G^a \\ G^b \\ 0 \\ 0
\end{bmatrix} \\
H &=& \begin{bmatrix}
0 & H^b & 0 & H^d
\end{bmatrix}
\end{eqnarray}
$$

に変換できる。


