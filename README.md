# GraduationResearch-v2 [![Static Badge](https://img.shields.io/badge/GitHub-repo-blue?logo=github)](https://github.com/Shimoyama-h26ms419/GraduationResearch-v2) [![Static Badge](https://img.shields.io/badge/Python-v3.14.5-green?logo=python&logoColor=white)](https://www.python.org/downloads/release/python-3145/) [![Static Badge](https://img.shields.io/badge/PyTorch-v2.12.0%2Bcu132-orange?logo=pytorch&logoColor=white)](https://pytorch.org/)

## 0. TL;DR
- 学部時代に行った [**卒業研究**](https://github.com/Shimoyama-h22s4059/GR2025) を基に、大学院で発展的に取り組んでいる研究のリポジトリです。

## 1. Overview（概要）

### 研究タイトル
> Vision Transformer によるアミノ酸配列のグラフ表示画像のGPCRクラス分類

### 研究目的
- 既存のCNNに代わり、Vision Transformerを使うことにより分類の性能向上を目指す

## 2. Background（背景）
- 近年、タンパク質のファミリー分類を行う研究が盛んに行われている
- CNNでは勾配消失問題により長距離のアミノ酸間の特徴を捉えづらい、などの問題が発生する
- Vision Transformerにより、この問題を解決できないかと考えた

## 3. Structure（構造）
- 📂 [`GraduationResearch-v2`](.)（このリポジトリ）
  - 📂 [`data`](/data)（データセットなどを保管する）
  - 📂 [`images`](/images)（作成したグラフ表示画像などを保管する）
  - 📂 [`jupyter`](/images)（Jupyter Notebookを保管する）
  - 📂 [`labels`](/images)（ラベルデータを保管する）
  - 📂 [`models`](/images)（学習済みのモデルを保管する）
  - 📄 [`requirements.txt`](/requirements.txt)（pipの依存関係の一覧）

## 4. Setup（環境構築）
環境構築の方法を説明します。

### 4.0 使用環境
- Python：`3.14.5`
- PyTorch：`2.12.0+cu132`
- その他のライブラリなどは  [📄 `requirements.txt`](/requirements.txt) に記載しています。

### 4.1 Pythonのインストール
1. [**Python公式ページ**](https://www.python.org/downloads/release/python-3145/) から **Python 3.14.5** をインストールします。
2. `PATH` を通してターミナルから **Python 3.14.5** を起動できることを確認します。

#### Windows 
```
py -3.14 -V
```

#### Linux
```
python3.14 -V
```

以下のように **Python 3.14.5** が正常にインストールされているかを確認します。
```terminaloutput
Python 3.14.5
```

### 4.2 リポジトリのクローン
ディレクトリは分かりやすい場所ならばどこでも構いません。

```
git clone https://github.com/Shimoyama-h26ms419/GraduationResearch-v2.git
```

次に、作業ディレクトリに移動します。
```
cd ./GraduationResearch-v2
```

### 4.3 仮想環境の作成
仮想環境（venv）の作成を行います。 以下のコマンドで仮想環境を `.venv` ディレクトリに作成します。

#### Windows
```
py -3.14 -m venv ./.venv
```

#### Linux
```
python3.14 -m venv ./.venv
```

次に仮想環境をアクティブにします。

#### Windows
```
./.venv/Script/activate
```

#### Linux
```
source ./.venv/bin/activate
```

コンソールのユーザー名の左に `(.venv)` と表示されることを確認します。

#### Windows
```terminaloutput
(.venv) PS C:\path\to\GraduationResearch-v2>
```

#### Linux
```terminaloutput
(.venv) user-name@computer-name:~/path/to/GraduationResearch-v2$
```

### 4.4 必要ライブラリのインストール
必要なライブラリなどを一括でインストールします。 以下のコマンドを順に実行してインストールします。

```
pip install torch torchvision --index-url https://download.pytorch.org/whl/cu132
pip install ipywidgets transformers[torch]
pip install -r requirements.txt
```

インストールが終了したら、CUDAが対応してるかを確認します。 `cuda` が出ればGPU対応、`cpu` が出ればGPUは非対応です。

```python
import torch

print("cuda" if torch.cuda.is_available() else "cpu")
```

## 5. Method（手法）
この研究の手法を以下に示します。

### 5.1 データセット
使用したデータセットは以下の通りです。

#### 5.1.1 BIAS-PROFS
ダウンロードは [**ここ**](https://www.cs.kent.ac.uk/projects/biasprofs/downloads.html) から可能です。

詳細は [📄 `/data/bias-profs-family.md`](/data/bias-profs-family.md) を参照してください。

#### 5.1.2 InterPro
ダウンロードは [![Static Badge](https://img.shields.io/badge/--gray?logo=jupyter) `/jupyter/download-interpro.ipynb`](/jupyter/download-interpro.ipynb) から可能です。

詳細は以下を参照してください。
- クラスごとの詳細：[📄 `/data/interpro-class.md`](/data/interpro-class.md)
- ファミリーごとの詳細：[📄 `/data/interpro-family.md`](/data/interpro-family.md)

### 5.2 グラフ表示画像 および ラベルCSV の作成
以下の Jupyter Notebook から利用できます。

- BIAS-PROFS：[![Static Badge](https://img.shields.io/badge/--gray?logo=jupyter) `/jupyter/processing-bias-profs.ipynb`](/jupyter/processing-bias-profs.ipynb)
- InterPro：[![Static Badge](https://img.shields.io/badge/--gray?logo=jupyter) `/jupyter/processing-interpro.ipynb`](/jupyter/processing-interpro.ipynb)

### 5.3 使用モデル
[`timm`](https://pypi.org/project/timm/) ライブラリを使い、[`timm/maxvit_small_tf_224.in1k`](https://huggingface.co/timm/maxvit_small_tf_224.in1k) を使用しました。

## 6. Results（結果）
> [!Note]
> 工事中です

## 7. Notice（注意点など）
- PyTorch は基本的に **GPU版** をインストールするべきです。
- Jupyter Notebook の機械学習では `SEED = 42` で固定しています。

## 8. ToDo
> [!Note]
> 工事中です

## 9. References（参考文献）
- Kawashima, Shuichi, and Minoru Kanehisa. "AAindex: amino acid index database." _Nucleic acids research_ 28.1 (2000): 374-374.
- Davies, Matthew N., et al. "On the hierarchical classification of G protein-coupled receptors." _Bioinformatics_ 23.23 (2007): 3113-3118.
- Blum, Matthias, et al. "InterPro: the protein sequence classification resource in 2025." _Nucleic acids research_ 53.D1 (2025): D444-D456.
- Vaswani, Ashish, et al. "Attention is all you need." _Advances in neural information processing systems 30_ (2017).
- Dosovitskiy, Alexey, et al. "An image is worth 16x16 words: Transformers for image recognition at scale." _arXiv preprint arXiv:2010.11929_ (2020).
- Tu, Zhengzhong, et al. "Maxvit: Multi-axis vision transformer." _European conference on computer vision_. Cham: Springer Nature Switzerland, 2022.
- 山口秀輝, and 齋藤裕. "タンパク質の言語モデル." _JSBi Bioinformatics Review_ 4.1 (2023): 52-67.

## 10. Citation（引用）
> [!Note]
> 工事中です
