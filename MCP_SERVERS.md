# 便利な MCP サーバー

このワークショップで役に立つリモート MCP サーバーを紹介します。

## Cloudflare Documentation MCP Server

https://github.com/cloudflare/mcp-server-cloudflare/tree/main/apps/docs-vectorize

```json
{
  "mcpServers": {
    "cloudflare": {
      "command": "npx",
      "args": ["mcp-remote@latest", "https://docs.mcp.cloudflare.com/sse"]
    }
  }
}
```

## DeepWiki

```json
{
  "mcpServers": {
    "deepwiki": {
      "command": "npx",
      "args": ["mcp-remote@latest", "https://mcp.deepwiki.com/sse"]
    }
  }
}
```

## Ramen API

```json
{
  "mcpServers": {
    "ramen-api": {
      "command": "npx",
      "args": ["mcp-remote@latest", "https://ramen-api.dev/mcp"]
    }
  }
}
```

## Memo MCP

```json
{
  "mcpServers": {
    "memo-mcp": {
      "command": "npx",
      "args": ["mcp-remote@latest", "https://memo-mcp-server.yusukebe.workers.dev/mcp"]
    }
  }
}
```
