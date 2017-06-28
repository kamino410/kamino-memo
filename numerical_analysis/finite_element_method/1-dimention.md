# １次元の重み付き残差法

次の微分方程式を数値的に解くことを考える。

$$
\begin{eqnarray}
\frac{d^2u}{dx^2}-\lambda = 0 \ \ \ (0 \leq x \leq L) \tag{1} \\
u | _ {x=0}=0, \ \ \  \frac{du}{dx} | _ {x=L} = 0
\end{eqnarray}
$$

ここで $$u | _ {x=0}=0$$ のように $$u$$ の値が分かっているような境界条件をディリクレ（Dirichlet）境界条件という。

また $$\frac{du}{dx} | _ {x=L} = 0$$ のように $$\frac{du}{dx}$$ の値が分かっているような境界条件をノイマン（Neumann）境界条件という。

## 概要

近似解を $$u'(x)$$ とすると、微分方程式を完全には満たさないため

$$
R(x) = \frac{d^2u'}{dx^2}-\lambda
$$

のように残差 $$R(x)$$ が生じる。
この残差をすべての点で0に近づければよいが、そのままでは逐次的な操作となるため難しい。

そこで重み関数 $$u^* (x)$$ を用いて重み付き残差平均

$$
\int u^* (x) R(x) dx
$$

を最小化しようというのが重み付き残差法である。
重み関数の選び方として選点法・モーメント法・最小二乗法・ガラーキン法などが考案された。
ここでは今日よく利用されるガラーキン法によって例題を解く。

重み付き残差法では上記の式そのものを解くのではなく、弱形式から弱解を求めることで近似解を得る。
こうすることで、近似解の導出が連立方程式を解く作業に置き換わるため、線形代数の知識を利用して（つまりコンピュータに解かせることができる形で）近似解を求めることができるようになる。

## 弱形式（Weak Formulation）の導出

式(1)の両辺に任意の重み関数 $$u^* (x)$$ をかけた上で領域内で積分すると

$$
\int_0^L u^* (x) \left( \frac{d^2u}{dx^2}-\lambda \right)dx = 0
$$

これを部分積分すると

$$
-\int_0^L \left( \frac{du^* }{dx}\frac{du}{dx}+u^* \lambda \right)dx + \left[u^* \frac{du}{dx}\right]_ 0^L=0
$$

ここで境界条件 $$\frac{du}{dx} | _ {x=L} = 0$$を代入、またディリクレ境界条件が課せられた境界上（今回は $$x=0$$）において $$u^* (x)=0$$ とすると（理由は後述）

$$
\int_0^L \left( \frac{du^* }{dx}\frac{du}{dx} + u^* \lambda \right) dx = 0 \tag{2}
$$

となる。

このとき式(2)は式(1)の **弱形式** であるといい、

『任意の $$u^* (x)$$ について式(2)が成立する ⇒ 式(1)が成立する』

を満たす。

## 近似解の離散化

$$0 \leq x \leq L$$ において$$N$$個の小区間に分割したときの $$u(x)$$ の折れ線近似解を $$\tilde{u}(x)$$ とすると弱形式全体は

$$
\int_0^L \left( \frac{du^* }{dx}\frac{du}{dx} + u^* \lambda \right) dx \simeq
\sum_{k=1}^N \left[ \int_{x_k}^{x_{k+1}} \left( \frac{du^* }{dx}\frac{d\tilde{u}_k}{dx} + \tilde{u}_k \lambda \right) dx \right]
$$

と近似できる。

折れ線近似として $$\tilde{u}_k(x)=a_k+b_kx$$ の関数形を仮定し、各区分点における $$\tilde{u}(x)$$ の値を $$\tilde{u}_1 , \tilde{u}_2, \dots , \tilde{u}_{n+1}$$ とすると

$$
\begin{pmatrix} \tilde{u}_k \\ \tilde{u}_{k+1} \end{pmatrix} =
\begin{bmatrix} 1 & x_k \\ 1 & x_{k+1} \end{bmatrix}
\begin{pmatrix} a_k \\ b_k \end{pmatrix}
$$

となるから、逆行列を求めて $$a_k, b_k$$ を消去すると

$$
\begin{eqnarray}
\tilde{u}_k(x) &=& \begin{bmatrix} 1 & x \end{bmatrix} \begin{pmatrix} a_k \\ b_k \end{pmatrix} \\
&=& \begin{bmatrix} \frac{x_{k+1}-x}{x_{k+1}-x_k} & \frac{x-x_k}{x_{k+1}-x_k} \end{bmatrix}
\begin{pmatrix} \tilde{u}_k \\ \tilde{u}_{k+1} \end{pmatrix} \tag{3} \\
\frac{d\tilde{u}}{dx} &=& \begin{bmatrix} \frac{d}{dx} \left( \frac{x_{k+1} - x}{x_{k+1} - x_k} \right)  & \frac{d}{dx} \left( \frac{x - x_k}{x_{k+1} - x_k} \right) \end{bmatrix} \begin{pmatrix} \tilde{u}_k \\ \tilde{u}_{k+1} \end{pmatrix} \\
&=& \begin{bmatrix} -\frac{1}{x_{k+1} - x_k} & \frac{1}{x_{k+1} - x_k} \end{bmatrix} \begin{pmatrix} \tilde{u}_k \\ \tilde{u}_{k+1} \end{pmatrix} \tag{4}
\end{eqnarray}
$$

これで区分点の値を用いて小区間における近似解とその1階微分を表現できた。

----

ここからは式を以下のようにまとめる。

$$
\begin{eqnarray}
l_k &=& x_{k+1} - x_k \\
N_k^T &=& \begin{bmatrix} \frac{x_{k+1}-x}{l_k} & \frac{x-x_k}{l_k} \end{bmatrix} \\
L_k^T &=& \begin{bmatrix} -\frac{1}{l_k} & \frac{1}{l_k} \end{bmatrix} \\
\tilde{U}_k &=& \begin{pmatrix} \tilde{u}_k \\ \tilde{u}_{k+1} \end{pmatrix} \\
U^* _ k &=& \begin{pmatrix} \tilde{u^* }_k \\ \tilde{u^* }_{k+1} \end{pmatrix} \\
\end{eqnarray}
$$

## 重み関数の離散化

$$u(x)$$ の離散化はできたので、次に $$u^* (x)$$ を離散化する。

ここではガラーキン法を用いることとしたため、$$u(x)$$ と同じ関数形を仮定して $$u^* _ k (x) = a^* _ k + b^* _ k x$$ とする。

すると $$u(x)$$ の離散化の手順をそのまま適用できるため

$$
\begin{eqnarray}
u^* _ k(x) &=& N_k^T U^* _ k \\
\frac{du^ * _ k }{dx} &=& L_k^T U^* _ k
\end{eqnarray}
$$

となる。

## 弱形式の離散化

以上をまとめると、小区間において成立すべき一次方程式は

$$
\begin{eqnarray}
\int_{x_k}^{x_{k+1}} \left( \frac{du^* }{dx}\frac{d\tilde{u}_k}{dx} + \tilde{u}_k \lambda \right) dx &=&
\int_{x_k}^{x_{k+1}} \left( L_k^T U^* _ k L_k^T \tilde{U}_k + N_k^T U^* _ k \lambda \right) \\
&=& (U^* _ k)^T \left[ L_k L_k^T \tilde{U}_k \int_{x_k}^{x_{k+1}} dx + \lambda \int_{x_k}^{x_{k+1}} N_k dx \right] \\
&=& (U^* _ k)^T \left[ \frac{1}{l_k} \begin{bmatrix} 1 & -1 \\ -1 & 1 \end{bmatrix} \tilde{U}_k + \frac{1}{2}l_k \begin{pmatrix} 1 \\ 1 \end{pmatrix} \right]
\end{eqnarray}
$$

これを対象領域で連立させると

$$
\begin{eqnarray}
&\sum& _ {k=1}^N \left[ \int_{x_k}^{x_{k+1}} \left( \frac{du^* }{dx}\frac{d\tilde{u}_k}{dx} + \tilde{u}_k \lambda \right) dx \right] \\
&=& \begin{bmatrix} u^* _ 1 & u^* _ 2 & \dots & u^* _ {n+1} \end{bmatrix} (A\tilde{u} + B)
\end{eqnarray}
$$

ただし

$$
\begin{eqnarray}
A &=& \begin{bmatrix}
  1/l_1 & -1/l_1 & 0 & \dots & 0 & 0 \\
  -1/l_1 & 1/l_1+1/l_2 & -1/l_2 & \dots & 0 & 0 \\
  0 & -1/l_2 & 1/l_2+1/l_3 & \dots & 0 & 0 \\
  \vdots & \vdots & \vdots & \ddots & \vdots & \vdots \\
  0 & 0 & 0 & \dots & 1/l_{n-1}+1/l_n & -1/l_n \\
  0 & 0 & 0 & \dots & -1/l_n & 1/l_n
\end{bmatrix} \\
B &=& \begin{pmatrix} \lambda l_1/2 \\ \lambda(l_1+l_2)/2 \\ \lambda(l_2+l_3)/2 \\ \vdots \\ \lambda(l_{n-1}+l_n)/2 \\ \lambda l_n/2 \end{pmatrix} \\
\tilde{u} &=& \begin{pmatrix} \tilde{u}_1 \\ \tilde{u}_2 \\ \tilde{u}_3 \\ \vdots \\ \tilde{u}_n \\ \tilde{u}_{n+1} \end{pmatrix}
\end{eqnarray}
$$

ここで $$u^* _ 1, u^* _ 2, \dots, u^* _ {n+1}$$ は任意関数であるべきなので

$$
A\tilde{u}+B=0
$$

を $$\tilde{u}$$ について調べればよい。

しかし、このままではAが逆行列を持たないため計算できない（これは問題の制約条件が不足していることと対応している）。

そこで「ディリクレ境界条件が課された境界上では $$u^* (x) = 0$$ とする」という条件を再利用する。

式の1行目に着目すると

$$
u^* \left( \frac{\tilde{u}_1}{l_1}-\frac{\tilde{u}_2}{l_1}+\frac{\lambda l_1}{2} \right) = 0
$$

ここで $$\frac{\tilde{u}_1}{l_1}-\frac{\tilde{u}_2}{l_1}+\frac{\lambda l_1}{2}=0$$ を満たす必要がない代わりに、 $$u^* _ 1 = 0$$ を満たすようにする。

$$
\begin{eqnarray}
A' &=& \begin{bmatrix}
  1 & 0 & 0 & \dots & 0 & 0 \\
  -1/l_1 & 1/l_1+1/l_2 & -1/l_2 & \dots & 0 & 0 \\
  0 & -1/l_2 & 1/l_2+1/l_3 & \dots & 0 & 0 \\
  \vdots & \vdots & \vdots & \ddots & \vdots & \vdots \\
  0 & 0 & 0 & \dots & 1/l_{n-1}+1/l_n & -1/l_n \\
  0 & 0 & 0 & \dots & -1/l_n & 1/l_n
\end{bmatrix}\\
B' &=& \begin{pmatrix} 0 \\ \lambda(l_1+l_2)/2 \\ \lambda(l_2+l_3)/2 \\ \vdots \\ \lambda(l_{n-1}+l_n)/2 \\ \lambda l_n/2 \end{pmatrix}
\end{eqnarray}
$$

と置けば

$$
\tilde{u} = -A'^{-1}B'
$$

より近似解 $$\tilde{u}$$ が求まる。
