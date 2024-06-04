# yumemi_front_cordingcheck

株式会社ゆめみ2024エンジニアサマーインターン＿フロントエンドエンジニアコーディング試験＿2406030025

## 起動

```sh
npm install
npm run dev
```

## 制約への対応

- React/Vue.jsのいずれかを用いてSPAを構築すること
  - Vue.jsを使用
- 都道府県一覧および総人口情報はRESAS APIのデータを用いること
  - `todouhuken.vue` 内処理にて使用
- グラフは Highcharts や Rechart.js などのサードパーティ製のグラフライブラリを用いて描画すること
  - [Chart.js](https://www.chartjs.org/docs/latest/)を使用
- Google Chrome最新版で正しく動くこと
  - 確認済み
- PC/スマートフォン表示に対応すること(レスポンシブデザイン対応)
  - 確認済み
- リンターやフォーマッターを適切に設定すること
  - リンターにはESLint、フォーマッターにはPrettierを使用
- styleは自分で記述し、UIフレームワークなどは原則使用しないこと
  - 完了
- TypeScriptで記述すること
  - 完了
- テストケース/テストコードを作成すること
  - オフライン時開発用の `view_graph.vue` のためのテストケースあり
- テスト実行時にエラーが発生しないこと
  - 確認済み
- ソースコードはGitで管理し、作成したソースコードはGitHubにアップロードすること
  - 完了
- Netlify / GitHub Pages / Firebase hosting / Vercel 等のホスティングサービスにデプロイし、インターネット経由で閲覧できる状態にすること
  - 着手

