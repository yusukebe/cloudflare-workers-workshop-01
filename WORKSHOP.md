# ワークショップ手順

## 1. リモート MCP を使う方法

[Cloudflare Radar MCP Server](https://github.com/cloudflare/mcp-server-cloudflare/tree/main/apps/radar) を使ってみます。

### 1. Claude Desktop を使う

Claude Desktop では以下の設定をいれればできます：

Claude Desktop の設定ファイル（`~/Library/Application Support/Claude/claude_desktop_config.json`）に以下を追加します：

```json
{
  "mcpServers": {
    "cloudflare": {
      "command": "npx",
      "args": ["mcp-remote", "https://radar.mcp.cloudflare.com/sse"]
    }
  }
}
```

## 2. Workers AI LLM Playground を使う

[Cloudflare AI Playground](https://playground.ai.cloudflare.com/)も使えます。

## 2. Hello World

## 3. ステートレスなリモート MCP サーバーを作る

## 4. Workers を消す
