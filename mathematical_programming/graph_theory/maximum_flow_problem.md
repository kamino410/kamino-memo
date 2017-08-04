# 最大流問題（maximum flow problem）

[フロー](flow.md)（流量）の最大化を目的とした問題について言及する。

## 定義

有向グラフ $$G=(V,E)$$ と各辺の正の容量 $$u:E\rightarrow \mathbb{R}_{++}$$ と供給点（source）$$s\in V$$ ・需要点（sink）$$t\in V$$ が与えられたとき、流量最大の可能流を求める問題を**最大流問題**もしくは**最大フロー問題**という。

## 最小カット（minimum cut）

グラフを始点側と終点側に分割する、すなわち $$s\in X, \ t \notin X$$ を満たす頂点の部分集合を $$X \subset V$$ としたとき、$$\partial (X)$$ を **s-tカット** という。

s-tカットの容量を $$\kappa_u(X)=\sum_{e\in \partial^+ (X)} u(e)$$ としたとき、これが最小であるカットを**最小カット**という。
流量保存則と容量制約より任意のs-tカットの容量は始点からの供給量以上でなければならなず、最小カットはグラフ上のボトルネックを示しているため、最小カットの容量を調べれば最大流量と一致する。

### 定理の証明

流量保存則より

$$
\begin{eqnarray}
\partial \varphi (s) &=& \partial \varphi(s) + \sum_{v \in X\backslash \{s\}} \partial \varphi (s) \\
&=& \sum_{v \in V}\partial \varphi(v) \\
&=& \sum_{e \in \partial^+ (X)}\varphi(e)-\sum_{e\in\partial^-(X)}\varphi(e)
\end{eqnarray}
$$

すなわち、任意のs-tカットの容量と $$s$$ からの供給量 $$\partial \varphi(s)$$ の間で

$$
\partial \varphi(s) \leq \kappa_u(X)
$$

が成り立つ。
次に任意のフロー $$\varphi$$ に対して**補助ネットワーク（auxiliary network）**（あるいは**残余ネットワーク（residual network）**）を次のように定義する。

$$
\begin{eqnarray}
&\ &\mathscr{N}_\varphi = (G_\varphi = (V,E_\varphi),u_\varphi) \\
&\ &\begin{cases}E_\varphi = E_\varphi^F \cup E_\varphi^B\\
E_\varphi^F \{e \in E \ | \ \varphi(e) < u(e)\}, \ E_\varphi^B \{e^r \ | \ e\in E, \varphi(e) > 0\} \\
e^r = (\partial^- e, \partial^+ e)\end{cases}
\end{eqnarray}
$$

これは、現在のフローについて容量制約に余裕がある辺（流量を追加できる辺）とフローの存在する辺（流量を削ることができる辺）を考えたものである（結局グラフ上のすべての辺が $$A_\varphi^F$$ と $$A_\varphi^B$$ のどちらかに属する）。

また、補助ネットワークから次のような**残余容量（residual capacity）** $$u_\varphi:E_\varphi \rightarrow \mathbb{R}$$ を定義する。

$$
u_\varphi(e) = \begin{cases}u(e) - \varphi(e) & (e \in E_\varphi^F) \\ \varphi(e^r) & (e \in E_\varphi^B)\end{cases}
$$

ここで現在のフローに補助ネットワーク上のあるフロー $$\psi$$ を追加して得られるフロー $$\varphi \oplus \psi$$ は次のように表される。

$$
(\varphi \oplus \psi)(e) = \begin{cases}\varphi(e)+\psi(e)-\psi(e^r) & (e\in E_\varphi^F, e^r \in E_\varphi^B) \\
\varphi(e) + \psi(e) & (e\in E_\varphi^F, e^r \notin E_\varphi^B) \\
\varphi(e)-\psi(e^r) & (a \notin E_\varphi^F, e^r \in E_\varphi^B)
\end{cases}
$$

ここで、$$\psi$$ が補助ネットワーク上の $$s$$ から $$t$$ への有向路であるとき、$$\psi$$ を**増加路（augmenting path）**という。
ここで最大流の最適性条件は次のように表される。

<center>
可能流 $$\varphi$$ が最大流<br />⇔　補助ネットワーク $$\mathscr{N}_\varphi$$ 上に増加路が存在しない<br />⇔　容量制約を等式で満たす辺（制約容量に余裕がない辺）が1つは存在する<br />⇔　最小カットが容量制約を等式で満たす
</center>

## 最大流アルゴリズム

最大流問題には様々なアルゴリズムが存在するが、大きく2通りに分類できる。

1. 補助ネットワーク上で増加路を探索し、可能流の流量を増加させていく方法（増加路法）
2. 流量保存則を緩和し各頂点に流量が留まることを許したフローを用いて辺ごとにフローを更新し、流量保存則を満たすフローを見つける方法（プリフロー・プッシュ法）

### 増加路法（augmenting path method）

基本的な手順は以下のようになる。

1. $$\varphi(e):=0(^\forall \in E)$$ とする
2. 補助ネットワーク $$\mathscr{N}_\varphi = (G_\varphi = (V,E_\varphi), u_\varphi)$$ を計算し、増加路 $$P$$ を探す
3. 増加路が見つからなければ終了する
4. 増加路の残余容量の和 $$\varepsilon = \min \{u_\varphi(e) \ | \ e \in E_\varphi(P)\}$$ を求め、$$\varphi := \varphi \oplus (\epsilon \cdot \chi_P)$$ と更新する
5. 2~4を繰り返す

増加路はどれを選択してもよく、増加路の選択が異なれば得られる最大流も異なる場合がある。

問題はどのように増加路を探索するかであり、この探索方法によってさらにいくつかのアルゴリズムに分類される。

#### 最大容量増加路法

手順2において常に増加路の残余容量の和 $$\varepsilon$$ が最大になるように増加路を選択する手法。
このような増加路の探索はボトルネック最短路問題に帰着するため弱多項式時間アルゴリズムとなる。

辺の容量の最大値を $$U = \max\{u(e)\ |\ e \in E\}$$ とすれば、時間計算量について以下の定理が成り立つ。

<center>
すべての辺の容量が正数　⇒　最大容量増加路法の繰り返し回数は $$O(m \log (nU))$$
</center><br />

### プリフロー・プッシュ法（preflow-push method）

プリフロー・プッシュ法では各頂点について次のような**残存量（excess/deficit）**を定義する。

$$
f_\varphi(v) = \sum_{e \in \partial^-v}\varphi(e)-\sum_{e \in \partial^+ v}\varphi(e)
$$

$$s,t$$ 以外の頂点の残存量が非負であるフローを**プリフロー**と呼ぶ。
また、残存量が正である点を**活動頂点・活性点（active vertex）**という。

プリフロー $$\varphi$$ に対して $$d:V \rightarrow \mathbb{Z}_+$$ が補助ネットワークの各辺 $$e \in E_\varphi$$ で

$$
d(\partial^+ e) \leq d(\partial^- e) + 1
$$

を満たし、$$d(s) = n$$ であるときフローの**距離ラベル（distance label）$$ という。
また、この式を等式で満たす辺を**可能辺（admissible arc / eligible arc）**という

基本的な手順は以下のようになる。

1. $$\varphi(e):=u(e)\ (^\forall e \in \partial^+ s)$$ , $$\varphi(e):=0\ (^\forall e \in E \backslash \partial ^+ s)$$ , $$d(s):= n$$ , $$d(v):=0\ (^\forall v \in V \backslash \{s\})$$ とする
2. 活性点 $$v$$ を選択
3. 活性点がなければ終了
3. $$v$$ を始点とする可能辺 $$a \in E_\varphi$$ を探す
4. 可能辺が存在すれば、$$e \in E_\varphi^F$$ のときは $$\varphi(e):=\varphi(e)+\min\{ f_\varphi(v), u_\varphi(e)\}$$ と更新し、$$e \in E_\varphi^B$$ のときは $$\varphi(a^r):=\varphi(a^r) - \min\{f_\varphi(v),u_\varphi(e)\}$$ と更新する
5. 可能編が存在しなければ $$d(v) := \min\{f(\partial^- e) \ | \ e \in E_\varphi, e\in \partial^+ v\} + 1$$ と更新する
6. 2~6を繰り返す
