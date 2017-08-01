# ラグランジュ乗数法（ラグランジュ未定乗数法）（lagrange multiplier）

ラグランジュ乗数法は、複数の変数に1つ以上の等式制約条件が課されたとき、それらの変数からなる関数の停留点を求める手法である。

停留点が求まれば、条件と関数の性質に応じてそれぞれの値を検証することで極大値・極小値を得ることができるため、主に非線形計画問題の解法として用いられる。

## 定理

$$n$$ 次元の変数 $$x$$ が次の $$m$$ 個の制約条件を満たすとする。

$$
G(x)=
\begin{pmatrix}
  g_1(x_1, \dots, x_n) \\
  \vdots \\
  g_m(x_1, \dots, x_n)
\end{pmatrix}
=0
$$

ただし、$$g_k(x)$$ は $$C^1$$ 級関数（連続微分可能つまり微分可能で導関数も連続）である。
また、制約条件を満たす点で $$\dim \left(\nabla g_k\right) = \dim\left(\frac{\partial g_k}{\partial x_1}, \cdots, \frac{\partial g_k}{\partial x_n}\right)=m$$ である（つまり $$\nabla g_i$$ 同士は一次独立）。

ここでm個の未知の変数 $$\lambda_k$$（**Lagrange乗数**と呼ぶ）を導入して、

$$
L(x,\lambda) \equiv f(x) - \sum_{k=1}^M \lambda_k g_k(x)
$$

のような**Lagrange関数**を定義したとき、

<center>
ある $$x$$ について $$\frac{\partial L}{\partial x_k}=0,\ \frac{\partial L}{\partial \lambda_k}=0$$ を満たす $$\lambda$$ が存在する<br>⇔　$$x$$ は関数 $$f(x)$$ の停留点
</center><br>

が成立する。

## 解説

2つ目の条件 $$\frac{\partial L}{\partial \lambda_k}=0$$ は結局 $$g_k(x^*) = 0$$ と同じであり、制約条件を満たすつまり実行可能解であるかの確認になっている。

1つ目の条件 $$\frac{\partial L}{\partial x_k}=0$$ は $$\nabla f(x^*) = \sum_{k=1}^M \lambda_k \nabla g_k(x^*)$$ が成立することを意味している。
左辺は関数 $$f(x)$$ の勾配ベクトル、右辺は制約関数の勾配ベクトルを示しており、関数 $$f(x)$$ の等高線と制約面が接していることを示している。
