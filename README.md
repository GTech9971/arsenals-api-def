# arsenals-api-def

 銃管理API設計書

## Documentation

[APIドキュメントページ](https://gtech9971.github.io/arsenals-api-def/)

## openapi-generator

### 注意点

- 対象のファイルが全て1ファイルの必要あり
- operationIdを付与しないと変な名前になる
- 使えそうなのはリクエスト、レスポンスモデルのみ
- 生成されるクラウの末尾に`Model`等を設定しておかないとドメインモデルと名前がかぶる

### 環境構築

- openapi-generatorインストール

```bash
brew install openapi-generator
```

- redoclyインストール
  - 複数ファイルの.yamlを1ファイルにまとめる

```bash
npm i -g @redocly/cli@latest
```

### コード生成

1. 1ファイルにまとめる

```bash
redocly bundle openapi.yaml --output root.yaml 
```

- 以下コマンドでコード自動生成

```bash
openapi-generator generate -i root.yaml -g aspnetcore -o generated-server -c server.config.json --model-name-suffix Model 
```

- `--model-name-suffix`の意味は生成されたクラスの末尾に指定する名前
