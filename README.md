かみのの勉強メモです。

# 目次

* 数学
  * 集合論
    * [集合](mathematics/set_theory/set.md)
    * [ZFC公理系](mathematics/set_theory/zfc_set_theory.md)
  * 数理論理学
    * [古典命題論理](mathematics/mathematical_logic/classical_propositional_logic.md)
    * [述語論理](mathematics/mathematical_logic/predicate_logic.md)
  * 代数学
    * [群](mathematics/algebra/group.md)
    * [環](mathematics/algebra/ring.md)
  * 線形代数
    * [行列式・対角和](mathematics/linear_algebra/determinant.md)
    * [特殊な行列](mathematics/linear_algebra/characteristic_matrix.md)
    * [階数・逆行列](mathematics/linear_algebra/inverse_matrix.md)
    * [ベクトル空間](mathematics/linear_algebra/vector_space.md)
    * [固有値問題](mathematics/linear_algebra/eigenvalue.md)
    * [相似変換](mathematics/linear_algebra/similarity_transformation.md)
    * [ジョルダン標準形・対角化](mathematics/linear_algebra/diagonalization.md)
  * 解析学
    * [ラプラス変換](mathematics/analysis/laplace_transform.md)
    * [フーリエ変換](mathematics/analysis/fourier_transform.md)
    * [凸集合・凸関数](mathematics/analysis/convex.md)
    * [ラグランジュ乗数法](mathematics/analysis/lagrange_multiplier.md)
  * 確率・統計
    * [確率分布](mathematics/statistics/probability_distribution.md)
* 計画数学
  * 線形計画法
    * [概要](mathematical_programming/linear/intro.md)
    * [シンプレックス法](mathematical_programming/linear/simplex_method.md)
    * [線形計画問題を解くプログラム](mathematical_programming/linear/program.md)
  * 非線形計画法
    * [無制約最小化問題](mathematical_programming/nonlinear/unconstrained.md)
    * [等式制約付き最小化問題](mathematical_programming/nonlinear/equality_constrained.md)
    * [一般の制約付き最小化問題](mathematical_programming/nonlinear/constrained.md)
* 数値解析
  * 有限要素法
    * [1次元の重み付き残差法](numerical_analysis/finite_element_method/1-dimention.md)
    * [2次元の重み付き残差法（ラプラス方程式）](numerical_analysis/finite_element_method/laplaces_equation.md)
    * [数値計算例](numerical_analysis/finite_element_method/examples.md)
* 制御理論
  * 概論
    * [概要](control/abstract/intro.md)
    * [線形システム](control/abstract/linear_system.md)
  * 古典制御理論
    * [伝達関数１](control/classical/transfer_function1.md)
    * [伝達関数２](control/classical/transfer_function2.md)
    * [伝達関数３](control/classical/transfer_function3.md)
    * [インパルス応答とステップ応答](control/classical/impulse_step_response.md)
    * [過渡応答](control/classical/transient_response.md)
    * [1次系の応答](control/classical/first_order_system.md)
    * [2次系の応答](control/classical/second_order_system.md)
    * [極・零点と過渡応答](control/classical/pole_zero.md)
    * [線形システムの安定性](control/classical/stability.md)
    * [フィードバック制御系の特性](control/classical/feedback.md)
    * [根軌跡](control/classical/root_locus.md)
    * [周波数応答](control/classical/frequency_response.md)
    * [ボード線図](control/classical/bode_diagram.md)
    * [フィードバック制御系の内部安定性](control/classical/stability_of_feedback.md)
  * 現代制御理論
    * [状態方程式](control/modern/state_space_equation.md)
    * [可制御性・可観測性](control/modern/controllability_observability.md)
    * [可制御正準形・可観測正準形](control/modern/canonical_form.md)
    * [正準分解](control/modern/canonical_decomposition.md)
* 計算機科学
  * グラフ理論
    * [概要](computer_science/graph_theory/intro.md)
    * [プログラムにおけるグラフ表現](computer_science/graph_theory/graph_expression.md)
  * アルゴリズム
    * [アルゴリズムのコスト](computer_science/algorithm/execution_cost.md)
    * [ソートアルゴリズム1](computer_science/algorithm/sort1.md)
    * [ソートアルゴリズム2](computer_science/algorithm/sort2.md)
    * [ソートアルゴリズム3](computer_science/algorithm/sort3.md)
    * [全探索](computer_science/algorithm/exhaustive_search.md)
    * [貪欲法](computer_science/algorithm/greedy.md)
    * [動的計画法１](computer_science/algorithm/dynamic_programming1.md)
    * [動的計画法２](computer_science/algorithm/dynamic_programming2.md)
    * [ヒープ・プライオリティキュー](computer_science/algorithm/heap.md)
    * [二分探索木](computer_science/algorithm/binary_search_tree.md)
    * [Union-Find木](computer_science/algorithm/union_find_tree.md)
    * [2部グラフ判定](computer_science/algorithm/bipartite_graph.md)
    * [最短経路問題](computer_science/algorithm/shortest_path.md)
  * 機械学習
    * [概要](computer_science/machine_learning/abstract.md)
    * [サポートベクターマシン](computer_science/machine_learning/svm.md)
    * [scikit-learnでMNIST](computer_science/machine_learning/scikit_mnist.md)
  * 言語処理
    * [言語処理100本ノック1](computer_science/language_processing/nlp100_1.md)
    * [言語処理100本ノック2](computer_science/language_processing/nlp100_2.md)
    * [言語処理100本ノック3](computer_science/language_processing/nlp100_3.md)
    * [言語処理100本ノック4](computer_science/language_processing/nlp100_4.md)
  * グラフィック
    * [ベジェ曲線](computer_science/graphic/bezier_curve.md)
  * セキュリティ
    * [サイバー攻撃](computer_science/security/cyber-terrorism.md)
    * [マルウェア](computer_science/security/malware.md)
* ネットワーク
  * プロトコル
    * [参照モデル](network/protocol/reference_model.md)
* 人力飛行機
  * [カメラ計測](hpa/camera_mesurement.md)
  * [翼型のベジェ曲線表現](hpa/foil_bezier.md)
* 開発関係
  * デバイス
    * [SteamVR / HTC Vive](develop/device/steamvr_vive.md)
    * [GPU](develop/device/gpu.md)
  * Git
    * [自分用の設定](develop/git/environment.md)
  * Python
    * [環境](develop/python/environment.md)
    * [matplotlib template](develop/python/matplotlib_template.md)
    * [行列演算](develop/python/matrix_operation.md)
    * [JUMAN/KNP](develop/python/juman_knp.md)
  * C#
    * [.Netの歴史](develop/cs/dotnet_history.md)
  * GitBook
    * [自分用の設定](develop/gitbook/my_setting.md)

# 参考文献

* 中島 匠一, 『代数と数論の基礎』, 共立出版株式会社, 2000
* 矢部 博, 『工学基礎 最適化とその応用』, 数理工学社, 2006
* 中山 司, 『流れ解析のための有限要素法入門』, 東京大学出版会, 2008
* 宇野 俊夫, 『独習 TCP/IP～IPv6対応～』, 翔泳社, 2010
* 秋葉 拓哉/岩田 陽一/北川 宣稔, 『プログラミングコンテストチャレンジブック 第2版』, マイナビ出版, 2012
* J. Glenn Brookshear (神林 靖/長尾 高宏 訳),  『入門コンピュータ科学～ITを支える技術と理論の基礎知識～』, アスキー・メディアワークス, 2014
* 杉江 俊治/藤田 政之, 『フィードバック制御入門』, コロナ社, 1999
* 近藤 嘉雪、 『定本 Cプログラマのためのアルゴリズムとデータ構造』, SB Creative, 1998
