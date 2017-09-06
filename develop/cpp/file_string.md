# ファイル・文字列

## 文字列->数値

`stringstream`を使うとよしなにしてくれるので楽。

```cpp
#include <iostream>
#include <sstream>
using namespace std;

int main() {
    stringstream ss;
    double d;

    ss << "12.345";
    ss >> d;

    cout << d << endl;
}
```

## 文字列のフォーマット

`cout`でフォーマットを指定するなら`boost`を使わないといけない。

```cpp
#include <boost/format.hpp>
#include <iostream>
using namespace std;

int main() {
    cout << boost::format("%2% %1%") % 3 % std::string("Hello") << endl;
}
```

面倒なので`stdio.h`を使う方が無難ではある。

## 文字列のsplit

`boost`にsplitがあるが、専用のAPIを覚えるのも面倒なので自前で実装する例を示す。

### char区切り文字

```cpp
#include <iostream>
#include <sstream>
using namespace std;

template <typename Enumerable>
void split(const std::string& s, char delim, Enumerable& res) {
    res.clear();

    std::stringstream ss(s);
    std::string item;

    while (std::getline(ss, item, delim)) {
        if (!item.empty()) { res.push_back(item); }
    }
}
```

### string区切り文字

```cpp
template <typename Enumerable>
void split(const std::string& s, const std::string& delim, Enumerable& res) {
    res.clear();
    std::string::size_type prep = 0;
    while (prep != std::string::npos) {
        std::string::size_type p = s.find(delim, prep);
        if (p == string::npos) {
            res.push_back(s.substr(prep));
            break;
        } else {
            res.push_back(s.substr(prep, p - prep));
        }
        prep = p + delim.size();
    }
}
```

## ファイルから1行ずつ読み込み

```cpp
#include <fstream>
#include <iostream>
using namespace std;

int main() {
    ifstream fr;
    string line;

    fr.open("input.txt", ios::in);
    if (!fr.is_open()) cout << "file open failed" << endl;

    while (getline(fr, line)) { cout << line << endl; }
}
```
