# yumemi_front_cordingcheck

株式会社ゆめみ2024エンジニアサマーインターン＿フロントエンドエンジニアコーディング試験＿2406030025

## 試験内容

~~大学の最終課題の合間を縫い、知らないツールであるESLintとPrettierを使い、小規模開発の大学生で触ることはないと高を括っていたVueを一から学び、二度と触らないと誓っていたはずのTypeScriptで制作物を作る~~

**以下サイトの課題に沿ったSPAを作る**  
<https://yumemi.notion.site/0e9ef27b55704d7882aab55cc86c999d>

## デプロイ先（GitHub Pages）

<https://unspeakablesnow.github.io/yumemi_front_cordingcheck/>

## 開発モード起動

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
  - オフライン時開発用の `view_graph.vue` のためのテストケース `case1.txt` あり
  - ~~他は簡単なconsole.logを多用した単体テスト（削除済み）と頻繁なビルドによってのみテストしていたため~~ `npm run build` が動くことがテスト
- テスト実行時にエラーが発生しないこと
  - 確認済み
- ソースコードはGitで管理し、作成したソースコードはGitHubにアップロードすること
  - 完了
- Netlify / GitHub Pages / Firebase hosting / Vercel 等のホスティングサービスにデプロイし、インターネット経由で閲覧できる状態にすること
  - 完了（リンクは上記）
