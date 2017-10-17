# 離散時間信号のフーリエ解析

## 離散フーリエ変換（Discrete Fourier Transform : DFT）

サンプル数 $$N$$ の信号に対してDFTとIDFTは次のように定義される。

$$\begin{eqnarray}
X_k &=& \sum_{n=0}^{N-1} x_n e^{-2\pi jnk/N} \\
x_n &=& \frac{1}{N} \sum_{n=0}^{N-1} X_k e^{2\pi jnk/N}
\end{eqnarray}$$

* $$X_k$$：$$k$$ 次高調波の周波数スペクトル
* $$|X_k|$$：$$k$$ 次高調波の振幅スペクトル
* $$\angle X_k$$：$$k$$ 次高調波の位相スペクトル
* $$|X_k|^2$$：$$k$$ 次高調波のエネルギースペクトル

サンプリング周波数を $$T$$ としたとき、$$0\sim N$$ は時間 $$NT$$ に相当する。
すなわち基本周波数は $$1/NT$$ 、$$k$$ 次高調波の周波数は $$k/NT$$ になる。
基本波の角周波数は $$2\pi/NT$$ 、$$k$$ 次高調波の角周波数は $$2k\pi/NT$$ である。

## ピリオドグラム（periodgram）

信号にはある程度のノイズが含まれていることが想定されるため、確率的な扱いをしたいケースがある。
**ピリオドグラム**は角周波数 $$\Omega$$ ごとにエネルギースペクトルの平均を計算し、ノイズの影響を減らしたものである。

$$\begin{eqnarray}
P(\Omega) = \frac{1}{N} \left| \sum_{n=0}^{N-1} x_n e^{-jn\Omega T} \right| ^2
\end{eqnarray}$$

## 離散フーリエ変換の行列表現

$$W = e^{-2\pi j/N}$$ とするとDFTは次のように表される。

$$\begin{eqnarray}
\begin{bmatrix} X_0 \\ X_1 \\ X_2 \\ \vdots \\ X_{N-1} \end{bmatrix}
&=& \begin{bmatrix} W^0 & W^0 & W^0 & \cdots & W^0 \\
W^0 & W^1 & W^2 & \cdots & W^{(N-1)} \\
W^0 & W^2 & W^4 & \cdots & W^{2(N-1)} \\
\vdots & \vdots & \vdots & \ddots & \vdots \\
W^0 & W^{N-1} & W^{2(N-1)} & \cdots & W^{(N-1)^2}
\end{bmatrix}
\begin{bmatrix}
x_0 \\ x_1 \\ x_2 \\ \vdots \\ x_{N-1}
\end{bmatrix}
\end{eqnarray}$$

これを $$X = Ax$$ と見れば、$$A$$ は $$AA^H = A^HA = I$$ を満たすため、逆フーリエ変換は次のように表される。

$$\begin{eqnarray}
x = \frac{1}{N} A^H X
\end{eqnarray}$$
