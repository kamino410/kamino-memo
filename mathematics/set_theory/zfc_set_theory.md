# ZFC公理系

[集合](set.md)で述べたような集合の定義にツェルメロ＝フレンケルの公理系（ZF）と選択公理（C）を加えた公理系。
集合の公理系として現在最も一般的である。

## 公理

### ZF1. 空集合の存在

元を1つも含まない集合が存在する。

ZF2と併せると空集合はただ一つに定まるため、これを $$\emptyset$$ と表す。

$$
\exists x \forall u \neg (u \in x)
$$

### ZF2. 外延性公理

同じ元から成る集合は等しい。

$$
\forall x \forall y (\forall u(u \in x \equiv u \in y) \rightarrow x = y)
$$

### ZF3. 非順序対の存在

$$
\forall x \forall y \exists z \forall u (u \in z \equiv (u=x \vee u = y))
$$

### ZF4. 和集合の公理

$$
\forall x \exists y \forall u (u \in y \equiv \exists v(u \in v \wedge v \in x))
$$

### ZF5. 冪集合の公理

$$
\forall x \exists y \forall u(u \in y \equiv u \in x)
$$

### ZF6. 置換公理

$$
\forall u \forall v \forall \omega (A(u,v) \wedge A(u,\omega) \rightarrow v = \omega) \rightarrow \forall x \exists y \forall v(v \in y \equiv \exists u(u \in x \wedge A(u,v)))
$$

### ZF7. 正則性公理

$$
\exists x A(x) \rightarrow \exists x (A(x) \wedge \neg \exists y(A(y) \wedge y \in x))
$$

### ZF8. 無限公理

$$
\exists (\exists u (u \in x) \wedge \forall u(u \in x \rightarrow \exists v(v \in x \wedge u \subset v \wedge \neg v = u)))
$$

### 選択公理

$$
\begin{eqnarray}
\forall x [\emptyset \notin x \wedge \forall u \forall v((u \in x \wedge v \in x \wedge \neg u = v) \rightarrow u \cap v = \emptyset)] \\
\rightarrow \forall x \exists y \forall v (v \in y \equiv \exists u(u \in x \wedge A(u,v)))
\end{eqnarray}
$$
