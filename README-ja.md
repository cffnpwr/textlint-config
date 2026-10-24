# @cffnpwr/textlint-config

[![GitHub License](https://img.shields.io/github/license/cffnpwr/textlint-config?style=flat)](./LICENSE)
[![npm Version](https://img.shields.io/npm/v/%40cffnpwr%2Ftextlint-config?style=flat)](https://www.npmjs.com/package/@cffnpwr/textlint-config)
[![JSR Version](https://jsr.io/badges/@cffnpwr/textlint-config)](https://jsr.io/@cffnpwr/textlint-config)

cffnpwrのための日本語文書向けtextlint共通設定です。

[README.md for English is available here](./README.md).

## 含まれるもの

`.textlintrc.json`と`.prh.yml`を同梱し、これらが参照するルールとプラグインをすべて依存に含みます。

| ルール・プラグイン | 用途 |
| --- | --- |
| [textlint-rule-preset-ja-technical-writing](https://github.com/textlint-ja/textlint-rule-preset-ja-technical-writing) | 日本語の技術文書向けルール（`no-mix-dearu-desumasu`は緩和） |
| [textlint-rule-preset-ja-spacing](https://github.com/textlint-ja/textlint-rule-preset-ja-spacing) | 日本語と他の文字の間のスペースに関するルール |
| [@textlint-ja/textlint-rule-preset-ai-writing](https://github.com/textlint-ja/textlint-rule-preset-ai-writing) | AI生成文に特有の表現の検出 |
| [@cffnpwr/textlint-rule-preset-ja-writing-extras](https://github.com/cffnpwr/textlint-rule-preset-ja-writing-extras) | 日本語文書向けの追加ルール |
| [@textlint-ja/textlint-rule-no-synonyms](https://github.com/textlint-ja/textlint-rule-no-synonyms) | 文書内で混在する類義語の検出 |
| [@textlint-ja/textlint-rule-no-insert-re](https://github.com/textlint-ja/textlint-rule-no-insert-re) | 「れ」の余分な挿入の検出 |
| [@textlint-ja/textlint-rule-no-dropping-i](https://github.com/textlint-ja/textlint-rule-no-dropping-i) | 「い抜き言葉」の検出 |
| [@textlint-ja/textlint-rule-no-insert-dropping-sa](https://github.com/textlint-ja/textlint-rule-no-insert-dropping-sa) | 「さ入れ言葉」「さ抜き言葉」の検出 |
| [textlint-rule-prefer-tari-tari](https://github.com/textlint-ja/textlint-rule-prefer-tari-tari) | 「〜たり」の並列使用の推奨 |
| [textlint-rule-no-mixed-zenkaku-and-hankaku-alphabet](https://github.com/textlint-ja/textlint-rule-no-mixed-zenkaku-and-hankaku-alphabet) | 全角と半角のアルファベットの混在の検出 |
| [textlint-rule-period-in-list-item](https://github.com/textlint-ja/textlint-rule-period-in-list-item) | リスト項目末尾の句点の検査 |
| [textlint-rule-ja-no-orthographic-variants](https://github.com/textlint-ja/textlint-rule-ja-no-orthographic-variants) | 表記ゆれの検出 |
| [textlint-rule-prh](https://github.com/textlint-rule/textlint-rule-prh) | `.prh.yml`の辞書による校正 |
| [textlint-plugin-latex2e](https://github.com/textlint/textlint-plugin-latex2e) | LaTeXファイルへの対応 |

## How to Install

`textlint`はpeer dependencyです。
このパッケージと一緒にプロジェクトへインストールしてください。

### npm

```sh
npm install -D textlint @cffnpwr/textlint-config
```

or

```sh
npx jsr add -D @cffnpwr/textlint-config
```

### yarn

```sh
yarn add -D textlint @cffnpwr/textlint-config
```

or

```sh
yarn dlx jsr add -D @cffnpwr/textlint-config
```

### pnpm

```sh
pnpm add -D textlint @cffnpwr/textlint-config
```

or

```sh
pnpm dlx jsr add -D @cffnpwr/textlint-config
```

### Bun

```sh
bun add -D textlint @cffnpwr/textlint-config
```

or

```sh
bunx jsr add -D @cffnpwr/textlint-config
```

### Deno

```sh
deno add -D npm:@cffnpwr/textlint-config
```

or

```sh
deno add -D jsr:@cffnpwr/textlint-config
```

## How to use

textlintには`extends`がなく、`--config`にはパッケージ名を渡せません。
代わりに、`node_modules`内の設定ファイルのパスを渡します。

```sh
textlint --config node_modules/@cffnpwr/textlint-config/.textlintrc.json <files>
```

スクリプトから使う場合は`package.json`に追記します。

```json
{
  "scripts": {
    "lint": "textlint --config node_modules/@cffnpwr/textlint-config/.textlintrc.json \"**/*.md\""
  }
}
```

`textlint`はプロジェクト自身の依存に加えてください。
Bunのisolatedレイアウト（`isolated` linker）では、`textlint`が直接の依存である場合にだけ`textlint`コマンドがリンクされます。
このパッケージのpeer dependencyとして入った`textlint`は、コマンドとしては使えません。

ルールとプラグインは、このパッケージの依存から解決されます。
hoistedとisolatedのどちらのレイアウトでも動作します。

## License

[MIT License](./LICENSE)
