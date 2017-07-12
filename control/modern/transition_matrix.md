# 状態方程式の解

$$
\dot{x} = Ax + Bu
$$

$$ \dot{x} = ax + bu $$ の解は $$e^{at}$$ を用いて次のように表されることが知られている。

$$
x(t) = e^{a(t-t_0)}x(t_0) + \int_{t_0}^t e^{a(t-\tau)} b u(\tau) d\tau
$$

また、$$e^{at}$$ はテイラー展開を利用して次のように表される。

$$
e^{at} = a + at + \frac{a^2t^2}{2!} + \frac{a^3t^3}{3!} + \cdots
$$

ここで $$a$$ を行列に拡張することを考えて

$$
e^{At} = A + At + \frac{A^2t^2}{2!} + \frac{A^3t^3}{3!} + \cdots
$$

と定義すると、次のような演算について $$e^{at}$$ と同じ形で表されることが確認できる。

$$
\begin{eqnarray}
&\ & \frac{d(e^{At})}{dt} = Ae^{At} = e^{At}A \\
&\ & e^{A(t_1+t_2)} = e^{At_1}e^{At_2} \\
&\ & (e^{At})^{-1} = e^{-At} \\
&\ & e^{At}|_{t=0} = I
\end{eqnarray}
$$

（ただし、$$e^{(A+B)t} = e^{At}e^{Bt}$$ は $$AB=BA$$ のときにしか成立しないなど、すべての演算が同じ形になるわけではない）

上記の変形を用いれば $$\dot{x} = Ax + B$$ の解は $$e^{at}$$ の場合と同じ形で表される。

$$
x(t) = e^{A(t-t_0)}x(t_0) + \int_{t_0}^t e^{A(t-\tau)} B u(\tau) d\tau
$$

# 遷移行列（state-transition matrix）

