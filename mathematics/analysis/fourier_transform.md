# フーリエ変換

フーリエ変換とは、時間や空間座標が変数の関数を、周波数を変数とする関数に変換する関数変換を指す。

信号に含まれる周波数成分の解析などに利用される。
変換後の関数は元の関数の「周波数領域表現」と呼ばれることがある。

## 定義

### フーリエ変換

<center>
$$
X(\omega) = \int_{-\infty}^\infty x(t)e^{-j\omega t}dt
$$
</center>

### フーリエ逆変換

<center>
$$
x(t) = \frac{1}{2\pi}\int_{-\infty}^\infty X(\omega)e^{j\omega t}d\omega
$$
</center>

## 性質

|| $$x(t)$$ | $$X(\omega)$$ |
|----|----|----|
|線形性| $$ax(t)+by(t)$$ | $$aX(\omega)+bY(\omega)$$ |
|相似性| $$x(at)$$ | $$\frac{1}{|a|}X \left( \frac{\omega}{a} \right)$$ |
|時間シフト| $$x(t-b)$$ | $$X(\omega)e^{-j\omega b}$$ |
|周波数シフト| $$x(t)e^{jat}$$ | $$X(\omega - a)$$ |
|畳み込み| $$(x * y)(t)$$ | $$X(\omega)Y(\omega)$$ |
|積| $$x(t)y(t)$$ | $$\frac{1}{2\pi}(X*Y)(\omega)$$ |
|時間反転| $$x(-t)$$ | $$X(-\omega)$$ |
|複素共役| $$\overline{x}(t)$$ | $$\overline{X}(\omega)$$ |
| $$x(t)$$微分| $$\frac{d}{dt}x(t)$$ | $$j\omega X(\omega)$$ |
| $$X(\omega)$$微分| $$(-jt)x(t)$$ | $$\frac{d}{d\omega}X(\omega)$$ |
|積分| $$\int_{-\infty}^t x(\tau) d\tau$$ | $$\frac{X(\omega)}{j\omega}+\pi X(0)\delta(\omega)$$ |
