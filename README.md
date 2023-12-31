# ESLintの適用

## ESLintとは

- ESLintはJavaScriptの静的検証ツール
- 静的検証なので、コードの実行前でも問題点が検出できる
- IDEやエディターによっては自動修正も可能（VSCodeなど）
- コーディング規約の自動適用に有用
- スタイルの統一や、バグの早期発見に役立つ
- スタイルだけでなく、セキュリティやパフォーマンスの問題も検出できる

## ESLintのインストール

- ESLintはグローバルにインストールすることもできるが、プロジェクトごとにインストールすることを推奨
- ESLintは開発時にのみ必要なので、`devDependencies`にインストールする
  - yarnの場合は`yarn add -D 'eslint@^8'`で-Dオプションをつけてインストール
  - Next.jsは最初からESLintが導入されているので、インストール不要
  - 実行時は`npx eslint`コマンドを使う
    - npxコマンドはローカルにインストールされたNodeモジュール(ライブラリ)を実行する
    - 具体的には`node_modules/.bin`ディレクトリにインストールされたモジュールを実行する
- ルールの適用方法はjsonに記述する方法と、JavaScriptに記述する方法がある
  - 今回はJavaScriptに記述する方法を採用
    - 設定ファイル`.eslintrc.js`をプロジェクトのルートディレクトリに配置する
    - 問題(ルール違反)の処理法は重大度0~2で指定する
      - 0: off (無視)
      - 1: warn (警告を出すが、終了コードには影響しない)
      - 2: error(エラーを出し、終了コードを1にする)
    - それぞれに対し、例外の設定やどのように処理するかを細かく指定できる
  - 全ルールの一覧[ESLint公式ドキュメント](https://eslint.org/docs/rules/)
  - どのルールが自動修正に対応しているかはチェックボックスで確認できる

### ESLintの実行

- ESLintはコマンドラインから実行する
- 自動的に修正可能なルールは`--fix`オプションをつけて以下のようなコマンドを実行する
  - `npx eslint --fix src/pages/**/*.js`
    - src/pages配下の全てのディレクトリを対象にする
- 自動修正できないルールは警告でチェックして手動で修正する必要がある

### TypeScript ESLintの導入

- TypeScriptの場合は、TypeScript ESLintを導入する
- ESLintの200以上のルールに加え、TypeScript固有のルールも100以上追加される
- 追加ルールの一覧[TypeScript ESLint公式ドキュメント](https://typescript-eslint.io/rules/)
  - TypeScript ESLintを動かすためには、2つの設定ファイルが必要
    - tsconfig.eslint.json
    - .eslintrc.js
