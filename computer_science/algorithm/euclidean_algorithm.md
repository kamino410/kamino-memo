# ユークリッドの互除法（Euclidean algorithm）

ある2つの自然数 $$a,b$$ の最小公倍数を求めるためのアルゴリズム。
すなわち $$ax + by = 0$$ となる整数 $$x,y$$ を求めることができる。

また後述するように $$ax + by = \gcd(a,b)$$ となる整数 $$x,y$$ を求める**拡張ユークリッドの互除法（extended Euclidean algorithm）**も存在する。

## 原理

$$a, b \ \ (b\neq 0)$$ の商 $$q = \mathrm{floor}(a/b)$$ と剰余 $$r = a \ \mathrm{mod} \ b$$ を用いれば $$a = qb + r$$ が成立する。

$$a = qb + r$$ より $$\gcd(b,r)$$ は $$a$$ を割り切れる。
また $$a-qb = r$$ より $$\gcd(a,b)$$ は $$r$$ を割り切れる。
よって、$$\gcd(a,b)$$ を求める問題は $$\gcd(b,r)$$ を求める問題と同値である。

また、$$r = 0$$ なら $$a$$ は $$b$$ の倍数のため、$$b$$ が最大公約数である。

よって $$r=0$$ を終了条件として再帰的に $$\gcd(b,r)$$ を求めることで $$\gcd(a,b)$$ が得られる。

## 手順

1. 大きい方の値を小さい方の値で割ったときの剰余を取る
2. 剰余が0なら小さい方の値が最小公倍数である
3. 剰余が0でないなら小さい方の値と剰余に関して上の手順を繰り返す

図的に表現するとこのようになる（21と56の最小公倍数は7）。

![alt text](euclidean.png)

2ステップで大きい方の値が半分以下になることが保証されるため、大まかな時間計算量は $$O(\log \max(a,b))$$ になる。

## 実装例

`x < y`でも1回目の呼び出しで入れ替えが行われるので、呼び出し時に大小は気にしなくて良い。

```rust
fn gcd(a: usize, b: usize) -> usize {
    if b == 0 { a } else { gcd(b, a % b) }
}

fn main() {
    let x = 21;
    let y = 56;
    println!("gcd({}, {}) = {}", x, y, gcd(x, y));
}
```

# 拡張ユークリッドの互除法（extended Euclidean algorithm）

$$ax + by = \gcd(a,b)$$ となる絶対値が最小の整数の組 $$x,y$$ を求めるアルゴリズム。

$$ax + by \neq \gcd(a,b)$$ なら解が存在しない。

## 原理

通常のユークリッドの互除法を適用していき、$$k$$ 回目の再帰で $$(a_k, b_k)$$ が得られたとする。
すると、この組も $$a_kx_k + b_ky_k = \gcd(a,b)$$ を満たさなければならない。
ここに $$b_{k-1} = a_k,\ \ b_k = a_{k-1} - \mathrm{floor}(a_{k-1} / b_{k-1}) \cdot b_{k-1}$$ を代入すると

$$\begin{eqnarray}
&\ & b_{k-1}x_k + (a_{k-1} - \mathrm{floor}(a_{k-1} / b_{k-1})\cdot b_{k-1})y_k = \gcd(a,b) \\
&\ & a_{k-1}y_k + b_{k-1} (x_k - \mathrm{floor}(a_{k-1} / b_{k-1})\cdot y_k) = \gcd(a,b)
\end{eqnarray}$$

となる。
よって、$$(a_k,b_k)$$ に対応する $$(x_k,y_k)$$ は

$$\begin{cases}
x_{k-1} = x_k - \mathrm{floor}(a_{k-1}/b_{k-1})\cdot y_k \\
y_{k-1} = x_k
\end{cases}$$

の漸化式を満たす。

アルゴリズムの結果 $$(a_n, b_n) = (a_n, 0)$$ で最小公倍数 $$\gcd(a,b) = a_n$$ が求まったとすれば $$a_n \cdot 1 + b_n \cdot 0 = \gcd(a,b)$$ が絶対値の最も小さい $$(x_n,y_n)$$ の組み合わせである。
上記の漸化式は絶対値が単調増加する数列になっているため $$(x_n,y_n)$$ の絶対値が最小であれば $$(x_0, y_0)$$ の絶対値は最小になる。

よって上記の漸化式を適用していけば絶対値が最小の組 $$(x,y)$$ が求まる。

## 実装例

```rust
fn extgcd(a: isize, b: isize) -> (isize, isize, isize) {
    if b == 0 {
        return (a, 1, 4);
    } else {
        let (gcd, y, x) = extgcd(b, a % b);
        return (gcd, x, y - (a / b) * x);
    }
}

fn main() {
    let (gcd, x, y) = extgcd(56, 21);
    println!("56 * {} + 21 * {} = {}", x, y, gcd);
}
```
