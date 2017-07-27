# 級数（series）

$$K$$ 上の値を順に並べて $$\{a_n\} \ \ (n=1,2,\cdots)$$ としたものを**数列（sequence）**という。

数列の部分和 $$S_n = \sum_{i=1}^n a_i$$ を**第 $$n$$ 部分和**という。
$$n\rightarrow \infty$$ としたときの和を**級数**といい、$$\sum a_n$$ で表す。

## 収束性

$$S_n$$ が $$n \rightarrow \infty$$ で収束するとき、級数 $$\sum a_n$$ は収束するという。

### 性質

$$\sum a_n, \sum b_n$$ が収束するなら次の性質が成り立つ。

* $$\sum (a_n + b_n)$$ は $$\sum a_n + \sum b_n$$ に収束する
* $$\sum ca_n\ \ (c\in K)$$ は $$c \sum a_n$$ に収束する

### コーシーの収束判定法

数列の収束性は次の性質を検証することで確かめられる。

<center>
数列 $$\{a_n\}$$ が収束する　⇔　$$^\forall \varepsilon > 0 \ ^\exists N \in \mathbb{N} \ (m,n\geq N \rightarrow ||a_m - a_n|| < \varepsilon)$$<br>⇔　$$\sum_{n\rightarrow \infty}a_n$$ のとき $$a_n \rightarrow 0$$
</center>

この性質を満たす数列を**コーシー列（Cauchy sequence）**・**基本列（fundamental sequence）**という。
