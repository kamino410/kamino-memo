# 離散コサイン変換（Discrete Cosine Transform：DCT）

## 定義

離散コサイン変換にはType Ⅰ~Ⅳのバリエーションがある（主に $$\cos$$ の内側の項の定義が違う）。
最も有名なのは以下に示すType ⅡでJPEG、MPEGなどにも利用されている。

$$\begin{eqnarray}
X_k &=& c_k \sum_{n=0}^{N-1} x_n \cos \frac{(2n+1)k \pi}{2N} \\
x_n &=& \sum_{k=0}^{N-1} X_k c_k \cos \frac{(2n+1)k \pi}{2N} \\
c_k &=& \begin{cases} \sqrt{\frac{1}{N}} & (k=0) \\ \sqrt{\frac{2}{N}} & (k \neq 0) \end{cases}
\end{eqnarray}$$
