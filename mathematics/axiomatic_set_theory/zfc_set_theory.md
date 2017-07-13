# ZFC公理系

[集合](set.md)で述べたような集合の定義にツェルメロ＝フレンケルの公理系（ZF）と選択公理（C）を加えた公理系。
集合の公理系として現在最も一般的である。

## 公理

### ZF1. 空集合の存在

元を1つも含まない集合が存在する、という公理。

ZF2と併せると空集合はただ一つに定まるため、これを $$\emptyset$$ と表す。

$$
\exists x \forall u \neg (u \in x)
$$

### ZF2. 外延性公理

同じ元から成る集合は等しい、という公理。

$$
\forall x \forall y (\forall u(u \in x \equiv u \in y) \rightarrow x = y)
$$

### ZF3. 非順序対の存在

任意の2つの元 $$x,y$$ のみを元とする集合 $$\{x,y\}$$ が存在する、という公理。
このような集合を**対**という。
この公理を用いて非順序対を定義できる。

$$
\forall x \forall y \exists z \forall u (u \in z \equiv (u=x \vee u = y))
$$

### ZF4. 和集合の公理

集合を元とする任意の集合 $$x$$ があり、$$x$$ に含まれる集合のいずれか（ $$v$$ ）に要素 $$u$$ が含まれているとする。
このときすべての $$u$$ を含むような集合 $$y$$ （つまり $$v$$ の和集合）が存在する、という公理。

$$
\forall x \exists y \forall u (u \in y \equiv \exists v(u \in v \wedge v \in x))
$$

### ZF5. 冪集合の公理

集合 $$x$$ のすべての部分集合を要素とするような集合 $$y$$ が存在する、という公理。

$$
\forall x \exists y \forall u(u \in y \equiv u \subset x)
$$

### ZF6. 置換公理

任意の論理式 $$A(u,v)$$ を $$u \rightarrow v$$ の射影を行う関数であると見立てる。
この関数が単射であるとき、集合 $$x$$ の各要素の写像の集まり $$y$$ も集合である、という公理。

$$
\forall u \forall v \forall \omega (A(u,v) \wedge A(u,\omega) \rightarrow v = \omega) \rightarrow \forall x \exists y \forall v(v \in y \equiv \exists u(u \in x \wedge A(u,v)))
$$

### ZF7. 正則性公理

論理式 $$A(x)$$ が真になる集合 $$x$$ が存在するなら、$$x \ni x_1 \ni x_2 \ni \dots \ni x'$$ となる順序が最小の $$x'$$ が存在する、という公理。

$$
\exists x A(x) \rightarrow \exists x (A(x) \wedge \neg \exists y(A(y) \wedge y \in x))
$$

また同値な表現である以下の論理式が用いられる事がある。

$$
\forall x(\forall y(y\in x \rightarrow A(y)) \rightarrow \forall x A(x))
$$

$$
\forall x (x \neq \emptyset \rightarrow \forall x \exists y(y \in x \wedge x \cap y = \emptyset))
$$

### ZF8. 無限公理

無限集合が1つは存在することを保証する公理。

$$
\exists (\exists u (u \in x) \wedge \forall u(u \in x \rightarrow \exists v(v \in x \wedge u \subset v \wedge \neg v = u)))
$$

素朴に書き換えると

$$
\exists x (x \neq \emptyset \wedge (\forall u \in x \exists v \in x (u \subsetneq v)))
$$

### 選択公理

元が互いに交わらず空集合を含まない集合 $$x$$ について、$$x$$ に含まれる集合から要素を1つずつ取り出したものも集合である、という公理。

$$
\begin{eqnarray}
&\ &\forall x [\emptyset \notin x \wedge \forall u \forall v((u \in x \wedge v \in x \wedge \neg u = v) \rightarrow u \cap v = \emptyset) \\
&\ & \rightarrow \exists y(y \subset \sigma(x) \wedge \forall u(u \in x \rightarrow \exists z(z \in u \wedge z \in y \wedge \forall w(w\in u \wedge w \in y \rightarrow w = z))))]
\end{eqnarray}
$$
