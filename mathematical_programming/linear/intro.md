# 線形計画問題（Linear Programming Problem）

> 制約付き最適化問題（constrained optimization）

>$$
\begin{eqnarray}
&\ &minimize : f(x) \\
&\ &s.t.
\begin{cases}
g_i(x) = 0 & (i=1,\dots,m) \\
h_j(x) \leq 0 & (j=1,\dots,l)
\end{cases} \\
&\ & f:R^n \rightarrow R,\ g_i:R^n \rightarrow R,\ h_i:R^n \rightarrow R
\end{eqnarray}
$$

## 定義

制約付き最適化問題のうち、$$f(x),g_i(x),h_j(x)$$のすべてが1次式である場合、この最適化問題を **線形計画問題（LP問題）** という。

線形計画問題は行列を用いて次のように表現できる。

$$
\begin{eqnarray}
&\ &minimize : c^Tx \\
&\ &s.t.
\begin{cases}
Ax=a\\
Bx \leq b
\end{cases} \\
&\ &A \in R^{m \times n}, \ B \in R^{l \times n}, \ a \in R^m, \ b \in R^l, \ c \in R^n, \ x \in R^n
\end{eqnarray}
$$

## 標準形

先ほどの式において$$x_i$$は自由変数であるが、正負がはっきりしないと解く手順の中で場合分けが必要になってしまう。そこで

$$
x_i = x_1' - x_2' \ \ \ (x_1', x_2' \geq 0)
$$

のように未知変数を1つ増やすことですべての未知変数が正であるものとして扱えるようになる。

また、不等式制約についても

$$
A_{ji}x_i \leq a_i \Leftrightarrow A_{ji}x_i + x_1' = a_i
$$

のように未知変数を1つ増やすことで等式制約に変換できる。

このとき追加した未知変数を特に **スラック変数** と呼ぶ。

以上を踏まえて新たに$$A,B,a,b,c,x,l,m,n$$を置き直すと、

$$
\begin{eqnarray}
&\ &minimize : c^Tx \\
&\ &s.t.
\begin{cases}
Ax=a\\
x_i \geq 0
\end{cases} \\
&\ &A \in R^{m \times n}, \ B \in R^{l \times n}, \ a \in R^m, \ b \in R^l, \ c \in R^n, \ x \in R^n
\end{eqnarray}
$$

となる。

これを線形計画問題の **標準形** という。

## 用語

### 実行可能解・実行可能領域

制約条件を満足するような$$x$$を **実行可能解（feasible solution）** といい、すべての実行可能解の集合$$S=\{x\in R^n | Ax=b, x\geq0\}$$を **実行可能領域（feasible region）** という。

### 基底行列・基底解

等式制約の係数行列$$A$$から$$m=rank(A)$$本の線形独立な列ベクトルを1組選んだとき、それらを並べて作る正則行列を$$B \in R^{m \times m}$$とおいて **基底行列（basis matrix）** といい、それに対応する$$m$$個の変数$$x_i$$を **基底変数（basic variable）** という。

逆に選ばれなかった$$n-m$$個の変数$$x_i$$を **非基底変数（nonbasic variable）** という。

$$
\begin{eqnarray}
Ax = b \\
\begin{bmatrix} B & N \end{bmatrix} \begin{bmatrix} x_B \\ x_N \end{bmatrix} = b
\end{eqnarray}
$$

ここで非基底変数がすべて0であると仮定すると、

$$
\begin{eqnarray}
Ax &=& b \\
\begin{bmatrix} B & N \end{bmatrix} \begin{bmatrix} x_B \\ 0 \end{bmatrix} &=& b \\
x = \begin{bmatrix}x_B \\ x_N \end{bmatrix} &=& \begin{bmatrix} B^{-1}b \\ 0 \end{bmatrix}
\end{eqnarray}
$$

のように解が求まる。
このように$$m=rank(A)$$個の基底変数を選び、非基底変数を0として得た解を **基底解（basic solution）** と呼ぶ。

実行可能解かつ基底解であるものを特に **実行可能基底解** と呼ぶ。

### 退化

基底解を得たとき、非基底変数だけでなく基底変数の中にも0の値をとるものがあるとき、 **退化（degenerate）** しているという。

逆に基底変数がすべて非零であるとき（$$x_B > 0, x_N = 0$$）、 **非退化（non-degenerate）** であるという。

退化の直観的・数学的な意味は後述する。

### 単体乗数

基底解$$x$$を得たとき、

$$
\begin{eqnarray}
c^Tx &=& c^T \begin{bmatrix} B^{-1}b \\ 0 \end{bmatrix} \\
&=& c_B^T B^{-1} b \\
&=& (B^{-1})^Tc_B b
\end{eqnarray}
$$

が成り立つ。

このときの$$(B^{-1})^Tc_B$$を **単体乗数（simplex multiplier）** という。

直観的には$$m$$個の基底変数を選んだときに、定数$$b$$が最小化すべき評価値$$c^Tx$$に対してどのような影響を与えるようになるかの重み付けを定める行列といえる。

### 最適解

目的関数を最小にする実行可能解を **最適解（optimal solution）** という。
