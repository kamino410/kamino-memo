# 線形写像・線形変換（linear mapping / linear transformation）

## 定義

$$U,V$$ を $$K$$ 上のベクトル空間とする。

$$U$$ 上のベクトルと $$V$$ 上のベクトルを対応させる写像 $$f:U\rightarrow V, f(x) = y$$ について次の条件を満たすとき、$$f$$ は $$U$$ から $$V$$ への**線形写像**であるという（[写像の定義](../native_set_theory/mapping.md)）。

1. $$f(x_1 + x_2) = f(x_1) + f(x_2) \ \ \ (x_1, x_2 \in U)$$
2. $$f(kx) = kf(x) \ \ \ (x \in U, k \in K)$$

特に同じベクトル空間 $$U$$ から $$U$$ への線形写像を**線形変換**という。

定義から明らかであるように $$V$$ は $$U$$ の部分空間である。
$$U$$ の次元を $$n$$、$$V$$ の次元を $$m$$とするとき、線型写像は $$m\times n$$ の行列 $$A$$ を用いて $$f(x) = Ax$$ と表される。

## 像と核（image / kernel）

線形写像 $$f:U\rightarrow V$$ に対して $$U$$ 全体の像 $$f(U)$$ を **$$f$$ の像**といい

$$
\mathrm{Im} (f) = \{y \ | \ y = f(x),\ x \in U\}
$$

と表す。

また、$$0_V$$ の原像 $$f^{-1}(0_V)$$ を **$$f$$ の核**といい

$$
\mathrm{Ker} (f) = \{x \ | \ x \in U,\ f(x) = 0_V\}
$$

と表す。
つまり写像によって原点に移されるようなベクトルの集まりを示している。

線形写像の定義より $$\mathrm{Im}(f),\ \mathrm{Ker}(f)$$ は共に $$U$$ の部分空間である。
また定義より $$f(\mathrm{Im}(f)) \subset V,\ f(\mathrm{Ker} (f)) \subset V$$ となるため、$$\mathrm{Im}(f),\ \mathrm{Ker}(f)$$ は共に $$f$$ の[不変部分空間](vector_space.md#不変部分空間)である。

## 階数と退化次数

線形写像 $$f:U\rightarrow V$$ の像 $$\mathrm{Im}(f)$$ の次元を **$$f$$ の階数**といい

$$
\mathrm{rank}(f) = \dim(\mathrm{Im}(f)) = \dim(V)
$$

と表す。

また、$$f$$ の核 $$\mathrm{Ker} (f)$$ の次元を **$$f$$ の退化次数**といい

$$
\mathrm{null}(f) = \dim (\mathrm{Ker}(f))
$$

と表す。
直観的には、写像によって $$\dim (\mathrm{Ker}(f))$$ 次元の部分空間 $$\mathrm{Ker}(f)$$ が $$0$$ 次元である原点に「つぶされている」つまり退化次数の分だけ次元が下がっていることを示している。

像の次数と退化次数を合わせれば元のベクトル空間の次数になっているはずなので、

$$
\mathrm{rank}(U) = \mathrm{rank}(f) + \mathrm{null}(f)
$$

が成立する。

## 階数と全射・単射

上記の定義から、$$f$$ の階数と[写像の種類](../native_set_theory/mapping.md#写像の分類)の間には次のような関係が得られる。

* $$\mathrm{rank}(f) = \dim U$$　⇔　線形写像 $$f:U\rightarrow V$$ は単射
* $$\mathrm{rank}(f) = \dim V$$　⇔　線形写像 $$f:U\rightarrow V$$ は全射
