# Installing the Trvlrr MCP server

Trvlrr is a hosted remote MCP server. There is nothing to install or run locally and no API
key: the person signs in to their own Trvlrr account in the browser the first time a tool is
used.

- Endpoint: `https://trvlrr.app/mcp` (Streamable HTTP)
- Auth: OAuth 2.1 with PKCE and dynamic client registration, discovered from the 401 the
  endpoint returns (`/.well-known/oauth-protected-resource`)

For clients that only run local (stdio) servers, bridge with `mcp-remote`:

```json
{
  "mcpServers": {
    "trvlrr": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://trvlrr.app/mcp"]
    }
  }
}
```

For clients that support remote servers directly:

```json
{
  "mcpServers": {
    "trvlrr": { "url": "https://trvlrr.app/mcp" }
  }
}
```

To check it works, ask: "Which countries have I been to?" — the client should open a Trvlrr
sign-in page, then answer from the `get_stats` tool.
