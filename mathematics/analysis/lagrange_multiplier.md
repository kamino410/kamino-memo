# ラグランジュ乗数法（ラグランジュ未定乗数法）（lagrange multiplier）

ラグランジュ乗数法は、複数の変数に1つ以上の制約条件が課されたとき、それらの変数からなる関数の停留点を求める手法である。

停留点が求まれば、それぞれの値を計算・比較することで極大値・極小値を得ることができるため、主に非線形計画問題の解法として用いられる。

----

次のような数理計画問題の解を求めることを考える。

$$
\begin{eqnarray}
maximize \ &f(x)&\\
s.t. \ &G(x)&=
\begin{pmatrix}
  g_1(x_1, \dots, x_n) \\
  \vdots \\
  g_3(x_1, \dots, x_n)
\end{pmatrix}
=0 
\end{eqnarray}
$$

一つのアプローチとして

1. 制約式を基に$$x_2,\dots,x_n$$を$$x_1$$の陽関数として求める
$$
\left\{
\begin{eqnarray}
x_2 &=& h_2(x_1) \\
&\vdots& \\
x_n &=& h_n(x_1)
\end{eqnarray}
\right.
$$
1. $$f(x)$$を$$x_1$$による関数として表す
$$f(x) = f(x_1)$$
1. $$\frac{df}{dx_1}=0$$を解いて停留点を求め、極大値を取る点を選ぶ

という手法があるが、指数関数や三角関数が含まれる場合、$$x_2,\dots,x_n$$を$$x_1$$の陽関数として記述することが難しい。

ラグランジュ乗数法は陽関数の導出をせずに停留点を得ることができるためこのような問題を回避できる。

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
また、制約条件を満たす点で$$\nabla g_k = \left(\frac{\partial g_k}{\partial x_1}, \cdots, \frac{\partial g_k}{\partial x_n}\right)\neq 0$$である。

ここでm個の未知の変数$$\lambda_k$$（**Lagrange乗数** と呼ぶ）を導入して、

$$
L(x,\lambda) \equiv f(x) - \sum_{k=1}^M \lambda_k g_k(x)
$$

のような **Lagrange関数** を定義したとき、

<center>
ある$$x$$について$$\frac{\partial F}{\partial x_k}=0, \frac{\partial F}{\partial \lambda_k}=0$$を満たす$$\lambda$$が存在する
⇔　$$x$$は関数$$f(x)$$の停留点
</center>

である。

## 極値の求め方



## 解説


