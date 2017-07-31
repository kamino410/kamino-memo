# ベクトル値関数（vector-valued function）

## 定義

ベクトル解析の分野において、スカラーまたはベクトルをベクトルに移すような関数 $$f : (K \mathrm{or} V) \rightarrow V$$ を**ベクトル値関数**または**ベクトル関数**という。

## 連続性（continuity）

定義域 $$U \subset V$$ 上でのベクトル関数の連続性は次のように定義される。

$$
\forall t \in U (\lim_{\tau \rightarrow t} f(\tau) = f(t))
$$

## 微分

定義域 $$U$$ 上の点 $$x_0$$ においてベクトル関数 $$f(x)$$ について

$$
\lim_{x \rightarrow x_0} \frac{f(x)-f(x_0)}{x-x_0}
$$

が存在するとき、$$f(x)$$ は $$x_0$$ において微分可能であるという。

## 微分の性質

ベクトル空間 $$V$$ の基底 $$e_i \ \ (i = 1 \sim n)$$ を用いて $$f(x) = \sum \alpha_i(x) e_i$$ と表されるとき、以下の性質が成立する。

* $$\lim_{x \rightarrow x_0}f(t) = \sum \lim_{x \rightarrow x_0} \alpha_i(x)e_i$$
* $$f(x)$$ が連続　⇔　$$\alpha_i(x)$$ がすべて連続
* $$f(x)$$ が連続　⇒　$$f'(x_0) = \sum \alpha'(x) e_i$$
