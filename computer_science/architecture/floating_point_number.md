# 浮動小数点数（floating point number）

主にコンピューターで小数を表すための数値表現手法。

## 原理

浮動小数点数では**符号ビット**・**指数フィールド**・**仮数フィールド**の3つで数値を保持する。

### IEEE 754の仕様

基数2の基本形式のみを示す。

参考：https://www.csee.umbc.edu/~tsimo1/CMSC455/IEEE-754-2008.pdf

#### 各部のビット長と指数バイアス値

||符号：S|指数：E|仮数：T|バイアス|
|----|----|----|----|----|
|symbol|$$b$$|$$w$$|$$t$$|$$bias$$|
|単精度(float)|1bit|8bit|23bit|127|
|倍精度(double)|1bit|11bit|52bit|1023|
|四倍制度|1bit|15bit|112bit|16383|

#### 表現値

||S|E|T|備考|
|----|----|----|----|----|
|qNan|$$*$$|$$2^w-1$$（全部`1`）|IEEEによる指定はなし|エラーを出さず伝播する|
|sNan|$$*$$|$$2^w-1$$（全部`1`）|IEEEによる指定はなし|エラーを出す|
|$$+\infty$$|$$0$$|$$2^w-1$$（全部`1`）|$$0$$（全部`0`）||
|$$-\infty$$|$$1$$|$$2^w-1$$（全部`1`）|$$0$$（全部`0`）||
|$$(-1)^S \times 2^{E-bias} \times (1+2^{-t}\times T)$$|$$*$$|$$1\sim 2^w-2$$|$$*$$|ケチ表現|
|$$(-1)^S \times 2^{1-bias} \times (0+2^{-t}\times T)$$|$$*$$|$$0$$|$$*$$||
|$$(-1)^S \times (+0)$$|$$*$$|$$0$$|$$0$$|符号付き0|