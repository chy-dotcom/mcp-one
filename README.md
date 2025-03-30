# EdgeOne Pages MCP

An MCP service for deploying HTML content to EdgeOne Pages and obtaining a publicly accessible URL.

<a href="https://glama.ai/mcp/servers/@TencentEdgeOne/edgeone-pages-mcp">
  <img width="380" height="200" src="https://glama.ai/mcp/servers/@TencentEdgeOne/edgeone-pages-mcp/badge" alt="EdgeOne Pages MCP server" />
</a>

## Demo

![](https://cloudcache.tencent-cloud.com/qcloud/ui/static/static_source_business/04ff9814-bcd3-442c-a2d0-eefd4ee1b13c.gif)

## Configure MCP

```json
{
  "mcpServers": {
    "edgeone-pages-mcp-server": {
      "command": "npx",
      "args": ["edgeone-pages-mcp"]
    }
  }
}
```

## Architecture

![EdgeOne Pages MCP Architecture](./assets/architecture.svg)

The architecture diagram illustrates the workflow:
1. Large Language Model generates HTML content
2. Content is sent to the EdgeOne Pages MCP Server
3. MCP Server deploys the content to EdgeOne Pages Edge Functions
4. Content is stored in EdgeOne KV Store for fast edge access
5. MCP Server returns a public URL
6. Users can access the deployed content via browser with fast edge delivery

## Features

* MCP protocol for rapid deployment of HTML content to EdgeOne Pages
* Automatic generation of publicly accessible URLs

## Implementation

This MCP service integrates with EdgeOne Pages Functions to deploy static HTML content. The implementation uses:

1. **EdgeOne Pages Functions** - A serverless computing platform that allows execution of JavaScript/TypeScript code at the edge.

2. **Key Implementation Details** :
   - Uses EdgeOne Pages KV store to store and serve the HTML content
   - Automatically generates a public URL for each deployment
   - Handles API errors with appropriate error messages

3. **How it works** :
   - The MCP server accepts HTML content through the `deploy-html` tool
   - It connects to EdgeOne Pages API to get the base URL
   - Deploys the HTML content using the EdgeOne Pages KV API
   - Returns a publicly accessible URL to the deployed content

4. **Usage Example** :
   - Provide HTML content to the MCP service
   - Receive a public URL that can be accessed immediately

For more information, see the [EdgeOne Pages Functions documentation](https://edgeone.ai/document/162227908259442688) and [EdgeOne Pages KV Storage Guide](https://edgeone.ai/document/162227803822321664).

## License

MIT