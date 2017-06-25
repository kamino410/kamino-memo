# 特殊な行列

## 正方行列（square matrix）

サイズが $$n \times n$$ である行列。

$$\begin{vmatrix}a_{11} & \cdots & a_{1n} \\ \vdots & \ddots & \vdots \\ a_{n1} & \cdots & a_{nn} \end{vmatrix}$$

## 対称行列（symmetric matrix）

$$A = A^t$$ を満たす行列。

$$\begin{vmatrix}a_{11} & \cdots & a_{1n} \\ \vdots & \ddots & \vdots \\ a_{n1} & \cdots & a_{nn} \end{vmatrix} \ \ \ \ (a_{ij} = a_{ji})$$

$$a_{ij} = a_{ji}$$

## 対角行列（diagonal matrix）

正方行列かつ対角成分以外が0である行列。

$$\begin{vmatrix}a_{11} & 0 & \cdots & \cdots & 0 \\ 0 & a_{22} & \ddots & \ddots & \vdots \\ \vdots & \ddots & \ddots & \ddots & \vdots \\ \vdots & \ddots & \ddots & a_{n-1,n-1} & 0 \\ 0 & \cdots & \cdots & 0 & a_{nn} \end{vmatrix}$$

$$a_{ij} = \left \{ \begin{matrix} \alpha_{ij} & (i=j) \\ 0 & else \end{matrix} \right.$$

## 三角行列（triangular matrix）

正方行列かつ対角成分より右上もしくは左下側の成分がすべて0の行列。

$$\begin{vmatrix}a_{11} & a_{12} & \cdots & \cdots & a_{1n} \\ 0 & a_{22} & \ddots & \ddots & \vdots \\ \vdots & \ddots & \ddots & \ddots & \vdots \\ \vdots & \ddots & \ddots & a_{n-1,n-1} & a_{n-1,n} \\ 0 & \cdots & \cdots & 0 & a_{nn} \end{vmatrix}$$

$$a_{ij} = \left \{ \begin{matrix}\alpha_{ij} & (i \leq j) \\ 0 & else \end{matrix}\right.$$

## 正則行列（regular matrix）

全ての列・行ベクトルが一次独立（線形独立）な行列。同値の条件として、逆行列が存在する行列でもある。詳しい性質については[階数・逆行列](inverse_matrix.md)を参照。

$$A^{-1}A = I$$
