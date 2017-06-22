# 単体法（シンプレックス法：simplex method）

## 概要

線形計画問題は

1. 実行可能基底解を1つ見つける
1. 「見つけた実行可能基底解より目的関数値が小さくなる実行可能基底解を探す」を繰り返す

というアルゴリズムによって最適解を求めることができる。
シンプレックス法は2番の手順を効率よく実現した解法である。

## 原理

最初の実行可能基底解が得られており、次のような形で表されているとする。

$$
\begin{eqnarray}
w &=& \begin{bmatrix} c_B^T & c_N^T \end{bmatrix} \begin{bmatrix} x_B \\ x_N \end{bmatrix} \\
b &=& \begin{bmatrix} B & N \end{bmatrix} \begin{bmatrix} x_B \\ x_N \end{bmatrix}
\end{eqnarray} \tag{1}
$$

ここで各変数を次のように置き直す。

$$
\begin{eqnarray}
\bar{N} &=& B^{-1}N \\
\bar{b} &=& B^{-1}b \\
\bar{c}_N &=& c_N - (B^{-1}N)^T c_B \\
\bar{w} &=& c_B^T B^{-1} b \\
&=& c_B^T \bar{b}
\end{eqnarray}
$$

これらを用いて式(1)を置き直すと次のようになる。

$$
\begin{eqnarray}
-\bar{w} &=& \bar{c}_N^T x_N - w \\
&=& \sum_{i=m+1}^n \bar{c}_i x_i  -w \\
\bar{b} &=& \bar{N}x_N + x_B \\
&=& \sum_{i=m+1}^n x_i B^{-1} a_i + x_B
\end{eqnarray} \tag{2}
$$

この式を **基底形式（basic form）** といい、$$\bar{c}_N$$を **相対費用係数** という。
$$x$$が実行可能基底解のとき

* $$x_N = 0$$ （非基底変数が0）
* $$\bar{w} = w$$ （）


