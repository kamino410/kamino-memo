# JUMAN++

京都大学の黒橋・河原研究室が開発した日本語の形態素解析ライブラリ。
言語モデルにRecurrent Neural Network Language Model(RNNLM)を採用しており、既存のMeCabなどより精度がよいと言われる。

## install

Linuxしか対応していないとのことなのでdockerで入れるのがよさそう。
サーバー用のrubyスクリプトが付属しているのでそれを起動してやる。
portはデフォルトでは`12000`。

### dockerfile

```dockerfile
FROM alpine:latest

RUN apk add --update --no-cache --virtual=build-deps \
    boost-dev g++ make ruby \
    && cd /usr/lib \
    && wget -q http://lotus.kuee.kyoto-u.ac.jp/nl-resource/jumanpp/jumanpp-1.01.tar.xz \
    && tar jxfv jumanpp-1.01.tar.xz \
    && rm jumanpp-1.01.tar.xz \
    && cd jumanpp-1.01/ \
    && ./configure \
    && make \
    && make install

CMD ruby /usr/lib/jumanpp-1.01/script/server.rb --cmd "jumanpp -B 5"
```

### pythonからサーバーへアクセス

ローカルに`client.rb`が必要。

```py
import subprocess
import re

client_script_path = './client.rb'

def analyze(text):
    raw_data = subprocess.Popen('echo {} | ruby {} --host localhost -p 12000'.format(text, client_script_path), shell=True, stdout=subprocess.PIPE, stderr=subprocess.STDOUT).stdout.readlines()
    res = []
    for block in raw_data:
        mcs = re.search(r'(@\s)?(.+?)\s(.+?)\s(.+?)\s(.+?)\s(.+?)\s(.+?)\s(.+?)\s(.+?)\s(.+?)\s(.+?)\s(.+?)\s(".+?"|NIL)', block.decode('utf-8'))
        if mcs is not None:
            dic = {}
            dic['表層形'] = mcs[2]
            dic['読み'] = mcs[3]
            dic['見出し語'] = mcs[4]
            dic['品詞大分類'] = mcs[5]
            dic['品詞大分類ID'] = mcs[6]
            dic['品詞細分類'] = mcs[7]
            dic['品詞細分類ID'] = mcs[8]
            dic['活用型'] = mcs[9]
            dic['活用型ID'] = mcs[10]
            dic['活用形'] = mcs[11]
            dic['活用形ID'] = mcs[12]
            dic['意味情報'] = {}
            if mcs[13] != 'NIL':
                mcs2 = re.findall(r'["\s]([^:]+?):([^\s]+)', mcs[13])
                for p in mcs2:
                    dic['意味情報'][p[0]] = p[1]
            dic['candidates'] = []
            if mcs[1] is not None:
                res[-1]['candidates'].append(dic)
            else:
                res.append(dic)
    return res
```

# KNP

## install

```dockerfile
FROM alpine:latest

RUN apk add --update --no-cache --virtual=build-deps \
    boost-dev g++ make ruby \
    && cd /usr/lib \
    && wget -q http://lotus.kuee.kyoto-u.ac.jp/nl-resource/jumanpp/jumanpp-1.01.tar.xz \
    && tar jxfv jumanpp-1.01.tar.xz \
    && rm jumanpp-1.01.tar.xz \
    && cd jumanpp-1.01/ \
    && ./configure \
    && make \
    && make install \
    && cd /usr/lib \
    && wget -q http://nlp.ist.i.kyoto-u.ac.jp/nl-resource/knp/knp-4.17.tar.bz2 \
    && tar jxvf knp-4.12.tar.bz2 \
    && rm knp-4.12.tar.bz2 \
    && cd knp-4.12/ \
    && ./configure \
    && make \
    && make install

CMD ruby /usr/lib/jumanpp-1.01/script/server.rb --cmd "jumanpp -B 5"
```
