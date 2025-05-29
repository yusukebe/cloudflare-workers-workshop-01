# Workshop Steps

## 1. Using Remote MCP

Let's try using [Cloudflare Radar MCP Server](https://github.com/cloudflare/mcp-server-cloudflare/tree/main/apps/radar).

### 1. Using Claude Desktop

You can use Claude Desktop with the following configuration:

Add the following to Claude Desktop's configuration file (`~/Library/Application Support/Claude/claude_desktop_config.json`):

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

## 2. Using Workers AI LLM Playground

You can also use [Cloudflare AI Playground](https://playground.ai.cloudflare.com/).

## 2. Hello World

## 3. Building a Stateless Remote MCP Server

## 4. Cleaning Up Workers