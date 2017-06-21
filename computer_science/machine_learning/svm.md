# サポートベクターマシン（support vector machine）

サポートベクターマシンは教師あり学習のパターン認識モデルの一種である。

## Python例

```py
import matplotlib.pyplot as plt
import numpy as np
from sklearn import svm

rx = np.random.rand(50)
ry = np.random.rand(50)

xs1 = []
ys1 = []
xs2 = []
ys2 = []
for x,y in zip(rx,ry):
    if 5*x+y > 3:
        xs1.append(x)
        ys1.append(y)
    else:
        xs2.append(x)
        ys2.append(y)

plt.scatter(xs1,ys1)
plt.scatter(xs2,ys2)

```
