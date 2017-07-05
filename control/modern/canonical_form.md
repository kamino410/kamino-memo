# 可制御正準形・可観測正準形

## 状態方程式の同値変換（conversion to equivalent model）

任意の状態方程式が与えられているとする。

$$
\begin{eqnarray}
\dot{x} &=& Ax + Bu \\
y &=& Cx
\end{eqnarray}
$$

このとき、任意の正則行列 $$T$$ を用いて

$$
\dot{\bar{x}} = T x
$$

と置くと、先程の状態方程式は

$$
\begin{eqnarray}
\dot{\bar{x}} &=& TAT^{-1} \bar{x} + TBu \\
y &=& CT^{-1} \bar{x}
\end{eqnarray}
$$

となり、$$\bar{A}=TAT^{-1},\ \bar{B} = TB,\ \bar{C} = CT^{-1}$$ をパラメーターとする同値な状態方程式に変換することができる。これを同値変換という。

また、同値なシステムの伝達関数は一致する。

## 1入力1出力システムの可制御正準形（controllable canonical form）

1入力1出力の $$n$$ 次元の状態変数を持つ可制御なシステムは

$$
\begin{eqnarray}
T &=& (M_C T_1)^{-1}\\
T_1 &=& \begin{bmatrix}
\alpha_1 & \alpha_2 & \cdots & \alpha_{n-1} & 1 \\
\alpha_2 & \alpha_3 & \cdots & 1 & 0 \\
\vdots & \vdots & \ddots & \vdots & \vdots \\
\alpha_{n-1} & 1 & \cdots & 0 & 0 \\
1 & 0 & \cdots & 0 & 0
\end{bmatrix} \\
\det(sI-A) &=& s^n + \alpha_{n-1}s^{n-1} + \cdots + \alpha_1 s + \alpha_0
\end{eqnarray}
$$

を用いて次のようなパラメーターを持つシステムに同値変換できる。

$$
\begin{eqnarray}
\bar{A} &=& \begin{bmatrix}
0 & 1 & 0 & \cdots & 0 \\
0 & 0 & 1 & \cdots & 0 \\
\vdots & \vdots & \vdots & \ddots & \vdots \\
0 & 0 & 0 & \cdots & 1 \\
-\alpha_0 & -\alpha_1 & -\alpha_2 & \cdots & -\alpha_{n-1}
\end{bmatrix} \\
\bar{B} &=& \begin{bmatrix}
0 \\ 0 \\ \vdots \\ 0 \\ 1
\end{bmatrix}
\end{eqnarray} \\
\bar{C} = C M_C
$$

これを**1入力1出力システムの可制御正準形**という。

## 1入力1出力システムの可観測正準形（observable canonical form）

1入力1出力の $$n$$ 次元の状態変数を持つ可観測なシステムは

$$
\begin{eqnarray}
T &=& T_1 M_O \\
T_1 &=& \begin{bmatrix}
\alpha_1 & \alpha_2 & \cdots & \alpha_{n-1} & 1 \\
\alpha_2 & \alpha_3 & \cdots & 1 & 0 \\
\vdots & \vdots & \ddots & \vdots & \vdots \\
\alpha_{n-1} & 1 & \cdots & 0 & 0 \\
1 & 0 & \cdots & 0 & 0
\end{bmatrix} \\
\det(sI-A) &=& s^n + \alpha_{n-1}s^{n-1} + \cdots + \alpha_1 s + \alpha_0
\end{eqnarray}
$$

を用いて次のようなパラメーターを持つシステムに同値変換できる。

$$
\begin{eqnarray}
\bar{A} &=& \begin{bmatrix}
0 & 0 & \cdots & 0 & -\alpha_0 \\
1 & 0 & \cdots & 0 & -\alpha_1 \\
0 & 1 & \ddots & \vdots & -\alpha_2 \\
\vdots & \ddots & \ddots & 0 & \vdots \\
0 & \cdots & 0 & 1 & -\alpha_{n-1}
\end{bmatrix} \\
\bar{C} &=& \begin{bmatrix}
0 & 0 & \cdots & 0 & 1
\end{bmatrix}
\end{eqnarray} \\
\bar{B} = T_1 M_O B
$$

これを**1入力1出力システムの可観測正準形**という。

## 多入力システムの可制御正準形（controllable canonical form）

多入力システムに関しても可制御正準形を定義できる。

$$B=\begin{bmatrix}b_1 & b_2 & \cdots & b_m\end{bmatrix}$$ であるとき、変換行列 $$T$$ は次のようにして求められる。

1. $$M_C = \begin{bmatrix}b_1 & b_2 & \cdots & A^{j}b_i & \cdots & A^{n-1}b_m\end{bmatrix}$$ の左側から順に一次独立なベクトルをなるべく多く選び、そのうち $$b_i$$ の積で表されているものの数を $$\mu_i$$ とする
   * つまり $$\mu_i = \min\{j \ | \ A^jb_i \in span[M_C]\}$$
   * これを**可制御性指数**と呼ぶ
   * $$\sum_{i=0}^m \mu_i = n$$
2. $$S=[\begin{array}{cccc|ccc|cc}b_1 & A b_1 & \cdots & A^{\mu_1-1}b_1 & b_2 & \cdots & A^{\mu_2-1}b_2 & \cdots & A^{\mu_m-1}b_m\end{array}]$$ とする
3. $$S^{-1}$$ の第 $$\sum_{j=1}^i \mu_j$$ 行目を $$\hat{s}=1$$ とする
4. $$T$$ を次のように定義する

$$
T=\left[\begin{array}{c} \hat{s}_1 \\ \hat{s}_1A \\ \vdots \\ \hat{s}_1 A^{\mu_1-1} \\\hline \hat{s}_2 \\ \vdots \\ \hat{s}_m A^{\mu_m-1}\end{array}\right]
$$

この同値変換によって得られる新しいパラメーターは $$(\bar{A}, \bar{B}, \bar{C})$$ は次のような形になる。

$$
\begin{eqnarray}
\bar{A} &=& \begin{bmatrix}\bar{A}_{11} & \cdots & \bar{A}_{1m} \\ \vdots & \ddots & \vdots \\ \bar{A}_{m1} & \cdots & \bar{A}_{mm}\end{bmatrix}\\
\bar{B} &=& \begin{bmatrix}\bar{B}_1 \\ \vdots \\ \bar{B}_m\end{bmatrix}\\
\bar{A}_{ii} &=& \begin{bmatrix}0 & 1 & 0 & \cdots & 0 \\ 0 & 0 & 1 & \cdots & \vdots \\ \vdots & \vdots & \vdots & \ddots & 0 \\ 0 & 0 & \cdots & 0 & 1 \\ * & \cdots & \cdots & \cdots & *\end{bmatrix} \ \ \ (\mu_i \times \mu_i)\\
\bar{A}_{ij} &=& \begin{bmatrix}0 & \cdots & \cdots & 0 \\ \vdots & \cdots & \cdots & \vdots \\ 0 & \cdots & \cdots & 0 \\ * & \cdots & \cdots & *\end{bmatrix} \ \ \ (\mu_i \times \mu_j, i\neq j) \\
\bar{B}_i &=& \begin{bmatrix}0 & \cdots & \cdots & \cdots & \cdots & \cdots & 0 \\ \vdots & \cdots & \cdots & \cdots & \cdots & \cdots & \vdots \\ 0 & \cdots & \cdots & \cdots & \cdots & \cdots & 0 \\ 0 & \cdots & 0 & 1 & * & \cdots & * \end{bmatrix} \ \ \ (\mu_i \times m, 中央はi列目)\\
\bar{C} &=& \begin{bmatrix}* & \cdots & * \\ \vdots & \cdots & \vdots \\ * & \cdots & *\end{bmatrix}
\end{eqnarray}
$$
