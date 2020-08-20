# WoT Deployment Task Force

TBD

## WoTデプロイメントポータル(案)

https://wot-deployment.netlify.app/

現在は仮に DP TF でコンテンツを執筆開始していますが、他の TF と横断で集約したり、コミュニティサイトとして発展させるなどの可能性もあり。

- 構成
  - [Docsify](https://docsify.js.org/) によるシンプルなサイト
  - index.html 単独動作、Markdown ファイル `xxxxx.md` に書いた記事を URL フラグメントで `/#/xxxxx` として読み込む構成
  - コンテンツは全て普通の Markdown なので任意のモダンなフレームワークによるサイトにいつでも変換可能
- デプロイ
  - [Netlify](https://www.netlify.com/) でホスティングしています
  - [デプロイログ](https://app.netlify.com/sites/wot-deployment/deploys)
- ドキュメント
  - [Netlify のヘルプ](https://docs.netlify.com/#we-re-here-to-help)
  - [Docsify の Netlify デプロイ](https://docsify.js.org/#/deploy?id=netlify)
