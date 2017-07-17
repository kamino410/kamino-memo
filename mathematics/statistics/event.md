# 標本空間と事象

## 定義

### 標本空間・全事象（sample space / whole event）

偶然現象を試行したとき起こりうるすべての結果の集合を**標本空間**または**全事象**といい、$$\Omega$$ で表す。

### 標本点（sample point）

標本空間の元、つまり試行によって起こりうる結果それぞれを**標本点**という。

### 事象（event）

標本空間の部分集合を**事象**という。
またただ1つの標本点からなる事象を**根源事象（elementary event）**といい、標本点を1つも含まない事象を**空事象**という。

### 和事象・積事象・余事象（union of events / intersection of events / complement event）

事象 $$A,B$$ の和集合 $$A \cup B$$・積集合 $$A \cap B$$・補集合 $$A^c$$ も事象となり、それぞれを**和事象**・**積事象**・**余事象**という。

### 排反事象

事象 $$A,B$$ に対して $$A \cap B = \emptyset$$ が成り立つとき、事象 $$A,B$$ は互いに排反である（mutually exclusive / disjoint）という。

## 完全加法族

空でない集合 $$\Omega$$ の部分集合の族 $$\mathscr{A}$$ が次の条件を満たすとき、**加法族（additive class）**という。

1. $$\Omega \in \mathscr{A}$$
2. $$A \in \mathscr{A} \rightarrow A^c \in \mathscr{A}$$
3. $$A \in \mathscr{A} \wedge B \in \mathscr{A} \rightarrow $$A\cup B \in \mathscr{A}$$

また3つ目の条件を

* $$A_i \in \mathscr{A} \rightarrow \bigcup_{i=1}^\infty A_i \in \mathscr{A} \  (i=1,2,\cdots)$$

に置き換えたものを**完全加法族（complete additive class）**または **$$\sigma$$-加法族**という。

完全加法族は有限回の合併 $$\cup$$、交叉 $$\cap$$、補演算$$\ ^c$$ について閉じており、確率を定義できる事象全体を為す族として解釈できる。
