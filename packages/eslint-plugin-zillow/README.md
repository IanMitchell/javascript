# eslint-plugin-zillow

> Zillow's ESLint config bundled into a "zero-conf" plugin

[![npm version](https://img.shields.io/npm/v/eslint-plugin-zillow.svg)](https://www.npmjs.com/package/eslint-plugin-zillow)
[![Build Status](https://travis-ci.org/zillow/javascript.svg?branch=latest)](https://travis-ci.org/zillow/javascript)

## Why

We want shareable configs to have as low of an overhead as possible. Users shouldn't have to know exactly what plugins are required by the config, install them and manage their versions manually. This plugin exposes [`eslint-config-zillow`](https://github.com/zillow/javascript/tree/latest/packages/eslint-config-zillow#readme) for reuse, with plugins automatically installed.

> See [https://github.com/eslint/eslint/issues/3458](https://github.com/eslint/eslint/issues/3458) for further discussion on this topic. Approach inspired by [`eslint-plugin-react-app`](https://github.com/mmazzarolo/eslint-plugin-react-app) and [`eslint-plugin-springload`](https://github.com/springload/eslint-plugin-springload).

## Usage

Install the plugin and its minimal peer dependencies:

```sh
npm i -D eslint prettier eslint-plugin-zillow
```

Configure ESLint to use this config. For example, in your package.json, this would be:

```json
  "eslintConfig": {
    "extends": "plugin:zillow/recommended"
  },
```

### Customizing Rules

You can configure the rules like every other `eslint` plugin.
Just keep in mind that if you want to change a rule of an included plugin (for example, `eslint-plugin-react`) you must prefix the rule with `zillow/` (necessary to prevent namespace collisions).

For example:

```json
{
  "extends": [
    "plugin:zillow/recommended"
  ],
  "rules": {
    "zillow/react/react-in-jsx-scope": ["warn"]
  }
}
```

### `prettier` Editor Plugin Integration

Unfortunately, super-useful editor plugins like `prettier-atom` and `prettier-vscode` do not load Prettier settings from ESLint config, which is where we load our Prettier options from. To workaround this, add a `.prettierrc.js` or `prettier.config.js` file to your root with the following content:

```js
module.exports = require('eslint-plugin-zillow/prettier.config');
```

## "Bundled" Plugins

We currently encapsulate the following plugins:

- [eslint-plugin-import](https://github.com/benmosher/eslint-plugin-import)
- [eslint-plugin-jsx-a11y](https://github.com/evcohen/eslint-plugin-jsx-a11y)
- [eslint-plugin-prettier](https://github.com/prettier/eslint-plugin-prettier)
- [eslint-plugin-react](https://github.com/yannickcr/eslint-plugin-react)