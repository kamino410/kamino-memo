# 離散通信路（discrete_channel）

送信する情報が標本化・量子化されたディジタル情報であるようなノイズのある通信路について考える。

## 通信路行列

送信する符号アルファベットを $$A=\{a_1,\cdots,a_n\}$$ 受信する符号アルファベットを $$B=\{b_1,\cdots,b_m\}$$ とおく。

記憶領域を持たない無記憶通信路を仮定する。
すると通信路の性質は「$$a_i$$ を送信したとき一定の確率で $$b_1\sim b_n$$ のいずれかが届く」という条件付き確率 $$P(b_j | a_i)$$ で表現できる。
これを次のような行列で表記したものを**通信路行列（channel matrix）**という。

$$
\begin{bmatrix}P(b_1|a_1) & P(b_1|a_2) & \cdots & P(b_1|a_n) \\
P(b_2|a_1) & P(b_2|a_2) & \cdots & P(b_2|a_n) \\
\vdots & \vdots & \ddots & \vdots \\
P(b_m|a_1) & P(b_m|a_2) & \cdots & P(b_m|a_n)
\end{bmatrix}
$$

また、通信路行列と $$A$$ の各符号アルファベットの生起確率がわかっていれば $$B$$ の各符号アルファベットの生起確率が得られる。

$$
\begin{bmatrix}P(b_1) \\ P(b_2) \\ \vdots \\ P(b_m) \end{bmatrix}
= \begin{bmatrix}P(b_1|a_1) & P(b_1|a_2) & \cdots & P(b_1|a_n) \\
P(b_2|a_1) & P(b_2|a_2) & \cdots & P(b_2|a_n) \\
\vdots & \vdots & \ddots & \vdots \\
P(b_m|a_1) & P(b_m|a_2) & \cdots & P(b_m|a_n)
\end{bmatrix}
\begin{bmatrix}P(a_1) \\ P(a_2) \\ \vdots \\ P(a_n)\end{bmatrix}
$$

>通信路の例

>* 2元対称通信路（binary symmetric channel）
>    * 確率 $$p$$ で正しい情報が伝達される通信路

>$$\begin{bmatrix}1-p & p \\ p & 1-p\end{bmatrix}$$

>* 2元消失通信路（binary symmetric erasure channel）
>    * 確率 $$p$$ で情報が判別不能になる通信路

>$$\begin{bmatrix}1-p & p & 0 \\ 0 & p & 1-p \end{bmatrix}$$

## 通信路の伝達情報量（transinformation）

[相互情報量](entropy.md#相互情報量（mutual-information）)での解説の通り、通信路を通ったあとの情報（通報）から得られる情報量（**伝達情報量**）は $$A,B$$ の相互情報量として定義できる。

$$
\begin{eqnarray}
I(A;B) &=& H(A) - H(A|B) \\
&=& \sum_{i=1}^n\sum_{j=1}^m P(a_i, b_j)\log_2 \frac{P(a_i,b_j)}{P(a_i)P(b_j)}
\end{eqnarray}
$$

## 通信路容量（channel capacity）

通信路行列は通信路固有のものであるため変えることは困難だが、送信する符号アルファベット $$A$$ の生起確率は符号化の方法によってある程度変えられる。

送信系列を変えたときの伝達情報量の最大値を**通信路容量**と呼び、次のように表す。

$$
C = \max_{P(a)} I(A;B)
$$

>例：通信路容量の例

>* 2元対称通信路

>通信路行列より、$$H(B|A) = - p \log p - (1-p) \log (1-p)$$ である。

>$$a_0$$ の生起確率を $$P(a_0)=w$$ としたとき、

>$$b_0$$ の生起確率は $$P(b_0)=P(a_0,b_0)+P(a_1,b_0)=(1-p)w+(1-p)(1-w)$$ となる。
>$$P(b_0) = q$$ と置けば、

>$$
\begin{eqnarray}
H(B) &=& -P(b_0)\log P(b_0) - P(b_1)\log P(b_1) \\
&=& - q \log q - (1-q)\log (1-q)
\end{eqnarray}
$$

>となるので

>$$
\begin{eqnarray}
I(A;B) &=& H(B) - H(B|A)\\
&=& - q \log q - (1-q)\log (1-q) + p \log p + (1-p) \log (1-p)
\end{eqnarray}
$$

>$$f(x) = - x\log x - (1-x)\log(1-x)$$ は $$x \in [0,1]$$ の範囲では $$x=1/2$$ で最大値 $$1$$ を取るため、$$q = 1/2$$ を満たすとき伝達情報量は最大値 $$1+p \log p + (1-p) \log (1-p)$$ を取る。

>よって通信路容量 $$C=\max I(A;B) = 1+p \log p + (1-p) \log (1-p)$$ である。

>* 2元消失通信路

>$$a_0$$ の生起確率を $$P(a_0)=w$$ としたとき、

>$$b_0, b_1, b_2$$ の生起確率は $$P(b_0)=(1-p)w, \ P(b_1)=(1-p)(1-w), \ P(b_2)=p$$ となり、

>$$
\begin{eqnarray}
H(B) &=& -P(b_0)\log P(b_0) - P(b_1)\log P(b_1) - P(b_2)\log P(b_2)\\
&=& - (1-p)w \log (1-p)w - (1-p)(1-w) \log (1-p)(1-w) - p \log p \\
&=& (1-p)\{w\log w+(1-w)\log(1-w)\} + (1-p)\log(1-p)
\end{eqnarray}
$$

>$$
\begin{eqnarray}
H(B|A) &=& - \sum_{A,B} P(A_i, B_j) \log P(B_j|A_i)\\
&=& -(1-p)w\log (1-p)-pw\log p \\
&\ &- (1-p)(1-w)\log(1-p)-p(1-w)\log p \\
&=& -p \log p - (1-p)\log(1-p)
\end{eqnarray}
$$

>となる。よって

>$$
\begin{eqnarray}
I(A;B) &=& H(B) - H(B|A) \\
&=& (1-p)\{w\log w+(1-w)\log(1-w)\} + (1-p)\log(1-p) \\
&\ & + p \log p + (1-p)\log(1-p) \\
&=& - (1-p)\{w\log w + (1-w)\log(1-w) \}
\end{eqnarray}
$$

>より $$w=1/2$$ のとき最大値は $$1-p$$ となる。

>よって通信路容量 $$C = 1-p$$ である。
