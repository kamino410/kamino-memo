# ビット配列を用いた演算

C言語で大規模なフラグを管理するときに利用する。

C++では`bool[]`を使えば良いが、`bool`は1変数あたり1byteが確保されるためそこそこ空間計算量に無駄がある。
この実装を使えばデータ容量を1/8程度に抑えられるため、空間計算量のオーダーを1つ弱下げることができる。

次のようなマクロを定義するのが鉄板らしい（C FAQという資料が出典？）。

```cpp
// int型をバケットとし、バケットの配列 uint64_t[] で1つの整数を管理する

// int型のビット数=バケット1つのサイズ
#define BUCKET_BITS (uint64_t)(sizeof(uint64_t) * 8)
// (b+1)番目のビットだけが1のバケットを返す
#define BITMASK(b) (1ul << ((b) % BUCKET_BITS))
// b番目のビットが属するバケットのindex
#define BITSLOT(b) ((b) / BUCKET_BITS)
// aのb番目のビットを1にする
#define BITSET(a, b) ((a)[BITSLOT(b)] |= BITMASK(b))
// aのb番目のビットを0にする
#define BITCLEAR(a, b) ((a)[BITSLOT(b)] &= ~BITMASK(b))
// aのb番目のビットが1かどうか
#define BITTEST(a, b) ((a)[BITSLOT(b)] & BITMASK(b))
// 数nbを表すために必要なバケットの数
#define BITNSLOTS(nb) ((nb + BUCKET_BITS - 1ul) / BUCKET_BITS)
```
