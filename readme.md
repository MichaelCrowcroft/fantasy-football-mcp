# Fantasy Football MCP Server

This project is a minimal proxy that connects your MCP client to the Sleeper Draft MCP server.

- **Endpoint**: `https://www.sleeperdraft.com/mcp`
- **Homepage**: `https://www.sleeperdraft.com`

## Overview

The Sleeper Draft MCP exposes Sleeper Draft data and tools over Model Context Protocol. This proxy forwards stdin/stdout requests from your local MCP client to the hosted Streamable HTTP endpoint at `https://www.sleeperdraft.com/mcp`.

## Usage

This server can be used with any MCP-compatible client. Below are examples for Claude Desktop.

### Direct connection via StreamableHttp

Add the following to your `claude_desktop_config.json`:

#### Mac/Linux

```json
{
  "mcpServers": {
    "sleeperdraft-mcp": {
      "command": "npx",
      "args": [
        "-y",
        "supergateway",
        "--streamableHttp",
        "https://www.sleeperdraft.com/mcp"
      ]
    }
  }
}
```

#### Windows

```json
{
  "mcpServers": {
    "sleeperdraft-mcp": {
      "command": "cmd",
      "args": [
        "/c",
        "npx",
        "-y",
        "supergateway",
        "--streamableHttp",
        "https://www.sleeperdraft.com/mcp"
      ]
    }
  }
}
```

## Build and usage

### Build

- Install dependencies:

```bash
npm install
```

- Build the CLI:

```bash
npm run build
```

### Run locally

- After building, start the proxy server:

```bash
node dist/index.js
```

### Use with Claude Desktop (local binary)

Point Claude Desktop at your local build by updating `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "sleeperdraft-mcp": {
      "command": "node",
      "args": [
        "/ABSOLUTE/PATH/TO/fantasy-football-mcp/dist/index.js"
      ]
    }
  }
}
```

Replace the path with your local absolute path to `dist/index.js`.

### Test with MCP Inspector

```bash
npm run build && npm test
```

This runs the server with the MCP Inspector UI: `npx @modelcontextprotocol/inspector node dist/index.js`.

### Optional: run via npm (if installed/published)

- If the package is installed globally:

```bash
fantasy-football-mcp
```

- Or via `npx` (if published to npm):

```bash
npx fantasy-football-mcp
```
