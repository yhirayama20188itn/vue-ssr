
## Vue.js + SSR（スクラッチ）
- この 実践 - Vue.js SSR では、Vue.js + Node.js(Express)でSSR環境を構築していきます。
- [参考](https://github.com/nkzttt/vue-ssr-test/blob/master/guide/ja.md)

### クライアントサイド
| Node.js | webpack | webpack-cli |
| :---:  | :---: | :---: |
| v10.15.1 | 4.29.6 | 3.2.3 |
- npm i -D webpack webpack-cli

| babel-loader | babel/core |babel/preset-env |
| :---:  | :---: | :---: |
| 8.0.5 | 7.3.4 | 7.3.4 |
- npm i -D babel-loader @babel/core @babel/preset-env

| vue | vue-loader | vue-template-compiler |
| :---:  | :---: | :---: |
| 2.6.8 | 15.7.0 | 2.6.8 |
| .vueファイルを使えるようにするもの |  |  |
- npm i -S vue（ vueはブラウザ上で使用するため、--saveのエイリアス-Sでインストール [参考](http://d.hatena.ne.jp/seinzumtode/20160226/1456450867)）
- npm i -D vue-loader
- npm install vue-template-compiler --save-dev

| css-loader | vue-style-loader | vue-router |
| :---:  | :---: | :---: |
| 2.1.0 | 4.1.2 | 3.0.2 |
- npm i -D vue-style-loader css-loader
- npm i -S vue-router

### サーバーサイド
| express | vue-template-compiler | vue-server-renderer |
| :---:  | :---: | :---: |
| 4.16.4 | 2.6.8 | 2.6.8 |
- npm i -S express
- npm i -S vue-template-compiler（パッケージvueとvue-template-compilerは同じバージョンである必要があります。）
- npm i -S vue-server-renderer

## 役割
### app.js
- app.js はアプリケーションのユニバーサルエントリーです。クライアントアプリケーションでは、このファイルにルート Vue インスタンスを作成し、DOM に直接マウントします。しかし、SSRの場合は責務はクライアント専用のエントリファイルに映されます。app.js はシンプルに createApp 関数をエクスポートします:

### entry-server.js
- サーバーエントリは描画ごとに繰り返し呼び出すことができる関数をデフォルトでエクスポートします。現時点では、アプリケーションインスタンスを作成して返す以外のことはほとんど行いませんが、後でサーバーサイドのルートマッチングとデータプリフェッチロジックを実行します。
- [参考](https://ssr.vuejs.org/ja/guide/structure.html#webpack%E3%81%AB%E3%82%88%E3%82%8B%E3%82%B3%E3%83%BC%E3%83%89%E6%A7%8B%E9%80%A0)