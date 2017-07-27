# Union-Find木

素集合を管理するためのデータ構造。
内部に複数の木構造を持ち、1つの木が1つの集合に相当する。

## 実装例

* 集合に根を1つ定義する。
* 初期状態は全ての値が独立した状態とする。
* ある値同士が同じ集合に属しているかは次のように判定する。
  1. 葉から順に値を探索する
  1. 発見したノードの親を辿り、木の根を見つける
     * このとき辿ったノードを根に直接繋げ、次の探索を高速化する（木の縮退）
  1. 辿り着いた根が同じであれば2つの値は同じ集合に属する
* 2つの集合は次のように併合する。
  1. 各集合の根を見つける
  1. 片方の根をもう片方の根の子ノードにする
* サイズは併合の際に計算し保持する。
  * 集合のサイズを求めるには全ノードの走査が必要となってしまうため

簡単のため集合の分割はできないものとする。

```cpp
#include <functional>
#include <iostream>
#include <vector>

using namespace std;

// Union-Find-Tree
struct UnionFind {
  vector<int> par;   //そのノードの親ノード
                     //（根ノードは自分を参照）
  vector<int> sizes; //そのノードを根とする木のサイズ
                     //（根でないノードについては無意味）
  int N;

  UnionFind(int n) : par(n), sizes(n, 1) {
    for (int i = 0; i < n; i++)
      par[i] = i;
    N = n;
  }

  int find(int x) {
    if (par[x] == x)
      return x;
    else
      return par[x] = find(par[x]);
  }

  void unite(int x, int y) {
    x = find(x);
    y = find(y);
    if (x == y)
      return;

    if (sizes[x] < sizes[y]) {
      par[x] = y;
      sizes[y] += sizes[x];
    } else {
      par[y] = x;
      sizes[x] += sizes[y];
    }
  }

  void show() {
    function<void(int)> f = [&](int x) {
      cout << x << ',';
      for (int y = 0; y < N; y++) {
        if (par[y] == x && y != x)
          f(y);
      }
    };
    for (int i = 0; i < N; i++) {
      if (par[i] == i) {
        f(i);
        cout << endl;
      }
    }
  }

  bool same(int x, int y) { return find(x) == find(y); }

  int size(int x) { return sizes[find(x)]; }
};

int main(void) {
  UnionFind uf(5);

  uf.unite(0, 1);
  uf.unite(1, 2);
  uf.show();

  return 0;
}
```
