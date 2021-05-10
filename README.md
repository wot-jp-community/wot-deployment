# WoT Deployment Task Force

本リポジトリは WoT 検討会の WoT Deployment Task Force で利用しているリポジトリです。現在のところ、主に開発者をターゲットに、WoTを使った基本的なデバイス/アプリを作成するために必要な情報を提供する 「Web of Thingsデプロイメントポータル」 を提供しております。

## WoTデプロイメントポータル

[![Netlify Status](https://api.netlify.com/api/v1/badges/d80259bd-f6de-4b53-8472-7a728694a5af/deploy-status)](https://app.netlify.com/sites/wot-deployment/deploys)

https://wot-deployment.netlify.app/ (https://wot-jp-cg.netlify.app へのリダイレクト)

DP TF でコンテンツを執筆開始しましたが、docs 配下のドキュメントは https://github.com/w3c/wot-jp-cg に移管しこちらでは更新停止中、WoT JP CG サイトにリダイレクト設定している状態です。

- 構成
  - [Docsify](https://docsify.js.org/) によるシンプルなサイトです。
  - index.html 単独動作、Markdown ファイル `xxxxx.md` に書いた記事を URL フラグメントで `/#/xxxxx` として読み込む構成
  - コンテンツは全て普通の Markdown なので任意のモダンなフレームワークによるサイトにいつでも変換可能
- デプロイ
  - [Netlify](https://www.netlify.com/) でホスティングしています
  - 現状ほぼ単なる静的ホスティング (と画像の自動圧縮など自動最適化) だけなのでデプロイに失敗することはほぼないと思うが、最新のデプロイ結果は上記の [Netlify Status バッジ](https://docs.netlify.com/monitor-sites/status-badges/) を参考に。黄色や赤になっている場合は[デプロイログ](https://app.netlify.com/sites/wot-deployment/deploys)を参照して原因を確認する。
- ドキュメント
  - [Netlify のヘルプ](https://docs.netlify.com/#we-re-here-to-help)
  - [Docsify の Netlify デプロイ](https://docsify.js.org/#/deploy?id=netlify)
