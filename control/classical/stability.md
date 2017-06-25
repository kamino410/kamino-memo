# 線形システムの安定性

## 安定性

線形システムに有界な大きさの任意の入力（$$|u(t)| < \infty$$）を加えたとき、出力も有界（$$|y(t)| < \infty$$）となるとき、システムは **安定（stable）** であるという。

逆に出力が無限に発散しうるとき、システムは **不安定（unstable）** であるという。

## 極と安定性　

線形システムの場合 **「ステップ応答が安定⇔システムが安定」** であることが知られている。

[極・零点と過渡応答](pole_zero.md)で述べた通り、過渡応答は$$G(s)$$の各極（$$s=-\sigma_i,-\alpha_i \pm j\omega_i$$）を用いて次式で表される。

$$
y(t) = A_0+\sum_{i=1}^M A_i e^{-\sigma_i t}+\sum_{i=1}^N\frac{B_i}{\omega_i} e^{-\alpha_i t} \sin{\omega_i t}
$$

ここで$$-\sigma_i, -\alpha_i > 0$$であれば第2項・第3項が$$t \rightarrow \infty$$のとき0に収束しないため、不安定となる。逆に$$-\sigma_i, -\alpha_i > 0$$でない限りステップ応答は有限な値に収束するはずである。

よって

<center>
全ての極の実部が負　⇔　システムが安定
</center>

が成り立つ。

## 安定性の判別

上記のように全ての極を調べればシステムの安定性が判別できるが、指数関数が絡むため面倒である。

そこで、ラウス・フルビッツらは比較的簡単に安定性を判別する手法を考案した。両者の手法は手順こそ異なるものの本質的には同じ数学的性質に依存している。

### フルビッツの安定判別法

極は伝達関数の分母をとって

$$
D(s) = a_n s^n + a_{n-1} s^{n-1} + \cdots + a_1 s + a_0 = 0
$$

であるとする。

ここで、各係数を用いて以下のような$$n \times n$$正方行列を作る。

$$
\begin{bmatrix}
a_{n-1} & a_{n-3} & a_{n-5} & \cdots & \cdots & \cdots & 0 \\
a_{n} & a_{n-2} & a_{n-4} & \cdots & \cdots & \cdots & \vdots \\
0 & a_{n-1} & a_{n-3} & a_{n-4} & \cdots & \cdots & \vdots \\
0 & a_{n} & a_{n-2} & a_{n-4} & \cdots & \cdots & \vdots \\
\vdots & \vdots & \vdots & \vdots & \ddots & \vdots & \vdots \\
\vdots & \cdots & \cdots & \cdots & \cdots & \ddots & \vdots \\
0 & \cdots & \cdots & \cdots & \cdots & a_2 & a_0
\end{bmatrix}
$$

左上を$$n-1$$として、下に行くと添え字を+1、右に行くと添え字を-2して、相当する$$a_i$$がない箇所は0とした行列である。

この行列の左上側を起点とした$$1\times1,\ 2\times2,\ \cdots,\ n \times n$$の小行列式$$H_i$$を導く。

$$
H_1 = \begin{vmatrix}a_{n_1}\end{vmatrix}, \ H_2 = \begin{vmatrix}a_{n_1} & a_{n-3} \\ a_n & a_{n-2}\end{vmatrix}, \ H_3 = \begin{vmatrix}a_{n_1} & a_{n-3} & a_{n-5} \\ a_n & a_{n-2} & a_{n-4} \\ 0 & a_{n-1} & a_{n-3}\end{vmatrix}, \ \cdots
$$

このとき

<center>
$$a_i>0$$ かつ $$H_i>0$$　⇒　全ての極の実部は負である
</center>

が成り立つ。
