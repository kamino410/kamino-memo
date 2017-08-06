# 最急降下法（steepest descent method）

傾きが最も急な方向を探索する手法。
あくまで探索方法を決定する手法であるため、実際の探索には直線探索などを用いる必要がある。

## 手順

1. 探索開始点を決める（$$x_0$$）
2. 停止条件が満たされていれば終了する
3. $$-\nabla f(x_k)$$ を探索方向とし $$x_{k+1}$$ を探索する

## 例

Armijo条件の直線探索を用いた最急降下法を実装する。

>Armijo条件

>定数 $$\xi \ (0 < \xi < 1)$$ と勾配ベクトル $$d_k$$ に対して

>$$
f(x_k + \alpha d_k) \leq f(x_k) + \xi \alpha \nabla f(x_k)^T d_k
$$

>を満たす $$\alpha > 0$$ を選ぶ。$$\alpha_{k+1} = \tau \alpha_k$$ の更新式を用いることが多い。

2変数の目的関数 $$f(x_1, x_2) = x_1^4 + x_2^4 + 2 x_1^2 + x_2^2 + x_1 x_2$$ の極小値を求める。

Armijo条件の直線探索のパラメーターとして $$\xi = 0.5, \tau = 0.8$$ を設定し、停止条件を $$(\nabla f(x_1, x_2))_x + (\nabla f(x_1, x_2))_y < 0.001$$ とする。

勾配ベクトルは $$\nabla f(x_1, x_2) = \begin{bmatrix}4x_1^3+4x_1+x_2 \\ 4x_2^3+2x_2+x_1\end{bmatrix}$$ である。

```rust
use std::io;

fn main() {
    let a: f64 = 5f64;
    let b: f64 = 5f64;
    println!("{:?}", steepest_descent(a, b));
}

fn cost_func(x1: &f64, x2: &f64) -> f64 {
    x1 * x1 * x1 * x1 + x2 * x2 * x2 * x2 + 2f64 * x1 * x1 + x2 * x2 + x1 * x2
}

fn grad_func(x1: &f64, x2: &f64) -> (f64, f64) {
    (
        -(4f64 * x1 * x1 * x1 + 4f64 * x1 + x2),
        -(4f64 * x2 * x2 * x2 + 2f64 * x2 + x1),
    )
}

fn steepest_descent(x1: f64, x2: f64) -> (f64, f64) {
    let mut x1 = x1;
    let mut x2 = x2;
    loop {
        let mut alpha: f64 = 0.5;
        let d = grad_func(&x1, &x2);
        let fx = cost_func(&x1, &x2);
        let dk = -0.5 * (d.0 * d.0 + d.1 * d.1);

        println!("{}, {}", x1, x2);

        while cost_func(&(x1 + alpha * d.0), &(x2 + alpha * d.1)) > fx + alpha * dk {
            alpha = alpha * 0.8;
        }
        x1 = x1 + alpha * d.0;
        x2 = x2 + alpha * d.1;
        if d.0.abs() + d.1.abs() < 0.00000001 {
            break;
        }
    }
    (x1, x2)
}

```
