# JUMAN++

京都大学の黒橋・河原研究室が開発した日本語の形態素解析ライブラリ。
言語モデルにRecurrent Neural Network Language Model(RNNLM)を採用しており、既存のMeCabなどより精度がよいと言われる。

## install

Linuxしか対応していないとのことなのでdockerで入れるのがよさそう。

### dockerfile

JUMAN++の方が高機能だが重いらしい。また、KNPはJUMANを入れていないとビルドできなかったので、とりあえず両方入れている。

```dockerfile
FROM alpine:latest

RUN apk add --update --no-cache wget boost-dev g++ make zlib-dev git \
    && cd ~/ \
    && wget http://nlp.ist.i.kyoto-u.ac.jp/nl-resource/juman/juman-7.01.tar.bz2 \
    && tar xf juman-7.01.tar.bz2 \
    && rm juman-7.01.tar.bz2 \
    && cd juman-7.01/ \
    && ./configure \
    && make && make install \
    && cd ~/ \
    && rm -R juman-7.01/ \
    && wget http://lotus.kuee.kyoto-u.ac.jp/nl-resource/jumanpp/jumanpp-1.01.tar.xz \
    && tar xf jumanpp-1.01.tar.xz \
    && rm jumanpp-1.01.tar.xz \
    && cd jumanpp-1.01/ \
    && ./configure \
    && make && make install \
    && cd ~/ \
    && rm -R jumanpp-1.01/ \
    && wget http://nlp.ist.i.kyoto-u.ac.jp/nl-resource/knp/knp-4.17.tar.bz2 \
    && tar xf knp-4.17.tar.bz2 \
    && rm knp-4.17.tar.bz2 \
    && cd knp-4.17/ \
    && ./configure \
    && make && make install \
    && cd ~/ \
    && rm -R knp-4.17/

RUN apk add python3 \
    && cd ~/ \
    && python3 -m pip install six \
    && wget http://lotus.kuee.kyoto-u.ac.jp/nl-resource/pyknp/pyknp-0.3.tar.gz \
    && tar xf pyknp-0.3.tar.gz \
    && rm pyknp-0.3.tar.gz \
    && cd pyknp-0.3/ \
    && python3 setup.py install

CMD sh
```

## pyknp

pythonラッパー。ただし、python3ではうまく動かなかった。

以下はとりあえず構文解析だけ使う方法。

### インストール

```
cd pyknp-3.01
python3 setup.py install
```

### 使い方

```py
from pyknp import MList
import subprocess

res = subprocess.Popen("echo '明日は晴れるだろう' | jumanpp", shell=True, stdout=subprocess.PIPE).communicate()[0].decode('utf-8')

ml = MList(res)

for m in ml.mrph_list():
    print(m.midasi)
    print(m.yomi)
    print(m.genkei)
    print(m.hinsi)
    print(m.hinsi_id)
    print(m.bunrui)
    print(m.bunrui_id)
    print(m.katuyou1)
    print(m.katuyou1_id)
    print(m.katuyou2)
    print(m.katuyou2_id)
    print(m.imis)
    print('----------')

```
