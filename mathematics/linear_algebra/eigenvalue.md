# 固有値問題（eigen）

## 固有値・固有ベクトル（eigenvalue, eigenvector）

任意の正方行列 $$A$$ に対して

$$
Ax = \lambda x \ \ \ (x \neq 0)
$$

を満たすような $$\lambda, x$$ の組み合わせ（**固有対**）を求める問題を**固有値問題**という。
またこのときの $$\lambda$$ を**固有値**、$$x$$ を $$\lambda$$ に対する**固有ベクトル**という。

## 解法

$$
\begin{eqnarray}
Ax &=& \lambda x \\
(A-\lambda I)x &=& 0
\end{eqnarray}
$$

ここで $$(A-\lambda I)$$ が正則であるとすれば、

$$
\begin{eqnarray}
(A-\lambda I)^{-1}(A-\lambda I)x &=& 0 \\
x &=& 0
\end{eqnarray}
$$

となり、固有対が存在しないことになる。ここから次の定理が導かれる。

<center>
$$\det [A - \lambda I] = 0$$　⇔　固有対が存在する
</center>

左辺の式を $$A$$ の**特性方程式**と呼び、これを解くことで固有値が得られる。

## 重複度・固有値の数

特性方程式に重解が含まれるとき、重複した解の数を $$d$$ として、対応する固有対を**重複度 $$d$$ の固有対** という。たとえば2重解に対応する固有対の重複度は2である。

重複度を考慮した固有対の数は行列の次数 $$n$$ と等しくなる。

## 固有ベクトルの一次独立性

任意の行列 $$A$$ の固有対は次の定理を満たす（一次独立の定義と特性方程式を合わせれば容易に証明できる）。

<center>
異なる固有値の固有ベクトルは互いに一次独立である
</center>

## 対角和・行列式と固有値

[ジョルダン標準形](diagonalization.md)を考慮すれば次のような関係が導ける。

$$
\begin{eqnarray}
\mathscr{tr} A &=& \sum_{i=1}^n \lambda_i \\
\det A &=& \prod_{i=1}^n \lambda_i
\end{eqnarray}
$$