# 職務経歴書・履歴書 (Typst)

datahaikuninja の職務経歴書および履歴書を `typst` でビルドするためのプロジェクトです。

## 概要

このプロジェクトは、[takeokunn/typst-resume-template](https://github.com/takeokunn/typst-resume-template) を参考に作成されています。
`typst` を利用して、YAML ファイルに記載されたデータから PDF 形式の職務経歴書を生成します。

## ディレクトリ構造

```
- resume
  - content/    # 経歴書に記載するデータを格納するディレクトリ
    - profile.yaml
    - overview.yaml
    - jobs.yaml
  - tmpl/       # `typst` のテンプレートファイルを格納するディレクトリ
    - profile.typ
    - overview.typ
    - jobs.typ
  - main.typ    # ビルドのエントリポイント
  - main.pdf    # 生成された PDF ファイル
- README.md
```

## 使用方法

### 1. 必要なツールのインストール

#### Typst

このプロジェクトは `typst` を使用します。`typst` がインストールされていない場合は、以下の方法でインストールしてください。

**macOS (Homebrew):**
```bash
brew install typst
```

その他の OS については、[公式ドキュメント](https://github.com/typst/typst) を参照してください。

#### フォント

このテンプレートは `HackGen` フォントの使用を想定しています。お使いのシステムにフォントがインストールされていない場合、正しく表示されない可能性があります。

以下のリンクからフォントをダウンロードし、インストールしてください。

*   [yuru7/HackGen](https://github.com/yuru7/HackGen)

### 2. データの編集

`resume/content/` ディレクトリ内の各 YAML ファイルを、ご自身の情報に合わせて編集してください。

### 3. PDF のビルド

以下のコマンドを実行すると、`resume/main.pdf` が生成・更新されます。

```bash
cd resume
typst compile main.typ
```

### 4. 職務経歴書の各セクションを更新（修正、削除、追加）する方法

職務経歴書の各セクションを更新する方法は、`resume/content/` ディレクトリ内の YAML ファイルを編集し、再度 PDF をビルドすることで行います。

以下に、具体的な手順を説明します。

#### 編集したいセクションに対応するファイルを特定する

まず、更新したい内容がどのファイルで管理されているかを確認します。

*   **氏名、連絡先、スキル概要など**: `resume/content/profile.yaml`
*   **職務要約（一覧表形式）**: `resume/content/overview.yaml`
*   **職務経歴の詳細**: `resume/content/jobs.yaml`

#### YAML ファイルを編集する

特定したファイルをテキストエディタで開いて編集します。

##### **修正**

既存のテキストを直接修正します。

例：`profile.yaml` の氏名を変更する
```yaml
# 修正前
name: "猫 太郎"

# 修正後
name: "犬 次郎"
```

##### **追加**

リスト（`-` で始まる行）になっている箇所に、同じ構造の項目を追記します。職務経歴などを追加する場合がこれに該当します。

例：`jobs.yaml` に新しい職務経歴を追加する
```yaml
# (既存の経歴)
- title: "株式会社キャット Web開発"
  # ... (中略) ...

# (ここから下を追記する)
- title: "株式会社バード Web開発"
  period:
    from: "25/8"
    to: "現在"
    span: "X年Xヶ月"
  workdetail:
    kind: "サービス"
    type: "Web"
    size: "3名"
  content: |
    株式会社バードでWeb開発を行った
  use-soft: |
    Git
    GCP
    Docker
    Jira
  lang-othor: |
    Go
    Next.js
    GCP
```

##### **削除**

リスト (`-` で始まる行のブロック) から、不要な項目をブロックごと削除します。

例：`jobs.yaml` から古い職務経歴を削除する
```yaml
# (このブロックを丸ごと削除する)
- title: "株式会社ドッグ Web開発"
  period:
    from: "22/10"
    to: "23/10"
    span: "1年10ヶ月"
  # ... (以下略) ...
```

#### PDF を再ビルドする

YAML ファイルの編集が完了したら、ターミナルで `resume` ディレクトリに移動し、再度ビルドコマンドを実行します。

```bash
cd resume
typst compile main.typ
```

これにより `main.pdf` が更新され、変更が反映されます。