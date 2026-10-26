# 年金・資産運用シミュレーター

公的年金(加入履歴の手入力)・付加年金・iDeCo・NISA・小規模企業共済・はぐくみ企業年金・国債(個人向け/新窓販/米国債既発債)・年金保険を、受取方法と税まで含めて年齢別に比較する静的Webアプリ。サーバー不要、入力は端末のブラウザ内だけに保存。

## ファイル構成
- `index.html` … アプリ本体(計算エンジンとUI)
- `vendor/chart.umd.js` … グラフ描画(Chart.js 4.4.1、MITライセンス)
- `manifest.webmanifest` / `sw.js` / `icons/` … ホーム画面追加とオフライン動作用
- `og.png` … SNSやLINEでURLを貼ったときに出るプレビュー画像(1200×630)

`vendor/` と `icons/` のフォルダも必ず一緒にアップロードする。抜けるとグラフが出ず、オフライン動作とアイコンも壊れる。

## 公開方法(GitHub Pages)
1. GitHubで新しいリポジトリを作る(例:`nenkin-sim`)
2. このフォルダの中身をすべてリポジトリ直下にアップロードしてコミット
3. Settings → Pages → Source を「Deploy from a branch」、Branch を `main` / `(root)` にして Save
4. 数分後に `https://<ユーザー名>.github.io/nenkin-sim/` で開ける

Netlify・Cloudflare Pages なら、フォルダをドラッグ&ドロップするだけで公開できる。

## アプリとして使う
- Chrome/Edge(PC・Android):アドレスバーのインストールアイコン、またはページ上部の「アプリとして追加」
- iPhone/iPad(Safari):共有 →「ホーム画面に追加」
- 一度開けば、以後はオフラインでも動く

## ローカルで試す
`index.html` をダブルクリックでも計算・グラフは動く(オフライン機能とホーム画面追加はhttps配信時のみ)。
`python3 -m http.server 8000` で http://localhost:8000 を開くとPWA機能も確認できる。

## 制度値の更新
`index.html` 内の `BOND_TYPES`(国債の利率)、`KISO_FULL`(老齢基礎年金満額)、`idecoLimit`(iDeCo上限)を書き換える。
更新したら `sw.js` の `VERSION` も変えると、利用者の端末に新しい版が配信される。

制度値は2026年10月時点。結果は概算で、投資・税務の助言ではない。
