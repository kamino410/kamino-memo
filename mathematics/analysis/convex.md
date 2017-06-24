# 凸集合・凸関数

## 凸集合

集合$$D$$（$$\subset R^n$$）について、内包する2点同士を結ぶ **凸結合** がすべて$$D$$に含まれているとき、$$D$$は **凸集合** であるという。

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

領域$$D$$で定義された関数 $$f:R^n \rightarrow R$$ が領域内の任意の2点 $$u,v\in D$$ について常に

$$
f((1-\lambda)u +\lambda v) \leq (1-\lambda)f(u) + \lambda f(v)
$$

が成立する時、$$f$$ は$$D$$上で **凸関数（convex function）** であるという。
また、不等号が $$<$$ であるときを特に **狭義凸関数（strictly convex function）** であるという。

### 性質

