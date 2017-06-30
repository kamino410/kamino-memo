# 2次元の重み付き残差法（ラプラス方程式）

曲線 $$\Gamma$$ に囲まれた領域 $$\Omega$$ におけるラプラス方程式の近似解を求める。

$$
\begin{eqnarray}
\frac{\partial^2\phi}{\partial x^2}+\frac{\partial^2\phi}{\partial y^2}&=&0 \ \ \ (x,y) \in \Omega \\
\frac{\partial\phi}{\partial n}|_ {(x,y) \in \Gamma_1} = \hat{q}(x,y)&,& \ \ \ \phi|_ {(x,y) \in \Gamma_2} = \hat{\phi}(x,y) \\
\Gamma = \Gamma_1 \cup \Gamma_2 &,& \ \ \ \Gamma_1 \cap \Gamma_2 = \emptyset
\end{eqnarray}
$$

ただし、$$\hat{q}(x,y), \hat{\phi}(x,y)$$ は既知とする。

## 概要

1次元のときと同じようにガラーキン法を用いる。

今回は2次元のため、領域を三角形の小領域に分割し、小領域内での解を平面に近似する。

## 弱形式の導出

任意関数 $$\phi^* (x,y)$$ を用いて

$$
\int\int_\Omega \phi^* \left( \frac{\partial^2\phi}{\partial x^2}+\frac{\partial^2\phi}{\partial y^2} \right) dxdy=0
$$

ここでガウスの発散定理を用いる。

>閉曲線 $$\Gamma$$ で囲まれる2次元領域 $$\Omega$$ において $$F(x,y), G(s,y)$$ が連続かつその1階偏導関数も連続なら
$$
\int\int_\Omega \left( \frac{\partial^2\phi}{\partial x^2}+\frac{\partial^2\phi}{\partial y^2} \right)dxdy =
\int_\Gamma (Fn_x+Gn_y)d\Gamma
$$
ただし $$\int_\Gamma d\Gamma$$ は反時計回りに取る。

>直感的には『領域全体でのポテンシャルの増減 = 領域境界における流入出の和』を示す式である。

$$
\int\int_\Omega \left[ \frac{\partial}{\partial x} \left( \phi^* \frac{\partial \phi}{\partial x} \right) + \frac{\partial}{\partial y} \left( \phi^* \frac{\partial \phi}{\partial y} \right) \right] dxdy = 0
$$

$$
\int_\Gamma \phi^* \left( \frac{\partial \phi}{\partial x}n_x + \frac{\partial \phi}{\partial y}n_y \right)d\Gamma = 0
$$

$$\frac{\partial\phi}{\partial n} = \frac{\partial \phi}{\partial x}n_x+\frac{\partial \phi}{\partial y}n_y$$ を用いて

$$
\int_\Gamma \phi^* \frac{\partial \phi}{\partial n}d\Gamma - \int\int_\Omega \left( \frac{\partial \phi^* }{\partial x}\frac{\partial \phi}{\partial x} + \frac{\partial \phi^* }{\partial y}\frac{\partial \phi}{\partial y} \right)dxdy = 0
$$

$$
\int_{\Gamma_1} \phi^* \frac{\partial \phi}{\partial n} d\Gamma + \int_{\Gamma_2} \phi^* \frac{\partial \phi}{\partial n}d\Gamma - \int\int_\Omega \left( \frac{\partial \phi^* }{\partial x}\frac{\partial \phi}{\partial x} + \frac{\partial \phi^* }{\partial y}\frac{\partial \phi}{\partial y} \right)dxdy = 0
$$

ノイマン境界条件を利用して

$$
\int_{\Gamma_1} \phi^* \hat{q} d\Gamma + \int_{\Gamma_2} \phi^* \frac{\partial \phi}{\partial n}d\Gamma - \int\int_\Omega \left( \frac{\partial \phi^* }{\partial x}\frac{\partial \phi}{\partial x} + \frac{\partial \phi^* }{\partial y}\frac{\partial \phi}{\partial y} \right)dxdy = 0
$$

ここでディリクレ境界条件が課せられた境界上では$$\phi^* =0$$と仮定する。

$$
\int_{\Gamma_1} \phi^* \hat{q}d\Gamma - \int\int_\Omega \left( \frac{\partial \phi^* }{\partial x}\frac{\partial \phi}{\partial x} + \frac{\partial \phi^* }{\partial y}\frac{\partial \phi}{\partial y} \right)dxdy = 0
$$

これが弱形式となる。

## 弱形式の離散化

近似解を$$\tilde{\phi}(x,y)$$とすると、これが満たすべき方程式は

$$
\begin{eqnarray}
\int\int_\Omega \left( \frac{\partial \phi^* }{\partial x}\frac{\partial \tilde{\phi}}{\partial x} + \frac{\partial \phi^* }{\partial y}\frac{\partial \tilde{\phi}}{\partial y} \right)dxdy - \int_{\Gamma_1} \phi^* \hat{q}d\Gamma = 0 \\
\tilde{\phi}=\hat{\phi}(x,y) \ \ \ (\Gamma_2上)
\end{eqnarray}
$$

である。

