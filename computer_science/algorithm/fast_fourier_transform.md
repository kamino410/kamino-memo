# 高速フーリエ変換（Fast Fourier Transform : FFT）

* Cooley-Tukey algorithm
  * mixed-radix algorithm
    * 小さい素数に対して最適化されたFFTを実装（ $$O(N^2)$$ ）
  * radix-2 algorithm
    * $$N=2^m$$ にのみ対応（ $$O(n \log n)$$ ）
* Prime Factor algorithm
  * データ長を互いに素になるように
  * 長さ $$p$$ のFFTは長さ $$p-1$$ の畳み込みになる

## 基本

わかりやすいように $$N$$ が因数2を持つとする。

$$\begin{eqnarray}
W_N &=& e^{-2\pi j/N} \\
X_k &=& \sum_{n=0}^{N-1} x_n W_N^{nk}
\end{eqnarray}$$

ここで右辺の奇数の項と偶数の項をわける。

$$\begin{eqnarray}
X_k &=& \sum_{b=0}^{N/2-1}\left( x_{2n} W_N^{(2n)k} + x_{2n+1} W_N^{(2n+1)k} \right) \\
&=& \sum_{b=0}^{N/2-1}\left( x_{2n} W_N^{(2n)k} + W^n_N x_{2n+1} W_N^{(2n)k} \right) \\
&=& \sum_{b=0}^{N/2-1}\left( x_{2n} + W_N^n x_{2n+1} \right) W_N^{(2n)k}
\end{eqnarray}$$

この操作により $$N^2$$ 回必要だった積の計算が $$2(N/2)^2$$ に減る。
これを $$N$$ の因数に対して再帰的に適用することで計算量を減らすのがFFTの基本概念となる。

$$N$$ が素数である場合はこの操作が適用できないが、数論より $$N$$ のFFTは $$N-1$$ の畳み込み積分に変換できるため、$$N-1$$ のFFTを行うことで高速に計算できる場合がある。

## 基数2のアルゴリズム（時間空間法）

### 理論

$$N=2^m$$ の場合は高速に計算が可能になる。

整数 $$a$$ を $$a = [a_{m-1}\cdots a_1 a_0] = 2a_{m-1} + \cdots + 2a_1 + a_0$$ のようにビット表現することにして、まずフーリエ変換の定義式を $$n$$ について展開する。

$$\begin{eqnarray}
X_k &=& \sum_{n=0}^{N-1} x_n W_N^{nk} \\
&=& \sum_{n_0=0}^1 \cdots \sum_{n_{m-2}=0}^1 \sum_{n_{m-1}=0}^1 x_n W_N^{k[n_{m-1}\cdots a_1a_0]} \\
&=& \sum_{n_0=0}^1 \cdots \sum_{n_{m-2}=0}^1 W_N^{k[n_{m-2}\cdots n_1n_0]} \sum_{n_{m-1}=0}^1 x_n W_N^{k n_{m-1}} \\
&=& \sum_{n_0=0}^1 W_N^{kn_0} \cdots \sum_{n_{m-2}=0}^1 W_N^{2^{m-2} kn_{m-2}} \sum_{n_{m-1}=0}^1 x_n W_N^{2^{m-1} k n_{m-1}}
\end{eqnarray}$$

※このとき $$n$$ に関して $$\sum$$ を分割することから**時間空間法**と呼ぶ。$$k$$ に関して $$\sum$$ を分割する手法は**周波数空間法**と呼ばれる。

次に $$N=2^m$$ であることを利用して書き直す。

$$\begin{eqnarray}
X_k &=& \sum_{n_0=0}^1 W_N^{kn_0} \cdots \sum_{n_{m-2}=0}^1 W_4^{kn_{m-2}} \sum_{n_{m-1}=0}^1 x_n W_2^{k n_{m-1}}
\end{eqnarray}$$

$$W_N^a = e^{-2\pi j a/N}$$ の $$a$$ に対する周期性を利用しながら $$k$$ もビット表現に展開する。

$$\begin{eqnarray}
X_{[k_{m-1}\cdots k_1 k_0]} &=& \sum_{n_0=0}^1 W_N^{[k_{m-1}\cdots k_1 k_0]n_0} \cdots \sum_{n_{m-2}=0}^1 W_4^{[k_1k_0]n_{m-2}} \sum_{n_{m-1}=0}^1 x_n W_2^{k_0 n_{m-1}}
\end{eqnarray}$$

この式を下のように区切り、再帰的に表現する。

$$\begin{eqnarray}
X_{[k_{m-1}\cdots k_1 k_0]} &=& \sum_{n_0=0}^1 W_N^{[k_{m-1}\cdots k_1 k_0]n_0} \left( \cdots \left( \sum_{n_{m-2}=0}^1 W_4^{[k_1k_0]n_{m-2}} \left( \sum_{n_{m-1}=0}^1 \left( x_n \right) W_2^{k_0 n_{m-1}} \right) \right) \right)
\end{eqnarray}$$

$$\begin{eqnarray}
&&\begin{cases}
r_0(n) = x_n \\
r_i(n_0, \cdots, n_{m-i-1}, k_0, \cdots, k_{i-1}) = \sum_{n_i=0}^1 W_{2^i}^{[k_{i-1}\cdots k_0]n_i} r_{i-1}(n_0, \cdots, n_{m-i}, k_0, \cdots, k_{i-2})
\end{cases} \\
&& (X_k = r_m(k_{m-1}, \cdots, k_0))
\end{eqnarray}$$

$$r_i$$ は $$n_0, \cdots, n_{m-i-1}, k_0, \cdots, k_{i-1}$$ を変数とする関数と見なせる。
そこで $$[n_0 \cdots n_{m-i-1} k_{i-1} \cdots k_0]$$ を各 $$r_i$$ の変数と見なす。

上の漸化式で $$k_{i-1}=\{0,1\}$$ のときで場合分けすると以下のようになる。

$$\begin{eqnarray}
&&\begin{bmatrix} r_i([n_0 \cdots n_{m-i-1} 0 k_{i-2} \cdots k_0]) \\ r_i([n_0 \cdots n_{m-i-1} 1 k_{i-2} \cdots k_0]) \end{bmatrix}\\ &=&
\begin{bmatrix}
r_{i-1}([n_0 \cdots n_{m-i-1} 0 k_{i-2} \cdots k_0]) + W_{2^i}^{[0 k_{i-2} \cdots k_0]} r_{i-1}([n_0 \cdots n_{m-i-1} 1 k_{i-2} \cdots k_0]) \\
r_{i-1}([n_0 \cdots n_{m-i-1} 0 k_{i-2} \cdots k_0]) + W_{2^i}^{[1 k_{i-2} \cdots k_0]} r_{i-1}([n_0 \cdots n_{m-i-1} 1 k_{i-2} \cdots k_0])
\end{bmatrix} \\
&=& \begin{bmatrix}
r_{i-1}([n_0 \cdots n_{m-i-1} 0 k_{i-2} \cdots k_0]) + W_{2^i}^{[k_{i-2} \cdots k_0]} r_{i-1}([n_0 \cdots n_{m-i-1} 1 k_{i-2} \cdots k_0]) \\
r_{i-1}([n_0 \cdots n_{m-i-1} 0 k_{i-2} \cdots k_0]) - W_{2^i}^{[k_{i-2} \cdots k_0]} r_{i-1}([n_0 \cdots n_{m-i-1} 1 k_{i-2} \cdots k_0])
\end{bmatrix}
\end{eqnarray}$$

この式より $$r_1(*),r_2(*),\cdots$$ を計算するとき、上段のあるペアの値は下段の対応するペアの値から計算できることがわかる（これをバタフライ演算と呼ぶ）。
よって下段から順に計算していけば領域計算量は $$O(N)$$ となり、ペアで計算を進めることによるメモ化の効果から時間計算量は $$O(n \log n)$$ となる。

### 実装

```py
import numpy as np

def radix2fft(data):
    n = len(data)
    r = 1; m = 0
    while r < n:
        r *= 2; m += 1
    if r != n:
        raise "data length is not exp of 2"
    res = np.array(data, dtype=np.complex)
    #indexがビット左右入れ替えになるよう置換
    j = 0
    for i in range(n - 2):
        if i < j:
            tmp = res[i]
            res[i] = res[j]
            res[j] = tmp
        k = int(n / 2)
        while k <= j:
            j = j - k
            k = int(k / 2)
        j += k
    #W^
    ws = [np.exp(-2j * np.pi * i / 2**m) for i in range(2**(m - 1))]
    st = 1
    for i in range(0, m):
        for a in range(st):
            for b in range(0, n, 2 * st):
                t0 = res[a + b] + ws[int(a * n / st / 2)] * res[a + b + st]
                t1 = res[a + b] - ws[int(a * n / st / 2)] * res[a + b + st]
                res[a + b] = t0
                res[a + b + st] = t1
        st *= 2
    return res

def radix2ifft(data):
    n = len(data)
    r = 1; m = 0
    while r < n:
        r *= 2; m += 1
    if r != n:
        raise "data length is not exp of 2"
    res = np.array(data, dtype=np.complex)
    #indexがビット左右入れ替えになるよう置換
    j = 0
    for i in range(n - 2):
        if i < j:
            tmp = res[i]
            res[i] = res[j]
            res[j] = tmp
        k = int(n / 2)
        while k <= j:
            j = j - k
            k = int(k / 2)
        j += k
    #W^
    ws = [np.exp(2j * np.pi * i / 2**m) for i in range(2**(m - 1))]
    st = 1
    for i in range(0, m):
        for a in range(st):
            for b in range(0, n, 2 * st):
                t0 = res[a + b] + ws[int(a * n / st / 2)] * res[a + b + st]
                t1 = res[a + b] - ws[int(a * n / st / 2)] * res[a + b + st]
                res[a + b] = t0
                res[a + b + st] = t1
        st *= 2
    return res/n

```

### 例（N=8）

$$r_0([n_0 n_1 n_2]) = x_{[n_2 n_1 n_0]}$$

$$r_0([000]) = x_0 \\
r_0([100]) = x_1 \\
r_0([010]) = x_2 \\
r_0([110]) = x_3 \\
r_0([001]) = x_4 \\
r_0([101]) = x_5 \\
r_0([011]) = x_6 \\
r_0([111]) = x_7$$

----

$$\begin{bmatrix} r_1([n_0 n_1 0]) \\ r_1([n_0 n_1 1]) \end{bmatrix}
= \begin{bmatrix}
1 & 1 \\ 1 & -1
\end{bmatrix}
\begin{bmatrix}
r_0([n_0 n_1 0]) \\
r_0([n_0 n_1 1])
\end{bmatrix}$$

$$r_1([000]) = r_0([000]) + r_0([001]) \\
r_1([100]) = r_0([100]) + r_0([101]) \\
r_1([010]) = r_0([010]) + r_0([011]) \\
r_1([110]) = r_0([110]) + r_0([111]) \\
r_1([001]) = r_0([000]) - r_0([001]) \\
r_1([101]) = r_0([100]) - r_0([101]) \\
r_1([011]) = r_0([010]) - r_0([011]) \\
r_1([111]) = r_0([110]) - r_0([111])$$

----

$$\begin{bmatrix} r_2([n_0 0 k_0]) \\ r_2([n_0 1 k_0]) \end{bmatrix}
= \begin{bmatrix}
1 & 1 \\ 1 & -1
\end{bmatrix}
\begin{bmatrix}
r_1([n_0 0 k_0]) \\
W_4^{[k_0]} r_1([n_0 1 k_0])
\end{bmatrix}$$

$$r_2([000]) = r_1([000]) + r_1([010]) \\
r_2([100]) = r_1([100]) + r_1([110]) \\
r_2([010]) = r_1([000]) - r_1([010]) \\
r_2([110]) = r_1([100]) - r_1([110]) \\
r_2([001]) = r_1([000]) + W_4^1r_0([011]) \\
r_2([101]) = r_1([100]) + W_4^1r_0([111]) \\
r_2([011]) = r_1([000]) - W_4^1r_0([011]) \\
r_2([111]) = r_1([100]) - W_4^1r_0([111])$$

----

$$\begin{bmatrix} r_3([0 k_1 k_0]) \\ r_2([1 k_1 k_0]) \end{bmatrix}
= \begin{bmatrix}
1 & 1 \\ 1 & -1
\end{bmatrix}
\begin{bmatrix}
r_2([0 k_1 k_0]) \\
W_8^{[k_1 k_0]} r_2([1 k_1 k_0])
\end{bmatrix}$$

$$r_3(0) = r_3([000]) = r_2([000]) + r_2([100]) \\
r_3(4) = r_3([100]) = r_2([000]) - r_2([100]) \\
r_3(1) = r_3([001]) = r_2([001]) + W_8^1r_2([101]) \\
r_3(5) = r_3([101]) = r_2([001]) - W_8^1r_2([101]) \\
r_3(2) = r_3([010]) = r_2([010]) + W_8^2r_2([110]) \\
r_3(6) = r_3([110]) = r_2([000]) - W_8^2r_2([110]) \\
r_3(3) = r_3([011]) = r_2([000]) + W_8^3r_2([111]) \\
r_3(7) = r_3([111]) = r_2([000]) - W_8^3r_2([111])$$
