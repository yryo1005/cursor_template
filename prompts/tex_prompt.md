# 共通指示
- TeXのテンプレートのリポジトリをサブモジュールとして追加し，`@cursor_TeX/README.md`に従いレポートを作成してください．

```text
git submodule add https://github.com/yryo1005/cursor_TeX.git
```

# ディレクトリ構造
```text
.
├── cursor-template/         # cursorへの指示等やTeXレポートのテンプレートをまとめたリポジトリ
│   ├── root_prompt.md       # プログラムの指示が書かれたドキュメント
|   ├── prompts/             # それぞれのタスクの指示が書かれたプロンプトがまとめられたフォルダ
│   │   ├── environment_construction_prompt.md      # 環境構築の指示が書かれたドキュメント
│   │   ├── machine_learning_prompt.md              # AIの学習の指示が書かれたドキュメント
│   │   ├── document.md                             # ドキュメントの指示が書かれたドキュメント
│   |   └── tex.py                                  # TeXの指示が書かれたドキュメント
|   └── srs/                 # それぞれのタスクの便利関数がまとめられたフォルダ
│       └── machine_learning_utils.py               # AIの学習で使用する便利関数がまとめられたファイル
│
├── cursor_TeX/              # TeXテンプレートがまとめられたリポジトリ
│   ├── README.md            # 文章を書く際の注意事項がまとめられたドキュメント
│   └── TeX_templates/       # TeXテンプレートがまとめられたフォルダ
│       └── Report               # レポートのテンプレート
│           ├── main.tex         # latexでコンパイルするソース
│           ├── sections/        # レポートの章ごとに分けられたソースをまとめたフォルダ
│           │   └── 01_introdcution.tex             # ソースは章ごとに分割する
│           └── figures/         # レポートの画像をまとめたフォルダ
```