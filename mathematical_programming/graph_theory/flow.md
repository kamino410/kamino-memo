# フロー（flow）

## 定義

ネットワークに何らかのもの（車・情報・水・製品など）を流すことを考えるとき、この流れを**フロー**という。
フローは有向辺に沿って流れ、頂点で分岐・合流するものとして考える。

以後、各辺の流量を与える関数を $$\varphi : E \rightarrow \mathbb{R}$$ と書くことにする。

## 容量制約（flow bound constraint）

一般的に、フローを考えるときそのネットワークの辺にはコストとして**容量制約**を設ける。
すなわち、ある辺の容量制約を与える関数を $$u: E \rightarrow \mathbb{R}$$ とすれば、

$$
0 \leq \varphi(e_k) \leq u(e_k)
$$

が常に成立することが問題への制約条件となる。

この条件を満たすようなフローを**実行可能流（feasible flow）**または**可能流**という。
とくにすべての頂点の供給量が $$0$$ であるような可能流を**循環流（circulation flow）**という。

## 流量保存則（mass balance constraint）

フローが供給点と需要点以外で出現・消失することはありえないので、各頂点の供給量・流入量・需要量・流出量の収支は一致するはずである。
これを**流量保存則**といい、次のように表す。

$$
\begin{eqnarray}
&\ & ^\forall v \in V \left(\sum_{e \in \partial^+ v} \varphi(e) - \sum_{e \in \partial^- v} \varphi(e) = b(v) \right) \\
&\ & \sum_{v \in V}b(v) = 0
\end{eqnarray}
$$

$$b(v_k)>0$$ は供給点、$$b(v_k)<0$$ は需要点、$$b(v_k)=0$$ は中継点であることを示している。

## フロー分解定理（flow decomposition theorem）

これを用いれば次のような定理を記述できる。

<center>
有向グラフ $$G = (V,E)$$ 上の任意の非負のフローを $$\varphi$$ とする<br>⇒　有向閉路 $$Q_k$$ 上のフローと $$\partial \varphi(v) > 0$$ である頂点から $$\partial \varphi(v) < 0$$ である頂点への有向路 $$P_k$$ 上のフローに分解できる
</center>

このように任意の非負のフロー $$\varphi$$ をいくつかの有向閉路上のフローと有向路上のフローに分けることを**フローの同符号分解（flow equisignum decomposition）**という。
