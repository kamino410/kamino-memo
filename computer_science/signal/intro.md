# 信号処理 概要

## 目的

|項目||
|----|----|
|雑音除去|雑音を取り除いて元の信号のみを取り出す|
|等化|歪んだ信号を元の信号に戻す|
|予測|過去の信号を使って未来の信号の値を予測する|
|データ圧縮|信号の冗長な成分を取り除いてコンパクトに表現する|
|システム同定|観測した信号からシステムの数学モデルを作成する|
|スペクトル推定|信号がどの周波数成分をどれくらい含むかを解析する|

## 信号の分類

|時間\\振幅|連続|離散|
|----|----|----|
|連続|アナログ信号|多値信号|
|離散|サンプル値信号|ディジタル信号|

* 偶信号／奇信号
  * 偶信号（even signal）
    * $$f(-t) = f(t), \ \ x_{-n} = x_{n}$$
  * 奇信号（odd signal）
    * $$f(-t) = -f(t), \ \ x_{-n} = -x_{n}$$
* 周期信号（periodic signal）
  * 基本周期（fundamental period）
    * $$f(t) = f(t+T), \ \ x_{n} = x_{n+N}$$ を満たす最小の $$T, \ \ N$$
  * 基本周波数（fundamental frequency）
    * $$1/T, \ \ 1/N$$

## A/D処理

|処理||
|----|----|
|標本化（sampling）|アナログ信号->サンプル値信号|
|量子化（quantization）|サンプル値信号->ディジタル信号|

## エネルギー（energy）

$$\begin{eqnarray}
E &=& \int_{-\infty}^\infty | x(t) | ^2 dt \\
E &=& \sum_{n=-\infty}^\infty |x_n|
\end{eqnarray}$$

$$E<\infty$$ を満たす信号は有限エネルギー信号（finite energy signal）と呼ばれる。

[パーセバルの等式](../../mathematics/analysis/fourier_transform.md#パーセバルの等式)も参照。

## 平均パワー（average power）

単位時間あたりのエネルギーは平均パワーと呼ばれる。

$$\begin{eqnarray}
P &=& \lim_{T\rightarrow\infty} \frac{1}{T} \int_{-T/2}^{T/2} |x(t)|^2dt \\
P &=& \lim_{N\rightarrow\infty} \frac{1}{2N+1} \sum_{n=-N}^N |x_n|^2
\end{eqnarray}$$

## 内積（inner product）

信号値 $$x$$ の複素共役を $$\bar{x}$$ と表現することにすると、信号の内積は次のように定義される。

$$\begin{eqnarray}
\langle x,y \rangle &=& \int_{-\infty}^\infty x(t) \bar{y}(t) dt \\
\langle x,y \rangle &=& \sum_{n=-\infty}^\infty x_n \bar{y_n}
\end{eqnarray}$$

## ノルム（norm）

信号のノルムは次のように定義される。

$$\begin{eqnarray}
||x|| = \sqrt{\langle x, x \rangle}
\end{eqnarray}$$

## 相互相関関数（cross correlation function）

$$\begin{eqnarray}
y^\tau &=& y(t-\tau) \\ \\
r_{xy}(\tau) &=& \langle x,y^\tau \rangle \\
&=& \int_{-\infty}^\infty x(t)\bar{y}(t-\tau)dt
\end{eqnarray}$$

ここで相互相関関数は $$0 \leq |r_{xy}(\tau)| \leq \|x\| \ \|y\|$$ を満たす。

また $$0 = r_{xy}(\tau)$$ なら $$x$$ と $$y^\tau$$ は**直交**しており、$$|r_{xy}(\tau)| = \|x\|\ \|y\|$$ なら**相似**であると言える。
