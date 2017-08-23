# 単純な梁の弾性応力解析

支持されている梁に荷重を加えたとき、変形量が微小であるものとして、梁の内部に働く応力について考える。

## 片持ち梁（集中荷重）

一方の端を固定支持した長さ $$l$$ の梁の反対側の端に $$W$$ の集中荷重を加える。

<img src="fig7.png" width=70%>

まず全体の釣り合いの式を考える。

$$\begin{cases}
R_A - W = 0 \\
M_A - Wl = 0
\end{cases}$$

次に位置 $$x$$ の仮想断面における釣り合いの式を考える。
切断法では断面の左右どちらかに着目して釣り合いの式を考えればその断面における応力が求まることが知られているため、左側についてだけ考える。

$$\begin{cases}
R_A - F = 0 \\
M_A - Fx + M = 0
\end{cases}$$

これらを解くと

$$\begin{cases}
F = W \\
M = -W(l-x)
\end{cases}$$

を得る。
これに基づいてSFD、BMDを描くと以下のようになる。

<img src="fig8.png" width=80%>

## 片持ち梁（等分布荷重）

長さ $$l$$ の片持ち梁全体に等分布荷重 $$w_0$$ を加える（なお分布荷重の値は単位長さあたりの大きさを表す）。

<img src="fig9.png" width=70%>

まず全体の釣り合いの式を考える。

$$\begin{cases}
R_A - \int_0^l w_0 d\xi = 0 \\
M_A - \int_0^l \xi \cdot w_0 d\xi = 0
\end{cases}$$

次に位置 $$x$$ の仮想断面における釣り合いの式を考える。

$$\begin{cases}
R_A - \int_0^x w_0 d \xi - F = 0 \\
M_A - \int_0^x \xi \cdot w_0 d\xi - Fx + M = 0
\end{cases}$$

これらを解くと

$$\begin{cases}
R_A = \frac{w_0l}{2} \\
M = - \frac{w_0}{2}(l-x)^2
\end{cases}$$

を得る。
これに基づいてSFD、BMDを描くと以下のようになる。

<img src="fig10.png" width=80%>

## ソースコード

```py
import matplotlib.pyplot as plt
import numpy as np

xs = np.linspace(0, 1, 100)
sfs = list(map(lambda x: 1, xs))
bms = -1 * (1 - xs)

plt.plot(xs, sfs, label='SFD')
plt.plot(xs, bms, label='BMD')

plt.title('cantilever / concentrated load (l=1,W=1)')
plt.xlabel('span')
plt.ylabel('shearing stress/bending stress')
plt.legend()

plt.show()

```

```py
import matplotlib.pyplot as plt
import numpy as np

xs = np.linspace(0, 1, 100)
sfs = list(map(lambda x: 1/2, xs))
bms = -1/2 * np.power(1 - xs, 2)

plt.plot(xs, sfs, label='SFD')
plt.plot(xs, bms, label='BMD')

plt.title('cantilever / uniformly-distributed load (l=1,W0=1)')
plt.xlabel('span')
plt.ylabel('shearing stress/bending stress')
plt.legend()

plt.show()

```
