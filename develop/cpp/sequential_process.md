# シーケンシャル処理

`<algorithm>`に色々あるっぽい。
linqの遅延実行のような機能はないので、毎回結果を格納する領域を確保しておく必要がある。

## all/any/none

`std::all_of`,`std::any_of`,`std::none_of`を使う。

```cpp
#include <algorithm>
#include <iostream>

int main() {
    int nums[] = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9};

    if (std::all_of(nums, nums + sizeof(nums) / sizeof(int),
                    [](int x) { return x >= 0; }))
        std::cout << "all numbers are not negative" << std::endl;
    else
        std::cout << "has some negative numbers" << std::endl;
}
```

## foreach

同じ配列上で処理を行う場合は`std::for_each`を使う。

```cpp
#include <algorithm>
#include <iostream>

int main() {
    int nums[] = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9};

    std::for_each(nums, nums + sizeof(nums) / sizeof(int),
                  [](int& x) { x *= 2; });
    for (auto x : nums) std::cout << x << ' ';
    std::cout << std::endl;
}
```

## map

`std::transform`を使う。
変換先の領域は予め確保しておく必要がある。
戻り値は末尾ポインタ。

メモリの使用量が気になる場合は`std::vector`へコピーして後から`resize`で縮める。

```cpp
#include <algorithm>
#include <iostream>

int main() {
    int nums[] = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9};
    char chs[10];

    char* end = std::transform(nums, nums + sizeof(nums) / sizeof(int), chs,
                               [](int x) { return 'a' + x; });

    std::for_each(chs, end, [](char x) { std::cout << x << ' '; });
    std::cout << std::endl;
}
```

## filter

`std::copy_if`を使う。
`map`同様にコピー先の領域は予め確保しておく必要がある。
戻り値は末尾ポインタ。

```cpp
#include <algorithm>
#include <iostream>

int main() {
    int nums[] = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9};
    int odds[10];

    int* end = std::copy_if(nums, nums + sizeof(nums) / sizeof(int), odds,
                            [](int x) { return x % 2; });

    std::for_each(odds, end, [](int x) { std::cout << x << ' '; });
    std::cout << std::endl;
}
```

## if & erase

`for`と`erase`を組み合わせる。

```cpp
#include <iostream>
#include <vector>

int main() {
    std::vector<int> nums = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9};

    for (auto it = nums.begin(); it != nums.end();) {
        if (*it % 2 == 0)
            it = nums.erase(it);
        else
            it++;
    }

    for (auto n : nums) std::cout << n << ' ';
    std::cout << std::endl;
}
```
