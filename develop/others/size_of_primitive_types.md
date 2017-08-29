# プリミティブ型のサイズ

## C++

>Configured with: --prefix=/Library/Developer/CommandLineTools/usr --with-gxx-include-dir=/usr/include/c++/4.2.1

>Apple LLVM version 8.1.0 (clang-802.0.42)

>Target: x86_64-apple-darwin16.7.0

>Thread model: posix


```cpp
#include <climits>
#include <iostream>

using namespace std;

int main() {
  cout << "sizeof(int) : " << sizeof(int) << endl;
  cout << "INT_MAX : " << INT_MAX << endl;
  cout << "sizeof(long) : " << sizeof(long) << endl;
  cout << "LONG_MAX : " << LONG_MAX << endl;
  cout << "sizeof(long long) : " << sizeof(long long) << endl;
  cout << "LLONG_MAX : " << LLONG_MAX << endl;
}
```

```
sizeof(int) : 4
INT_MAX : 2147483647
sizeof(long) : 8
LONG_MAX : 9223372036854775807
sizeof(long long) : 8
LLONG_MAX : 9223372036854775807
```

## rust

>rustc 1.19.0 (0ade33941 2017-07-17)

```rust
use std::mem::size_of;

fn main() {
    println!("size of i32 : {}", size_of::<i32>());
    println!("max value of i32 : {}", i32::max_value());
    println!("size of i64 : {}", size_of::<i64>());
    println!("max value of i64 : {}", i64::max_value());
    println!("size of isize : {}", size_of::<isize>());
    println!("max value of isize : {}", isize::max_value());
}
```

```
size of i32 : 4
max value of i32 : 2147483647
size of i64 : 8
max value of i64 : 9223372036854775807
size of isize : 8
max value of isize : 9223372036854775807
```

## python

3系からはサイズに上限がなくなった（ただし当然ながら`float`のサイズには上限がある）。
