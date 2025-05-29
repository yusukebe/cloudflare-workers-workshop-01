# Prerequisites

## Required Setup

Please follow the [Cloudflare Workers guide](https://developers.cloudflare.com/workers/get-started/guide/) and complete the following tasks:

- Create a Cloudflare account
- Create a project template with C3
- Start a development server with Wrangler
- Deploy with Wrangler

## Additional Preparation

### Install Claude Desktop

Please download and install Claude Desktop from [Claude Desktop](https://claude.ai/download).

### Think about what kind of MCP server you want to build

Please think about what kind of remote MCP server you want to build by referring to the following articles:

- [Model Context Protocol (MCP) Demo Day](https://blog.cloudflare.com/ja-jp/mcp-demo-day/)
- [Thirteen new MCP servers from Cloudflare](https://blog.cloudflare.com/ja-jp/thirteen-new-mcp-servers-from-cloudflare/)

Here's what I've built:

- [ramen-api](https://github.com/yusukebe/ramen-api) - MCP version of [Ramen API](https://github.com/yusukebe/ramen-api), which allows restaurant registration and retrieval
- [memo-mcp-server](https://github.com/yusukebe/memo-mcp-server) - Simple memo registration system that can save memos using Cloudflare D1