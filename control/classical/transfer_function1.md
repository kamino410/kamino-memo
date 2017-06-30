# 伝達関数１（Transfer Function）

## 伝達関数表現

線形システムを微分方程式のまま計算すると、システムの結合が連立微分方程式で表現されることになり扱いづらい。

そこで[ラプラス変換](mathematics/analysis/laplace_transform.md)を用いて **$$t$$の微分⇔$$s$$の掛け算** となるような媒介変数表示にすることで、次のような利益がある。

1. システムの特性をひとつの **伝達関数$$G(s)$$** として表現できるようになる。
1. システムの直列結合を **伝達関数の積** として表現できるようになる。
1. システムの並列結合を **伝達関数の和** として表現できるようになる。

### 例

線形システムA、Bを直列に結合してみる。

<center>
<img src="fig1.png" style="width: 350px" border=1px/>

$$
\begin{eqnarray}
  \left\{
    \begin{array}{l}
      a_2\frac{d^2y_1(t)}{dt^2} + a_1\frac{dy_1(t)}{dt} + a_0y_1 = b_1\frac{du_1(t)}{dt} + b_0u_0(t) \\
      c_2\frac{d^2y_2(t)}{dt^2} + c_1\frac{dy_2(t)}{dt} + c_0y_2 = d_1\frac{dy_1(t)}{dt} + d_0y_1(t)
    \end{array}
  \right.
\end{eqnarray}
$$
</center>

このままでは扱いづらい。

----------------

そこで $$y_1(t)$$、$$y_2(t)$$、$$u(t)$$ を全ての初期値を0としてラプラス変換する。

$$
\begin{eqnarray}
  Y_1(s) &=& \mathscr{L}[y_1(t)] \\
  Y_2(s) &=& \mathscr{L}[y_2(t)] \\
  U(s) &=& \mathscr{L}[u(t)]
\end{eqnarray}
$$

これを利用して書き直すと

$$
\begin{eqnarray}
  \begin{array}{l}
    (a_2s^2 + a_1s + a_0) Y_1(s) = (b_1s + b_0) U(s) \\
    (c_2s^2 + c_1s + c_0) Y_2(s) = (d_1s + d_0) Y_1(s)
  \end{array}
\end{eqnarray}
$$

さらに $$Y_1(s)$$ を消してひとつの式にまとめると

$$
Y_2(s) = \frac{d_1s+d_0}{c_2s^2+c_1s+c_0} \cdot \frac{b_1s+b_0}{a_2s^2+a_1s+a_0} U(s)
$$

簡潔に記述できた。

-----------

上の式において

$$
\begin{eqnarray}
  G_A(s) &=& \frac{b_1s+b_0}{a_2s^2+a_1s+a_0} \\
  G_B(s) &=& \frac{d_1s+d_0}{c_2s^2+c_1s+c_0}
\end{eqnarray}
$$

はそれぞれA、Bのシステムの入出力比を表しているといえる。
つまり $$G_A(s)$$、$$G_B(s)$$ はA、Bの **システムの特性を表現する関数** になっている。

これを **伝達関数** と呼ぶ。
