# CPU

## 主要メーカー

### Intel（アメリカ：カリフォルニア）

* Pentium
* Core Series

### AMD（Advanced Micro Device）（アメリカ：カリフォルニア）

* AMD Series

### ARM（Advanced RISC Machine）（イギリス：ケンブリッジ）

* ARM

### Microchip（アメリカ：アリゾナ）

* PIC

### Atmel（アメリカ：カリフォルニア）

※ 2016年に買収によりMicrochipの子会社化

* AVR

## 用語

### 命令セット（instruction set / collection of instructions）

CPUが解読・実行できる命令の集まりのこと。
命令セットの仕様はハードウェアレベルで実装されるため通常はプロセッサーごとに命令セットが異なる。

#### RISC（Reduced Instruction Set Computer）

比較的単純な回路で基本的な命令セットのみを実現するという設計方針。

#### CISC（Complex Instruction Set Computer）

複雑な回路でより多くの複雑な命令セットを実現するというという設計方針。

#### オペランドで指定するアドレスの個数による分類

* 0アドレス命令形式
* 1アドレス命令形式
* 2アドレス命令形式
* 3アドレス命令形式

### セグメント方式

プログラムやデータをセグメントという可変な大きさのまとまりで管理するメモリ管理方式。

### 互換CPU・互換プロセッサー

CPUにおける**互換性**とは命令セットが同じであることを指す。

### x86

Intelが開発したマイクロプロセッサの命令セットアーキテクチャ。

* 1978年 Intel 8086・8088
  * 16bitレジスタ・16bit外部データバス（8088は8bit）・20bitのアドレス指定（1MiBアドレス空間）
  * 4つのセグメントレジスタ＋16bitでセグメントの切り替えなしに20bitのアドレス指定が行える

https://www.intel.co.jp/content/dam/www/public/ijkk/jp/ja/documents/developer/IA32_Arh_Dev_Man_Vol1_Online_i.pdf
