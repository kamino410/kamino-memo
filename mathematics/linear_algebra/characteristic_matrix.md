# 特殊な行列

## 実行列・エルミート行列（real-valued matrix / Hermitian matrix）

成分が実数値を取る行列を**実行列**、複素数値を取る行列を**エルミート行列**という。

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

## 正定値行列・負定値行列（positive definite matrix / negative definite matrix）

実正方行列かつ $$^\forall v \in R^n \ (v^T A v > 0)$$ を満たす行列を**正定値行列**という。
エルミート正方行列については $$^\forall v \in R^n (\mathrm{Re}(v^* A v) > 0 \wedge \mathrm{Im}(v^* A v) = 0)$$ を満たすものをいう（ただし $$v^*$$ は $$v$$ の共軛転置行列）。

また不等式が $$\geq$$ になるとき、**半正定値行列（positive-semidefinite matrix）**・**非負定値行列（nonnegative-definite matrix）**という。

不等号が逆転したものを**負定値業列**・**半不定地行列**・**非正定値行列**という。
