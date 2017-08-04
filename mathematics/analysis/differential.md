# 微分（differential）

## 微分可能性

定義域 $$D$$ 上で定義される関数 $$f(x)$$ と $$x_0 \in D$$ について次のように定義される。

<center>
$$\lim_{x\rightarrow x_0} \frac{f(x)-f(x_0)}{x-x_0}$$ が存在する<br />⇔　右極限 $$f_+'(x_0) = \lim_{x\rightarrow x_0}\frac{f(x)-f(x_0)}{x-x_0}$$ と左極限 $$f_+'(x_0) = \lim_{x\rightarrow x_0}\frac{f(x)-f(x_0)}{x-x_0}$$ が一致する<br />⇔　微分可能である
</center><br />

また条件を緩めて右極限のみが存在する場合を**右微分可能**、左極限のみが存在する場合を**左微分可能**という。

## 導関数（derivative）

定義域 $$D$$ 上で定義される関数 $$f(x)$$ が微分可能であるとき、

$$
f'(x) = \lim_{h\rightarrow 0}\frac{f(x+h)-f(x)}{h}
$$

を**導関数**という。

## 導関数の性質

関数 $$f(x),g(x)$$ が $$x = x_0$$ の近くで定義され、いずれも微分可能であるとき、以下の性質が成立する。

* $$(cf)'(x_0) = cf'(x)$$
* $$(f \pm g)'(x_0) = f'(x_0) \pm g'(x_0)$$
* $$(fg)'(x_0) = f'(x_0)g(x_0) + f(x_0)g'(x_0)$$
* $$g(x_0) \neq 0 \rightarrow \left( \frac{f}{g} \right) ' (x_0) = \frac{f'(x_0)g(x_0)-f(x_0)g'(x_0)}{g(x_0)^2}$$

## 極値

$$f(x)$$ が $$x=x_0$$ の近傍で $$f(x_0) > f(x) \ \ (x_0 \neq x)$$ を満たすとき、$$f(x)$$ は $$x_0$$ で**極大**であるといい、$$f(x_0)$$ を**極大値**という。
同様に、不等号が $$\geq$$ であるときは**広義の極大**・**広義の極大値**、$$<$$ であるときは**極小**・**極小値**、$$\leq$$ であるときは**広義の極小**・**広義の極小値**という。
また、極大値と極小値をまとめて**極値**と呼ぶ。

極値の必要条件は次のように与えられる。

<center>
関数 $$f(x)$$ が $$x=x_0$$ の近傍で定義され $$C^1$$ 級であり、$$x_0$$ で極値を持つ<br />⇒　$$f'(x_0) = 0$$
</center><br />

極値の十分条件は次のように与えられる。

<center>
関数 $$f(x)$$ が $$x=x_0$$ の近傍で定義され $$C^n$$ 級かつ $$f^{(i)}(x_0)=0\ \ (i = 1,\cdots, n-1), \ f^{(n)}(x_0)\neq 0$$<br />⇒　$$n$$ が偶数かつ $$f^{(n)}(x_0) < 0$$ なら $$f(x_0)$$ は極大値<br />　$$n$$ が偶数かつ $$f^{(n)}(x_0) > 0$$ なら $$f(x_0)$$ は極小値<br />$$n$$ が奇数なら $$f(x_0)$$ は極値ではない
</center><br />

## 平均値の定理（mean-value theorem）

$$[a,b]$$ を含む定義域で定義された関数 $$f(x)$$ が $$(a,b)$$ で微分可能であるとき、次の性質が成り立つ。

$$
^\exists c (a<c<b) (f'(c) = \frac{f(b)-f(a)}{b-a})
$$

## コーシーの平均値の定理（Cauchy's mean-value theorem）

$$[a,b]$$ を含む定義域で定義された関数 $$f(x),g(x)$$ が $$(a,b)$$ で微分可能であるとき、次の性質が成り立つ。

$$
^\exists c(a<c<b) (\frac{f'(c)}{g'(x)} = \frac{f(b)-f(a)}{g(b)-g(a)})
$$

## ロピタルの定理（l'Hôpital's rule）

$$a$$ を含む開区間で微分可能な関数 $$f(x), g(x)$$ について $$g'(x) \neq 0$$ とする。
このとき以下の性質が成り立つ。

<center>
$$f(a)=g(a)=0$$ かつ $$\lim_{x\rightarrow a} \frac{f'(x)}{g'(x)} = L$$ が存在する<br />⇔　$$\lim_{x\rightarrow a}\frac{f(x)}{g(x)} = L$$
</center><br />

同値な定理として、開区間 $$(a,\infty)$$ で微分可能な関数 $$f(x),g(x)$$ について

<center>
$$\lim_{x \rightarrow \infty}f(x) = \lim_{x \rightarrow \infty}g(x) = 0$$ かつ $$\lim_{x \rightarrow \infty}\frac{f'(x)}{g'(x)} = L$$ が存在する<br />⇔　$$\lim_{x \rightarrow \infty}\frac{f(x)}{g(x)} = L$$
</center><br />

がある。

また、$$a$$ を含む開区間で $$a$$ 以外の点で微分可能な関数 $$f(x),g(x)$$ について、

<center>
$$\lim_{x\rightarrow a}f(x) = \lim_{x\rightarrow a}g(x) = \infty$$ かつ $$\lim_{x\rightarrow a}\frac{f'(x)}{g'(x)} = L$$ が存在する<br />⇔　$$\lim_{x\rightarrow a}\frac{f(x)}{g(x)} = L$$
</center><br />

が成立する。

この定理は[不定形の極限値](limit_continuity.md#不定形の極限)を求める手段の1つである。
