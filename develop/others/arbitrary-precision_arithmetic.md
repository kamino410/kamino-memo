# 任意精度演算（arbitrary-precision arithmetic）

**任意精度演算**とは数値の精度を任意に設定できるような演算システムによる演算を指す。

通常の命令セットに組み込まれている32bit/64bitの整数・浮動小数点数では扱えない桁数の大きな数値を扱うために利用する。
プロセッサーのアキュムレーターではなくソフトウェア的な実装によって演算を行うためパフォーマンスは低下する。

主な利用目的として公開鍵番号方式の実装などがある。

## 使用例

### 多倍長整数

rustの場合は[rust-num](https://github.com/rust-num/num)に`BigInt`があるのでこれを使う。
現状decimalは公式には出ていない。

```rust
extern crate num;
use num::bigint::BigInt;

use std::io::{stdin, stdout, Write};

fn main() {
    let mut s1 = String::new();
    let mut s2 = String::new();

    print!("Please enter first number : ");
    let _ = stdout().flush();
    stdin().read_line(&mut s1).expect(
        "Did not enter a correct string",
    );

    print!("Please enter first number : ");
    let _ = stdout().flush();
    stdin().read_line(&mut s2).expect(
        "Did not enter a correct string",
    );

    match (s1.trim().parse::<BigInt>(), s2.trim().parse::<BigInt>()) {
        (Ok(n1), Ok(n2)) => println!("{}", n1 + n2),
        _ => println!("parse faild"),
    }
}
```

```rust
extern crate num;
use num::bigint::BigInt;
use num::bigint::ToBigInt;

fn main() {
    let n = 1202303.to_bigint().unwrap();
    let m = 1134523.to_bigint().unwrap();
    println!("{}", n * m);
}
```

C++の場合はGMP（GNU Multiple Precision Arithmetic library）というライブラリがある。

```
brew install gmp
```

```
g++ main.cpp -lgmpxx -lgmp
```

```cpp
#include<iostream>
#include<gmpxx.h>

using namespace std;

int main (void){
  mpz_class a, b;
  a.set_str("1231345234523", 10);
  b.set_str("2352342347856", 10);
  a += b;
  cout << a.get_str() << endl;
}

```

### 任意精度浮動小数点数

pythonのdecimalは任意精度演算に対応している。

```py
from decimal import Decimal
a = 32 - (54.2 - 52.0) / 0.1
b = int(32 - (54.2 - 52.0) / 0.1)

#数値で書いた時点で基数2に変換されてしまうので文字列からdecimalに変換する
c = 32 - (Decimal('54.2') - Decimal('52.0')) / Decimal('0.1')

print(a, b, c)

```

```
9.999999999999972 9 10
```

C++とGMP。

```cpp
#include<iostream>
#include<gmpxx.h>

using namespace std;

int main (void){
  mpf_class a, b;
  a.set_str("12313452.34523", 10);
  b.set_str("235.2342347856", 10);
  a += b;
  mpf_out_str(stdout, 10, 0, a.get_mpf_t());
  cout << endl;
}

```
