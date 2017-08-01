# 微分（differential）

## 微分可能性

定義域 $$D$$ 上で定義される関数 $$f(x)$$ と $$x_0 \in D$$ について次のように定義される。

<center>
$$\lim_{x\rightarrow x_0} \frac{f(x)-f(x_0)}{x-x_0}$$ が存在する<br>⇔　右極限 $$f_+'(x_0) = \lim_{x\rightarrow x_0}\frac{f(x)-f(x_0)}{x-x_0}$$ と左極限 $$f_+'(x_0) = \lim_{x\rightarrow x_0}\frac{f(x)-f(x_0)}{x-x_0}$$ が一致する<br>⇔　微分可能である
</center>

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
$$f(a)=g(a)=0$$ かつ $$\lim_{x\rightarrow a} \frac{f'(x)}{g'(x)} = L$$ が存在する<br>⇔　$$\lim_{x\rightarrow a}\frac{f(x)}{g(x)} = L$$
</center>

同値な定理として、開区間 $$(a,\infty)$$ で微分可能な関数 $$f(x),g(x)$$ について

<center>
$$\lim_{x \rightarrow \infty}f(x) = \lim_{x \rightarrow \infty}g(x) = 0$$ かつ $$\lim_{x \rightarrow \infty}\frac{f'(x)}{g'(x)} = L$$ が存在する<br>⇔　$$\lim_{x \rightarrow \infty}\frac{f(x)}{g(x)} = L$$
</center>

がある。

また、$$a$$ を含む開区間で $$a$$ 以外の点で微分可能な関数 $$f(x),g(x)$$ について、

<center>
$$\lim_{x\rightarrow a}f(x) = \lim_{x\rightarrow a}g(x) = \infty$$ かつ $$\lim_{x\rightarrow a}\frac{f'(x)}{g'(x)} = L$$ が存在する<br>⇔　$$\lim_{x\rightarrow a}\frac{f(x)}{g(x)} = L$$
</center>

が成立する。

この定理は[不定形の極限値](limit_continuity.md#不定形の極限)を求める手段の1つである。
