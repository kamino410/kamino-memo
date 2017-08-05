# 単一始点最短経路問題（single source shortest path problem）

## 定義

有向グラフ $$G=(V,E)$$ と各枝の長さ $$l:E \rightarrow \mathbb{R}$$ と始点 $$s\in V$$ が定まったもとで、$$s$$ から到達可能な各頂点への最短路とその長さを、もし負閉路が存在して無限に小さな経路が存在するときはその負閉路の1つを出力する問題。

## 最短路長に関する三角不等式

有向グラフ $$G=(V,E)$$ において、$$s$$ から各頂点 $$v\in V$$ までのある有向路長（有向路が存在しない場所も長さ $$+\infty$$ の有向路として考える）を $$d(v)$$ とする。
このとき以下の定理が成立する。

<center>
すべての頂点について $$d(v)$$ が始点 $$s$$ からの最短路長である<br />⇔　$$^\forall e \in E\ (d(\partial^- e) \leq d(\partial^+ e)+l(e))$$
</center><br />

この式は**最短路長に関する三角不等式**と呼ばれる。
この定理をある有向路 $$P_v$$ に限って適用すれば、次の系を得る。
ただし、頂点 $$v$$ までの最短路長を $$d^*(v)$$ とする。

<center>
ある有向路が始点 $$s$$ から終点 $$v$$ までの最短路である<br />⇔　$$^\forall e \in E(P_v) \ (d^*(\partial^- e) = d^*(\partial^+ e)+l(e))$$
</center><br />

すなわち、その有効路に含まれるすべての辺で三角不等式が等号で成り立てば、有向路は最短路であることを示している。

この定理を始点から再帰的に適用していくことで問題を解くことができる。

## 解法

単一始点最短経路問題の解法として[ダイクストラ法](../../computer_science/algorithm/shortest_path.md#ダイクストラ（dijkstra）法)と[ベルマンフォード法](../../computer_science/algorithm/shortest_path.md#ベルマンフォード（bellman-ford）法)がある。
これらの詳細はアルゴリズムの項目で解説する。