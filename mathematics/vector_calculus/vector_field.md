# ベクトル場（vector field）

## 定義

ユークリッド空間上の各点にベクトル的な量が与えられているとき、その分布を表したものを**ベクトル場**という。
ベクトル場はベクトル値関数 $$V: M \rightarrow R^m \ \ (M \subset R^m)$$ によって表現される。

## 操作

直交座標系 $$\vec{e_1}, \vec{e_2}, \vec{e_3}$$ による3次元ベクトル場 $$\vec{v} = v_1\vec{e_1} + v_2\vec{e_2} + v_3\vec{e_3}$$ 上の点 $$\vec{x} = (x_1,x_2,x_3)$$ におけるベクトル操作についてまとめる。

### 勾配（gradient）

ある点におけるベクトル場の勾配は次のように定義される。

$$\begin{eqnarray}
\nabla = \frac{\partial}{\partial x_1} \vec{e_1} + \frac{\partial}{\partial x_2} \vec{e_2} + \frac{\partial}{\partial x_3} \vec{e_3}
\end{eqnarray}$$

として

$$\begin{eqnarray}
\mathrm{grad}\ \vec{v} = \nabla \vec{v} = \frac{\partial v}{\partial x_1} \vec{e_1} + \frac{\partial v}{\partial x_2} \vec{e_2} + \frac{\partial v}{\partial x_3} \vec{e_3}
\end{eqnarray}$$

### 発散（divergence）

発散は次のように定義され、ある点における流入と流出の大きさを表す。

$$\begin{eqnarray}
\mathrm{div}\ \vec{v} = \nabla \cdot \vec{v} = \frac{\partial v_1}{\partial x_1} + \frac{\partial v_2}{\partial x_2} + \frac{\partial v_3}{\partial x_3}
\end{eqnarray}$$

### 回転（rotate）

ベクトルの回転は次のように定義される。

$$\begin{eqnarray}
\mathrm{rot}\ \vec{v} = \nabla \times \vec{v} &=& \begin{pmatrix}\frac{\partial}{\partial x_1} \\ \frac{\partial}{\partial x_2} \\ \frac{\partial}{\partial x_3}\end{pmatrix} \times \begin{pmatrix}v_1 \\ v_2 \\ v_3\end{pmatrix}
\end{eqnarray}$$
