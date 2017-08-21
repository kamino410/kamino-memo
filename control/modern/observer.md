# オブザーバ（observer）

## 概要

[極配置](pole_placement.md)で導入した状態フィードバックは状態変数が観測できることを前提にしている。
しかし、システムによってはすべての状態変数がセンサーなどで計測できないことがある。
そこで**オブザーバー**と呼ばれるシステムを並行して動作させ、状態変数の推定値 $$w$$ を得ることで状態フィードバックを行う。

状態オブザーバーの基本形は次のような形で表される。

$$
\begin{cases}
\dot{z} = Fz + Gy + Hu \\
w = Wz + Vy
\end{cases}
$$

十分な時間が経過したとき、実際の状態変数 $$x$$ とオブザーバの出力 $$w$$ の推定誤差 $$||x-w||$$ が0に収束するように各パラメーターを選ぶ。
一般にこのようなパラメーターは複数存在する。

## 同一次元状態オブザーバ

線形システム

$$
\begin{cases}
\dot{x} = Ax + Bu \\
y = Cx
\end{cases}
$$

と状態変数と同じ次元数を持つ状態オブザーバを**同一次元状態オブザーバ**という。
同一次元状態オブザーバはもとのシステムのパラメーターを用いて次のように定義する。

$$
\begin{cases}
\dot{z} = Az + Bu + G(y-Cz) \\
w = z
\end{cases}
$$

ここで次の定理が成立する。

<center>
対 $$(A,C)$$ が可制御　⇒　$$(A-GC)$$ の固有値を任意に配置できる
</center><br />

よって推定誤差を任意の速さで0に収束させうる。

## 最小次元状態オブザーバ

推定したい状態変数 $$x$$ の次元は $$n$$ 、システムから得られる出力は $$r$$ 次元なので、状態オブザーバが推定すべき状態の次元は $$(n-r)$$ 以上である。
状態オブザーバの次元数が最小 $$(n-r)$$ であるものを**最小次元状態オブザーバ**という。

まず $$T$$ が $$n\times n$$ の正則行列になるように適当な $$D$$ を選択する。

$$
T = \begin{bmatrix}C \\ D \end{bmatrix}
$$

$$T$$ を用いた同値変換を行い、$$C,D$$ に対応する部分を添字 $$1,2$$ で表わせば

$$
\begin{eqnarray}
\bar{x}&=& Tx = \begin{bmatrix}\bar{x}_1 \\ \bar{x}_2 \end{bmatrix} \\
\bar{A}&=& TAT^{-1} = \begin{bmatrix}\bar{A}_{11} & \bar{A}_{12} \\ \bar{A}_{21} & \bar{A}_{22} \end{bmatrix} \\
\bar{B}&=& TB = \begin{bmatrix}\bar{B}_1 \\ \bar{B}_2 \end{bmatrix} \\
\bar{C}&=& CT^{-1} = \begin{bmatrix}I_r & 0\end{bmatrix}
\end{eqnarray}
$$

となる。

ここで $$\bar{x}_2$$ の同一次元状態オブザーバは次のようになる。

$$
\begin{cases}
\dot{\tilde{z}} = \bar{A}_{22} \tilde{z} + \bar{A}_{21}y + \bar{B}_2 u + \tilde{G}[(\dot{y}-\bar{A}_{11}y-\bar{B}_1u)-\bar{A}_{12}\tilde{z}] \\
\bar{w}_2 = \tilde{z}
\end{cases}
$$

$$\dot{y}$$ を除くために $$z = \tilde{z}-\tilde{G}y$$ とすれば

$$
\begin{eqnarray}
\dot{\tilde{z}} &=& [\bar{A}_{22} - \tilde{G}\bar{A}_{12}]z + [\bar{A}_{22} \tilde{G} + \bar{A}_{21} - \tilde{G}(\bar{A}_{12}\tilde{G}+\bar{A}_{11})]y + [\bar{B}_2 - \tilde{G} \bar{B}_1]u \\
w &=& T^{-1}\begin{bmatrix}y \\ \bar{w}_2 \end{bmatrix} = T^{-1}\begin{bmatrix}0\\I_{n-r}\end{bmatrix}z + T^{-1}\begin{bmatrix}I_r \\ \tilde{G} \end{bmatrix}y
\end{eqnarray}
$$

対 $$(A,C)$$ が可観測なら $$(\bar{A}_{22}, \bar{A}_{12})$$ も可観測となるため、同一次元オブザーバの解説の通り、$$[\bar{A}_{22}-\tilde{G}\bar{A}_{12}]$$ の固有値を任意に設定するような $$\tilde{G}$$ が存在する。
