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
* [過渡応答](control/classical/transient_response.md)
* [1次系の応答](control/classical/first_order_system.md)
* [2次系の応答](control/classical/second_order_system.md)
* [極・零点と過渡応答](control/classical/pole_zero.md)

### 現代制御
* [状態方程式](control/modern/state_space_equation.md)
* [可制御性・可観測性](control/modern/controllability_observability.md)

----

## 計算機科学
### 論理
* [論理演算](computer_science/logic/operation.md)

### グラフ理論
* [概要](computer_science/graph_theory/intro.md)
* [プログラムにおけるグラフ表現](computer_science/graph_theory/graph_expression.md)

### アルゴリズム
* [アルゴリズムのコスト](computer_science/algorithm/execution_cost.md)
* [全探索](computer_science/algorithm/exhaustive_search.md)
* [貪欲法](computer_science/algorithm/greedy.md)
* [動的計画法１](computer_science/algorithm/dynamic_programming1.md)
* [動的計画法２](computer_science/algorithm/dynamic_programming2.md)
* [ヒープ・プライオリティキュー](computer_science/algorithm/heap.md)
* [二分探索木](computer_science/algorithm/binary_search_tree.md)

### 言語処理
* [言語処理100本ノック1](computer_science/language_processing/nlp100_1.md)
* [言語処理100本ノック2](computer_science/language_processing/nlp100_2.md)
* [言語処理100本ノック3](computer_science/language_processing/nlp100_3.md)

### セキュリティ
* [サイバー攻撃](computer_science/security/cyber-terrorism.md)
* [マルウェア](computer_science/security/malware.md)

----

## ネットワーク
### プロトコル
* [参照モデル](network/protocol/reference_model.md)
  * OSI参照モデル
  * TCP/IP階層モデル

----

## 開発関係
### デバイス
* [SteamVR / HTC Vive](develop/device/steamvr_vive.md)

### Python
* [環境](develop/python/environment.md)

### C#
* [.Netの歴史](develop/cs/dotnet_history.md)

# 参考文献

* 中山 司, 『流れ解析のための有限要素法入門』, 東京大学出版会, 2008
* 宇野 俊夫, 『独習 TCP/IP～IPv6対応～』, 翔泳社, 2010
* 秋葉 拓哉/岩田 陽一/北川 宣稔, 『プログラミングコンテストチャレンジブック 第2版』, マイナビ出版, 2012
* J. Glenn Brookshear (神林 靖/長尾 高宏 訳),  『入門コンピュータ科学～ITを支える技術と理論の基礎知識～』, アスキー・メディアワークス, 2014
