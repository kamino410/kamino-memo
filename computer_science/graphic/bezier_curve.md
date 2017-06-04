# ベジェ曲線（Bézier_curve）

ベジェ曲線とは$$N+1$$個の制御点から得られる$$N$$次曲線である。

フォントなど大幅な拡大縮小が想定される画像の表現には3次ベジェ曲線が利用される。

## 定義

制御点を$$C_0, \dots, C_{N+1}$$とすると、ここから得られる$$N$$次曲線は次のように表される。

$$
\begin{eqnarray}
P(t) &=& \sum_{i=0}^N C_i B_i^n(t) \\
B_i^n(t) &=& \ _ n C_i t^i(1-t)^{n-1} \\
&=& \frac{n!}{i!(n-i)!}t^i(1-t)^{n-i}
\end{eqnarray}
$$

$$B_i^n(t)$$はバーンスタイン基底関数と呼ばれる。

## 3次ベジェ曲線の描画例

```py
import matplotlib.pyplot as plt
import numpy as np

def bezier3(p0, p1, p2, p3, n):
    ts = [i/n for i in range(n)]
    ts.append(1)
    def f(t):
        a0 = (1-t)**3
        a1 = 3 * (1-t)**2 * t
        a2 = 3 * (1-t)* t**2
        a3 = t**3
        return (
            a0*p0[0] + a1*p1[0] + a2*p2[0] + a3*p3[0],
            a0*p0[1] + a1*p1[1] + a2*p2[1] + a3*p3[1]
        )
    return map(f, ts)

ps = list(bezier3((0,0),(0.3,0.3),(0.3,0),(1,0),100))
xs = list(map(lambda p: p[0], ps))
ys = list(map(lambda p: p[1], ps))

plt.plot(xs, ys)
plt.xlim(0, 1)
plt.ylim(0, 1)
plt.show()

```
