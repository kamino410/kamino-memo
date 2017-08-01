# 無制約最小化問題

次の問題について考える。

$$
\begin{eqnarray}
minimize &\ & \ f(x) \ \ \ (x \in R^n) \\
s.t. &\ &
\begin{cases}
x \in D \subseteq R^n, \ \ \ f:D \rightarrow R
\end{cases}
\end{eqnarray}
$$

## 最適性条件

$$f(x)$$ が $$x^* $$ の近傍で2回連続微分可能であるとき、次のことが成り立つ。

<center>
$$\nabla f(x^* ) = 0$$ かつ $$\nabla^2 f(x^* )$$ が半正定値行列　⇔　$$x^* $$ は局所的最小解である。
</center><br>

また $$f(x)$$ が凸関数であるとき $$x^* $$ は大域的最小解となる。
