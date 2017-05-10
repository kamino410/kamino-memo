# 2次元の重み付き残差法（ラプラス方程式）

曲線 $$\Gamma$$ に囲まれた領域 $$\Omega$$ におけるラプラス方程式の近似解を求める。

<center>
$$
\begin{eqnarray}
\frac{\partial^2\phi}{\partial x^2}+\frac{\partial^2\phi}{\partial y^2}&=&0 \ \ \ (x,y) \in \Omega \\
\frac{\partial\phi}{\partial n}|_ {(x,y) \in \Gamma_1} = \hat{q}(x,y)&,& \ \ \ \phi|_ {(x,y) \in \Gamma_2} = \hat{\phi}(x,y) \\
\Gamma = \Gamma_1 \cup \Gamma_2 &,& \ \ \ \Gamma_1 \cap \Gamma_2 = \emptyset
\end{eqnarray}
$$
</center>

ただし、$$\hat{q}(x,y), \hat{\phi}(x,y)$$ は既知とする。

## 概要

1次元のときと同じようにガラーキン法を用いる。

今回は2次元のため、領域を三角形の小領域に分割し、小領域内での解を平面に近似する。

## 弱形式の導出

任意関数 $$\phi^* (x,y)$$ を用いて

<center>
$$
\int\int_\Omega \phi^* \left( \frac{\partial^2\phi}{\partial x^2}+\frac{\partial^2\phi}{\partial y^2} \right) dxdy=0
$$
</center>

ここでガウスの発散定理を用いる。

>閉曲線 $$\Gamma$$ で囲まれる2次元領域 $$\Omega$$ において $$F(x,y), G(s,y)$$ が連続かつその1階偏導関数も連続なら
<center>
$$
\int\int_\Omega \left( \frac{\partial^2\phi}{\partial x^2}+\frac{\partial^2\phi}{\partial y^2} \right)dxdy =
\int_\Gamma (Fn_x+Gn_y)d\Gamma
$$
</center>
ただし $$\int_\Gamma d\Gamma$$ は反時計回りに取る。

>直感的には『領域全体でのポテンシャルの増減 = 領域境界における流入出の和』を示す式である。

<center>
$$
\int\int_\Omega \left[ \frac{\partial}{\partial x} \left( \phi^* \frac{\partial \phi}{\partial x} \right) + \frac{\partial}{\partial y} \left( \phi^* \frac{\partial \phi}{\partial y} \right) \right] dxdy = 0
$$
</center>

<center>
$$
\int_\Gamma \phi^* \left( \frac{\partial \phi}{\partial x}n_x + \frac{\partial \phi}{\partial y}n_y \right)d\Gamma = 0
$$
</center>

$$\frac{\partial\phi}{\partial n} = \frac{\partial \phi}{\partial x}n_x+\frac{\partial \phi}{\partial y}n_y$$ を用いて

<center>
$$
\int_\Gamma \phi^* \frac{\partial \phi}{\partial n}d\Gamma - \int\int_\Omega \left( \frac{\partial \phi^* }{\partial x}\frac{\partial \phi}{\partial x} + \frac{\partial \phi^* }{\partial y}\frac{\partial \phi}{\partial y} \right)dxdy = 0
$$
</center>

<center>
$$
\int_{\Gamma_1} \phi^* \frac{\partial \phi}{\partial n} d\Gamma + \int_{\Gamma_2} \phi^* \frac{\partial \phi}{\partial n}d\Gamma - \int\int_\Omega \left( \frac{\partial \phi^* }{\partial x}\frac{\partial \phi}{\partial x} + \frac{\partial \phi^* }{\partial y}\frac{\partial \phi}{\partial y} \right)dxdy = 0
$$
</center>

ノイマン境界条件を利用して

<center>
$$
\int_{\Gamma_1} \phi^* \hat{q} d\Gamma + \int_{\Gamma_2} \phi^* \frac{\partial \phi}{\partial n}d\Gamma - \int\int_\Omega \left( \frac{\partial \phi^* }{\partial x}\frac{\partial \phi}{\partial x} + \frac{\partial \phi^* }{\partial y}\frac{\partial \phi}{\partial y} \right)dxdy = 0
$$
</center>

ディリクレ境界条件を利用して

<center>
$$
\int_{\Gamma_1} \phi^* \hat{q}d\Gamma - \int\int_\Omega \left( \frac{\partial \phi^* }{\partial x}\frac{\partial \phi}{\partial x} + \frac{\partial \phi^* }{\partial y}\frac{\partial \phi}{\partial y} \right)dxdy = 0
$$
</center>

これが弱形式となる。

