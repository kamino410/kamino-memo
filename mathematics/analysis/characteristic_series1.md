# 特殊な級数1

## 正項級数（positive term series）

## 定義

各項が正である級数 $$\sum a_n \ (a_i > 0)$$ を**正項級数**という。

### 比較判定法による収束判定

正項級数 $$\sum a_n, \sum b_n$$ について、

$$
^\exists n_0 > 0 \ ^\exists K > 0 \ ^\forall n > n_0\ (a_n \leq Kb_n)
$$

が成立するとき、次の性質を満たす。

* $$\sum b_n$$ が収束する　⇒　$$\sum a_n$$ も収束する
* $$\sum a_n$$ が発散する　⇒　$$\sum b_n$$ も発散する

これはある $$n_0$$ 以降の項について常に $$a_n \leq Kb_n$$ すなわち $$a_n = O(b_n)$$（[ランダウの記号](limit_continuity.md#ランダウの記号（Landau-symbol）)）であるときの性質を利用したものである。

発散・収束を調べたい正項級数があるとき、発散・収束の仕方がわかっている級数を用意して比較すればよいということを示している。

### コーシーの判定法による収束判定

正項級数 $$\sum a_n$$ について、

$$
\lim_{n\rightarrow \infty} \ ^n\sqrt{a_n} = r
$$

が存在するとき、次の性質を満たす。

* $$0 \leq r < 1$$　⇒　$$\sum a_n$$ は収束する
* $$1 < r \leq \infty$$　⇒　$$\sum a_n$$ は発散する

### ダランベールの判定法による収束判定

正項級数 $$\sum a_n$$ について、

$$
\lim_{n\rightarrow \infty} \frac{a_{n+1}}{a_n} = r
$$

が存在するとき、次の性質を満たす。

* $$0 \leq r < 1$$　⇒　$$\sum a_n$$ は収束する
* $$1 < r \leq \infty$$　⇒　$$\sum a_n$$ は発散する

## 交代級数（alternating series）

### 定義

隣り合う項がそれぞれ異符号であるような級数 $$\sum a_n = \sum(-1)^{n-i}b_n \ \ (b_n > 0, i \in \{0,1\})$$ を**交代級数**という。

### ライプニッツの定理

交代級数 $$\sum a_n = \sum(-1)^{n-i}b_n \ \ (b_n > 0, i \in \{0,1\})$$ について、次の性質が成り立つ。

<center>
$$\{b_n\}$$ が減少数列で $$n\rightarrow \infty$$ のとき $$b_n \rightarrow 0$$<br />⇒　交代級数 $$\sum a_n$$ は収束する
</center><br />
