# 共通指示
- 作成する各関数には，日本語の概要、引数のデータ型/形状，戻り値のデータ型/形状をコメント（Docstring）で明記する．
- プログラムの作成・整備が終了した段階で，メインロジックや関数の関係性をグラフなどで説明した `document.md` を作成すること．
- 人間がコードを読む際の可読性を担保してください．ネストが深くなると人間のデバックが困難になるので，その様なプログラムは避けるべきでしょう．
  
---

# 読み込むドキュメント
指示に応じ，下記の指定したドキュメントを読み込んでください．

| 対象タスク | 参照すべきプロンプトファイル |
| :--- | :--- |
| AIの学習 | @cursor_template/prompts/machine_learning_prompt.md |
| ドキュメントの作成 | @cursor_template/prompts/document_prompt.md |
| 仮想環境の作成 | @cursor_template/prompts/environment_construction_prompt.md |
| TeXレポートの作成 | @cursor_template/prompts/tex_prompt.md |

---

# ディレクトリ構造の例
```text
.
├── cursor-template/         # cursorへの指示等やTeXレポートのテンプレートをまとめたリポジトリ
│   ├── root_prompt.md       # プログラムの指示が書かれたドキュメント
|   ├── prompts/             # それぞれのタスクの指示が書かれたプロンプトがまとめられたフォルダ
│   │   ├── environment_construction_prompt.md      # 環境構築の指示が書かれたドキュメント
│   │   ├── machine_learning_prompt.md              # AIの学習の指示が書かれたドキュメント
│   │   ├── document.md                             # ドキュメントの指示が書かれたドキュメント
│   |   └── tex.py                                  # TeXの指示が書かれたドキュメント
|   ├── srs/                 # それぞれのタスクの便利関数がまとめられたフォルダ
│   |   └── machine_learning_utils.py               # AIの学習で使用する便利関数がまとめられたファイル
|   └── TeX_templates/       # TeXテンプレートがまとめられたフォルダ
│       └── Report           # レポートのテンプレート
│           ├── main.tex         # latexでコンパイルするソース
│           ├── sections/        # レポートの章ごとに分けられたソースをまとめたフォルダ
│           │   └── 01_introdcution.tex             # ソースは章ごとに分割する
│           └── figures/         # レポートの画像をまとめたフォルダ
├── .gitignore               # outputs/ や datasets/、除外
│
├── ex001_mnist_cnn/         # 実験001: 全比較手法で共通の条件（例: MNISTに対するCNN）
│   ├── model.py             # この実験で使用するモデル構造（CNN）の定義
│   ├── utils.py             # load_dataloader, load_model, 各種関数を定義
│   └── train.ipynb          # ハイパーパラメータやseedのループを回して学習を実行する主体
│
├── ex002_cifar10/           # 実験002: （例: CIFAR-10に対する実験）
│   ├── model.py
│   ├── utils.py
│   └── train.ipynb
│
├── outputs/                 # 実験結果の出力先（.gitignoreに対象設定）
│   ├── ex001_mnist_cnn/
│   │   ├── SGD/             # 比較する手法 1
│   │   │   ├── 0.001_32/    # ハイパーパラメータ（学習率_バッチサイズ）
│   │   │   │   ├── 0/       # seed 0 の結果
│   │   │   │   │   ├── best_model.pth
│   │   │   │   │   └── log.json
│   │   │   │   └── 1/       # seed 1 の結果
│   │   │   │       ├── best_model.pth
│   │   │   │       └── log.json
│   │   │   └── 0.01_64/
│   │   │       └── ...
│   │   └── Adam/            # 比較する手法 2
│   │       └── ...
│   └── ex002_cifar10/
│       └── ...
│
├── order.md                 # 作成するプログラムの指示が書かれたドキュメント (order_k.mdのように通し番号がある場合がある)
├── document.md              # メインロジックやコード仕様を解説したドキュメント
└── report.md                # 実施した全実験の結果や考察をまとめたレポート (report_k.mdのように通し番号がある場合がある)
```