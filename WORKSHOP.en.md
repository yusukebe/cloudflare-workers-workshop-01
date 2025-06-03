# Workshop Instructions

## 1. Using Remote MCP Servers

Remote MCP servers are MCP servers accessible over the internet.

### Connecting with Claude Desktop

Open Claude Desktop settings:

```
macOS: ~/Library/Application Support/Claude/claude_desktop_config.json
Windows: %APPDATA%\Claude\claude_desktop_config.json
```

To open with VS Code:

```bash
code ~/Library/Application\ Support/Claude/claude_desktop_config.json
```

Add the following:

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

### Connecting with AI Playground

Access [Cloudflare AI Playground](https://playground.ai.cloudflare.com/) and enter the URL in the MCP Servers field.

## 2. Hello World - Creating Your First MCP Server

```bash
npm create cloudflare@latest -- my-mcp-server --template=cloudflare/ai/demos/remote-mcp-authless
cd my-mcp-server
npm run dev
```

## 3. Testing and Verification

### Using MCP Inspector

Used for testing MCP servers during development.

```bash
# Official Inspector
npx @modelcontextprotocol/inspector@latest

# Or Muppet Kit version
npx @muppet-kit/inspector@latest
```

### Using Claude Desktop

Add to Claude Desktop settings:

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

## 4. Building Your Own MCP Server

Create an MCP server with your own ideas.

If you don't have ideas, try building a TODO management MCP server using Cloudflare D1 based on this example:

https://github.com/yusukebe/todo-mcp-server

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

Your created MCP server is immediately available to others. Remember to clean up resources after the workshop.

### Resource Cleanup

```bash
npx wrangler delete
```

## 6. Advanced - MCP Server with Authentication

OAuth-based authentication implementation. See [Cloudflare official documentation](https://developers.cloudflare.com/agents/model-context-protocol/authorization/) for details.
