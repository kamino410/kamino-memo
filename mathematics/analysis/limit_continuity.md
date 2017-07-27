# 関数の極限と連続性

## 関数の定義

実数全体の集合 $$R$$ の部分集合 $$D \subset R$$ において、$$D$$ の全ての元を $$R$$ 上に移すような写像 $$f:D \rightarrow R$$ が存在するとき、$$f(x)$$ を $$D$$ を**定義域**とする**関数**という。
また、$$f$$ の像を**値域**という。

以下では定義域 $$D$$ が区間か区間の和になっているものだけを考える。

## 境界点

$$D$$ 内の数列 $$\{x_n\}$$ と $$D$$ 外の数列 $$\{y_n\}$$ について

$$
\lim_{n\rightarrow \infty} x_n = \lim_{n \rightarrow \infty} y_n = x_0
$$

を満たすようなものが存在するとき、点 $$x_0$$ は $$D$$ の**境界点**であるという。

## 極限値（limit）

定義域 $$D$$ で定義された関数 $$f(x)$$ について、領域 $$D$$ 内の $$x$$ が $$D$$ 内のある点または境界点 $$x_0$$ に漸近するとき、

$$
\lim_{x \rightarrow x_0} f(x) = a
$$

が成立するなら、$$a$$ は $$x_0$$ における $$f(x)$$ の**極限値**であるという。

特に $$x>x_0$$ の範囲から近づくときを**右極限**、$$x<x_0$$ の範囲から近づくときを**左極限**といい、次のように表す。

$$
\lim_{x\rightarrow x_0+0} f(x), \ \ \ \lim_{x\rightarrow x_0-0}f(x)
$$

また、$$a=\infty, -\infty$$ となることを**無限大に発散する**という。

### $$\varepsilon - \delta$$ 論法

極限値の厳密な定義は $$\varepsilon - \delta$$ 論法によって示される。

$$
^\forall \varepsilon > 0\ ^\exists \delta > 0\ ((0<|x-x_0|<\delta) \wedge (x \in D) \rightarrow |f(x)-a|<\varepsilon)
$$

つまり任意の $$\varepsilon$$ が定まれば、$$f(x)$$ と $$a$$ の差がある $$\delta$$ より小さくなる（漸近する）ことを述べている。

### 極限値の性質

$$f(x), g(x)$$ が $$x = x_0$$ の周辺で定義されており、$$\lim_{x\rightarrow x_0}f(x)=\alpha$$、$$\lim_{x\rightarrow x_0}g(x)=\beta$$ ならば以下が成り立つ。

* $$\lim_{x\rightarrow x_0} (f(x)+g(x)) = \alpha + \beta$$
* $$\lim_{x\rightarrow x_0} cf(x) = c\alpha$$
* $$\lim_{x\rightarrow x_0} f(x)g(x) = \alpha \beta$$
* $$\lim_{x\rightarrow x_0} \frac{f(x)}{g(x)} = \frac{\alpha}{\beta}\ \ (\beta \neq 0)$$

また、$$f(x), g(x), h(x)$$ が領域 $$D$$ で定義される関数で、$$D$$ 内のある点または境界点 $$x_0$$ と領域 $$D$$ 内の $$x\neq x_0$$ に関して $$f(x) \leq g(x) \leq h(x)$$ が満たされるとき、以下の性質が成立する。

* $$x_0$$ について $$f(x), g(x)$$ に極限が存在する　⇒　$$\lim_{x\rightarrow x_0} f(x) \leq \lim_{x \rightarrow x_0}g(x)$$
* $$\lim_{x\rightarrow x_0} f(x) = \lim_{x\rightarrow x_0}g(x)$$　⇒　$$\lim_{x\rightarrow x_0} f(x) = \lim_{x\rightarrow x_0}h(x) = \lim_{x\rightarrow x_0} g(x)$$

## 連続性（continuity）

関数 $$f(x)$$ が定義域 $$D$$ 内の全ての点 $$x_0$$ で

$$
\lim_{x \rightarrow x_0} f(x) = f(x_0)
$$

を満たすとき、$$f(x)$$ は $$x_0$$ において**連続**であるという。
また、$$D$$ 上の任意の点で $$f(x)$$ が連続なら $$f(x)$$ は $$D$$ 上の**連続関数**であるという。

### 連続性の性質

$$f(x),g(x)$$ が同じ定義域を持つ連続関数なら次の性質を満たす。

* $$f(x)+g(x)$$ も連続関数
* $$cf(x) \ \ (c \in R)$$ も連続関数
* $$f(x)g(x)$$ も連続関数
* $$\frac{f(x)}{g(x)} \ \ (g(x)\neq 0)$$ も連続関数

また、$$f(x)$$ の値域が $$g(x)$$ の定義域に含まれるとき、

* $$g(f(x))$$ も連続

## 連続関数の性質

### 有界性

関数 $$f(x)$$ が定義域 $$D$$ で連続で

$$
^\exists k \in R \ ^\forall x \in D\ (f(x)\leq k)
$$

を満たすとき、$$f(x)$$ は**上に有界**であるといい、

$$
^\exists k \in R \ ^\forall x \in D\ (f(x)\geq k)
$$

を満たすとき、$$f(x)$$ は**下に有界**であるという。

上にも下にも有界であるとき、単に**有界**であるという。

### 単調増加性

関数 $$f(x)$$ が定義域 $$D$$ で連続であるとする。

* $$x < y \rightarrow f(x) \leq f(y)$$　⇒　$$f(x)$$ は**単調増加関数**である
* $$x < y \rightarrow f(x) < f(y)$$　⇒　$$f(x)$$ は**狭義の単調増加関数**である
* $$x < y \rightarrow f(x) \geq f(y)$$　⇒　$$f(x)$$ は**単調減少関数**である
* $$x < y \rightarrow f(x) > f(y)$$　⇒　$$f(x)$$ は**狭義の単調減少関数**である

### 中間値の定理

関数 $$f(x)$$ が $$[a,b]$$ で連続で、$$f(a) \neq f(b)$$ とする。

このとき、任意の $$\eta \in [f(a),f(b)]$$ について $$f(\xi) = \eta$$ を満たす $$a<\xi<b$$ が少なくとも1つは存在する。

### 最大値と最小値

閉区間 $$[a,b]$$ で有界かつ連続な関数 $$f(x)$$ は閉区間内で最大値・最小値を取る。
