# 2段階法（two phase method）

[シンプレックス法](simplex_method.md)では最初に実行可能基底解が1つ求まっている状態からアルゴリズムを開始したが、問題によっては最初の実行可能基底解を得ること自体が困難である。

そこで、初期解を求めてからシンプレックス法を適用するのが2段階法である。

## 手順

1. $$b_i \geq 0$$ となるよう制約条件の符号を調整する
2. シンプレックス表を書き、基底形式に $$A$$ の各列の和 $$d_i$$ を用いて $$u = -d_1 x_1 - d_2 x_2 - \cdots - d_n x_n + u_0$$ としたものを目的関数と見てシンプレックス法の掃き出しを行う
    * $$u_0$$ はなんでもよいが $$u_0 = b_1 + b_2 + \cdots + b_m$$ とすることが多い
3. $$-u$$ の行のベクトルが $$0$$ になれば初期の実行可能基底解が得られている状態になるので $$w$$ を目的関数と見てシンプレックス法の掃き出しを行う
    * $$-u$$ の行のベクトルが $$0$$ にならなければ問題は実行不可能

## 原理

標準形の線形計画問題を考える。
ただし、$$b_i\geq 0$$ になるよう制約条件の符号を調整してあるものとする。

$$
\begin{eqnarray}
minimize : &\ & c^Tx \\
s.t. &\ &
\begin{cases}
Ax=b\\
x_i \geq 0
\end{cases} 
\end{eqnarray}
$$

ここですべての要素が非負である**人為変数（artificial variable）** $$v$$ を導入して

$$
\begin{eqnarray}
minimize : &\ & c^Tx \\
s.t. &\ &
\begin{cases}
Ax + v =b\\
x_i \geq 0 \\
v_i \geq 0
\end{cases} 
\end{eqnarray}
$$

とする。

ここで $$A' = \begin{bmatrix}A & I\end{bmatrix}$$、$${x'}^T = \begin{bmatrix}x^T & v^T \end{bmatrix}$$、$$u = v_1 + v_2 + \cdots + v_m$$ とすれば $$x,v$$ を変数とする線形計画問題になる。

$$
\begin{eqnarray}
minimize : &\ & u \\
s.t. &\ &
\begin{cases}
A'x' = b\\
{x'}_i \geq 0
\end{cases} 
\end{eqnarray}
$$

ここで $$x_0^T = [0,0,\cdots,0]$$、$$v_0^T = [b_1, b_2, \cdots, b_m]$$、$${x'_0}^T = \begin{bmatrix}x_0^T & v_0^T\end{bmatrix}$$ とすれば、$$x'_0$$ は明らかにこの問題の実行基底解である。

上記を初期解としてシンプレックス法を用いてこの問題の最適解を求めれば $$v=0$$、$$x_i$$ のいくつかが基底となる、元の問題に対する実行可能基底解が得られる。
逆に $$v = 0$$ となる最適解が存在しなければ元の問題が実行不可能であることがわかる。

人為変数は一度基底変数から外れれば再び基底変数に選ばれることはないはずなので、シンプレックス表から省くことができる。

また、初期解の基底形式を求めれば $$u = c_x x + c_v v$$ として

$$
\begin{eqnarray}
z_N^T &=& c_x^T - B^{-1}Nc_v^T \\
&=& B^{-1}N \begin{bmatrix} 1 \\ \vdots \\ 1 \end{bmatrix}
\end{eqnarray}
$$

となるので、目的関数は $$B^{-1}N = A$$ の $$i$$ 列目の要素の和 $$d_i$$ を取って

$$
u = -d_1 x_1 - d_2 x_2 - \cdots - d_n x_n + u_0
$$

と記述できる。
$$u_0$$ はなんでも良いが、$$b_1 + b_2 + \cdots + b_m$$ としておけば最適解が $$u=0$$ になるため、定数項を $$u_0 = b_1 + b_2 + \cdots + b_m$$ としておくことが多い。
