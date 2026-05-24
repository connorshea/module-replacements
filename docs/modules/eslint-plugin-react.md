---
description: Modern alternatives to the eslint-plugin-react package for React/JSX-specific linting rules
---

# Replacements for `eslint-plugin-react`

## `@eslint-react/eslint-plugin`

[`@eslint-react/eslint-plugin`](https://github.com/Rel1cx/eslint-react) is not a drop-in replacement, but a feature‑rich alternative that covers many of the same (and additional) rules.

Flat config example:

```ts
import eslintReact from '@eslint-react/eslint-plugin' // [!code ++]
import reactPlugin from 'eslint-plugin-react' // [!code --]

export default [
  {
    files: ['**/*.{jsx,tsx}'],
    plugins: {
      react: reactPlugin, // [!code --]
      '@eslint-react': eslintReact // [!code ++]
    },
    rules: {
      ...reactPlugin.configs.recommended.rules, // [!code --]
      ...eslintReact.configs.recommended.rules, // [!code ++]

      'react/no-unknown-property': 'error', // [!code --]
      '@eslint-react/dom/no-unknown-property': 'error' // [!code ++]
    }
  }
]
```

> [!NOTE]
> `@eslint-react/eslint-plugin` is not a drop‑in replacement. Use [their migration guide](https://www.eslint-react.xyz/docs/migrating-from-eslint-plugin-react) to map rules/options and automate changes where possible.

## Oxlint

[Oxlint](https://oxc.rs/docs/guide/usage/linter.html) is a high-performance linter for JavaScript and TypeScript, built on the Rust-based `Oxc` compiler stack. It's intended to be fully backwards-compatible with ESLint, having ported most of the ESLint rules, as well as those from popular plugins including `eslint-plugin-react`.

The migration process from ESLint is covered in [the Oxlint documentation](https://oxc.rs/docs/guide/usage/linter/migrate-from-eslint.html), and can be done automatically from an ESLint flat config using [`npx @oxlint/migrate`](https://github.com/oxc-project/oxlint-migrate).

> [!NOTE]
> Oxlint is not necessarily a full drop-in replacement, as not all of the `eslint-plugin-react` rules have been, or will be, implemented. Check [the GitHub issue](https://github.com/oxc-project/oxc/issues/1022) to view the progress.
