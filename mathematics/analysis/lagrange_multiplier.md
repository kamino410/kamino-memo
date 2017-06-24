# ラグランジュ乗数法（ラグランジュ未定乗数法）（lagrange multiplier）

ラグランジュ乗数法は、複数の変数に1つ以上の等式制約条件が課されたとき、それらの変数からなる関数の停留点を求める手法である。

停留点が求まれば、それぞれの値を計算・比較することで極大値・極小値を得ることができるため、主に非線形計画問題の解法として用いられる。

## 定理

n次元の変数$$x$$が次のm個の制約条件を満たすとする。

$$
G(x)=
\begin{pmatrix}
  g_1(x_1, \dots, x_n) \\
  \vdots \\
  g_m(x_1, \dots, x_n)
\end{pmatrix}
=0
$$

ただし、$$g_k(x)$$は$$C^1$$級関数（連続微分可能つまり微分可能で導関数も連続）である。
また、制約条件を満たす点で$$dim \left(\nabla g_k\right) = dim\left(\frac{\partial g_k}{\partial x_1}, \cdots, \frac{\partial g_k}{\partial x_n}\right)=m$$である（つまり$$\nabla g_i$$同士は一次独立）。

ここでm個の未知の変数$$\lambda_k$$（**Lagrange乗数** と呼ぶ）を導入して、

$$
L(x,\lambda) \equiv f(x) - \sum_{k=1}^M \lambda_k g_k(x)
$$

のような **Lagrange関数** を定義したとき、

<center>
ある$$x$$について$$\frac{\partial F}{\partial x_k}=0, \frac{\partial F}{\partial \lambda_k}=0$$を満たす$$\lambda$$が存在する<br>⇔　$$x$$は関数$$f(x)$$の停留点
</center>

が成立する。

## 解説


