# 正準分解（canonical decomposition）

ある任意のシステムが与えられたとき、可制御性と可観測性の概念に基づいていくつかのサブシステムに分割する事ができ、これを**カルマンの正準分解**という。

## 定理

$$
\begin{eqnarray}
\dot{x} &=& Ax + Bu \\
y &=& Cx
\end{eqnarray}
$$

は適当な同値変換を用いて

$$
\begin{eqnarray}
\dot{\bar{x}} &=& F\bar{x} + Gu \\
y &=& H\bar{x} \\
F &=& \begin{bmatrix}
F^{aa} & F^{ab} & F^{ac} & F^{ad} \\
0 & F^{bb} & 0 & F^{bd} \\
0 & 0 & F^{cc} & F^{cd} \\
0 & 0 & 0 & F^{dd}
\end{bmatrix} \\
G &=& \begin{bmatrix}
G^a \\ G^b \\ 0 \\ 0
\end{bmatrix} \\
H &=& \begin{bmatrix}
0 & H^b & 0 & H^d
\end{bmatrix}
\end{eqnarray}
$$

に変換できる。

## 解説

参考：http://ogyahogya.hatenablog.com/entry/2015/10/18/%E5%8F%AF%E5%88%B6%E5%BE%A1%E6%80%A7%E3%83%BB%E5%8F%AF%E8%A6%B3%E6%B8%AC%E6%80%A7

## 概要

システム内部の状態変数 $$x$$ が取りうる値全体の集合（状態空間）を $$\chi$$ とおく。

可制御性行列 $$M_C$$・可観測性行列 $$M_O$$ を利用すると、可制御空間 $$\chi_C$$ と不可観測空間 $$\chi_\bar{O}$$ は

$$
\begin{eqnarray}
\chi_C &=& \mathrm{Im}M_C \\
\chi_\bar{O} &=& \mathrm{Ker}M_O
\end{eqnarray}
$$

であり、かつそれぞれが $$A$$ について[不変な部分空間](../../mathematics/linear_algebra/vector_space.md#不変部分空間)であることが証明できる。

ここで部分空間 $$\chi^a, \chi^b, \chi^c, \chi^d$$ を次のように定義する。

$$
\begin{eqnarray}
\chi^a &=& \chi_C \cap \chi_\bar{O} \\
\chi_C &=& \chi^a \oplus \chi^b \\
\chi_\bar{O} &=& \chi^a \oplus \chi^c \\
\mathbb{R}^n &=& \chi^a \oplus \chi^b \oplus \chi^c \oplus \chi^d
\end{eqnarray}
$$

それぞれの基底を $$\Xi^a, \Xi^b, \Xi^c, \Xi^d$$ とすると

$$
\begin{eqnarray}
A \Xi^a &=& \Xi^a F^{aa} \\
A \Xi^b &=& \Xi^a F^{ab} + \Xi^b F^{bb} \\
A \Xi^c &=& \Xi^a F^{ac} + \Xi^c F^{cc} \\
A \Xi^d &=& \Xi^a F^{ad} + \Xi^b F^{bd} + \Xi^c F^{cd} + \Xi^d F^{dd}
\end{eqnarray}
$$

と表されることがわかる。

ここで

$$
T^{-1} = \begin{bmatrix} \Xi^a & \Xi^b & \Xi^c & \Xi^d \end{bmatrix}
$$

なる同値変換によって上記の形に変換することができる。

### $$\chi_C = \mathrm{Im}M_C$$ であることの証明

[状態方程式の解](state_space_equation.md#状態方程式の解)より

$$
x(t) = e^{A(t-t_0)}x(t_0) + \int_{t_0}^t e^{A(t-\tau)} B u(\tau) d\tau
$$

である。

まず $$\chi_C \subset \mathrm{Im}M_C$$ を示す。可制御性の条件を「時刻 $$0$$ から適当な有限時刻 $$T$$ で $$x$$ を原点に移すような入力 $$u(t)$$ が存在する」と考えると

$$
\begin{eqnarray}
0 &=& e^{AT}x(0) + \int_0^T e^{A(T-\tau)}Bu(\tau) d\tau \\
x(0) &=& - \int_0^T e^{A\tau}Bu(\tau) d\tau
\end{eqnarray}
$$

が満たされるはずである。

右辺をテイラー展開して

$$
x(0) = -\int_0^T (I+A(-\tau)+\frac{A^2(-\tau)^2}{2!} + \cdots)Bu(\tau)d\tau
$$

さらに[ケーリー・ハミルトンの定理](../../mathematics/linear_algebra/cayley_hamilton.md)を用いれば $$A^n, A^{n+1}, \cdots$$ は $$A^0 \sim A^{n-1}$$ の一次多項式として表せるため

$$
x(0) = \begin{bmatrix}B & AB & \cdots & A^{n-1}B\end{bmatrix} \begin{pmatrix}* \\ * \\ \vdots \\ *\end{pmatrix} \in \mathrm{Im}M_C
$$

となり $$\chi_C \subset \mathrm{Im}M_C$$ が示された。

次に $$\chi_C \supset \mathrm{Im}M_C$$ を示す。

（書いてる途中）

## 手順まとめ

1. 可制御性行列 $$M_C$$ と可観測性行列 $$M_O$$ を求める
2. 可制御空間 $$\chi_C = \mathrm{Im}M_C$$・不可観測空間 $$\chi_\bar{O} = \mathrm{Ker}M_O$$ を求める
3. 部分空間 $$\chi^a, \chi^b, \chi^c, \chi^d$$ の基底 $$\Xi^a, \Xi^b, \Xi^c, \Xi^d$$ を求める（以下の条件を満たすなら選び方は任意）
    * $$\chi^a = \chi_C \cap \chi_\bar{O}$$
    * $$\chi_C = \chi^a \oplus \chi^b$$
    * $$\chi_\bar{O} = \chi^a \oplus \chi^c$$
    * $$R^n = \chi^a \oplus \chi^b \oplus \chi^c \oplus \chi^d$$
4. $$T^{-1} = \begin{bmatrix} \Xi^a & \Xi^b & \Xi^c & \Xi^d \end{bmatrix}$$ を変換行列としてシステムを同値変換する
