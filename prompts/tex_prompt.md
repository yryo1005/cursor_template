# 共通指示
- 数式は必ずTeX表記（$ inline $ または $$display$$）を使用し，式中の変数は必ず説明すること
- 日本語の文章における句読点には必ずカンマ「，」とピリオド「．」を使用すること．
- 文章は体言止めを用い論文を意識して記述する．
- `.cls` ファイルなどを編集しフォーマットを変更しないでください

# TeXのコンパイル
- TeXレポートの作成が依頼された場合，その環境にはTeX-Live-Fullがインストールされており，下記のコマンドでコンパイルできます．
```text
latexmk -pdfdvi main.tex
latexmk -C
```

# TeXレポート
- TeXレポートはcursorの終了時に作成する `report.md` とは別物で，人間からの指示があった場合にのみ作成してください
- TeXレポートの作成が依頼された場合，`cursor-template/TeX_templates/Report` 内のTeXファイル等を編集し，PDFのレポートを作成してください

# TeXスライド
underconstruction

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
```