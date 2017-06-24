# 等式制約付き最小化問題

$$x \in D \subseteq R^n$$

$$f:D \rightarrow R$$

$$g_i:R^n \rightarrow R$$

について次の問題を考える。

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

この問題における局所的最小解は $$x^* $$ は次のような条件を満たす（ただし後述するように局所的最小解の中に最適解があるとは限らない）。

$$x^* $$ において $$f,g$$ は微分可能であるとする。

### 1次導関数に対する条件

<center>
$$x^* $$ が局所的最小解　⇒　$$x^* $$ は停留点（$$\frac{\partial}{\partial x_i}f(x^* )=0$$となる点）
</center>

[ラグランジュ乗数法](../../mathematics/analysis/lagrange_multiplier.md)より、停留点は次の条件を満たすため、これが局所的最小解への条件となる。

<center>
$$L(x,\lambda) \equiv f(x) - \sum_{k=1}^M \lambda_k g_k(x)$$ として
</center>

<center>
$$\frac{\partial F}{\partial x_k}=0, \frac{\partial F}{\partial \lambda_k}=0$$
</center>

ただし逆は成立しない（停留点には極大点や鞍点などが含まれるため）。

### 2次導関数に対する条件

<center>
$$\nabla^2 f(x^* )$$ が正定値行列
</center>

上の条件で求めた停留点が極小点であるための条件。

## 解法

実行可能領域$$D$$において$$f(x)$$が下に凸でない場合、有界でないために解が存在しなかったり、極小点でない境界上の点が解になったりするため、必ずしも局所的最小解が解になるとは限らない。
そのため、事前に関数の凸性を調べるなどの操作が必要になる。

### 局所的最小解の求め方

局所的最小解の候補となる停留点は[ラグランジュ乗数法](../../mathematics/analysis/lagrange_multiplier.md)を用いて導ける。
導き出された停留点についてヘッセ行列が正定値であるかを調べ、極小点であるか判定する。
