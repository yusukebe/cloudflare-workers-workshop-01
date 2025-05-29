# 前提条件

## 必須事項

[Cloudflare Workers のガイド](https://developers.cloudflare.com/workers/get-started/guide/)を参考に以下のことをやってきてください。

- Cloudflare のアカウントをつくります
- C3 で雛形を作成します
- Wrangler で開発サーバを立ち上げます
- Wrangler でデプロイします

## 追加でやってきてほしいこと

### Claude Desktop をインストールしてくる

[Claude Desktop](https://claude.ai/download) からダウンロードしてインストールしてください。

### どんな MCP サーバーを作りたいかを考えてくる

以下の記事を参考に自分がどんなリモート MCP サーバーを作りたいか考えてきてください。

- [Model Context Protocol（MCP）Demo Day](https://blog.cloudflare.com/ja-jp/mcp-demo-day/)
- [Cloudflare から 13 の新しい MCP サーバー](https://blog.cloudflare.com/ja-jp/thirteen-new-mcp-servers-from-cloudflare/)

自分はこんなのを作りました。

- [ramen-api](https://github.com/yusukebe/ramen-api) - [Ramen API](https://github.com/yusukebe/ramen-api)というラーメン屋の登録と取得ができる API を MCP 化したものです。
- [memo-mcp-server](https://github.com/yusukebe/memo-mcp-server) - 簡単なメモ登録ができて、Cloudflare D1 を使ってメモを保存できるものです。
