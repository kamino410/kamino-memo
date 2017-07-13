# 素朴集合論の集合演算（native set theory）

[集合の定義](set.md)に基づく、単なるものの集まりとしての集合の性質について述べられたものである。

## 基本となる記号

1. 集合 $$A, B, \cdots$$
2. 要素 $$x, y, \cdots$$
3. 包含記号 $$A \subset B$$
    * 集合論の部分集合の定義は $$A \subset B \Leftrightarrow \forall x (x \in A \Rightarrow x \in B)$$ とするのが一般的
    * $$A \subsetneq B$$ は**真部分集合**と呼ぶことで区別する

また、暗黙的に次のような記号が使われることが多い。

1. 整数（integers）の集合 $$Z$$
2. 有理数（rational numbers）の集合 $$Q$$
3. 実数（real numbers）の集合 $$R$$
4. 複素数（complex numbers）の集合 $$C$$

## 等号の公理

一般に等号 $$=$$ が満たす次のような性質が集合においても成立することを前提として議論を進める。
厳密な定義の例は[ZFC公理系](../axiomatic_set_theory/zfc_set_theory.md)へ。

1. 反射律 $$A = A$$
2. 対称律 $$A=B \Rightarrow B=A$$
3. 推移律 $$(A=B \wedge B=C) \Rightarrow A = C$$

## 和集合・共通部分（積集合）（union / intersection）

### 定義

* 和集合 $$A \cup B := \{x \ | \ x \in A \vee x \in B \}$$
* 共通部分（積集合）$$A \cap B := \{x \ | \ x \in A \wedge x \in B \}$$

### 性質

1. $$A \cup A = A, \ A \cap A = A$$（冪等律）
2. $$A \cup B = B \cup A, \ A \cap B = B \cap A$$（可換律）
3. $$(A\cup B) \cup C = A \cup (B \cup C), \ (A \cap B) \cap C = A \cap (B \cap C)$$（結合律）
4. $$(A \cup B)\cap C = (A \cap C) \cup (B \cap C), \ (A \cap B) \cup C = (A\cup C)\cap(B \cup C)$$（分配律）
5. $$A\cap (A \cup B) = A, \ A \cup(A\cap B) = A$$（吸収律）
1. $$A\cup B \supset A, \ A\cup B \supset B$$
2. $$(C \supset A \wedge C \supset B) \rightarrow C \supset A \cup B$$
3. $$A\cap B \subset A, \ A \cap B \subset B$$
4. $$(C \subset A \wedge C \subset B) \rightarrow C \subset A \cap B$$
5. $$A \subset B \rightarrow ((A \cap B = A) \wedge (A \cup B = B))$$

## 空集合（empty set）

### 定義

$$\emptyset = \{\}$$

### 性質

1. どのような集合にも属する $$\forall A ( \emptyset \in A)$$
2. $$\forall A (A \cap \emptyset = \emptyset)$$
3. $$\forall A (A \cup \emptyset = A)$$

## 補集合（complement）

### 定義

全体集合を $$X$$ として

$$A^c := \{x \in X \ | \ x \notin A\}$$

### 性質

1. $$A \cap A^c = \emptyset$$
2. $$A \cup A^c = X$$
3. $$(A\cup B)^c = A^c \cap B^c, \ (A\cap B)^c = A^c \cup B^c$$（ド・モルガンの法則）

## 集合差（difference）

### 定義

$$A \backslash B := \{x \ | \ x \in A \wedge x \notin B\}$$

### 性質

全体集合を $$X$$ として

1. $$A^c = X \backslash A$$
2. $$A \backslash B = A \cap B^c$$

## 対称差（symmetric difference）

### 定義

$$A \ominus B := (A \backslash B) \cup (B \backslash A)$$

## 直積／デカルト積（direct product / Cartesian product）

### 定義

$$A \times B := \{(x,y) \ | \ x \in A \wedge y \in B\}$$

