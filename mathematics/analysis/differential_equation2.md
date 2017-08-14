# 微分方程式2（differential equation）

## 特殊な1階線形微分方程式

### 直接積分形

$$
y' = f(x)
$$

#### 一般解

$$
\begin{eqnarray}
y' &=& f(x) \\
\frac{dy}{dx} &=& f(x) \\
\int dy &=& \int f(x) dx \\
y &=& \int f(x) dx
\end{eqnarray}
$$

### 変数分離形

$$
y' = g(x)h(y) \ \ \ (h(y)\neq 0)
$$

#### 一般解

$$
\begin{eqnarray}
y' &=& g(x)h(y) \\
\int \frac{1}{h(y)}dy &=& \int g(x) dx
\end{eqnarray}
$$

## 一般の1階線形微分方程式

### 同次形

$$
y' + P(s)y = 0
$$

#### 一般解

$$
\begin{eqnarray}
y' + P(x)y &=& 0 \\
\int \frac{1}{y} &=& -\int P(x)dx \\
\log |y| &=& -\int P(x) dx \\
y &=& Ce^{-\int P(x) dx}
\end{eqnarray}
$$

### 非同次形

$$
y' + P(x)y = Q(x)
$$

#### 一般解

同次形の定数項が $$u(x)$$ であるとする。

$$
\begin{eqnarray}
\{u(x)\cdot e^{-\int P(x)dx} \}' + P(x)\cdot u(x)\cdot e^{-\int P(x)dx} &=& Q(x) \\
u'(x) \cdot e^{-\int P(x)dx} - u(x) \cdot P(x) \cdot e^{-\int P(x)dx} + P(x) \cdot u(x) \cdot e^{-\int P(x)dx} &=& Q(x) \\
u'(x) \cdot e^{-\int P(x)dx} &=& Q(x)
\end{eqnarray}
$$

直接積分形として処理して

$$
\begin{eqnarray}
\frac{du}{dx} &=& Q(x) e^{\int P(x)dx} \\
u(x)&=&\int Q(x)e^{\int P(x)dx} dx + C \\
y &=& e^{-\int P(x)dx}\left\{\int Q(x)e^{\int P(x)dx} dx + C\right\}
\end{eqnarray}
$$

$$u(x)$$ は任意の関数を表現できる形のためこれを一般解としてよい。

### ベルヌーイの微分方程式

$$
y' + P(x)y = Q(x)y^n \ \ \ (n\neq 0,1)
$$

#### 一般解

$$
\begin{eqnarray}
y' + P(x)y &=& Q(x)y^n \\
(-n+1)y^{-n}y' + (-n+1)P(x)y^{-n+1} &=& (-n+1)Q(x) \\
(y^{-n+1})' + (-n+1)P(x)y^{-n+1} &=& (-n+1)Q(x) \\
\end{eqnarray}
$$

一階線形微分方程式の非同次形に当てはめて

$$
y^{-n+1} = e^{-\int P(x)dx}\left\{(-n+1)\int Q(x)e^{\int (-n+1)P(x)dx} dx + C\right\}
$$
