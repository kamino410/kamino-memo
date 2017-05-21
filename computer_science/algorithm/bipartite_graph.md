# 2部グラフ判定

与えられたグラフが2部グラフであるかの判定について言及する。

## 解ける問題の例

```
頂点数nの多重編・ループのない無向グラフがある。
隣接している頂点同士が違う色になるように頂点に色を塗る。
2色以内ですべての頂点を塗ることができるか判定せよ。
```

2部グラフが応用できる問題、というより2部グラフの定義そのもの。

色をつけたノードに繋がるノードを見つけて別の色を塗る、という操作を再帰的に行えば良い（深さ優先探索）。ただし、連結グラフでない可能性があるため、`main()`の中で`dfs()`を各頂点に対して呼び出す必要がある。

## 実装例

```cpp
#include <iostream>
#include <utility>
#define MAX 4

using namespace std;

int g[MAX][MAX] = {{0, 1, 0, 1}, {1, 0, 1, 1}, {0, 1, 0, 0}, {1, 1, 0, 0}};
int color[MAX];

bool dfs(int v, int c) {
  color[v] = c;
  for (int i = 0; i < MAX; i++) {
    if (g[v][i] == 1) {
      if (color[i] == c)
        return false;
      if (color[i] == 0)
        return dfs(i, c == 1 ? -1 : 1);
    }
  }
  return true;
}

int main(void) {
  for (int i = 0; i < MAX; i++)
    color[i] = 0;
  auto res = true;
  for (int i = 0; i < MAX; i++) {
    if (color[i] == 0)
      res &= dfs(0, 1);
  }
  cout << res << endl;
  return 0;
}
```
