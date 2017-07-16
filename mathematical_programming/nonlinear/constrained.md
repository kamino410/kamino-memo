# 一般の制約付き最小化問題

次の問題について考える。

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
\right. \\
&x \in D \subseteq R^n,& \ \ \ f:D \rightarrow R, \ \ \ g_i,h_i:D \rightarrow R
\end{eqnarray}
$$

## 有効制約式

不等式制約条件について、$$h_i(x')=0$$ であるとき、この制約式を $$x'$$ での**有効制約式（active constraint）**という。

## 最適性条件

$$x^* $$ において $$f,g$$ は連続1階微分可能かつ2階微分可能であるとする。

### 1次導関数に対する条件

局所的最小解 $$x^*$$ において、効いているすべての制約式 $$h_i$$ に対して $$\nabla h_i(x^*)$$ が線形独立ならば、適当な $$l$$ 次元ベクトル $$z^* = \begin{bmatrix}z_1^* & \cdots & z_l^*\end{bmatrix}^T$$ が存在して、$$(x^*, z^*)$$ が次の条件を満足する。

$$
\begin{eqnarray}
&\ & \nabla_x L(x^*, z^*) = \nabla f(x^*) + \sum_{i=1}^l z_i^* \nabla h_i(x^*) = 0 \\
&\ & \nabla_z L(x^*, z^*) = h(x^*) \leq 0 \\
&\ & z_i^* \geq 0 \ \ \ (i = 1, \cdots, l) \\
&\ & z_i^* h_i(x^*) = 0 \ \ \ (i = 1, \cdots, l)
\end{eqnarray}
$$

これを**KKT条件（Karush-Kuhn-Tucker condition）**という。

### 2次導関数に対する条件

局所的最小解 $$x^*$$ において、KKT条件を満足する $$z^*$$ が存在するとする。

さらに効いているすべての制約式 $$h_i$$ に対して $$\nabla h_i(x^*)^Tv = 0$$ となる零でない任意のベクトル $$v \in R^n$$ に対して適当な正の数 $$c,\beta$$ と連続なベクトル値関数 $$\phi:[0,c) \rightarrow R^n$$ が存在し、 $$\phi(0) = x^*, \ h_i(\phi(\tau)) = 0 \ \ (\tau \in (0,c)), \ \lim_{\tau \rightarrow 0}\frac{\phi(\tau)-\phi(0)}{\tau} = \beta v$$ が成立するとする（2次の制約想定）。

このとき、

$$
v^T \nabla_x^2 L(x^*,z^*)v = v^T \left(\nabla^2 f(x^*) + \sum_{i=1}^l z^*_i \nabla^2 h_i(x^*) \right) \geq 0
$$

が成立する。
