# マルコフ情報源（Markov source）

マルコフ情報源は最も基本的な記憶のある情報源（情報源記号の生起確率が前後の情報源記号に依存する情報源）である。
シャノンの情報理論以前から確率過程（stochastic process）の研究で提唱されていたマルコフ連鎖の概念を情報源に適用したものである。

## 定義

情報源記号の生起確率がその直前の $$m$$ 個の情報源記号に依存するとき、これを $$m$$ 重マルコフ情報源（mth-order Markov source）という。

特に $$m=1$$ のとき**単純マルコフ情報源（simple Markov source）**という。

## 状態遷移図・シャノン線図（state transition diagram / Shannon diagram）

情報源記号が $$n$$ 個の $$m$$ 重マルコフ情報源は $$n^m$$ の状態を持つことになる。
取りうる状態を $$S = \{s_1, \cdots, s_{n^m}\}$$ としたとき、ある状態からある状態へ遷移するときの条件付き確率を行列表記したものを**遷移確率行列**という。

$$
\begin{bmatrix}P(s_1|s_1) & P(s_1|s_2) & \cdots & P(s_1|s_{n^m}) \\
P(s_2|s_1) & P(s_2|s_2) & \cdots & P(s_2|s_{n^m}) \\
\vdots & \vdots & \ddots & \vdots \\
P(s_{n^m}|s_1) & P(s_{n^m}|s_2) & \cdots & P(s_n|s_{n^m})
\end{bmatrix}
$$

また、これを図にしたものを**状態遷移図**または**シャノン線図**という。

## マルコフ情報源の平均情報量（エントロピー）

情報源記号を $$A = \{a_1, \cdots, a_n\}$$ とする $$n$$ 元 $$m$$ 重マルコフ情報源の平均情報量は次のように計算できる。

まず、遷移を無限回繰り返したときの各状態の生起確率（**定常確率分布**）を求める。
定常確率分布を $$u^T=\begin{bmatrix}P(s_1)& \cdots& P(s_{n^m})\end{bmatrix}$$、任意の初期状態を $$u^*$$ とすれば

$$
\begin{eqnarray}
u &=& P^\infty u^* \\
&=& P P^\infty u^* \\
&=& P u
\end{eqnarray}
$$

となるため、

$$
\begin{cases}
(P-E)u = 0 \\
\sum u_i = 1 \\
u_i \geq 0
\end{cases}
$$

を満たす $$u$$ を求めればよい。

次に求めた定常確率分布 $$u=\begin{bmatrix}P(s_1)& \cdots& P(s_{n^m})\end{bmatrix}$$ を用いて

$$
\begin{eqnarray}
H(A) &=& \sum_{s_i\in S}^{n^m} P(s_i)H(A|s_i) \\
&=& - \sum_{s_i\in S}^{n^m} P(s_i) \sum_{a_j \in A}^n P(a_j|s_i) \log P(a_j|s_i)
\end{eqnarray}
$$

を計算すれば平均情報量が求まる。
