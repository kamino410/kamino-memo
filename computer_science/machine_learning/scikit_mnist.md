# scikit-learnでMNIST

とりあえず試したみた。

scikit-learnにもMNISTの縮小版データが含まれているらしいが解像度が低いとのことなので、MNIST本家からデータを落としてくることにした。

## 環境

```
macOS Sierra 10.12.5
python 3.6.0
numpy 1.12.0
scikit-learn 0.18.1
```

## データの取得・変換

とりあえずダウンロード。

```sh
wget http://yann.lecun.com/exdb/mnist/train-images-idx3-ubyte.gz
wget http://yann.lecun.com/exdb/mnist/train-labels-idx1-ubyte.gz
wget http://yann.lecun.com/exdb/mnist/t10k-images-idx3-ubyte.gz
wget http://yann.lecun.com/exdb/mnist/t10k-labels-idx1-ubyte.gz
gzip -d *
```

imagesの方は、先頭に`マジックナンバー(4byte)・データ総数(4byte)・画像縦幅(4byte)・画像横幅(4byte)`が書かれており、その後ひたすら1byteデータ（28×28ビットの画像の画素値）が並んでいる。

labelsの方は、先頭に`マジックナンバー(4byte)・データ総数(4byte)`が書かれており、その後ひたすら1byteデータ（画像に書かれている数字）が並んでいる。

BSD系の`od`コマンドは改行位置の指定ができないっぽいのでとりあえず16要素ごとに改行されたスペース区切りのtxtファイルに。

```sh
od -An -v -j16 -tu1 train-images-idx3-ubyte | sed 's/^ *//' | tr -s ' ' > train-images.txt
od -An -v -j8 -tu1 train-labels-idx1-ubyte | sed 's/^ *//' | tr -s ' ' > train-labels.txt
od -An -v -j16 -tu1 t10k-images-idx3-ubyte | sed 's/^ *//' | tr -s ' ' >  test-images.txt
od -An -v -j8 -tu1 t10k-labels-idx1-ubyte | sed 's/^ *//' | tr -s ' ' > test-labels.txt
```

## Pythonへデータを取り込み

```py
import numpy as np
from sklearn.ensemble import RandomForestClassifier

print("Loading MNIST data...")
images = np.loadtxt('train-images.txt', dtype=np.uint8)
images = images.reshape((-1, 28*28))

labels = np.loadtxt('train-labels.txt', dtype=np.uint8)
labels = labels.reshape((-1))
print("...Completed")

print("Loading test MNIST data...")
test_images = np.loadtxt('test-images.txt', dtype=np.uint8)
test_images = test_images.reshape((-1, 28*28))

test_labels = np.loadtxt('test-labels.txt', dtype=np.uint8)
test_labels = test_labels.reshape((-1))
print("...Completed")

```

## 学習・テスト

ランダムフォレストを使ってみる。

```py
import numpy as np
from sklearn.ensemble import RandomForestClassifier

print("Fitting...")
rfc = RandomForestClassifier()
rfc.fit(images, labels)

print("Testing...")
print(rfc.score(test_images, test_labels))

```

```
0.9452
```
