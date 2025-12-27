## プロジェクト概要

datahaikuninja の職務経歴書および履歴書を typst でビルドする

## ディレクトリ構造

```
- resume
  - content
    - foo.yaml # tmpl/foo.typ から参照されるデータ
    - bar.yaml # tmpl/bar.typ から参照されるデータ
    - ...
  - tmpl
    - foo.typ # content/foo.typ を参照するテンプレートファイル
    - bar.typ # content/bar.typ を参照するテンプレートファイル
    - ...
  - main.typ # tmpl を include して pdf を出力するビルドスクリプト
- README.md # このプロジェクトの概要、使用方法等を記載する
```

## あなた(gemini)に求めること

1. あなたは、このファイル(instruction.md) のディレクトリ構造に従ってファイルを配置する
2. あなたは、この箇条書きの 3 に記載する成果物(pdf)をビルドするために必要な yaml および typst ファイルを生成する
3. あなたが生成する yaml および typst ファイルを使用すると、以下の公開リポジトリと同等の pdf ファイルが成果物として出力される
  * [takeokunn/typst-resume-template/blob/main/cv/cv.pdf](https://github.com/takeokunn/typst-resume-template/blob/main/cv/cv.pdf)
4. pdf をビルドするために typst の外部ツールを使用しない（例：nix）
  * [ShinoharaTa/typst-work-resume](https://github.com/ShinoharaTa/typst-work-resume/blob/main/README.md) に記載されているビルド方法を参考にする
5. README.md を生成する

## あなた(gemini)に禁止すること

1. nix を使用することを禁止します
