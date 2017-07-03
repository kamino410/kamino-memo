# 周波数応答（frequency response）

## 周波数特性

安定な線形システムに一定周波数の正弦波を加え続けると、定常状態の出力も同じ周波数の正弦波になることが知られている。

このとき、出力の振幅と位相は入力と伝達関数 $$G(s)$$ に依存して変化する。
特に入力の周波数に対する変化の特性を**周波数特性**と呼ぶ。

## 伝達関数と周波数特性

伝達関数 $$G(s) = N(s)/D(s)$$ の安定な線形システムに一定周波数の正弦波 $$u(t) = e^{j\omega t} = \cos \omega t + j \sin \omega t$$ を加えたときの出力 $$y(t)$$ について考えると、

$$
\begin{eqnarray}
Y(s) &=& G(s) \mathscr{L}[u(t)] \\
Y(s) &=& G(s) \frac{1}{s-j\omega}
\end{eqnarray}
$$

$$G(s)$$ の極 $$p_i$$を用いて右辺を部分分数分解すると

$$
\begin{eqnarray}
Y(s) &=& \frac{K_0}{s-j\omega} + \sum_{i=1}^n \frac{K_i}{s-p_i} \\
y(t) &=& K_0 e^{j \omega t} + \sum_{i=1}^n K_i e^{p_it}
\end{eqnarray}
$$

安定なシステムであることから $$Re[p_i] < 0\ (i = 1 \sim n)$$ を満たすため、 $$t \rightarrow \infty$$ のとき、第二項は無視できる

$$
y(t) \simeq K_0 u(t)
$$

また部分分数分解の係数の性質より

$$
K_0 = \lim_{s \rightarrow j\omega}(s-j\omega)G(s) = G(j\omega)
$$

であることを利用すると

$$
\begin{eqnarray}
y(t) &=& G(j\omega)u(t) \\
&=& |G(j\omega)|\ e^{j(\omega t + \phi)}
\end{eqnarray}
$$

が得られる。（ただし $$\phi = \angle G(j\omega)$$ ）

### 周波数伝達関数

上記の式より次のことがわかる。

* 出力の振幅は入力の振幅の $$|G(j\omega)|$$ 倍になる（これを**ゲイン**と呼ぶ）
* 出力の位相は入力の位相より $$\phi$$ だけ進んだものになる（これを**位相差**と呼ぶ）

このようにシステムの周波数特性は $$s=j\omega$$ とした伝達関数から得られる。
この伝達関数を特に**周波数伝達関数**と呼ぶ。
