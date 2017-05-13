かみのの勉強メモです。

# 目次

## 数学

### 線形代数
* [行列式](mathematics/linear_algebra/determinant.md)

### 解析学
* [ラプラス変換](mathematics/analysis/laplace_transform.md)
* [フーリエ変換](mathematics/analysis/fourier_transform.md)

----

## 数値解析
### 有限要素法
* [1次元の重み付き残差法](numerical_analysis/finite_element_method/1-dimention.md)
* [2次元の重み付き残差法（ラプラス方程式）](numerical_analysis/finite_element_method/laplaces_equation.md)

----

## 制御理論
### 概論
* [古典制御理論と現代制御理論](control/classical_vs_modern.md)
* [線形システム](control/linear_system.md)

### 古典制御理論
* [伝達関数１](control/classical/transfer_function1.md)
  * 伝達関数表現
* [伝達関数２](control/classical/transfer_function2.md)
  * 伝達関数とブロック線図
  * むだ時間を含む系
* [伝達関数３](control/classical/transfer_function3.md)
  * proper／strictly proper／improperな伝達関数
* [インパルス応答とステップ応答](control/classical/impulse_step_response.md)
* [1次系の応答](control/classical/first_order_system.md)
* [2次系の応答](control/classical/second_order_system.md)

### 現代制御
* [状態方程式](control/modern/state_space_equation.md)
* [可制御性・可観測性](control/modern/controllability_observability.md)

----

## 計算機科学
### 論理
* [論理演算](computer_science/logic/operation.md)

### アルゴリズム
* [アルゴリズムのコスト](computer_science/algorithm/execution_cost.md)
* [全探索](computer_science/algorithm/exhaustive_search.md)
* [貪欲法](computer_science/algorithm/greedy.md)
* [動的計画法１](computer_science/algorithm/dynamic_programming1.md)
* [動的計画法２](computer_science/algorithm/dynamic_programming2.md)

### 言語処理
* [言語処理100本ノック1](computer_science/language_processing/nlp100_1.md)
* [言語処理100本ノック2](computer_science/language_processing/nlp100_2.md)
* [言語処理100本ノック3](computer_science/language_processing/nlp100_3.md)

----

## ネットワーク
### プロトコル
* [参照モデル](network/protocol/reference_model.md)
  * OSI参照モデル
  * TCP/IP階層モデル

----

## 開発関係
### Linux
* [ssh](develop/linux/ssh.md)
* [Vim](develop/linux/vim.md)
* [init.vim](develop/linux/init_vim.md)

### Python
* [環境](develop/python/environment.md)

# 参考文献

* 中山 司, 『流れ解析のための有限要素法入門』, 東京大学出版会, 2008
* 宇野 俊夫, 『独習 TCP/IP～IPv6対応～』, 翔泳社, 2010
* 秋葉拓哉/岩田陽一/北川宣稔, 『プログラミングコンテストチャレンジブック 第2版』, マイナビ出版, 2012
