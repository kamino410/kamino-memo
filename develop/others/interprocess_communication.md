# プロセス間通信

## 手法

プロセス間でデータをやり取りするための手法はいくつか存在する。
基本的にOS依存のため、特定のOSで動作しなかったりAPIが異なったりする。

* メッセージキュー
* ソケット
* パイプ
* セマフォ
* 共有メモリ
* メモリマップドファイル

## python

### パイプ

`subprocess`を使えばとりあえず動いた。
ただし、書き込みが終わった後に`flush`が必要なため、子プロセス側で明示的に`flush`していないケースではうまくいかなかった。

子
```cpp
#include <iostream>

using namespace std;

int main() {
    int a;
    cin >> a;
    cout << a << endl << feof;
}
```

親
```py
import subprocess as sub

# shellを経由するときは shell = True のオプションを付ける
p = sub.Popen("./a.out", stdin=sub.PIPE, stdout=sub.PIPE, )

p.stdin.write("5\n".encode())

lines = p.stdout.read()
print(lines)
if p.poll() is None:
    p.terminate()
```
