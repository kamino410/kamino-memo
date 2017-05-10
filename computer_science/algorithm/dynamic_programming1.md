# 動的計画法１（Dynamic Programming）

問題を部分問題に分割したうえで、部分問題の計算結果を記録しながら解いていくアルゴリズム。

特徴としては

* 分割統治法を利用する
  * 部分問題を再帰的に解くことで問題全体を解く
* メモ化
  * 前のステップで計算した評価値を利用して次のステップの評価値を計算する

## 解ける問題の例１

有名な問題として01ナップサック問題がある。

```
重さ$$w_i$$、価値$$v_i$$の品物がn個ある。
ここから重さの総和がWを超えないように持っていく品物を選ぶ。
持っていける品物の総価値の最大値はいくらか？
```

この問題を全探索で解くと $$O(2^n)$$ の処理になる。

全探索の場合`xxxx010`の重さと価値の総和を計算するという処理が難度も実行されており、計算量がかさむ要因になっている。
そこでこの計算をメモ化してみる。

### 使う品物・重さの制限を絞り部分問題とする方法

i番目までの品物から重さの総和がj以下になるよう選択したときの価値の最大値をテーブルに記憶するとする。

このとき、各要素を$$dp[i,j]$$とすると

<center>
$$
\begin{eqnarray}
dp[0,j] &=& 0 \\
dp[i+1,j] &=&
\begin{cases}
dp[i,j] & (j < w_i) \\
max(dp[i,j], dp[i, j-w_i]+v_i) & else
\end{cases}
\end{eqnarray}
$$
</center>

の漸化式が立てられる。

この方法では計算量は$$O(nW)$$となり、$$W$$が極端に大きくならない限りは十分効率的なアルゴリズムといえる。

#### 実装例

どの組み合わせが利用されたかの列挙も表示する例。

最大値だけが欲しい場合は後半のラムダ式以降を削ればよい。

```cpp
#include<iostream>
#include<algorithm>
#include<vector>

using namespace std;

int main (void) {
    const int N = 4;
    const int W = 5;
    int products[N][2] = {
        { 2, 3 },
        { 1, 2 },
        { 3, 4 },
        { 2, 2 }
    };
    
    //----------
    
    int dp[N + 1][W + 1];

    for (int i = 0; i <= N; i++)
        for (int j = 0; j <= W; j++)
            dp[i][j] = 0;

    //----------

    for (int i = 0; i < N; i++)
        for (int j = 1; j <= W; j++)
            if (j < products[i][0])
                dp[i + 1][j] = dp[i][j];
            else
                dp[i + 1][j] = max(dp[i][j], dp[i][j - products[i][0]] + products[i][1]);
    
    cout << dp[N][W] << endl << endl;

    //----------

    function<void(int,int,vector<int>)> f = [&](int i, int j, vector<int> v){
        if (i == 0){
            for (auto num : v)
                cout << num << ',';
            cout << endl;
            return;
        }

        if (dp[i][j] == dp[i - 1][j])
            f(i - 1, j, v);

        int pj = j - products[i - 1][0];
        if (pj >= 0 && dp[i][j] == dp[i - 1][pj] + products[i - 1][1]) {
            v.push_back(i);
            f(i - 1, pj, v);
            v.pop_back();
        }
        return;
    };    
    
    vector<int> a;
    f(N, W, a);

    return 0;
}

```

### 使う品物・価値の制限を絞り部分問題とする方法



#### 実装例

