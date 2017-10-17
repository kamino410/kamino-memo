# フーリエ変換

フーリエ変換とは、時間や空間座標が変数の関数を、周波数を変数とする関数に変換する関数変換を指す。

信号に含まれる周波数成分の解析などに利用される。
変換後の関数は元の関数の「周波数領域表現」と呼ばれることがある。

## 定義

### フーリエ変換

$$\begin{eqnarray}
X(\omega) = \int_{-\infty}^\infty x(t)e^{-j\omega t}dt
\end{eqnarray}$$

### フーリエ逆変換

$$\begin{eqnarray}
x(t) = \frac{1}{2\pi}\int_{-\infty}^\infty X(\omega)e^{j\omega t}d\omega
\end{eqnarray}$$

## 性質

|| $$x(t)$$ | $$X(\omega)$$ |
|----|----|----|
|線形性| $$ax(t)+by(t)$$ | $$aX(\omega)+bY(\omega)$$ |
|相似性| $$x(at)$$ | $$\frac{1}{\|a\|}X \left( \frac{\omega}{a} \right)$$ |
|時間シフト| $$x(t-b)$$ | $$X(\omega)e^{-j\omega b}$$ |
|周波数シフト| $$x(t)e^{jat}$$ | $$X(\omega - a)$$ |
|畳み込み| $$(x * y)(t)$$ | $$X(\omega)Y(\omega)$$ |
|積| $$x(t)y(t)$$ | $$\frac{1}{2\pi}(X*Y)(\omega)$$ |
|時間反転| $$x(-t)$$ | $$X(-\omega)$$ |
|複素共役| $$\overline{x}(t)$$ | $$\overline{X}(\omega)$$ |
| $$x(t)$$微分| $$\frac{d}{dt}x(t)$$ | $$j\omega X(\omega)$$ |
| $$X(\omega)$$微分| $$(-jt)x(t)$$ | $$\frac{d}{d\omega}X(\omega)$$ |
|積分| $$\int_{-\infty}^t x(\tau) d\tau$$ | $$\frac{X(\omega)}{j\omega}+\pi X(0)\delta(\omega)$$ |

### 周期関数のフーリエ変換

一般に三角関数の整数倍の和（複素数表記なら複素指数関数の複素数倍の和）で表される周期関数は次のようにフーリエ変換できる。

$$\begin{eqnarray}
x(t) &=& \sum_{n=-\infty}^\infty c_n e^{jn\omega_0t} \\
c_n &=& \frac{1}{T} \int_{-T/2}^{T/2} x(t) e^{-jn\omega_0\tau} \ d\tau \ \ \ (n=0,\ \pm1,\ \pm2,\ \cdots)
\end{eqnarray}$$

### パーセバルの定理（Parseval's theorem）

フーリエ変換はユニタリ作用素であることを示した定理。
ユニタリ作用素とはヒルベルト空間上の自己同型写像、すなわち線形性及び（一般的、抽象的な意味での）内積とそこから定まる位相の関係を保つような全単射を指す。

より一般的には関数のL2ノルムの積分とその周波数スペクトルのL2ノルムの積分が一致することを示した**プランシュレルの定理**がある。

#### パーセバルの等式

パーセバルの定理から導き出される等式。
時間領域におけるエネルギーと周波数領域におけるエネルギーが等しくなることを示している。

$$\begin{eqnarray}
\int_{-\infty}^\infty |x(t)|^2 dt = \frac{1}{2\pi} \int_{-\infty}^\infty |X(\omega)|^2 d\omega
\end{eqnarray}$$
