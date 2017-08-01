# 自分用のキーボード環境

## Windows

キーボードドライバーの設定をUSにしてFILCO Majestouch MINILA USを使用。
日本語入力はMicrosoft IMEをそのまま使用。

## Macbook

US配列のMacbookを使用。

* システム環境設定 > キーボード > キーボード
  * Macbook内蔵キーボード
    * `caps lock` -> `command`
    * `control` -> `caps lock`
    * `command` -> `control`
    * copy, paste, undoなどに`a`の隣のキーを使うため
  * MINILA
    * `control` -> `command`
    * `command` -> `control`
    * キーボード側で`caps lock`と`control`を交換してあるので、こう設定しておけば上と同じ要領で使える
* iTerm > configuration
  * `control` -> `command`
  * `command` -> `control`
  * キーボードドライバーの設定を逆転させて元に戻してある
  * コマンド中止（`ctrl-c`）や zsh のショートカット（`ctrl-r`とか`ctrl-p`/`ctrl-n`とか）に`a`の隣のキーを使うため
  * iTerm のショートカット（タブ操作等）は`command`で実行することになる
* 日本語入力
  * Google日本語入力をインストール（ことえりは予測変換がイケてない）
  * システム環境設定 > キーボード > 入力ソース
    * 「ABC」と「ひらがな（Google）」を選択
    * 再起動しないとひらがながうまく認識されなかった
  * 英・かなをインストール
    * キーボードの左`command`を英、右`command`をかなに割り当て
    * キーボードドライバーで`control`と`command`を入れ替えてあるので画面上では「`control L`」「`control R`」と表示される
  * システム環境設定 > キーボード > ショートカット > 入力ソース
    * 「前の入力ソースに切り替え」に```option-` ```を割り当て
    * MINILAには右スペシャルキーが存在しないので、US配列デフォルトの```alt-` ```で入力ソースを切り替えられるようにしておく
