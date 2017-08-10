# 伝達関数行列（transfer function matrix）

## 定義

$$
\begin{eqnarray}
\dot{x} &=& Ax + Bu \\
y &=& Cx
\end{eqnarray}
$$

をラプラス変換すると

$$
\begin{eqnarray}
sX(s) &=& AX(s) + bU(s) \\
Y(s) &=& cX(s)
\end{eqnarray}
$$

となるため、入力と出力の関係を直接表した式

$$
\begin{eqnarray}
Y(s) &=& G(s)U(s) \\
G(s) &=& C(sI-A)^{-1}B
\end{eqnarray}
$$

が得られる。
このときの $$G(s)$$ を**伝達関数行列**と呼ぶ。

## 性質

互いに同値なシステムに対する伝達関数行列はすべて等しい。

$$G(s)$$ に変換行列 $$T$$ に関する同値変換を施すと

$$
\begin{eqnarray}
\bar{G}(s) &=& CT^{-1}(sTT^{-1} - TAT^{-1})^{-1} TB \\
&=& C(sI-A)^{-1}B \\
&=& G(s)
\end{eqnarray}
$$

となり、変換前後で一致する。

また、[カルマンの正準分解](canonical_decomposition.md)を用いれば、$$G(s)$$ は可制御可観測なサブシステムの係数によってのみ表現されることがわかる。

$$
G(s) = H^b(sI-F^{bb})^{-1}G^b
$$

# 実現問題

ある伝達関数行列 $$G(s)$$ が与えられたとき、それを実現する状態方程式を求める問題を**実現問題**という。

## 実現可能性

伝達関数行列の各要素が次のよう表されているとする。

$$
g_{ij} = \frac{N_{ij}(s)}{D_{ij}(s)}
$$

$$N_{ij}(s), \ D_{ij}(s)$$ が $$s$$ の多項式で表されるとき（有理関数であるとき）、次の定理が成立する。

<center>
伝達関数行列の各要素が有理関数かつ厳密にプロパーである<br />⇔　それを実現する状態方程式が存在する
</center><br />

## 最小実現

実現問題の解において、状態変数の次数が最小のものを**最小実現**という。
最小実現にも状態変数の取り方が異なる同値な表現が複数存在する。

### 条件

最小実現について次の定理が成立する。

<center>
状態方程式が可制御可観測　⇔　実現問題の最小実現である
</center><br />

これは後述するハンケル行列の同値変換を考えることで証明できる。

### 最小実現の次数

伝達関数行列の各要素の分母 $$D_{ij}(s)$$ の最小公倍多項式 $$\gamma(s)$$ の次数を $$\nu$$ とする。

ここで次のように**マルコフパラメータ**を定義する。

$$
J_k = CA^kB
$$

$$e^{At}$$ のラプラス変換を考慮すると、マルコフパラメータは次の性質を満たす。

$$
G(s) = \sum_{i=1}^\infty J_{i-1} s^{-i}
$$

またマルコフパラメータを用いて次のように**ハンケル行列**を定義する。

$$
\begin{eqnarray}
H_l &=& \begin{bmatrix} J_0 & J_1 & \cdots & J_{l-1} \\
J_1 & J_2 & \cdots & J_l \\
\vdots & \vdots & \ddots & \vdots \\
J_{l-1} & J_l & \cdots & J_{2l-2}\end{bmatrix} \\
&=& \begin{bmatrix}C \\ CA \\ \vdots \\ CA^{k-1} \end{bmatrix}
\begin{bmatrix}B & AB & \cdots & A^{k-1}B \end{bmatrix} = M_C M_O
\end{eqnarray}
$$

$$\gamma(s)$$ の次数 $$\nu$$ によるハンケル行列の階数 $$\mathrm{rank} H_\nu$$ を**マクミラン次数**という。


最小実現　⇔　状態方程式が可制御可観測　⇔　$$\mathrm{rank} M_CM_O = n$$ 、であるからマクミラン次数について次の定理が成立する。

<center>
最小実現における状態変数の次元数　＝　マクミラン次数
</center><br />
