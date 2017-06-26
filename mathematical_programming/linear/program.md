# 線形計画問題を解くプログラム

## Python

いくつかライブラリが存在するが、LP問題に限ればPuLPが良さそう。

### サンプル1

$$
\begin{eqnarray}
minimize : 2x_1+3x_2 \\
s.t. \begin{cases}
4x_1+x_2 &\geq& 13 \\
3x_1+2x_2 &\geq& 16 \\
x_1+2x_2 &\geq& 8
\end{cases} \\
x_1 \geq 0, \ \ \ x_2 \geq 0
\end{eqnarray}
$$

>Python 3.6.1, PuLP 1.6.5

```py
import pulp

problem = pulp.LpProblem('sample', pulp.LpMinimize)

x1 = pulp.LpVariable(name='x1', lowBound=0)
x2 = pulp.LpVariable(name='x2', lowBound=0)

problem += 2*x1 + 3*x2

problem += 4*x1 + x2 >= 13
problem += 3*x1 + 2*x2 >= 16
problem += x1 + 2*x2 >= 8

status = problem.solve()
print("Status :", pulp.LpStatus[status])
print()

print(problem)

print("Result")
print("cost :", problem.objective.value())
for v in problem.variables():
    print(v.name, v.value())

```

### サンプル2

$$
\begin{eqnarray}
minimize : -4x_1-5x_2-2x_3-8x_4 \\
s.t. \begin{cases}
2x_1+2x_2+x_3+3x_4 \geq 5
\end{cases} \\
x_1, x_2, x_3, x_4 \in \{0, 1\}
\end{eqnarray}
$$

```py
import pulp

problem = pulp.LpProblem('sample', pulp.LpMaximize)

x1 = pulp.LpVariable(name='x1', lowBound=0, upBound=1, cat=pulp.LpInteger)
x2 = pulp.LpVariable(name='x2', lowBound=0, upBound=1, cat=pulp.LpInteger)
x3 = pulp.LpVariable(name='x3', lowBound=0, upBound=1, cat=pulp.LpInteger)
x4 = pulp.LpVariable(name='x4', lowBound=0, upBound=1, cat=pulp.LpInteger)

problem += 4*x1+5*x2+2*x3+8*x4

problem += 2*x1 + 2*x2 + x3 + 3*x4 <= 5

status = problem.solve()
print("Status :", pulp.LpStatus[status])
print()

print(problem)

print("Result")
print("cost :", problem.objective.value())
for v in problem.variables():
    print(v.name, v.value())

```
