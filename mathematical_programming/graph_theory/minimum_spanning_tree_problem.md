# 最小木問題（minimum spanning tree problem）

## 問題

連結な無向グラフ $$G = (V,E)$$ と各辺の重み $$w:E \rightarrow \mathbb{R}$$ があるとき、枝の重みが最小となる全域木を求める問題を**最小木問題**という。
また、このときの全域木を**最小木**と呼ぶ。

## 全域木の性質

$$G$$ の全域木 $$T=(V,F)$$ について、以下は同値な条件である。

1. $$T = (V,F)$$ は木である
    * 全域木の定義
2. $$T = (V,F)$$ は閉路を含まないが、$$F$$ に属さない辺 $$e \in E \backslash F$$ を1本加えるとただ1つの閉路を持つ
    * この閉路を**基本閉路（fundamental cycle）**といい、その辺集合を $$C(T|e)$$ と表す
3. $$T = (V,F)$$ は連結であるが、任意の辺を1本取り除くと連結でなくなる
    * 連結でなくなった2つの木の頂点同士を結ぶような辺の集合を**基本カット（fundamental cut）**といい $$C^*(T|e)$$ と表す（取り除いた辺も含まれる）

これを利用すれば次のような操作で別の全域木を得ることができる。

1. 基本閉路の任意の辺 $$e' \in C(T|e)$$ に対し、$$F \cup \{e\} \backslash \{e'\}$$ の誘導する部分グラフも全域木である
2. 基本カットの任意の辺 $$e' \in C^*(T|e)$$ に対し、$$F \backslash \{e\} \cup \{e'\}$$ が誘導する部分グラフも全域木である

## 閉路最適性条件

基本閉路に注目したときの最適性条件は次のように与えられる。

<center>
連結グラフ $$G = (V,E)$$ 上の全域木 $$T$$ が最小木である<br />⇔　任意の辺 $$^\forall e \in E \backslash F,\ ^\forall a' \in C(T|e) \ (w(a) \geq w(a'))$$
</center><br />

すなわち、どの基本閉路を追加しても総コストがこれ以上小さくならないことが最適性条件である。

## カット最適性条件

基本カットに注目したときの最適性条件は次のように与えられる。

<center>
連結グラフ $$G = (V,E)$$ 上の全域木 $$T$$ が最小木である<br />⇔　$$^\forall e \in F, \ ^\forall e' \in C^*(T|e) \ (w(e)\leq w(e'))$$
</center><br />

すなわち、どの辺を削除して基本カットの1本につなぎ替えるにしても総コストがこれ以上小さくならないことが最適性条件である。

## 最小木アルゴリズム

最小木問題を解くアルゴリズムとしては[Prim法](../../computer_science/algorithm/minimum_spanning_tree_problem.md#prim法)と[Kruskal法](../../computer_science/algorithm/minimum_spanning_tree_problem.md#kruskal法)が有名。
