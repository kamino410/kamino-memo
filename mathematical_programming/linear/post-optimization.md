# 感度解析と再最適化

$$
\begin{eqnarray}
minimize : &\ & c_B^Tx_B + c_N^Tx_N \\
s.t. &\ &
\begin{cases}
Bx_B + Nx_N=b\\
x_B, x_N \geq 0
\end{cases}
\end{eqnarray}
$$

ある線形計画問題の最適解が求まっているとする。

ここで、目的関数や制約条件が変化したときに最適解がどのように変化するかを調べることを**感度解析（sensitivity analysis）**という。

また、目的関数や制約条件が変化した問題の最適解をもとの問題の最適解から効率よく求める方法が知られており、これを**再最適化（post-optimization）**という。

## 最適解の表現

求まっている最適解における最適基底行列を $$B^*$$、最適非基底行列を $$N^*$$、最適変数を $$x^* = \begin{bmatrix} x_B^* & 0\end{bmatrix}$$、最適値を $$w^*$$ とする。

このとき次の条件を満たしているはずである。

$$
x_B^* = {B^*}^{-1}b \geq 0, \ \ \ w^* = {c_B^*}^T x_B^*, \ \ \ z_{N^*} = c_{N^*} - ({B^*}^{-1}N^*)^T c_{B^*} \geq 0
$$

## 目的関数の係数が変化した場合の再最適化

目的関数が $$c^T x \rightarrow (c + \Delta c)^T x$$ と変化したとする。

このとき、新しい最適性基準 $$\hat{z}_N$$ は

$$
\begin{eqnarray}
\hat{z}_{N^*} &=& (c_{N^*} + \Delta c_{N^*}) - ({B^*}^{-1}N^*)^T(c_{B^*} + \Delta c_{B^*}) \\
&=& z_{N^*} + \Delta c_{N^*} - ({B^*}^{-1}N^*)^T\Delta c_{B^*}
\end{eqnarray}
$$

となり、新しい最適値 $$\hat{w}$$ は

$$
\begin{eqnarray}
\hat{w} &=& (c_{B^*} + \Delta c_{B^*})^T x_{B^*} \\
&=& w^* + \Delta c_{B^*}^T x_{B^*}
\end{eqnarray}
$$

となる。
よって次の結論を得る。

1. $$\Delta c_{N^*} - ({B^*}^{-1}N^*)^T\Delta c_{B^*} \geq 0$$ なら最適性条件は満たされるため新しい最適値 $$\hat{w} = w^* + \Delta c_{B^*}^T x_{B^*}$$ を得る
2. 新しい最適性条件が満たされないなら単体法を適用して再最適化を行う

## 制約条件の定数項が変化した場合の再最適化

制約条件の定数項が $$b \rightarrow b + \Delta b$$ と変化したとする。

このとき、最適性基準は影響を受けず、新しい最適基底変数 $$\hat{x}_{B^*}$$ は

$$
\begin{eqnarray}
\hat{x}_{B^*} &=& {B^*}^{-1} (b + \Delta b)
&=& x_{B^*} + {B^*}^{-1} \Delta b
\end{eqnarray}
$$

となり、新しい最適値 $$\hat{w}$$ は

$$
\begin{eqnarray}
\hat{w} &=& c_{B^*}^T{B^*}^{-1}(b+\Delta b) \\
&=& w^* + c_{B^*}^T{B^*}^{-1} \Delta b
\end{eqnarray}
$$

となる。
よって次の結論を得る。

1. 新しい最適基底変数について $$\hat{x}_{B^*} \geq 0$$ なら実行可能基底解であるため、$$\hat{w} = w^* + c_{B^*}^T{B^*}^{-1} \Delta b$$ が最適値になる
2. 新しい最適基底変数が実行不可能なら双対単体法を適用して最最適化を実行する
