# 一般の制約付き最小化問題

次の問題について考える。

$$
\begin{eqnarray}
minimize &\ &f(x) \\
s.t. &\ &
\begin{cases}
\begin{matrix}
G(x) =
\begin{pmatrix}
  g_1(x_1, \dots, x_n) \\
  \vdots \\
  g_l(x_1, \dots, x_n)
\end{pmatrix}
\leq 0 \\
H(x) =
\begin{pmatrix}
  h_1(x_1, \dots, x_n) \\
  \vdots \\
  h_m(x_1, \dots, x_n)
\end{pmatrix}
= 0
\end{matrix} \\ \\
x \in D \subseteq R^n, \ \ \ f:D \rightarrow R, \ \ \ g_i,h_i:D \rightarrow R
\end{cases}
\end{eqnarray}
$$

## 有効制約式

不等式制約条件について、$$g_i(x')=0$$ であるとき、この制約式を $$x'$$ での**有効制約式（active constraint）**という。
以降、$$x'$$ の下での有効制約式を示すインデックスを $$i \in E(x')$$ と表記する。

## 最適性条件

$$x^* $$ において $$f,g$$ は連続1階微分可能かつ2階微分可能であるとする。

### 1次導関数に対する条件

#### 概要

1次導関数に対する条件は大まかに言えば次の形で示される。

<center>
$$x^*$$ が局所的最小解である<br>⇒　（制約想定を満たす　→　$$x^*$$ についてKKT条件を満たすKKT乗数 $$(\lambda, \mu)$$ が存在する）が成立する
</center><br>

つまり、制約想定が満たされる問題でのみKKT条件を最適性条件として利用することができる。

#### 制約想定（constraint qualification）

厳密な制約想定は**Abadieの制約想定**と呼ばれる。
これを示すための前提知識は複雑なのでここでは省略する。

一般的にはAbadieの制約想定の十分条件であるものを用いる。

* 1次独立の制約想定（LICQ）
  * $$\nabla h_i(x^*)\ \ (i = 1, \cdots, m)$$ と $$\nabla g_j(x^*)\ \ ( j\in E(x^*))$$ は一次独立
* Slaterの制約想定
  * $$g_j$$ は凸関数であり、$$g_i(\hat{x}) < 0\ \ (j = 1, \cdots, l)$$ となる $$\hat{x} \in R^n$$ が存在する
* MF（Mangasarian-Fromovitz）の制約想定
  * $$\nabla h_i(x^*) \ \ (i = 1, \cdots, m)$$ が一次独立で $$\nabla h_i(x^*)^T y = 0 \ \ (i=1,\cdots,m), \ \nabla g_j(x^*)^T y < 0 \ \ (j\in E(x^*))$$ を満たす $$y\in R^n$$ が存在する

それぞれの関係は、「LICQ　⇒　MF　⇒　Abadie」、「Slater　⇒　MF」である。

なお、MFの制約想定を不等式制約のみの問題に制限したものをCottleの制約想定という。

* Cottleの制約想定
  * $$\langle \nabla g_j(x^*), y\rangle < 0 \ \ (j \in E(x^*))$$ を満たす $$y \in R^n$$ が存在する


#### KKT条件（Karush-Kuhn-Tucker condition）

次の条件を**KKT条件**という。

$$
\begin{cases}
1: & \nabla f(x^*) + \sum_{i=1}^m \lambda_i \nabla h_i (x^*) + \sum_{j = 1}^l \mu_j \nabla g_j(x^*) = 0 \\
2: & h(x^*) = 0 \\
3: & g_j(x^*) \leq 0, \ \ \mu_j \geq 0, \ \ \mu_j g_j(x^*) = 0 \ \ (j = 1, \cdots, l)
\end{cases}
$$

----

ラグランジュ関数

$$
L(x,\lambda,\mu) = f(x) + \sum_{i=1}^m \lambda_i h_i (x) + \sum_{j = 1}^l \mu_j  g_j(x)
$$

を用いれば次のように書き直すこともできる。

$$
\begin{cases}
1: & \nabla_x L(x^*,\lambda,\mu) = 0 \\
2: & \nabla_\lambda L(x^*,\lambda,\mu) = 0 \\
3: & g_j(x^*) \leq 0, \ \ \mu_j \geq 0, \ \ \mu_j g_j(x^*) = 0 \ \ (j = 1, \cdots, l)
\end{cases}
$$

----

条件1は目的関数 $$f(x)$$ の等高線と制約条件の等高線が接していることを示している。
直感的に言えば、曲面を組み合わせて作った地形の上にボールを転がすとき、重力 $$-\nabla f(x)$$ と曲面から受ける抗力 $$-\lambda_i \nabla h_i(x), -\mu_j \nabla g_j(x)$$ の和が釣り合う点が最も低い場所（局所的最小解）であることを示している。

条件2は等式制約条件を満たすことを示している。
ボールの例で言えば、曲面の上にレールが敷かれており、ボールはそのレールの上だけを転がることができる、ということを示している。

条件3は $$g_j(x)=0$$ もしくは $$\mu_j = 0$$ のどちらかを満たすことを示しており、**相補性条件**と呼ばれる。
これは条件1にて、有効制約式は $$\nabla g_j(x)$$ を考慮し、有効制約式でないものは $$\mu_j = 0$$ とすることで $$\nabla g_j(x)$$ を考慮しないようにすることを示している。
ボールの例で言えば、ボールが最も低い場所にいるときに接していない曲面から受ける抗力は無視する、ということを示している。

----

また、関数の凸性を考慮すれば次の定理が成立する。

<center>
$$f,g_i$$ が凸関数で $$h_i$$ は一次関数、かつ $$(x^*,\lambda^*,\mu^*)$$ がKKT条件を満たす<br>⇒　$$x^*$$ は大域的最小解である
</center><br>

このとき制約想定は不要である。

### 2次導関数に対する必要条件

<center>
$$x^*$$ が局所的最小解かつ $$x^*$$ でLICQが成立する<br>⇒　$$^\forall y \in C(x^*) \ (y^T \nabla^2_{xx} L(x^*,\lambda^*,\mu^*)y \geq 0)$$
</center><br>

### 2次導関数に対する十分条件

<center>
$$(x^*, \lambda^*, \mu^*)$$ がKKT条件を満たし $$^\forall y \in C(x^*) \ (y^T \nabla^2_{xx} L(x^*,\lambda^*,\mu^*)y \geq 0)$$ を満たし、かつ $$\mu_j^* - g_j(x^*) > 0 \ \ (j = 1,\cdots,l)$$ を満たす<br>⇒　$$x^*$$ は狭義の局所的最小解である
</center><br>

ただし、

$$
C(x) = \{ y \ | \ \langle \nabla h_i(x), y \rangle = 0 \ \ (i=1,\cdots,m) \ \wedge \ \langle \nabla g_j(x),y \rangle = 0 \ \ (j \in E(x)) \}
$$

である。
