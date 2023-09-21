# 【Digi−Angler 用】[Bun](https://bun.sh/) + [Next.js](https://nextjs.org/) + [TypeScript](https://www.typescriptlang.org/ja/) + [Tailwind CSS](https://tailwindcss.com/) テンプレート

## プロジェクトのセットアップ

これは一般的な手順の概要であり、具体的なバージョンや設定に応じて調整が必要かもしれません。プロジェクトの要件に合わせてカスタマイズしてください。

`bunx` は、Bun フレームワークの一部として提供されているユーティリティです。[`bunx create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app) コマンドを使用して、Next.js、TypeScript、Tailwind CSS のプロジェクトを簡単にセットアップできます。以下はその手順です。

1. プロジェクトディレクトリを作成し、bunx create-next-appコマンドを実行します。

```bash
bunx create-next-app <プロジェクト名>
```

2. プロジェクトディレクトリに移動します。

```bash
cd <プロジェクト名>
```

3. 開発サーバーを起動します。

```bash
bun run dev
```

## ESLint + Prettier の導入

4. ESLint の各種必要なプラグインをインストールします。

```bash
bun add -D @typescript-eslint/parser 
```

```bash
bun add -D @typescript-eslint/eslint-plugin eslint-plugin-react eslint-config-airbnb eslint-config-airbnb-typescript
```

5. .eslintrc.json を以下に修正します。

```bash
{
  "env": {
  "browser" : true,
  "node" : true,
  "es2022" : true
  },
  "parser": "@typescript-eslint/parser",
  "parserOptions": {
    "ecmaVersion": "latest",
    "project": "./tsconfig.json",
    "ecmaFeatures": {
      "jsx": true
    }
  },
  "extends": [
    "eslint:recommended",
    "next/core-web-vitals",
    "plugin:@typescript-eslint/recommended",
    "plugin:react/recommended",
    "airbnb",
    "airbnb-typescript"
  ],
  "plugins": ["@typescript-eslint", "react"],
  "rules": {
    "linebreak-style": ["error", "windows"],
    "react/react-in-jsx-scope": "off",
    "react/function-component-definition": [
      2,
      {
        "namedComponents": "arrow-function",
        "unnamedComponents": "arrow-function"
      }
    ],
    "react/prop-types": "off"
  }
}
```

6. Prettier の各種必要なプラグインをインストールします。

```bash
bun add -D prettier eslint-config-prettier
```

7. .prettierrc.json をルートフォルダに追加します。

```bash
{
  "endOfLine": "lf",
  "semi": true,
  "singleQuote": true,
  "jsxSingleQuote": false,
  "tabWidth": 2,
  "trailingComma": "es5",
  "printWidth": 60
}
```

8. .prettierignore ファイルも作成します。

```bash
# next.js build output
.next
out
# dotenv environment variables file (build for Zeit Now)
.env
.env.local
# Dependency directories
node_modules
# Logs
npm-debug.log*
yarn-debug.log*
yarn-error.log*
```
