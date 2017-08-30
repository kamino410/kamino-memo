# C++メモ

## クラスと構造体

C++の`class`と`struct`の違いはメンバーがデフォルトで`public`になるか`private`になるかだけ。

オブジェクト間の代入や値渡しはコピーになる。

### 引数

引数で値渡しをすると、コンストラクタは呼び出されないがデストラクタは呼び出される。
返り値として返す場合も一時オブジェクトが作成され、もとのオブジェクトにコピーした後、一時オブジェクトを廃棄する際にデストラクタが実行される。

そのため、内部で動的にメモリを確保しているオブジェクトを代入・値渡しするのは基本NG。
コピーコンストラクタをうまく使えばこの問題を回避できる。

## フレンド関数

```cpp
class myclass {
  int a;

public:
  void set_a(int);
  int get_a();
  friend int func(myclass);
};

int func(myclass ob) {
  myclass ob2;
  //引数・関数の内部変数のmyclassのprivateメンバーにアクセスできる
  cout << ob.a << ',' << ob2.a << endl;
}
```

## 共用体

複数の変数にメモリを共有させたもの。
型名を省略すると無名共用体となり、個々のメンバーはグローバル変数と同じ要領でアクセスできるようになる。

```cpp
union hoge {
  double d;
  unsigned char bytes[sizeof(double)];
};

int main() {
  hoge obj;

  obj.d = 1.2345;
  for (int i = 0; i < sizeof(double); i++) {
    cout << (int)obj.bytes[i] << " " << endl;
  }
}
```

## インライン関数

インラインに関する構文はあくまでコンパイラに対する「要求」であり、条件によってはインライン化されないこともある（static変数を参照している、switch文やgoto文を利用している、再帰しているなど）。
細かい部分はコンパイラ依存。

### 例1

`inline`キーワードを使う。

```cpp
class myclass {
  int a;

public:
  void set_a(int);
  int get_a();
};

inline void myclass::set_a(int num) { a = num; }

inline int myclass::get_a() { return a; }
```

### 例2

`class`の宣言内に直接書く。

```cpp
class myclass {
  int a;

public:
  void set_a(int num) { a = num; };
  int get_a() { return a; };
};
```
