# 単一始点最短経路問題

## 問題の特徴

* 始点から各頂点への最短距離を求める
* 「"最短距離が確定している頂点"に隣接する頂点の最短距離を再計算する」を繰り返せば全ての点への最短距離が求まる。
* 負の閉路がある場合は最短距離が定まらないため解けない

## ベルマンフォード（Bellman-Ford）法

重み付きグラフの単一始点最短経路問題を解くための手法。

次のような特徴がある。

* 負の重み付けがあっても対応できる
* 負の閉路の検出が可能
* 隣接行列を用いたときの計算量は $$O(|V|^3)$$
* 隣接リストを用いたときの計算量は $$O(|V|\cdot |E|)$$

### 手法

1. 頂点 $$i$$ までのその時点での最短距離を $$d[i]$$ に格納するものとする。

1. 以下の式を全ての頂点に対して繰り返し実行し、すべての $$d[i]$$ が更新されなくなったら計算が完了したものとする。ただし $$d[s] = 0$$（始点）, $$d[i]=INF$$ を初期値として利用する。

$$
d[i] = \min\{d[j]+c_{ji}\ |\ e=(i,j)\in E\}
$$

全ての頂点に対して繰り返し実行するのは、グラフが負の重み付けを持つ場合、最短距離が確定しているかの判断ができないため。

### 負の閉路の判定

負の閉路がない限り、$$d[i]$$ の更新は高々 $$|V|-1$$ 回しか行われないため、検証のアルゴリズムは最大でも $$(|V|-1)\cdot |E|$$ 回しか実行されない。

そのため、この回数を超えてループが実行されていればグラフに負の回路が存在することがわかる。

### 問題例

#### グラフ1

```mermaid
graph LR;
  A((A:始点))-->|2|B((B));
  B-->|4|C((C));
  A-->|5|C;
  B-->|10|E((E));
  B-->|6|D((D));
  C-->|2|D;
  E-->|3|F((F));
  D-->|-1|F;
  E-->|5|G((G));
  F-->|9|G;
```

#### グラフ2

```mermaid
graph LR;
  A((A:始点))-->|2|B((B))
  A-->|3|C((C))
  C-->|-1|B
  B-->|-3|D((D))
  D-->|2|C
```

### 実装例

無向グラフを検証する場合は逆向きの辺を追加することで対応できる。

```rust
struct Edge {
    from: usize,
    to: usize,
    cost: isize,
}

struct Vert {
    dist: isize,
    updated: bool,
}

struct Graph {
    vert_count: usize,
    start_vert: usize,
    edges: Vec<Edge>,
}

fn bellman_ford(graph: &Graph) -> Result<Vec<isize>, &str> {
    let mut verts: Vec<Vert> = Vec::new();
    for _ in 0..graph.vert_count {
        verts.push(Vert { dist: 0, updated: false });
    }
    verts[graph.start_vert].updated = true;

    for _ in 0..(graph.vert_count - 1) {
        let mut updated = false;
        for e in graph.edges.iter() {
            if verts[e.from].updated &&
                (!verts[e.to].updated || verts[e.from].dist + e.cost < verts[e.to].dist)
            {
                verts[e.to].dist = verts[e.from].dist + e.cost;
                verts[e.to].updated = true;
                updated = true;
            }
        }
        if !updated {
            return Ok(verts.iter().map(|v| v.dist).collect());
        }
    }
    Err("graph has negative circuit")
}

fn main() {
    let mut edges: Vec<Edge> = Vec::new();
    edges.push(Edge { from: 0, to: 1, cost: 2 });
    edges.push(Edge { from: 1, to: 2, cost: 4 });
    edges.push(Edge { from: 0, to: 2, cost: 5 });
    edges.push(Edge { from: 1, to: 4, cost: 10 });
    edges.push(Edge { from: 1, to: 3, cost: 6 });
    edges.push(Edge { from: 2, to: 3, cost: 2 });
    edges.push(Edge { from: 4, to: 5, cost: 3 });
    edges.push(Edge { from: 3, to: 5, cost: -1 });
    edges.push(Edge { from: 4, to: 6, cost: 5 });
    edges.push(Edge { from: 5, to: 6, cost: 9 });

    let graph = Graph { vert_count: 7, start_vert: 0, edges };

    let res = bellman_ford(&graph);

    match res {
        Ok(v) => {
            for d in v.iter() {
                println!("{}", d);
            }
        }
        Err(s) => println!("{}", s),
    }
}
```

#### グラフ1

```
0
2
5
7
12
6
15
```

#### グラフ2

```
graph has negative circuit
```

## ダイクストラ（Dijkstra）法

非負の重み付きグラフの単一始点最短経路問題を解くための手法。

次のような特徴がある。

* 隣接行列を用いたときの計算量は $$O(|V|^2)$$
* プライオリティーキューを用いたときの計算量は $$O(|E|\log |V|)$$

### 手法

重み付けが非負である場合、「未検証の頂点のうち最も $$d[i]$$ が小さいものから順に隣接する頂点の最短距離を再計算する」を繰り返せば、最も $$d[i]$$ が小さい頂点は最短距離が確定していることが帰納的に保証されるため、全ての頂点について最短距離が求まる。

```cpp

```
