# 等式制約付き最小化問題

$$f:R^n \rightarrow R,\ \  g_i:R^n \rightarrow R$$について次の問題を考える。

$$
\begin{eqnarray}
minimize \ &f(x)& \\
s.t. \ &G(x)& =
\begin{pmatrix}
  g_1(x_1, \dots, x_n) \\
  \vdots \\
  g_m(x_1, \dots, x_n)
\end{pmatrix}
=0
\end{eqnarray}
$$

## 最適性条件

<center>
$$x^* $$が大域的最小解
⇔　$$x^* $$は停留点（$$\frac{\partial}{\partial x_i}f(x^* )=0$$となる点）のうち$$f(x)$$の値が最小となるもの
</center>

## 解法

大域的最小解の候補となる停留点は[ラグランジュ乗数法](../../mathematics/analysis/lagrange_multiplier.md)を用いて導ける。

単に大域的最小解を得るだけならば、極大点・極小点・鞍点などを区別する必要がないため、それぞれの停留値（$$f(x)$$）を求め、値が最小になるものを選択すれば良い。
