# GitBook

## 自分用の設定

### Plugin

* mathjax-commonhtml
  * gitbook-plugin-mathjaxを使うとmathjax形式になってしまうため、htmlにレンダリングしてくれるものを採用。
* mermaid-2
  * Atomのmarkdown-preview-enhancedと互換性を保つため、タグではなくコードブロックを使いたかった。
* expandable-chapters
  * SUMMARYでインデントをつけると、レンダリングしたときに折りたたみできるようになる。
* search-pro
  * マルチバイト文字の検索・検索結果のハイライトの機能追加。

### 導入方法

```
node: v7.10.0
npm: 4.2.0
GitBook CLI version: 2.3.0
GitBook version: 3.2.2
mathjax-commonhtml: 0.0.6
expandable-chapters: 0.2.0
mermaid-2: 0.0.3
search-pro: 2.0.2
```

`book.json`に次の記述を追加する。

```json
{
  "plugins":["mathjax-commonhtml","expandable-chapters","mermaid-2","-lunr","-search","search-pro"]
}
```

次にプラグインをインストールする。

```
gitbook install
```

ただし、なぜか`mermaid-2`だけはこれではうまく動作しなかった。

ので、`mermaid-2`だけ`npm`コマンドから直接インストールしておく。

```
npm install gitbook-plugin-mermaid-2
```

インストール後、`index.js`の33行目あたりに1行追加する（[参考](http://shingaki.me/web/%E3%83%AD%E3%83%BC%E3%82%AB%E3%83%AB%E3%81%ABgitbook%E3%81%AE%E7%92%B0%E5%A2%83%E3%82%92%E6%A7%8B%E7%AF%89%E3%81%97%E3%81%A6mermaid-js%E3%82%92%E3%83%97%E3%83%A9%E3%82%B0%E3%82%A4%E3%83%B3%E3%81%A7/)）。

```js
js: [
      'bower_components/mermaid/dist/mermaid.min.js',
      'plugin.js'
    ]
```

以上。
