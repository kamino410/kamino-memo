# マトロイド（matroid）

参考：http://www.ieice-hbkb.org/files/12/12gun_02hen_05.pdf

マトロイドは[ベクトル空間](../../mathematics/linear_algebra/vector_space.md)におけるベクトル集合の一次独立・従属といった概念の組み合わせ論的な側面を抽象化した系である。

## 定義

有限集合 $$E$$ とその部分集合族 $$\mathcal{I} \subset 2^E$$ の組 $$\mathbf{M} = (E,\mathcal{I})$$ が

1. $$\emptyset \in \mathcal{I}$$
2. $$A \subset B \in \mathcal{I} \Rightarrow A \in \mathcal{I}$$
3. $$A,B\in\mathcal{I}, \ |A| < |B|\ \Rightarrow \ ^\exists b \in B \backslash A \ (A \cup \{b\} \in \mathcal{I})$$

を満たすとき、これを**マトロイド**といい、$$E$$ を**台集合（ground set）**、$$\mathcal{I}$$ を**独立集合族**という。
また独立集合族の元 $$A\in \mathcal{I}$$ を**独立集合（independent set）**という。

----

条件1は空集合を含むことを示している。

条件2は $$\mathcal{I}$$ に含まれる集合の冪集合も $$\mathcal{I}$$ に含まれることを示している。
例えば $$\{1,2,3\} \in \mathcal{I}$$ なら $$\{\emptyset,\{1\},\{2\},\{3\},\{1,2\},\{2,3\},\{1,3\},\{1,2,3\}\} \subset \mathcal{I}$$ である。

条件3は $$\mathcal{I}$$ から要素数の異なる2つの元を選び出すと、要素数の大きい方にしか含まれていない元（要素）のどれかを選んで要素数の小さい方に追加してできる集合も $$\mathcal{I}$$ に含まれていることを示している。
例えば $$\{\{1\}, \{1,2,3\} \} \subset \mathcal{I}$$ なら $$\{1,2\},\{1,3\}$$ のどちらかが $$\mathcal{I}$$ に含まれていなければならない。

----

また、$$\mathcal{I}$$ に選ばれなかった部分集合 $$A \in 2^E \backslash \mathcal{I}$$ を**従属集合**という。

## 基（base）

独立集合族 $$\mathcal{I}$$ の中で包含関係で極大であるものを**基**といい、基の集合 $$\mathcal{B}$$ を**基族**という。
上記の条件2より、ある $$\mathcal{I}$$ のすべての基の要素数は一致するのは明らかである。
基の要素数 $$n$$ をマトロイド $$\mathbf{M}$$ の**階数（rank）**という。

マトロイド $$\mathbf{M}$$ の基族 $$\mathcal{B} = \{B_1, \cdots, B_n\}$$ がわかれば、各基の冪集合の和集合を取ることで独立集合族を $$\mathcal{I} = \bigcup_{i=1}^n 2^{B_i}$$ のように表せる。
この意味でマトロイドの「基」と呼んでいる。

----

例えばマトロイド $$\mathbf{M} = (E,\mathcal{I})$$ が $$E = \{1,2,3\}, \ \mathcal{I} = \{\{1\},\{2\},\{3\},\{1,2\},\{2,3\},\{1,3\}\}$$ であるとき、基族は $$\{\{1,2\},\{2,3\},\{1,3\}\}$$ であり、階数は $$2$$ である。

## 基族に対する定理

マトロイドの定義に従えば、基族であるための必要十分条件は次の2つの条件が成立することである。

1. $$\mathcal{B}\neq \emptyset$$
2. $$A,B \in \mathcal{B}, \ b \in A \backslash B \ \Rightarrow \ ^\exists e \in B \backslash A \ ((A\backslash\{b\}) \cup \{e\} \in \mathcal{B})$$

----

マトロイドの定義を変形していけば導ける。

## 階数関数

任意の部分集合 $$X \subset E$$ に対してマトロイドの**階数関数** $$\rho:e^E \rightarrow \mathbb{Z}$$ を次のように定義する。

$$
\rho(X) = \max \{|I|\ | \ I\subset X, I \in \mathcal{I}\}
$$

この関数は次のような性質を満たす。

1. $$\rho(\emptyset) = 0$$
2. $$^\forall X \subset E \ (\rho(X)\leq |X|)$$
3. $$X \subset Y \Rightarrow \rho(X)\leq \rho(Y)$$
4. $$^\forall X,Y \subset E \ (\rho(X)+\rho(Y) \geq \rho(X\cap Y) + \rho(X\cup Y))$$

特に4は**劣モジュラ性（submodularity）**と呼ばれる性質であり、マトロイドに関する効率的なアルゴリズムの存在に深く関与している。

## サーキット（circuit）

従属集合のうち包含関係で極小のものを**サーキット**といい、$$\mathcal{C}$$ で表す。

サーキットは次の性質を満たす。

1. $$\emptyset \notin \mathcal{C}$$
2. $$A,B \in \mathcal{C}, \ A\subset B \ \Rightarrow \ A = B$$
3. $$A,B \in \mathcal{C}, \ j \in A \cap B \ \Rightarrow \ ^\exists C \in \mathcal{C} \ (C \subset (A \cup B) \backslash \{j\})$$

## 閉包関数（closure function）

任意の部分集合 $$X \subset E$$ に対して

$$
\mathrm{cl}(X) = \{ j \ | \ \rho(X) = \rho(X \cup \{j\})\}
$$

と定義される関数を**閉包関数**という。

閉包関数は次の性質を満たす。

1. $$^\forall B \in \mathcal{B} \ (\mathrm{cl}(B) = E)$$
2. $$^\forall I \in \mathcal{I} \ ^\forall j \in (\mathrm{cl}(I)-I) \ (I \cup \{j\} \in 2^E \backslash \mathcal{I})$$
