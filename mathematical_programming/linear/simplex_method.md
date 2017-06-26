# 単体法（シンプレックス法：simplex method）

## 概要

線形計画問題は

1. 実行可能基底解を1つ見つける
1. 「見つけた実行可能基底解より目的関数値が小さくなる実行可能基底解を探す」を繰り返す

というアルゴリズムによって最適解を求めることができる。
シンプレックス法は2番の手順を効率よく実現した解法である。

## 事前知識：基底形式（basic form）

$$x$$を基底解、つまり $$x = \begin{bmatrix}x_B \\ x_N\end{bmatrix} = \begin{bmatrix}B^{-1}b \\ 0\end{bmatrix}$$ とする。

ここでLP問題の標準形を以下のように表す。

$$
\begin{eqnarray}
w &=& \begin{bmatrix} c_B^T & c_N^T \end{bmatrix} \begin{bmatrix} x_B \\ x_N \end{bmatrix} \\
b &=& \begin{bmatrix} B & N \end{bmatrix} \begin{bmatrix} x_B \\ x_N \end{bmatrix}
\end{eqnarray} \tag{1}
$$

$$B$$に逆行列が存在するという性質を利用してこの式を変形すると次のようになる。

$$
\begin{eqnarray}
\omega &=& c_B^T B^{-1}b + (c_N^T-c_B^TB^{-1}N)x_N \\
B^{-1}b &=& x_B + B^{-1}Nx_N
\end{eqnarray} \tag{2}
$$

この式を **基底形式（basic form）** といい、$$\bar{c}_N^T = c_N^T-c_B^TB^{-1}N$$ を **相対費用係数** という。

## 解法

事前に実行可能基底解 $$x = \begin{bmatrix}x_B \\ x_N\end{bmatrix} = \begin{bmatrix}B^{-1}b \\ 0\end{bmatrix} \geq 0$$ が得られているものとする。

まず、現在の解が最適解であるか確認するため、$$x_N$$が非負の値を持つと仮定する。式(2)の

$$
\omega = c_B^T B^{-1}b + (c_N^T-c_B^TB^{-1}N)x_N
$$

より、$$c_N^T-c_B^TB^{-1}N$$ が
