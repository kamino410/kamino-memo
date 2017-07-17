# 確率・確率空間

## 定義

### 可測空間（measurable space）

空でない集合 $$\Omega$$ とその完全加法族 $$\mathscr{A}$$ の組 $$(\Omega, \mathscr{A})$$ を**可測空間**という。

### 確率空間（probability space）

可測空間に対して、$$\mathscr{A}$$ 上で定義され $$P(\Omega)=1$$ を満たす測度を**確率測度（probability measure）** $$P$$ といい、これを加えて $$(\Omega, \mathscr{A}, P)$$ としたものを**確率空間**という。

確率空間は、ある偶然現象について生じうる事象とそれぞれの生起確率をまとめたものである。

### コルモゴロフの公理

確率測度の定義は、次のようなコルモゴロフの公理の形で示すことができる。

1. すべての事象の生じる確率は $$0 \sim 1$$ の範囲になる
    * $$\forall A \in \mathscr{A} (0 \leq P(A) \leq 1)$$
2. 全事象 $$S$$ が生じる確率は1である
    * $$P(S) = 1$$
3. 有限個の排反事象に関する和の法則が成立する
    * $$\forall A_1 \in \mathscr{A} \ \forall A_2 \in \mathscr{A} (A_1 \neq A_2 \rightarrow A_1 \cap A_2 = \emptyset) \rightarrow P\left(\bigcup_{i=1}^\infty A_i\right) = \sum_{i=1}^\infty P(A_i)$$
