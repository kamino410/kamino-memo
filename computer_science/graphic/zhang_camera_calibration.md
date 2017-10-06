# Zhangの方法によるカメラキャリブレーション

パターンをプリントした板を用意し、それを違う角度から撮影した何枚かの画像からカメラパラメーターを取得する手法。

## 表記の約束ごと

二次元座標を $$\mathrm{m} = \begin{bmatrix}u ,v\end{bmatrix}^T$$ 、三次元座標を $$\mathrm{M} = \begin{bmatrix}X,Y,Z\end{bmatrix}^T$$ 、それぞれの末尾に要素 $$1$$ を加えたものを $$\tilde{\mathrm{m}} = \begin{bmatrix}u,v,1\end{bmatrix}$$ 、$$\tilde{\mathrm{M}} = \begin{bmatrix}X,Y,Z,1\end{bmatrix}$$ と表記する。

ピンホールカメラを3次元座標 $$M$$ と画像上の点 $$m$$ の関係を定義するものとして見ると、その関係は

$$\begin{eqnarray}
s \tilde{\mathrm{m}} = A\begin{bmatrix}R & t\end{bmatrix} \tilde{\mathrm{M}}
\end{eqnarray}$$

と表される（$$s$$ はスケール、$$R$$ は回転行列、$$t$$ は並進ベクトル）。

ここで $$A$$ はカメラの特性を表す行列で、次のように構成される。

$$\begin{eqnarray}
A = \begin{bmatrix} \alpha & \gamma & u_0 \\ 0 & \beta & v_0 \\ 0 & 0 & 1 \end{bmatrix}
\end{eqnarray}$$

$$\alpha, \ \beta$$ はそれぞれ画像の $$u, v$$ 軸方向のスケール、$$(u_0,v_0)$$ は画像中心の座標、$$\gamma$$ はアフィン歪みの歪度を表している。

## パターン面と画像のホモグラフィ

一般性を失わずにパターン面を $$Z=0$$ と仮定できる。
すると先程の式は次のような同次の線形変換になる。

$$\begin{eqnarray}
s\tilde{\mathrm{m}} &=& H \tilde{\mathrm{M}} \\
H &=& \begin{bmatrix}h_1 & h_2 & h_3\end{bmatrix} = A \begin{bmatrix}r_1 & r_2 & t\end{bmatrix}
\end{eqnarray}$$

$$r_1, \ r_2$$ は直交するため、

$$\begin{eqnarray}
h_1^TA^{-T}A^{-1}h_2 &=& 0 \\
h_1^TA^{-T}A^{-1}h_1 &=& h_2^TA^{-T}A^{-1}h_2
\end{eqnarray}$$

の2つの制約式が得られる。

## 解法

$$A^{-T}A^{-1}$$ に注目すると、

$$\begin{eqnarray}
B&=&A^{-T}A^{-1} = \begin{bmatrix}B_{11} & B_{12} & B_{13} \\ B_{12} & B_{22} & B_{23} \\ B_{13} & B_{23} & B_{33}\end{bmatrix} \\
&=& \begin{bmatrix} \frac{1}{\alpha^2} & - \frac{\gamma}{\alpha^2 \beta} & \frac{v_0 \gamma - u_0 \beta}{\alpha^2 \beta} \\ -\frac{\gamma}{\alpha^2 \beta} & \frac{\gamma^2}{\alpha^2 \beta^2} +\frac{1}{\beta^2} & -\frac{\gamma(v_0 \gamma - u_0 \beta)}{\alpha^2 \beta^2} - \frac{v_0}{\beta^2} \\ \frac{v_0 \gamma - u_0 \beta}{\alpha^2 \beta} & -\frac{\gamma(v_0 \gamma - u_0 \beta)}{\alpha^2 \beta^2} - \frac{v_0}{\beta^2} & \frac{(v_0 \gamma - u_0 \beta)^2}{\alpha^2 \beta^2} + \frac{v_0^2}{\beta^2} + 1 \end{bmatrix}
\end{eqnarray}$$

とおける。
ここで

$$\begin{eqnarray}
b &=& \begin{bmatrix} B_{11} & B_{12} & B_{22} & B_{13} & B_{23} & B_{33}  \end{bmatrix}^T \\
h_i &=& \begin{bmatrix} h_{i1} & h_{i2} & h_{i3} \end{bmatrix}^T \\
v_{ij} &=& \begin{bmatrix} h_{i1}h_{j1} & h_{i1}h_{j2} + h_{i2}h_{j1} & h_{i2}h_{j2} & h_{i3}h_{j1} + h_{i1}h_{j3} & h_{i3}h_{j2} + h_{i2}h_{j3} & h_{i3}h_{j3} \end{bmatrix}^T
\end{eqnarray}$$

とすると、先程の制約式は次のように表される。

$$\begin{eqnarray}
\begin{bmatrix} v_{12}^T \\ (v_{11} - v_{22})^T \end{bmatrix}b = 0
\end{eqnarray}$$

未知パラメーターは $$b$$ の6つのため、$$H$$ が3つ以上つまりパターンを別角度から撮影した画像が3枚以上あればパラメーターを推定できる。
