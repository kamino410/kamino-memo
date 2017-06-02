# GPU関連の用語

## GPUとは

Graphics Processing Unitの略で画像処理を高速に実行できるよう設計されたコンピューターの構成要素のひとつ。
画像の描画に必要な演算を並列化し、高速に処理することができる。

## 主なGPU開発企業

ほぼ2社独占状態。

* NVIDIA
* AMD

## 主なGPUシリーズ

### NVIDIA GeForce / AMD Radeon
DirectX用に最適化されている。ゲーム向け。

### NVIDIA Quadro / AMD FirePro
OpenGL用に最適化されている。3DCGやCAD向け。

### NVIDIA Telsa / AMD FireStream
GPGPU（General-purpose computing on graphics processing units）向けに最適化されている。

### NVIDIA Tegra
モバイル用。

## 開発プラットフォーム

### CUDA（Compute Unified Device Architecture）

NVIDIAが開発したGPUプログラミング向けの統合開発環境。
対応言語はC/C\+\+に準拠（ただし、C\+\+は一部の構文にのみ対応）したCUDA C/C\+\+で、ファイル拡張子には`cu`、`cuh`などが用いられる。
CUDA 7の時点でラムダ式などC\+\+11の一部の規格に対応済み。

その他、CUDA ToolkitというSDKが公開されている。
CUDA ToolkitにはC\+\+のテンプレートプログラミングライブラリ（主にvector<T>とか）のThrustなどが含まれており、これらを通してCUDA以外の開発環境でもGPUの資産を利用することができる。
