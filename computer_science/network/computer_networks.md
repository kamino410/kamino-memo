# Computer Networks読書メモ

## 1 INTRODUCTION

* computer network
  * 自律的に動くマシンを互いに情報を交換できるよう接続したもの
* distributed system
  * 独立したマシンを接続して構築されているが、ユーザーからは1つの大きなシステムと見なせるもの
* middleware
  * 分散システムを実現するための統一的なモデルに基づいた機能を提供するソフトウェア
  * ex) World Wide Web

### 1.1 USES OF COMPUTER NETWORKS

ざっと読み飛ばした。

### 1.2 NETWORK HARDWARE

transmission technologyとscaleの観点から分類できるが、この本では主にscaleの観点から解説する。

#### transmission technology

* broadcast
  * 全員に伝送される、自分宛てでなければ破棄
* point-to-point
  * 送信元から特定の送信先にだけ伝送される
  * 特に1対1ならunicasting

#### scale

|Class|Keywords|
|---|---|
|Personal(PAN)|PCと周辺機器の接続<br>・Bluetooth|
|Local(LAN)|1つの建物で完結しているネットワーク<br>・AP(Access Point) / wireless router / base station<br>・IEEE 802.11(WiFi)：無線、11\~100Mbps<br>・IEEE 802.3(Ethernet)：有線、100M\~1Gbps<br>・VLAN：1つのLANを複数のLANに分割する技術|
|Metropolitan(MAN)|都市間を結ぶネットワーク<br>・cable TV network<br>・IEEE 802.16(WiMAX)|
|Wide(WAN)|国や大陸内を結ぶネットワーク<br>LANとの違いとして多くの場合はネットワークプロバイダーや電話会社が運営しており、異なる方式のネットワーク同士を結ぶことで構築されている<br>・subnet：hostを結ぶswitching element / transmission lineの集まり（ip addressにおけるsubnetは派生的な意味）<br>・VPN：WANを介した仮想的な専用ネットワーク<br>・ISP network：Internet Service Providerが提供するネットワーク<br>・衛星回線<br>・routin algorithm：ルーターに用いるアルゴリズム|
|Internetworks|ネットワーク同士を結んで構築した巨大なネットワーク<br>・network：subnet+hosts、実際は曖昧な意味で用いられることが多い。あえて定義するなら「単一の技術に基づく通信網とマシンの集まり」<br>・gateway：network同士を結ぶ役割を担うハードウェア・ソフトウェア、異なる通信方式の変換機能を含む|

### 1.3 NETWORK SOFTWARE

#### 1.3.1 Protocol Hierarchies

カプセル化・交換可能性のため、プロトコルを複数のlayerに分割する考え方が一般的。

* peer
  * 各layerのinstance
  * マシン同士が通信しているとき、同じプロトコルでやり取りしているソフトウェア（ハードウェア）同士のこと
* network architecture
  * layerと対応するprotocolの定義から定まる

#### 1.3.2 Design Issues for the Layers

各layerの設計において留意すべき問題。

* 信頼性の問題
  * 符号化における信頼性
    * error detection
    * error correction
  * ルーティング
    * ある経路が使用不可であるとき、他の経路を使うようにする
* 進化(evolution)の問題
  * 規模の拡大・新技術の投入に応じて各layerのプロトコルを差し替えることで対応する
  * addressing/naming：ネットワーク内で送信元・送信先を特定すること
  * internetworking：一度に送れる情報のサイズや情報へ順序を付加する方法などが異なるプロトコルのネットワークを繋げること
  * scalable：ネットワークの拡大に柔軟に対応できること
* リソースの問題
  * なるべくマシン同士が干渉しないようなリソースの配分が必要
  * statistical multiplexing：統計に基づいて短い期間ごとに帯域を利用者（host）に振り分ける手法
  * flow control：高速な送信元から低速な送信先への送信をどうするか？
    * 送信元へ受信完了のフィードバックを返す手法がよく用いられる
  * congestion（輻輳）：伝送路の飽和、当然処理しきれない分は破棄されることになる->再送が頻発するためいつまでたっても輻輳から回復できなくなる
    * 輻輳を感知したら送信量を抑える方法がよく用いられる
  * Quality of Services（QoS）：リアルタイム性が重視されるアプリの通信などに優先的に帯域を割り当てる仕組み（単にサービス品質の意味でも用いられる）
* セキュリティの問題
  * 暗号化・信頼できる認証で対応
  * eavesdropping：立ち聞き・盗み聞き
  * surreptitious changes：データの改竄

#### 1.3.3 Connection-Oriented Versus Connectionless Service

ネットワークアーキテクチャーはconnection-oriented / connectionlessの2つに分類できる。

* Connection-oriented
  * 電話に倣った設計
  * connection：connectionの確立->通信->connectionの破棄
    * チューブのような役割を果たす
    * 送った順にデータが届く
  * negotiation：message size / QoS requiredなどの取り決め
    * 送信元・送信先・subnetで利用可能なものでなければならない
    * 一方がproposeし他方がaccept / reject / counter-proposalのいずれかを返す方法が一般的
* Connectionless
  * 郵便に倣った設計
  * packet：network layerにおけるmessage
  * store-and-forward switching：すべてのmessageを受け取ってから次のノードに流す手法
  * cut-through switching：受け取ったmessageから順次次のノードに流す手法

----

* reliability：ここでは途中でデータが失われないことを指す
* reliable connection-oriented service
  * message sequences
    * message boundaryが固定
  * byte streams
* unreliable connection-oriented service
  * 速度優先のアプリ（voice over IPなど）に利用可能
* unreliable connectionless service
  * datagram serviceとも呼ばれる
  * 様々なnetworkで利用される
* reliable connection-oriented service
  * acknowledged datagram serviceとも呼ばれる
* request-reply service
  * server-client modelでよく用いられる

Ethernetはreliableなものは提供していない。

#### 1.3.4 Service Primitives

通信を利用するプロセスは規定された操作の集まり（primitives）でserviceへ指示を出す。
当然、serviceによってprimitivesは異なる。
多くの場合、protocolはOSの組み込みとして提供されるので、システムコールがprimitivesに相当する。

#### 1.3.5 The Relationship of Services to Protocols

serviceとprotocolは全く別の概念であり、完全に切り離して考えることができる。

* service
  * layerが上位のlayerに対して提供するprimitiveの集まり
  * インターフェース
* protocol
  * 同じlayerのpeer entityが交わすpacket / messageのフォーマット・意味を定義するルール
  * layerの実装に関するルール

### 1.4 REFERENCE MODELS

layered networksの具体例としてOSI参照モデルとTCP/IP参照モデルについて見ていく。
OSI参照モデルのprotocols自体は現在は使われていないが、そのmodel自体は広く用いられている。
TCP/IP参照モデルはmodelはあまり使われないが、protocolsは広く用いられている。

#### 1.4.1 The OSI Reference Model

1983年にInternational Standards Organization(ISO)が統一的なprotocolを設計する先駆けとして提唱したモデル。
1995年に改定された。
OSIはOpen Systems Interconnectionの略。
OSI参照モデル自体はserviceやprotocolを定義するものではないので、network architectureではない。

1. The Physical Layer
    * `1`を送信したとき`0`ではなく`1`を受信するにはどうすればよいか、という問題に対処する
    * データから電気信号への変換法、伝送レート、双方向に通信できるようにするか、通信開始・終了の方法、コネクターのピン数、ピンの役割などを規定する
2. The Data Link Layer
    * 通信時のエラーを確実に検出する機能を提供するのが主な役割
    * 通信開始の方法も規定
    * 入力データをdata framesに分解し、このframeを順に送信する
    * reliable serviceの場合は受信後にacknowledgement frameを返信することで信頼性を確保する
    * broadcast networkの場合、shared channelへのアクセスをどう制御するかも問題になる
      * これに対処するためのsublayerとしてmedium access control sublayerがある
3. The Network Layer
    * subnetにおける処理を規定する
    * どのようにpacketを送信元から送信先へ導くかのアルゴリズムを提供するのが主な役割
    * 動的なルートテーブルの更新、初期接続時の動作、輻輳への対処、QoS機能の提供、protocolの異なるネットワーク同士の接続に関する問題（addressingの方法が異なる、packetサイズの上限を超えているなど）への対処などを担う
    * broadcast networkの場合は話が単純なのでそんなに規定すべきことがない
4. The Transport Layer
    * transport layerより上のlayerは送信元と送信先の間でのみ機能するprotocol（end-to-end）
      * 逆に1~3層は間のswitchやrouterなどの機材にも関与するprotocol
    * セッション層からの入力データを必要なら分割してネットワーク層に流し、受取先ですべてが届いたかを確認する
    * どのserviceを利用するかはconnection作成時に確認される
    * error-free point-to-point channel
      * トランスポート層が提供する典型的なservice
      * 送った順にbyteが届く
      * error-freeと言っても完全ではない（実用的に許容できる程度のエラー発生率であることを示す）
    * broadcasting
5. The Session Layer
    * sessionを構築する（としか書かれてない）
    * dialog control（対話制御）
      * 誰が話す番か管理するためのprotocol
    * token management
      * 二人が同時に重要な操作を実行しないようtokenによって管理するためのprotocol
    * synchronization
      * 長い通信中にエラーが生じても途中回復できるようにチェックポイントを設ける
6. The Presentation Layer
    * 伝送される情報の文法・意味を定義する
    * 内部データ表現が異なるマシン同士で通信するため、通信に用いる"標準的な"表現方法を設ける
7. The Application Layer
    * （役割については詳述されてない）
    * HTTP(HyperText Transfer Protocol)
      * WWWの基本的なprotocolとして利用されている

#### 1.4.2 The TCP/IP Reference Model

ARPANETの歴史とTCP/IP参照モデル
* DoD（アメリカ防衛省）をスポンサーとしたreserch networkとして発足
* 100以上の大学・機関の設備を結ぶネットワークに発展
* 後に衛星回線や無線回線を搭載するとき、既存のprotocolでは難しくなった
* そこで1974年に新しい参照アーキテクチャーとしてTCP/IP参照モデルが提唱された
  * 1989年に改定
* DoDの懸念としてソ連にARPANETを破壊されないかというものがあった
  * そのため一部のhardwareが喪失してもロスタイムなく機能し続けることが求められた
* ファイルの送信から電話まで幅広い用途に対応できる必要があった

----

1. The Link Layer
    * OSI参照モデルのData Linkに相当
    * connectionless internet layerに対して下位層がどのようなserviceを提供すべきか定義したもの（当初はconnectionlessのみを想定していたため）
    * ここまでの説明におけるlayerのようなはっきりした概念ではなかった
2. The Internet Layer
    * OSI参照モデルのNetworkに相当
    * hostがpacketを任意のnetworkに流し込め、個々のpacketが独立に相手に届けられるようなserviceを規定する
    * インターネットでは公式のpacketのformat / protocolとしてIP(Internet Protocol)、その補助機能としてICMP(Internet Control Message Protocol)が規定されている
3. The Transport Layer
    * OSI参照モデルのTransportに相当
    * TCP(Transmission Control Protocol)
      * reliable connection-oriented protocol / byte stream
      * routing algorithmを内包する
      * 低速な送信先に高速にデータ転送してパンクさせないための機能も含まれている
    * UDP(User Datagram Protocol)
      * unreliable connectionless protocol
      * 正確さより迅速さが重要視されるときによく用いられる
4. The Application Layer
    * sessionやpresentationの機能もここに含まれる
      * 多くのアプリケーションではこの辺りの機能はさほど肥大化しない
    * TELNET：virtual terminal
    * FTP：ファイル転送用のprotocol
    * SMTP：電子メール用のprotocol
    * DNS：動的名前解決
    * HTTP：WWWで重用されるprotocol
    * RTP：音声・映像のリアルタイムな伝送を目的としたprotocol

#### 1.4.3 The Model Used in This Book

OSI参照モデルはmodelの説明に適しており、TCP/IP参照モデルはprotocolの説明に適している。

この本では折衷案として次のようなハイブリッドモデルに基づいて説明を進める。

1. Physical
    * 電気信号などの異なる種類の媒体を通してどのようにbitを伝送するか
2. Link
    * 直接接続されているデバイス間において、どのように適度な信頼性を保ちつつ有限な長さのmessageを伝送するか
3. Network
    * 複数のlinkや小規模なnetworkをどのように繋げてnetworkとして機能させるか
    * 目的地への経路探索などの機能を含む
4. Transport
    * Network層の伝送の信頼度を高める
5. Application
    * ネットワークを利用するためのprogramを提供する

#### 1.4.4 A Comparison of the OSI and TCP/IP Reference Models

2つの参照モデルは、end-to-end serviceを提供するtransport層が存在しているなど共通する箇所もある一方で、いくつかの重要な違いがある。

OSI参照モデルはServices / Interfaces / Protocolsの3つの概念を支柱としている。
このモデルの功績はこの3つの概念の違いを明示したことにある。

* service：そのlayerが何をするか（どうするかではない）を示す
* interface：上位layerがそのlayerに対してどのようなアクセスが可能であるかを示す（その際に必要なパラメーターの定義も含む）
* protocol：そのlayerの仕事内容（実装）を示す

TCP/IP参照モデルはもともとこの3つの区別が曖昧で、OSI参照モデルよりlayerの透過性が悪い。

またOSI参照モデルは対応するprotocolの設計前に提案されたため、特定のprotocolによるバイアスがかかっていない。
逆にTCP/IP参照モデルは特定のprotocol群によるバイアスがかかっている上、透過性が悪いため他の実装に当てはまりにくいことがある。
一方でTCP/IP参照モデルは実際にprotocolを設計した経験を元に提案できたという利点がある。
例えばデータリンク層はもともとpoint-to-pointで設計されていたが、broadcastの出現と共に新たなsublayerが追加された。
そのほかにもsublayerが追加された例はいくつかあるらしい。
またOSI protocolは他のprotocolを利用するnetworkとの接続を想定していなかった。

OSI参照モデルはネットワーク層でconnection-oriented / connectionless両方に対応し、トランスポート層でconnection-orientedに対応している。
TCP/IP参照モデルはネットワーク層でconnectionlessに対応し、トランスポート層で両方に対応している。
ユーザーが実際に利用する際に参照するのはトランスポート層なのでOSIの仕様ではユーザーが選択することができなくなってしまっていることになる。

#### 1.4.5 A Critique of the OSI Model and Protocols

この本の第二版が出た頃（1989）にはOSI参照モデルとprotocol群が覇権を握ると主張する専門家が多くいたが、実際にはそうならなかった。
その要因は次のようにまとめられる。

1. Bad timing
    * 「提唱->研究（活性期間1）->標準化->投資・普及（活性期間2）」（apocalypse of the two elephants：”標準化の定理”）の標準化の段階で破綻した
      * 標準化が早すぎると早熟で失敗、標準化が遅すぎるとみんな他の技術に投資してしまう、標準化期間が短すぎると破綻してしまう
    * OSI protocolsが登場したときにはすでにTCP/IP protocolsが教育・研究機関へ浸透しつつあった
2. Bad technology
    * serviceとprotocolsの定義が非常に複雑だった
    * addressing, flow control, error controlが各layerで何度も登場した
      * 批判の例として、Saltzerらがerror controlは上位layerで一括して行うべきであると指摘している
3. Bad implementations
    * 複雑なservece, protocolsの定義も相まって非常に重かった
    * 対象的に、TCP/IP protocolsはBSDに非常によい実装がされた上で搭載されていた
4. Bad politics
    * TCP/IPはUNIXの1機能として認知されることになった
    * OSIはヨーロッパの通信省による手先、といったイメージがあった
    * イメージはともかく、官僚が推し進めようとする不適当な標準化は研究者やプログラマーには浸透しなかった

#### 1.4.6 A Critique of the TCP/IP Reference Model

ここまでにもちらほら出てきたように、TCP/IP参照モデルにもいくつか問題がある。

1. 前述のように、service / interface / protocolの区別が不明瞭である
2. 他のプロトコル群にあまり当てはまらない
    * 例えばBluetoothをTCP/IP参照モデルで記述するのはほぼ不可能
3. リンク層がlayered protocolsにおけるlayerとしての体裁を保っていない
    * どちらかと言えばinterfaceに相当する
4. 物理層とデータリンク層の区別がない
5. IP / TCP protocols以外は微妙なものが含まれたまま広まってしまった
    * TELNETは10 char/secのテレタイプ端末にのみ対応しており、GUIやマウスには対応していないが、現在も使われている

### 1.5 EXAMPLE NETWORKS

#### 1.5.1 The Internet

The Internetは特定のprotocolsを用いるnetworkの集合体。
特定の誰かによって企画されたものでも制御されるものでもない。
これについて深く理解するためにThe Internetの歴史を紐解く。

**The ARPANET**

冷戦真っ只中の1950年代後半、アメリカ防衛省が核戦争の中でも利用可能な司令網を欲したことからARPANETの開発が始まった。
当時は司令に公衆電話網が用いられていたが、toll office->switching office->telephoneという階層構造になっていたため重要なtoll officeが破壊されると通信網が機能しなくなるという欠点があった。
