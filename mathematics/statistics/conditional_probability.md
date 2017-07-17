# 条件付き確率（conditional probability）

## 定義

### 条件付き確率

確率空間 $$(\Omega, \mathscr{A}, P)$$ において、事象 $$A,B \in \mathscr{A} \ (P(B)>0)$$ が与えられているとき、以下で定義される実数値関数は確率測度となる。

$$
P(A|B) = \frac{P(A\cap B)}{P(B)}
$$

これを事象 $$B$$ が起きたという条件下での事象 $$A$$ の**条件付き確率**という。

## 基本的な性質

$$A,B \in \mathscr{A},\ \ P(A),P(B) > 0$$ について以下が成立する。

1. $$P(A\cap B) = P(A)P(B|A) = P(B)P(A|B)$$ （乗法定理）
2. $$P(A|B) = P(A) \rightarrow P(B|A) = P(B)$$
3. $$P(A\cap B) \leq P(B|A), \ P(A \cap B) \leq P(A|B)$$

## 全確率の定理

$$A_i, B \in \mathscr{A} \ (i = 1,2, \cdots, n)$$ について、$$\bigcup_{i=1}^n A_i = \Omega,\ A_i \cap A_j = \phi \ (i \neq j)$$ が成り立ち、$$P(A_i) > 0$$ であるとき以下が成り立つ。

$$
P(B) = \sum_{i=1}^n P(A_i)P(B|A_i)
$$

## ベイズの定理（Bayes theorem）

$$A_i,B \in \mathscr{A} \ (i=1,2,\cdots,n)$$ について、$$\bigcup_{i=1}^n A_i = \Omega,\ A_i \cap A_j = \phi \ (i \neq j)$$ が成り立ち、$$P(A_i), \ P(B) > 0$$ であるとき以下が成り立つ。

$$
P(A_j|B) = \frac{P(A_j)P(B|A_j)}{\sum_{i=1}^n P(A_i)P(B|A_i)} \ \ \ (j = 1,2,\cdots,n)
$$
