# 制約付き最小化問題

$$f:R^n \rightarrow R,\ \  g_i,h_i:R^n \rightarrow R$$について次の問題を考える。

$$
\begin{eqnarray}
&minimize& \ f(x) \\
&s.t.&
\left \{
\begin{matrix}
G(x) =
\begin{pmatrix}
  g_1(x_1, \dots, x_n) \\
  \vdots \\
  g_m(x_1, \dots, x_n)
\end{pmatrix}
= 0 \\
H(x) =
\begin{pmatrix}
  h_1(x_1, \dots, x_n) \\
  \vdots \\
  h_l(x_1, \dots, x_n)
\end{pmatrix}
\leq 0
\end{matrix}
\right.
\end{eqnarray}
$$

## 最適性条件

### 1次導関数に対する条件

$$x^* $$において$$f,g,h$$が連続微分可能であるとする。

<center>

</center>
