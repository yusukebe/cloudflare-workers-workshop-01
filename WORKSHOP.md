# ワークショップ手順

## 1. リモート MCP を使う方法

リモート MCP サーバーは、インターネット経由でアクセス可能な MCP サーバーです。

### Claude Desktop で接続

Claude Desktop 設定を開きます。

```
macOS: ~/Library/Application Support/Claude/claude_desktop_config.json
Windows: %APPDATA%\Claude\claude_desktop_config.json
```

VS Code で開く場合。

```bash
code ~/Library/Application\ Support/Claude/claude_desktop_config.json
```

以下を追加。

```json
{
  "mcpServers": {
    "cloudflare": {
      "command": "npx",
      "args": ["mcp-remote@latest", "https://radar.mcp.cloudflare.com/sse"]
    }
  }
}
```

### AI Playground で接続

[Cloudflare AI Playground](https://playground.ai.cloudflare.com/) にアクセスして、MCP Servers 欄に URL を入力します。

## 2. Hello World - 最初の MCP サーバー作成

```bash
npm create cloudflare@latest -- my-mcp-server --template=cloudflare/ai/demos/remote-mcp-authless
cd my-mcp-server
npm run dev
```

## 3. 動作確認

### MCP Inspector を使う

開発中の MCP サーバーのテストに使用できます。

```bash
# 公式Inspector
npx @modelcontextprotocol/inspector@latest

# または Muppet Kit版
npx @muppet-kit/inspector@latest
```

### Claude Desktop を使う

Claude Desktop 設定に追加:

```json
{
  "mcpServers": {
    "cloudflare": {
      "command": "npx",
      "args": ["mcp-remote@latest", "http://localhost:8787/mcp"]
    }
  }
}
```

## 4. 自分の MCP サーバーを作る

あなたのアイデアで MCP サーバーを作ってみてください。

もし、アイデアがない場合は、Cloudflare D1 を使った TODO 管理の MCP サーバー作ったので、それを真似してみてください。

https://github.com/yusukebe/todo-mcp-server

### 基本構造

```typescript
export class MyMCP extends McpAgent {
  server = new McpServer({
    name: 'My MCP Server',
    version: '1.0.0'
  })

  async init() {
    // ツールの定義
    this.server.tool(
      'hello',
      {
        name: z.string()
      },
      async ({ name }) => {
        return {
          content: [
            {
              type: 'text',
              text: `Hello, ${name}!`
            }
          ]
        }
      }
    )
  }
}
```

## 5. 共有とテスト

作成した MCP サーバーは即座に他の人も利用可能です。ワークショップ終了後はリソース削除を忘れずに。

### リソース削除

```bash
npx wrangler delete
```

## 6. 発展編 - 認証付き MCP サーバー

OAuth を使った認証機能の実装。詳細は[Cloudflare 公式ドキュメント](https://developers.cloudflare.com/agents/model-context-protocol/authorization/)を参照してください。
