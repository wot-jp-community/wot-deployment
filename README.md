# WoT Deployment Task Force

TBD

## WoTデプロイメントポータル(案)

[![Netlify Status](https://api.netlify.com/api/v1/badges/d80259bd-f6de-4b53-8472-7a728694a5af/deploy-status)](https://app.netlify.com/sites/wot-deployment/deploys)

https://wot-deployment.netlify.app/

現在は仮に DP TF でコンテンツを執筆開始していますが、他の TF と横断で集約したり、コミュニティサイトとして発展させるなどの可能性もあり。

- 構成
  - [Docsify](https://docsify.js.org/) によるシンプルなサイト
  - index.html 単独動作、Markdown ファイル `xxxxx.md` に書いた記事を URL フラグメントで `/#/xxxxx` として読み込む構成
  - コンテンツは全て普通の Markdown なので任意のモダンなフレームワークによるサイトにいつでも変換可能
- デプロイ
  - [Netlify](https://www.netlify.com/) でホスティングしています
  - 現状ほぼ単なる静的ホスティング (と画像の自動圧縮など自動最適化) だけなのでデプロイに失敗することはほぼないと思うが、最新のデプロイ結果は上記の [Netlify Status バッジ](https://docs.netlify.com/monitor-sites/status-badges/) を参考に。黄色や赤になっている場合は[デプロイログ](https://app.netlify.com/sites/wot-deployment/deploys)を参照して原因を確認する。
- ドキュメント
  - [Netlify のヘルプ](https://docs.netlify.com/#we-re-here-to-help)
  - [Docsify の Netlify デプロイ](https://docsify.js.org/#/deploy?id=netlify)
