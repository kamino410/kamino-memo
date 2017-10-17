# 素数・素因数分解（prime / prime factorization）

## 素数判定

### ナイーブな実装

ナイーブに実装すると $$O(\sqrt{n})$$ 。
数回だけ判定するような場合はこの方が速そう。

```cpp
#include <cmath>
#include <iostream>

bool is_prime(long n) {
    if (n % 2 == 0) return false;
    for (int i = 3; i <= sqrt(n); i += 2)
        if (n % i == 0) return false;
    return true;
}

int main() {
    std::cout << is_prime(1245156371) << std::endl;
    return 0;
}
```

### エラトステネスの篩

素数判定表を作りながら計算すると $$O(\sqrt{n}/\log n)$$ 。

下のコードはコンパイル時に最適化オプション付けないと`std::sqrt()`で重くなるっぽいので注意。

```cpp
#include <cmath>
#include <iostream>
#include <vector>

//n以下の素数判定表
std::vector<bool> make_prime_checklist(long n) {
    std::vector<bool> list(n + 1, true);
    list[0] = list[1] = false;
    for (int i = 4; i <= n; i += 2) list[i] = false;
    for (int i = 3; i <= std::sqrt(n); i += 2)
        if (list[i])
            for (int j = 2 * i; j <= n; j += i) list[j] = false;
    return list;
}

//n以下の素数リスト
std::vector<long> make_prime_list(long n) {
    auto list = make_prime_checklist(n);
    std::vector<long> ps;
    for (int i = 0; i < list.size(); i++)
        if (list[i]) ps.push_back(i);
    return ps;
}

int main() {
    for (auto p : make_prime_list(100)) std::cout << p << ' ';
    std::cout << std::endl;
    return 0;
}
```

## 素因数分解

### ナイーブな実装

ナイーブな実装として $$2\sim$$ の値で割れるか試していくと $$O(\sqrt{n})$$ 。
これでも十分速い。

```cpp
#include <cmath>
#include <iostream>
#include <vector>

std::vector<std::pair<long, long>> prime_factrize(long n) {
    std::vector<std::pair<long, long>> facts;
    long until = std::sqrt(n);
    for (long i = 2; n != 1 && i <= until; i++) {
        long c = 0;
        while (n % i == 0) c++, n /= i;
        if (c) facts.push_back(std::make_pair(i, c));
    }
    if (n > 1) facts.push_back(std::make_pair(n, 1));
    return facts;
}

int main() {
    for (auto p : prime_factrize(11234))
        std::cout << p.first << "**" << p.second << std::endl;
    return 0;
}
```

### 素数リストを利用

エラトステネスの篩を利用して素数リストを作ってから割れるか試していくと $$O(\sqrt{n}/\log n)$$ 程度らしい（素数定理から素数の出現率を近似）。
大量の数値の素因数分解を求めるときはこちらの方が速そう。

```cpp
//make_prime_list()が必要

//素数リストから素因数分解
std::vector<std::pair<long, long>> prime_factrize(std::vector<long> primes,
                                                  long n) {
    std::vector<std::pair<long, long>> facts;
    long until = std::sqrt(n);
    for (auto p : primes) {
        if (n == 1 || p > until) break;
        long c = 0;
        while (n % p == 0) c++, n /= p;
        if (c) facts.push_back(std::make_pair(p, c));
    }
    if (n > 1) facts.push_back(std::make_pair(n, 1));
    return facts;
}

int main() {
    long to = 10000;
    auto ps = make_prime_list(std::sqrt(to));
    for (long i = 1; i <= to; i++) {
        std::cout << i << "....";
        for (auto p : prime_factrize(ps, i))
            std::cout << p.first << "**" << p.second << ' ';
        std::cout << std::endl;
    }
    return 0;
}
```
