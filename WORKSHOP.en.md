# Workshop Instructions

## 1. Using Remote MCP Servers

Remote MCP servers are MCP servers accessible over the internet.

### 1-1. Connecting with Claude Desktop

Add to Claude Desktop config (`~/Library/Application Support/Claude/claude_desktop_config.json`):

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

### 1-2. Connecting with AI Playground

Access [Cloudflare AI Playground](https://playground.ai.cloudflare.com/) and enter the URL in the MCP Servers field.

## 2. Hello World - Creating Your First MCP Server

```bash
npm create cloudflare@latest -- my-mcp-server --template=cloudflare/ai/demos/remote-mcp-authless
cd my-mcp-server
npm run dev
```

## 3. Testing with MCP Inspector

Used for testing MCP servers during development.

```bash
# Official Inspector
npx @modelcontextprotocol/inspector@latest

# Or Muppet Kit version
npx @muppet-kit/inspector@latest
```

## 4. Building Your Own MCP Server

### Basic Structure

```typescript
export class MyMCP extends McpAgent {
  server = new McpServer({
    name: 'My MCP Server',
    version: '1.0.0'
  })

  async init() {
    // Tool definition
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

## 5. Sharing and Testing

Your MCP server is immediately available to others. Remember to clean up resources after the workshop.

## 6. Advanced - MCP Server with Authentication

OAuth-based authentication implementation. See [Cloudflare official documentation](https://developers.cloudflare.com/agents/model-context-protocol/authorization/) for details.
