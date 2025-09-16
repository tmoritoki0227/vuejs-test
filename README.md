# vuejs-test

- node18がEOLとなっている,最新を導入した　msiをつかった。Dockerは使わず
- PowerShell の実行ポリシー変更。`npm create vite@latest -y`の時に必要となった
```
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned -Force
```
- 書いてあった。マニュアルの見方に慣れよう。止まった風に見える画面が入力待ちである。
  - Project name: app
  - Select a framework: Vue
  - Select a variant: TypeScript
- plugin
  - TypeScript Vue Plugin (Volar) 入らなかった
  - Vue Language Features (Volar)　入らなかった
  - Vetur入らなかった
- パスワードジェネレーターを動かす方法
  - https://github.com/murcubcc110/vuejs-sample-passwdgen をクローンして(1)で動いた
    ```
    git clone <あなたのリポジトリURL>
    cd <プロジェクト名>

    # どのパッケージマネージャを使うかは “ロックファイル” で判断
    # 1) package-lock.json がある → npm
    npm ci      # なければ npm install でも可
    npm run dev

    # 2) pnpm-lock.yaml がある → pnpm
    #    (初回だけ) corepack enable
    #    corepack prepare pnpm@latest --activate  # 必要なら
    # pnpm install
    # pnpm dev

    # 3) yarn.lock がある → yarn
    #    (初回だけ) corepack enable
    # yarn
    # yarn dev
    ```
    ![alt text](image.png)

- Vueってなに？

    Web画面を作るためのJavaScriptフレームワーク。

    ボタンを押したら数字が増える、入力したら画面が変わる…みたいな**“動くUI”を超カンタンに書ける**ようにしてくれる。

    コンポーネントという小さな部品を組み合わせて画面を作る。

    データが変わると、Vueが自動でDOMを書き換えて見た目を更新してくれる（＝リアクティブ）。
    ふつうは .vue という1ファイルに、見た目・ロジック・スタイルをまとめる

- npmの「scripts」（今回いちばん重要）

    **package.json の "scripts" に書く“作業コマンドの別名”**です。

    例（Vite プロジェクトの定番）：
    ```json
    {
        "scripts": {
            "dev": "vite",
            "build": "vue-tsc -b && vite build",
            "preview": "vite preview"
        }
    }
    ```

    実行は npm run dev / npm run build のように短く呼べる“ボタン”だと思えばOK。

    何が実行されるかは package.json を見れば分かります。npm run で一覧表示もできます。

- npm run dev：開発用。ローカルで即動くサーバを立てる（HMR＝保存で即反映）。

- npm run build：本番用。最適化された静的ファイルを dist/ に出力。
- Vite（ヴィート）って？

    **超速い“開発サーバ & ビルドツール”**です。Vue の作者（Evan You）が作りました。

    Vue 用だけじゃなく React / Svelte / 素のJS でも使えます。