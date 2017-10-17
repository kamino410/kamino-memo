# 連続時間信号のフーリエ解析

## 解析でよく用いる連続時間正規直交信号（orthonormal signal）

$$\begin{eqnarray}
f_n(t) &=& \begin{cases}
1 & (n = 0) \\
\sqrt{2}\cos(n\omega_0t) & (n = 1, 2, \cdots)
\end{cases} \\ \\
g_n(t) &=& \sqrt{2}\sin(n\omega_0t) \ \ \ (n = 1,2,\cdots)
\end{eqnarray}$$

ここで $$f_0(t), f_1(t), f_2(t), \cdots, g_1(t), g_2(t), \cdots$$ は1周期のノルムが1であり互いに直交するため正規直交系であると言える。

>検証

>$$f_n(t), g_n(t)$$ の定義域を1周期分に限ったものを $$f'_n(t), g'_n(t) \ \ (0\leq t \leq \frac{2\pi}{n\omega_0})$$ とすると

>$$\begin{eqnarray} \|f'_n\| &=& \frac{n\omega_0}{2\pi} \int_0^{2\pi/n\omega_0} \| f'_n(\tau)\| \ d\tau \\ &=& \frac{n\omega_0}{2\pi} \int_0^{2\pi/n\omega_0} 2\cos^2(n\omega_0\tau) \ d\tau \\ &=& \frac{n\omega_0}{2\pi} \int_0^{2\pi/n\omega_0} (\cos(2n\omega_0\tau) + 1) d\tau \\ &=& \frac{n\omega_0}{2\pi} \left\{ \left[ \frac{1}{2n\omega_0}\sin(2n\omega_0\tau) \right]_0^{2\pi/n\omega_0} + \left[ \tau \right]_0^{2\pi/n\omega_0} \right\} \\ &=& 1 \end{eqnarray}$$

>$$\begin{eqnarray} \|g'_n\| &=& \frac{n\omega_0}{2\pi} \int_0^{2\pi/n\omega_0} \|g'_n(\tau)\| \ d\tau \\ &=& \frac{n\omega_0}{2\pi} \int_0^{2\pi/n\omega_0} 2\sin^2(n\omega_0\tau) \ d\tau \\ &=& \frac{n\omega_0}{2\pi} \int_0^{2\pi/n\omega_0} (1-\cos(2n\omega_0\tau)) d\tau \\ &=& \frac{n\omega_0}{2\pi} \left\{ \left[ \tau \right]_0^{2\pi/n\omega_0} - \left[ \frac{1}{2n\omega_0}\sin(2n\omega_0\tau) \right]_0^{2\pi/n\omega_0} \right\} \\ &=& 1 \end{eqnarray}$$

>$$\begin{eqnarray} r_{f'_n g'_n} &=& \frac{n\omega_0}{2\pi} \int_0^{2\pi/n\omega_0} 2\sin(n\omega_0\tau)\cos(n\omega_0\tau) \ d\tau \\ &=& \frac{n\omega_0}{2\pi} \int_0^{2\pi/n\omega_0} \sin(2n\omega_0\tau) \ d\tau \\ &=& \frac{n\omega_0}{2\pi} \left[ -\frac{1}{2n\omega_0} \cos(2n\omega_0\tau) \right]_0^{2\pi/n\omega_0} \\ &=& 0 \end{eqnarray}$$
