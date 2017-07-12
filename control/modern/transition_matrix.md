# 状態方程式の解

状態方程式 $$\dot{x} = Ax + Bu$$ の解について考える。

$$a,b$$ をスカラとしたとき、$$ \dot{x} = ax + bu $$ の解は $$e^{at}$$ を用いて次のように表されることが知られている。

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

ただし、$$e^{(A+B)t} = e^{At}e^{Bt}$$ は $$AB=BA$$ のときにしか成立しないなど、すべての演算が同じ形になるわけではない。
また、3つ目に示す通り $$A$$ の正則・非正則にかかわらず $$e^{At}$$ は正則になる。

上記の変形を用いれば $$\dot{x} = Ax + B$$ の解は $$e^{at}$$ の場合と同じ形で表される。

$$
x(t) = e^{A(t-t_0)}x(t_0) + \int_{t_0}^t e^{A(t-\tau)} B u(\tau) d\tau
$$

これが状態方程式の解となる。

# 遷移行列（state-transition matrix）

上記の式で入力を $$u = 0$$ とすれば、時刻 $$t$$ における状態変数は初期状態 $$x(t_0)$$ を用いて次のように表される。

$$
x(t) = e^{A(t-t_0)}x(t_0)
$$

このときの係数 $$e^{A(t-t_0)}$$ を**遷移行列**という。

## 要素の計算

遷移行列の要素は定義の式 $$e^{At} = A + At + \frac{A^2t^2}{2!} + \frac{A^3t^3}{3!} + \cdots$$ から計算できるほか、[ラプラス変換](../../mathematics/analysis/laplace_transform.md)を用いても計算できる。

$$t_0 = 0$$ として、$$e^At$$ の性質から

$$
\frac{d(e^{At})}{dt} = Ae^{At}
$$

両辺をラプラス変換すると

$$
\begin{eqnarray}
s\mathscr{L}[e^{At}] - e^{A \cdot 0} &=& A\mathscr{L}[e^{At}] \\
s\mathscr{L}[e^{At}] - I &=& A\mathscr{L}[e^{At}] \\
e^{At} &=& \mathscr{L}^{-1}[(sI-A)^{-1}]
\end{eqnarray}
$$

となり、これを計算すれば遷移行列の要素が求まる。
ただし、$$\mathscr{L}^{-1}[M]$$ は行列 $$M$$ の各要素を逆ラプラス変換した行列に等しい。
