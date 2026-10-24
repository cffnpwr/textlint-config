# @cffnpwr/textlint-config

[![GitHub License](https://img.shields.io/github/license/cffnpwr/textlint-config?style=flat)](./LICENSE)
[![npm Version](https://img.shields.io/npm/v/%40cffnpwr%2Ftextlint-config?style=flat)](https://www.npmjs.com/package/@cffnpwr/textlint-config)
[![JSR Version](https://jsr.io/badges/@cffnpwr/textlint-config)](https://jsr.io/@cffnpwr/textlint-config)

A shared textlint configuration for Japanese writing, maintained by cffnpwr.

[日本語のREADMEはこちら](./README-ja.md)

## What's Included

The package ships `.textlintrc.json` and `.prh.yml`, and depends on every rule and plugin they reference.

| Rule or plugin | Purpose |
| --- | --- |
| [textlint-rule-preset-ja-technical-writing](https://github.com/textlint-ja/textlint-rule-preset-ja-technical-writing) | Technical writing rules for Japanese (`no-mix-dearu-desumasu` is relaxed) |
| [textlint-rule-preset-ja-spacing](https://github.com/textlint-ja/textlint-rule-preset-ja-spacing) | Spacing rules between Japanese and other characters |
| [@textlint-ja/textlint-rule-preset-ai-writing](https://github.com/textlint-ja/textlint-rule-preset-ai-writing) | Detects expressions typical of AI-generated text |
| [@cffnpwr/textlint-rule-preset-ja-writing-extras](https://github.com/cffnpwr/textlint-rule-preset-ja-writing-extras) | Additional rules for Japanese writing |
| [@textlint-ja/textlint-rule-no-synonyms](https://github.com/textlint-ja/textlint-rule-no-synonyms) | Detects synonyms mixed within a document |
| [@textlint-ja/textlint-rule-no-insert-re](https://github.com/textlint-ja/textlint-rule-no-insert-re) | Detects inserted `re` in 「ら抜き」 style expressions |
| [@textlint-ja/textlint-rule-no-dropping-i](https://github.com/textlint-ja/textlint-rule-no-dropping-i) | Detects dropped 「い」 in 「い抜き」 style expressions |
| [@textlint-ja/textlint-rule-no-insert-dropping-sa](https://github.com/textlint-ja/textlint-rule-no-insert-dropping-sa) | Detects inserted or dropped 「さ」 |
| [textlint-rule-prefer-tari-tari](https://github.com/textlint-ja/textlint-rule-prefer-tari-tari) | Prefers repeating 「〜たり」 |
| [textlint-rule-no-mixed-zenkaku-and-hankaku-alphabet](https://github.com/textlint-ja/textlint-rule-no-mixed-zenkaku-and-hankaku-alphabet) | Detects mixed full-width and half-width alphabets |
| [textlint-rule-period-in-list-item](https://github.com/textlint-ja/textlint-rule-period-in-list-item) | Checks periods at the end of list items |
| [textlint-rule-ja-no-orthographic-variants](https://github.com/textlint-ja/textlint-rule-ja-no-orthographic-variants) | Detects orthographic variants |
| [textlint-rule-prh](https://github.com/textlint-rule/textlint-rule-prh) | Proofreading by the dictionary in `.prh.yml` |
| [textlint-plugin-latex2e](https://github.com/textlint/textlint-plugin-latex2e) | LaTeX file support |

## How to Install

`textlint` is a peer dependency. Install it in your project together with this package.

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

## How to Use

textlint has no `extends` option, and `--config` does not accept a package name. Pass the path to the
configuration file inside `node_modules` instead.

```sh
textlint --config node_modules/@cffnpwr/textlint-config/.textlintrc.json <files>
```

To use it from a script, add it to `package.json`.

```json
{
  "scripts": {
    "lint": "textlint --config node_modules/@cffnpwr/textlint-config/.textlintrc.json \"**/*.md\""
  }
}
```

Add `textlint` to your project's own dependencies. With the Bun `isolated` linker, the `textlint`
command is linked only when `textlint` is a direct dependency, so the copy installed through this
package's peer dependency is not available as a command.

The rules and plugins are resolved from the dependencies of this package. They work with both the
hoisted and the isolated layouts.

## License

[MIT License](./LICENSE)
