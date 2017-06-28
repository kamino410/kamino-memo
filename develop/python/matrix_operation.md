# Pythonで行列演算

`numpy.array`と`numpy.matrix`があるが、`numpy.array`を使っている人が多い、というか`numpy.matrix`の存在が空気になりつつある。

## 定義

$$
A = \begin{bmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \\ 7 & 8 & 9 \end{bmatrix}
$$

```py
import numpy as np

A = np.array([[1,2,3],[4,5,6],[7,8,9]])

```

## 加減算

$$
\begin{eqnarray}
A + B &=& \begin{bmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \\ 7 & 8 & 9 \end{bmatrix} + \begin{bmatrix} 1 & 4 & 7 \\ 2 & 5 & 8 \\ 3 & 6 & 9 \end{bmatrix} \\
&=& \begin{bmatrix} 2 & 6 & 10 \\ 6 & 10 & 14 \\ 10 & 14 & 18 \end{bmatrix}
\end{eqnarray}
$$

$$
\begin{eqnarray}
A - B &=& \begin{bmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \\ 7 & 8 & 9 \end{bmatrix} - \begin{bmatrix} 1 & 4 & 7 \\ 2 & 5 & 8 \\ 3 & 6 & 9 \end{bmatrix} \\
&=& \begin{bmatrix} 0 & -2 & -4 \\ 2 & 0 & -2 \\ 4 & 2 & 0 \end{bmatrix}
\end{eqnarray}
$$

```py
import numpy as np

A = np.array([[1,2,3],[4,5,6],[7,8,9]])
B = np.array([[1,4,7],[2,5,8],[3,6,9]])

print(A + B)
print(A - B)

```

## 積

```py
import numpy as np

A = np.array([[1,2,3],[4,5,6],[7,8,9]])
B = np.array([[1,4,7],[2,5,8],[3,6,9]])

print(np.dot(A, B))
# A*B にすると m_ij = a_ij * b_ij の行列ができてしまう

```

## 逆行列

$$A^{-1}$$を求める時は`numpy.linalg.inv(A)`を使う。

ただし、求めた逆行列を使って$$A^{-1}b$$を求めたいときは`numpy.linalg.solve(A,b)`を使った方が高速になる模様。

参考：http://d.hatena.ne.jp/sleepy_yoshi/20120513/p1

```py
import numpy as np

A = np.array([[1,1,-1],[-2,0,1],[0,2,1]])
b = np.array([1,2,3])

print(np.linalg.inv(A))
print(np.linalg.solve(A, b))

```
