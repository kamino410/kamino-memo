# フィードバック制御系の内部安定性

図のようなフィードバック制御系について考える。

プロパー性に関する議論を省略するため、$$P(s) = \frac{N_P(s)}{D_P(s)}$$ は厳密にプロパー、$$K(s)=\frac{N_K(S)}{D_K(S)}$$ はプロパーであると仮定する。

![alt text](feedback.png)

## 内部安定性（internal stability）

入力 $$r,d$$ と出力 $$u,y$$ の間で記述される次の4つの伝達関数すべてが安定であるかどうかを**内部安定性**と呼ぶ。

$$
\begin{eqnarray}
\begin{cases}
G_{ur}(s) = \frac{K(s)}{1+P(s)K(s)} = \frac{D_P(s)N_K(s)}{\phi(s)} \\
G_{ud}(s) = \frac{-P(s)K(s)}{1+P(s)K(s)} = \frac{-N_P(s)N_K(s)}{\phi(s)} \\
G_{yr}(s) = \frac{P(s)K(s)}{1+P(s)K(s)} = \frac{N_P(s)N_K(s)}{\phi(s)} \\
G_{yd}(s) = \frac{P(s)}{1+P(s)K(s)} = \frac{N_P(s)D_K(s)}{\phi(s)}
\end{cases} \\ \\
\phi(s) = D_P(s)D_K(S)+N_P(s)N_K(s)
\end{eqnarray}
$$

またこのときの $$\phi(s)$$ を**特性多項式（characteristic polynominal）**と呼ぶ。

4つの伝達関数の分母は同じであるため、内部安定性に関して次の定理が成り立つ。

<center>
フィードバック制御系が内部安定である<br>⇔　特性多項式 $$\phi(s) = 0$$ のすべての根の実部が負
</center>

### 解説

以前述べたようにフィードバック制御系の $$r$$ から $$y$$ への伝達関数は $$G_{yr}(s)$$ となる。

ここで $$P(s) = \frac{1}{s-1}, \ K(s)=\frac{s-1}{s}$$ のシステムについて考えると、

$$
G_{yr}(s) = \frac{1}{s+1}
$$

となり、一見安定であるかのように見える。しかし、$$y$$ の初期値 $$y_0$$ を考慮すると

$$
y(s) = \frac{1}{s+1}r(s) + \frac{s}{(s+1)(s-1)}y_0
$$

となり、第二項に不安定極が残り $$y_0 \neq 0$$ の場合は発散してしまうことがわかる。

これは $$D_P(s) = s-1$$ の不安定極と $$N_K=s-1$$ の零点が相殺されたために生じたものと解釈できる。
フィードバック制御系の安定性を考える際はこの**不安定な極零相殺（unstable pole-zero cancellation）**に注意しなければならないため、上記の特性多項式を用いた評価が必要になる。
