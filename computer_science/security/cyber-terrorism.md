# サーバー攻撃

ネットワークを介して行われるクラッキングを **サイバー攻撃** という。

## 情報の狙い方による分類

### スパイウェア（spyware）

寄生したマシン上のデータを収集し、配信者の元に報告するマルウェアを **スパイウェア** と呼ぶ。

狭義にはユーザーのインターフェース操作を記録し、情報を抜き出すソフトウェアを指す。

#### キーロガー

キーボード入力を記録するスパイウェアを特に **キーロガー** と呼ぶ。

### スニッフィング（sniffing）

盗聴、特にネットワークを流れる情報を抜き出すことで情報を盗む手法を **スニッフィング** と呼ぶ。

### フィッシング（phishing）

偽装されたソフト・サービスを利用するユーザーが現れるのを待ち、そのユーザーから情報を抜き取る手法を **フィッシング** と呼ぶ。

`fishing`と綴りが異なるのは単なる言葉遊び。

## 攻撃方法による分類

### 踏み台攻撃

ゾンビマシンを利用して間接的に攻撃を行い、攻撃元を偽装する攻撃を **踏み台攻撃** という。

### 中間者攻撃（Man-in-the-middle：MITM attack）

通信開始の段階で通信の間に割り込み、双方の通信相手に成りすますことで情報を盗む攻撃を **中間者攻撃** という。

DNS偽装・証明書の検証不備による脆弱性・脆弱な暗号の解読などにより暗号化通信のセッションに割って入るため、通信者からは暗号化通信で保護されているように見える。

## その他の用語

### バックドア

コンピュータに侵入するための非正規のルート（裏口）を **バックドア** という。

### ルートキット

攻撃・潜入のために利用されるツール群のうち、ルート権限の確保・活動の隠ぺい・バックドアの設置など、攻撃者が継続的に活動できるような環境を作るものを **ルートキット** と呼ぶ。

### ゾンビマシン

マルウェアに侵入され、遠隔操作できる状態になったマシンを **ゾンビマシン** という。

"役に立たなくなったもの・悪の手先になったもの"といったニュアンス。

### ランサムウェア（ransomware）

感染したマシンのファイルを暗号化し、復号と引き換えに金銭を要求する身代金要求型ウイルスに用いられるマルウェアを **ランサムウェア** という。