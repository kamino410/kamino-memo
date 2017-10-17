# 冪乗（exponentiation）

## 高速に冪乗

$$x^n$$ を計算する際、偶数なら $$x^{2(n/2)}$$ 奇数なら $$x^{2(n/2)+1}$$ と分解することで時間計算量が $$O(\log n)$$ になる。

```cpp
#include <iostream>

long power(long x, int n) {
    if (n == 0)
        return 1;
    else if (n % 2)
        return x * power(x, n - 1);
    else
        return power(x * x, n / 2);
}

int main() {
    std::cout << power(14, 15) << std::endl;
    return 0;
}
```

## 冪乗の剰余

$$x^n \mod m$$ を高速に計算したい。

### 周期性を利用する

[合同類](../../mathematics/algebra/residue_ring.md#合同類（congruent_class）)の性質上、同じ数をかけ合わせていったときの$$\mathrm{mod}$$は周期的に循環する。

### フェルマーの小定理を利用する

$$m$$ が素数で $$x,m$$ が互いに素である場合、フェルマーの小定理が利用できる。

>**フェルマーの小定理**

>素数 $$p$$ と整数 $$a$$ が互いに素であるとき $$a^{p-1} \equiv 1 (\mathrm{mod}\ p)$$

これによって上記の循環の周期が $$p-1$$ であることが確定するため実装が少し楽になる。
もう一歩踏み込むと次の法則が利用できる。

### 平方剰余の相互法則を利用する

$$m$$ が素数で $$x,m$$ が互いに素である場合、次の法則を利用できる。

>**平方剰余の相互法則（reciprocity law）**

>相異なる奇素数 $$p,q$$ に関して

>$$\begin{eqnarray}\left(\frac{q}{p}\right)\left(\frac{p}{q}\right) = (-1)^{\frac{p-1}{2}\frac{q-1}{2}}\end{eqnarray}$$


>**オイラーの基準**

>奇素数 $$p$$ と自然数 $$a$$ が互いに素であるとき

>$$\begin{eqnarray}\left(\dfrac{a}{p}\right)\equiv a^{\frac{p-1}{2}}(\mathrm{mod}\ p)\end{eqnarray}$$

オイラーの基準から

$$x^n \equiv \begin{eqnarray}x^{n \ \mathrm{mod} \ m} \equiv x^l x^{\frac{p-1}{2}} \equiv \left(\frac{a}{p}\right)\ (\mathrm{mod}\ p)\end{eqnarray}$$

である。
$$\left(\frac{a}{p}\right)$$ は平方剰余の相互法則から求めることができるため、$$x^l$$ を両辺に掛け合わせて剰余を取ればよい。
