# ラプラス変換（Laplace Transform）

ラプラス変換とは、関数$$y(t)$$を **$$t$$の微積分⇔$$s$$の掛け算** となるような媒介変数$$s$$を用いて$$Y(s)$$とするような関数変換を指す。

微積分を掛け算として計算できるため、線形微分方程式を調べる際に役立つ。

## 定義

### ラプラス変換

<center>
$$
F(s) = \mathscr{L}[f(t)] = \int_0^\infty f(t)e^{-st} dt \ \ \ (t \geq 0)
$$
</center><br />

### 逆ラプラス変換

<center>
$$
f(t) = \lim_{p \to \infty} \frac{1}{2 \pi i} \int_{c-ip}^{c+ip} F(s) e^{st} ds \ \ \ (c > 0)
$$
</center><br />

## 変換表

|f(t)|F(s)|
|----|----|
| $$\delta (t) = \begin{cases} \infty & (x=0) \\ 0 & (x \neq 0 ) \end{cases}$$ ※デルタ関数| $$1$$ |
| $$u_s(t) = \int \delta (t) dt = 1$$ | $$\frac{1}{s}$$ |
| $$t$$ | $$\frac{1}{s^2}$$ |
| $$\frac{t^n}{n!}$$ | $$\frac{1}{s^{n+1}}$$ |
| $$e^{-at}$$ | $$\frac{1}{s+a}$$ |
| $$te^{-at}$$ | $$\frac{1}{(s+a)^2}$$ |
| $$\sin \omega t$$ | $$\frac{\omega}{s^2+\omega^2}$$ |
| $$\cos \omega t$$ | $$\frac{s}{s^2+\omega^2}$$ |
| $$e^{-at}\sin \omega t$$ | $$\frac{\omega}{(s+a)^2+\omega^2}$$ |
| $$e^{-at}\cos \omega t$$ | $$\frac{s+a}{(s+a)^2+\omega^2}$$ |

## 性質

|| $$f(t)$$ | $$F(s)$$ |
|----|----|----|
|線形性| $$af(t)+bg(t)$$ | $$aF(s)+bG(t)$$ |
|相似性| $$f(at)$$ | $$\frac{1}{a}F\left( \frac{s}{a} \right)$$ |
|時間シフト| $$f(t-a)$$ | $$e^{-as}F(s)$$ |
|畳み込み| $$\int_0^t f(t-\tau)g(\tau)d\tau$$ | $$F(s)G(s)$$ |
|微分| $$\frac{d}{dt}f(t)$$ | $$sF(s)-f(0)$$ |
|n階微分| $$\frac{d^n}{dt^n}f(t)$$ | $$s^nF(s)-\left\{s^{n-1}f(0)+s^{n-2}f'(0) + \dots + f^{(n-1)}(0)\right\}$$ |
|積分| $$\int_0^tf(t)dt$$ | $$\frac{1}{s} \left\{F(s)+f^{(-1)}(0)\right\}$$ |
|n重積分| $$\int \int \dots \int_0^tf(t)(dt)^n$$ | $$s^{-n}F(s)+s^{-n}f^{(-1)}(0)+\left\{s^{-(n-1)}f^{-2}(0)+\dots+s^{-1}f^{(-n)}(0)\right\}$$ |

## 初期値・最終値の定理

<center>
$$\lim_{t \to +0}f(t) = \lim_{s \to \infty}sF(s)$$
</center><br />

<center>
$$f(t)$$ が収束するなら $$\lim_{t \to \infty}f(t) = \lim_{s \to 0}sF(s)$$
</center><br />
