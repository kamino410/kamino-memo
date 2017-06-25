# 行列式（Determinant）

行列式は正方行列に対して定義される量。

幾何的には各列ベクトルが張る体積要素（3次元なら平衡六面体）の大きさを示すものとして理解できる。

## 定義

<center>
$$
\sum _ {\phi \in S} sgn(\phi)x_{1 \phi(1)}x_{2\phi(2)} \dots x_{n\phi(n)}
$$
</center>

<br>

1. $$\ _ n P_n (= n!)$$の順列から1つ取り出す
1. 取り出した順列に基づいて各列の異なる行の要素同士を掛け合わせる
1. $$(1\dots n)$$の要素同士を入れ替えて取り出した順列をつくるときの入れ替え操作の回数の偶奇を調べ、正負を決める

という操作を繰り返し、それらを足し合わせたものになっている。

## 性質

行列式は主に次のような性質を満たす。

### その1

行・列に対する対称性

$$|A^t| = |A|$$

### その2

**n重線型性**

$$\begin{vmatrix} a_1 \\ \vdots \\ a_i' \\ \vdots \\ a_n \end{vmatrix} \ + \  \begin{vmatrix} a_1 \\ \vdots \\ a_i'' \\ \vdots \\ a_n \end{vmatrix} \ = \  \begin{vmatrix} a_1 \\ \vdots \\ a_i' + a_i'' \\ \vdots \\ a_n \end{vmatrix}$$

$$|kA| = k|A| \ \ \ (k \in R)$$

### その3

行・列ベクトルを入れ替えると行列式の符号が逆転する（**交代性**）

$$\begin{vmatrix} a_1 \\ \vdots \\ a_i \\ \vdots \\ a_j \\ \vdots \\ a_n \end{vmatrix} \ = \  - \ \begin{vmatrix} a_1 \\ \vdots \\ a_j \\ \vdots \\ a_i \\ \vdots \\ a_n \end{vmatrix}$$

### その4

乗算

$$|AB| = |A| \cdot |B|$$

$$|A^n| = |A|^n$$
