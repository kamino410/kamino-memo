# Projector / Camera Mathematics

## Rendering

### Abstract

* Model
  * Vertices coordinates : $${}^M p_i$$
  * Model Transformation Matrix : $${}^W(T_m)_M$$
    * Transport vector : $${}^W(t_m)_M$$
    * Rotation matrix : $${}^W(R_m)_M$$
* Camera
  * View Transformation Matrix : $${}^V(T_v)_W$$
    * Transport vector : $${}^V(t_v)_W$$
    * Rotation matrix : $${}^V(R_v)_W$$
  * Projection Matrix : $${}^VP$$
  * Viewport Matrix : $${}^VV$$

### Notation

* Lower case : 3 dimentional vector
* Upper case : Matrix
* Tilde : Homogeneous vector
* Subscripts : Transformation from {right} coordinate to {left} coordiname

### Transformation Matrix

#### Rotation Matrix

X-Y-Z Euler angle $$(\theta_x,\theta_y,\theta_z)$$ (rotate $$\theta_z$$ around $$z$$ axis, $$\theta_y$$ around $$y$$ axis, $$\theta_x$$ around $$x$$ axis)

$$
\begin{eqnarray}
R = \begin{bmatrix} 1 & 0 & 0 \\ 0 & C_{\theta_z} & -S_{\theta_z} \\ 0 & S_{\theta_z} & C_{\theta_z} \end{bmatrix}
\begin{bmatrix}C_{\theta_y} & 0 & S_{\theta_y} \\ 0 & 1 & 0 \\  -S_{\theta_y} & 0 & C_{\theta_y} \end{bmatrix}
\begin{bmatrix}C_{\theta_x} & -S_{\theta_x} & 0 \\ S_{\theta_x} & C_{\theta_x} & 0 \\ 0 & 0 & 1 \end{bmatrix}
\end{eqnarray}
$$

Rotation matrix is orthogonal matrix

$$
\begin{eqnarray}
R^{-1} &=& R^T \\
R^T R &=& R_z^TR_y^TR_x^TR_xR_yR_z = I
\end{eqnarray}
$$

#### Transport Matrix

Transformation matrix (Rotate -> Place to position of transport vector)

$$
\begin{eqnarray}
T &=&
\left[ \begin{array}{ccc:c}
1 & 0 & 0 \\ 0 & 1 & 0 & t \\ 0 & 0 & 1 \\ \hdashline 0 & 0 & 0 & 1
\end{array} \right]
\left[ \begin{array}{ccc:c}
& & & 0 \\ & R & & 0 \\ & & & 0 \\ \hdashline 0 & 0 & 0 & 1
\end{array} \right]
= \left[ \begin{array}{ccc:c}
\\ & R & & t \\ \\ \hdashline 0 & 0 & 0 & 1
\end{array} \right] \\
T^{-1} &=&
\left[ \begin{array}{ccc:c}
& & & 0 \\ & R^T & & 0 \\ & & & 0 \\ \hdashline 0 & 0 & 0 & 1
\end{array} \right]
\left[ \begin{array}{ccc:c}
1 & 0 & 0 \\ 0 & 1 & 0 & -t \\ 0 & 0 & 1 \\ \hdashline 0 & 0 & 0 & 1
\end{array} \right]
= \left[ \begin{array}{ccc:c}
& & & \\ & R^T & & -R^Tt \\ & & & \\ \hdashline 0 & 0 & 0 & 1
\end{array} \right]
\end{eqnarray}
$$

### Projection Matrix

Frustum is placed on -z direction.

* Front boader
  * top : $$t$$
  * bottom : $$b$$
  * right : $$r$$
  * left : $$l$$
  * z-axis distance : $$n$$
* Back boader
  * z-axis distance : $$f$$
  
#### Perspective Projection

$$
\begin{eqnarray}
P = \begin{bmatrix}
\frac{2n}{r-l} & 0 & \frac{r+l}{r-l} & 0 \\
0 & \frac{2n}{t-b} & \frac{t+b}{t-b} & 0 \\
0 & 0 & -\frac{f+n}{f-n} & -\frac{2fn}{f-n} \\
0 & 0 & -1 & 0
\end{bmatrix}
\end{eqnarray}
$$

#### Orthographic Projection

$$
\begin{eqnarray}
P = \begin{bmatrix}
\frac{2}{r-l} & 0 & 0 & -\frac{r+l}{r-l} \\
0 & \frac{2}{t-b} & 0 & -\frac{t+b}{t-b} \\
0 & 0 & -\frac{2}{f-n} & -\frac{f+n}{f-n} \\
0 & 0 & 0 & 1
\end{bmatrix}
\end{eqnarray}
$$
