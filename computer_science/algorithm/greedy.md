# 貪欲法（Greedy algorithm）

問題を部分問題に分割したうえで、その場の評価値が最大になる選択肢を選びながら部分問題を解いていく手法。
欲張り法、グリーディ算法とも。

特徴としては

* 手続きの中で現在解いている問題しか保持しない・一度選択した要素を再考しない
  * つまり問題の「保留」はしない
* 部分問題の評価値の計算方法・ソートのアルゴリズムだけで実装できる
* 多項式時間で解ける
* 得られる解が最適解である保証はない

## 厳密解が求まる問題の例

```
n個の仕事がある。
各仕事は時刻$$s_i$$に始まり$$t_i$$に終わる。
また、開始時刻と終了時刻が一致する仕事を兼任することはできない。
できるだけ多くの仕事に参加するにはどうすればよいか。
```

この問題は、開始時刻からスタートし「終了時刻が最も早い仕事を選んでその時刻に立つ」を繰り返せば最適解が得られる。

## 実装例（C++）

>g++ (Ubuntu 4.8.4-2ubuntu1~14.04.3) 4.8.4

```cpp
#include<iostream>
#include<algorithm>

using namespace std;

int main (void) {
    const int N = 10;
    int work_period[N][2] = {
        { 1, 2 }, { 1, 3 }, { 2, 5 },
        { 3, 7 }, { 4, 5 }, { 5, 6 },
        { 8, 9 }, { 7, 9 }, { 6, 10 },
        { 8, 10 }
    };
    
    //----------
    
    pair<int, int> itv[N];
    
    for (int i = 0; i < N; i++) {
        itv[i].first = work_period[i][1];
        itv[i].second = work_period[i][0];
    }
    sort(itv, itv + N);
    
    int ans = 0, t = 0;
    for (int i = 0; i < N; i++) {
        if(t < itv[i].second) {
            ans++;
            t = itv[i].first;
        }
    }
    
    cout << ans << endl;
    
    return 0;
}
```
