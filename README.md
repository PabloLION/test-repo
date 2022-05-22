# test-repo

repo for making tests

## Problem description

### Test

```bash
yarn install && yarn lint
```

### Problem

1. In the first commit on this branch, the `yarn lint` command works correctly.
2. In the second commit, the `yarn lint` command fails.

### Reproduction

1. Run `yarn init` to create a whatever new repo.
2. Install packages with `yarn` following [Getting Started - Linting your TypeScript Codebase](https://typescript-eslint.io/docs/linting/)

   ```bash
     yarn add --dev eslint typescript @typescript-eslint/parser @typescript-eslint/eslint-plugin
   ```

3. Add this `eslintConfig` to `package.json`, then run `yarn lint`. The command works.

   ```json
   "eslintConfig": {
       "env": {
         "node": true
       },
       "extends": [
         "eslint:recommended",
         "plugin:@typescript-eslint/recommended"
       ],
       "parser": "@typescript-eslint/parser",
       "plugins": [
         "@typescript-eslint"
       ],
       "root": true
     },
   ```

4. Add these two lines to `eslintConfig.extends`, then the command fails.

   ```json
   "plugin:@typescript-eslint/recommended-requiring-type-checking",
   "plugin:@typescript-eslint/strict"
   ```

5. I also tested with `.eslintrc.js` and `.eslintrc.cjs`. Both failed with same error.

### Env

I'm using MacBook Pro (2021, 16'), which has M1 chips.

VSCode

```plaintext
Version: 1.67.1
Commit: da15b6fd3ef856477bf6f4fb29ba1b7af717770d
Date: 2022-05-06T12:37:14.619Z
Electron: 17.4.1
Chromium: 98.0.4758.141
Node.js: 16.13.0
V8: 9.8.177.13-electron.0
OS: Darwin arm64 21.3.0
```
