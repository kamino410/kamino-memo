# 可制御正準形・可観測正準形

## 状態方程式の同値変換（conversion to equivalent model）

任意の状態方程式が与えられているとする。

$$
\begin{eqnarray}
\dot{x} &=& Ax + Bu \\
y &=& Cx
\end{eqnarray}
$$

このとき、任意の正則行列 $$T$$ を用いて

$$
\dot{\bar{x}} = T x
$$

と置くと、先程の状態方程式は

$$
\begin{eqnarray}
\dot{\bar{x}} &=& TAT^{-1} \bar{x} + TBu \\
y &=& CT^{-1} \bar{x}
\end{eqnarray}
$$

となり、$$\bar{A}=TAT^{-1},\ \bar{B} = TB,\ \bar{C} = CT^{-1}$$ をパラメーターとする同値な状態方程式に変換することができる。これを同値変換という。

## 可制御正準形（controllable canonical form）



## 可観測正準形（observable canonical form）

