# 凸集合・凸関数

## 凸集合

集合$$D$$（$$\subseteq R^n$$）について、内包する2点同士を結ぶ **凸結合** がすべて$$D$$に含まれているとき、$$D$$は **凸集合** であるという。

条件を数式にすると

$$
u,v\in D\\
S = \{(1-\lambda)u+\lambda v \ | \ 0 \leq \lambda \leq 1\}
$$

について

$$
S \subset D
$$

が成立すること。

## 凸関数

### 定義

凸集合$$D$$における関数 $$f:D \rightarrow R$$ が領域内の任意の2点 $$u,v\in D$$ について常に

$$
f((1-\lambda)u +\lambda v) \leq (1-\lambda)f(u) + \lambda f(v) \ \ \ (0 \leq \lambda \leq 1)
$$

が成立する時、$$f$$ は$$D$$上で **凸関数（convex function）** であるという。特に

$$
f((1-\lambda)u +\lambda v) \leq (1-\lambda)f(u) + \lambda f(v) \ \ \ (0 < \lambda < 1)
$$

であるときを **狭義（強意）の凸関数（strictly convex function）** であるという。

また、$$-f$$が凸関数であるとき、$$f$$は **凹関数** であるという。

### 性質

#### その1

$$f$$が凸関数　⇔　エピグラフ $$\mathscr{epi} f$$ が凸集合

>エピグラフ

>ある関数を描画した$$n+1$$次元のグラフにおける関数より上側の領域のこと。
>$$
\mathscr{epi}f=\{(x,r)\ | \ x\in D, r \geq f(x), r \in R\} \subseteq R^{n+1}
$$

#### その2

$$D$$が開凸集合であり、その内部で$$f$$が連続微分可能であるとき、

$$f$$が凸関数　⇔　次のいずれかが成立する

1. $$f(v) \geq f(u) + \nabla f(x)^T (v-u)$$
1. $$(\nabla f(v)-\nabla f(u))^T (v-u)\geq0$$

上の性質を$$\nabla f$$の単調性という。
