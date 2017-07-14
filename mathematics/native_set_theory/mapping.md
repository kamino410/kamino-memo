# 写像（mapping）

## 定義

集合 $$X,Y$$ があり、集合 $$X$$ の各元について対応するただ１つの $$Y$$ の元が定まっているとき、この対応を $$X$$ から $$Y$$ への**写像 $$f$$**という。

このときの $$X$$ を**始集合（源/source）**、$$Y$$ を**終集合（行き先/target/destination）**と呼ぶ。
特に終集合が数であるとき $$f$$ を**関数**と呼ぶ。

また、$$f$$ が部分集合 $$W \subset X$$ についてのみ定義されているとき $$W$$ を写像の**定義域**と呼ぶ。

## 写像の表現方法

* 内包的表現（intensional expression）
  * $$x\in X$$ に対応する行き先 $$y\in Y$$ を式などで記述する方法
* 外延的表現（extensional expression）
  * $$x\in X$$ に対応する行き先 $$y\in Y$$ を一組ずつ記述する方法
  * 元が無限個のときには厳密さに欠ける表現となる

## グラフ（graph）

写像 $$f:X \rightarrow Y$$ について、直積 $$X \times Y$$ の部分集合

$$
\Gamma_f := \{(x,f(s)) \ | \ x \in X \} \subset X \times Y
$$

を **$$f$$ のグラフ**という。

## 像・逆像（image / inverse image）

写像 $$f:X \rightarrow Y$$ があるとき、 $$A \subset X$$ の各元の行き先の集合 $$f(A)$$ を **$$A$$ の像**と呼ぶ。

$$
f(A) := \{f(x) \ | \ x \in A \} = \{y \in Y \ | \ \exists x \in X(y = f(x)) \}
$$

また、$$B \subset Y$$ の各元を行き先に持つ $$X$$ の元の集合 $$f^{-1}(B)$$ を **$$B$$ の逆像**と呼ぶ。

$$
f^{-1}(B) := \{x \in X \ | \ f(x) \in B \}
$$

## 写像の分類

### 全射

写像 $$f:X \rightarrow Y$$ があるとき、すべての $$x\in X$$ に対して対応する $$x \in X$$ が存在するとき、$$f$$ は**全射**であるという。

$$
\forall y \in Y ( \exists x \in X (y = f(x)))
$$

### 単射

写像 $$f:X \rightarrow Y$$ があるとき、すべての $$x \in X$$ がそれぞれ異なる $$y \in Y$$ に対応するとき、$$f$$ は**単射**であるという。

$$
\forall x_1, x_2 \in X ((f(x_1) = f(x_2))\rightarrow (x_1 = x_2))
$$

### 全単射

写像 $$f:X \rightarrow Y$$ が全射かつ単射であるとき、$$f$$ は**全単射**であるという。
