# 古典命題論理（classical propositional logic）

真偽が定まる記述のことを**命題（proposition）**という。

古典論理学は命題間の関係を記述する分野である。
命題変数の関係の記述には**命題論理式（論理式）**を用いる。

## 命題論理式の構成要素

### 命題定数

「真である」という命題を $$\top$$、「偽である」という命題を $$\bot$$ と表す。

### 命題変数

任意の命題を代表する記号を**命題変数**という。

### 命題演算子

1. $$p \vee q$$（論理和）
    * $$p,q$$ いずれもが偽のとき $$p \vee q$$ は偽、それ以外は真
2. $$p \wedge q$$（論理積）
    * $$p,q$$ いずれもが真のとき $$p \wedge q$$ は真、それ以外は偽
3. $$\neg p$$（否定）
    * $$p$$ が真（偽）なら $$\neg p$$ は偽（真）
4. $$p \rightarrow q$$（含意）
    * $$p$$ が真で $$q$$ が偽のとき $$p \rightarrow q$$ は偽、それ以外は真
5. $$p \equiv q$$（同値）
    * $$p,q$$ の真偽が一致するとき真、それ以外は偽

## 論理式の分類

### 恒真式（tautology）

論理式に含まれる命題変数がどのような値を取っても常に値が真になる論理式。$$A$$ が恒真式であることを $$\models A$$ と表す。

### 充足可能（satisfiable）

論理式に含まれる命題変数の値をうまく選べば値が真になる論理式。

### 充足不可能（unsatisfiable）

論理式に含まれる命題変数がどのような値を取っても常に値が偽になる論理式。

## 恒真式の例

任意の命題に対して成立する恒真式は、与えられた命題の真偽を判定する際に定理として利用できる。

1. $$A \wedge A \equiv A, \ A \vee A \equiv A$$（冪等性）
2. $$(A \wedge B) \wedge C \equiv A \wedge (B \wedge C)$$<br>$$(A \vee B) \vee C \equiv A \vee (B \vee C)$$（結合律）
3. $$A \wedge B \equiv B \wedge A, \ A \vee B \equiv B \vee A$$（交換律）
4. $$A \wedge (A \vee B) \equiv A, \ A \vee (A \wedge B) \equiv A$$（吸収律）
5. $$A \wedge (B \wedge C) \equiv (A \wedge B) \vee (A \wedge C)$$<br>$$A \vee (B \wedge C) \equiv (A \vee B) \wedge (A \vee C)$$（分配律）
6. $$\neg \neg A \equiv A$$（2重否定律）
7. $$\neg (A \vee B) \equiv \neg A \wedge \neg B$$<br>$$\neg(A \wedge B) \equiv \neg A \vee \neg B$$（ド・モルガンの法則）
8. $$A \rightarrow B \equiv \neg A \vee B$$
9. $$A \wedge \neg A \equiv \bot, \ A \vee \neg A \equiv \top$$（排中律）
10. $$A \vee \bot \equiv A, \ A \vee \top \equiv \top$$
11. $$A \wedge \top \equiv A, \ A \wedge \bot \equiv \bot$$
12. $$A \wedge (A \rightarrow B) \rightarrow B$$（前件肯定）
13. $$\neg B \wedge (A \rightarrow B) \rightarrow \neg A$$（後件否定）
14. $$(A \equiv B) \equiv ((A \rightarrow B) \wedge (B \rightarrow A))$$

## 双対原理（duality principle）

次の組み合わせはそれぞれ**双対**の関係であるという。

1. $$\wedge, \vee$$
2. $$\top, \bot$$
3. $$\neg A, A$$

上記以外の命題定数・演算子を含まない論理式を $$A$$ とすると、それらを双対で置き換えた論理式 $$A^*$$ を**双対式**という。

双対式について成立する次の定理を**双対原理**という。

1. $$\models (A \rightarrow B) \rightarrow (B^* \rightarrow A^*)$$
2. $$\models (A \equiv B) \rightarrow (A^* \equiv B^*)$$
