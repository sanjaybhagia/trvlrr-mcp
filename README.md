<p align="center"><img src="assets/logo-400.png" width="120" alt="Trvlrr"></p>

# Trvlrr MCP server

**Your travel journal in any AI assistant.** Connect [Trvlrr](https://trvlrr.app) to Claude,
ChatGPT, Cursor, Raycast or any app that speaks the
[Model Context Protocol](https://modelcontextprotocol.io), and ask about every trip you've
taken and the ones you're planning — flights, trains, stays, activities and expenses — see your
lifetime travel stats, find photos by describing them, add a booking by pasting it, or import a
whole trip from another app.

```
https://trvlrr.app/mcp
```

A hosted, remote server (Streamable HTTP). There's nothing to install and no API key: the first
time a tool is used you sign in to your own Trvlrr account in the browser and approve the
connection. You can disconnect it any time from **Profile → Connected apps** in Trvlrr.

> This repository holds connection instructions and configuration only. The Trvlrr service and
> its server code are not here.

## Try asking

- "Which countries have I been to, and how many trips have I taken?"
- "Where are we staying in Kyoto, and when do we fly home?"
- "Add this hotel confirmation to my Japan trip."
- "Find my photo of the Rialto Bridge." *(Trvlrr Plus)*
- "Plan a relaxed day in Hakone around what we've booked."
- "Bring this itinerary across from my notes."

## Connect it

| App | How |
|---|---|
| **Claude** | Listed in Claude's connector directory: Settings → Connectors → Discover → **Trvlrr** ([listing](https://claude.ai/directory/connectors/trvlrr)). |
| **ChatGPT** | Add as a plugin with the URL above (Developer mode, on Plus, Pro, Business, Enterprise and Edu). |
| **Claude Code** | `claude mcp add --transport http trvlrr https://trvlrr.app/mcp` |
| **Cursor** | Settings → MCP → Add server, or add `mcp.json` from this repo to `~/.cursor/mcp.json`. |
| **VS Code** | Command palette → *MCP: Add Server* → HTTP → `https://trvlrr.app/mcp` |
| **Gemini CLI** | `gemini extensions install https://github.com/sanjaybhagia/trvlrr-mcp` |
| **Raycast** | In the *Model Context Protocol Registry* extension, under official servers. |
| **Anything else** | Point it at `https://trvlrr.app/mcp`; for stdio-only apps use `npx -y mcp-remote https://trvlrr.app/mcp` (see [llms-install.md](llms-install.md)). |

Step-by-step guides, with screenshots of where each setting lives: **[trvlrr.app/assistants](https://trvlrr.app/assistants)**.

## Tools

| Tool | What it does |
|---|---|
| `list_trips` | Every trip, newest first: dates, status, places, travellers, photo count. |
| `get_trip` | One trip in full — transport, stays, activities, documents; optionally costs, packing list and photos. |
| `get_stats` | Lifetime numbers over trips that have happened: countries, cities, flights, distance, days away. |
| `search_photos` | Find photos by describing them. *Trvlrr Plus.* |
| `get_file` | Open a photo or a trip document such as an e-ticket. |
| `import_trip` | Bring in a whole trip with its transport, stays, activities and expenses. |
| `save_items` | Add or update transport, stays, activities, expenses, packing items or places. |
| `update_trip` | Change a trip's details, merge two trips, settle flagged cancellations. |
| `update_profile` | The travel profile, the homes you've lived in, and the people you travel with. |
| `delete_items` | Permanently delete trips or items, after the person confirms. |

Every tool has annotations (read-only or destructive) and an output schema. Trvlrr can't book
or pay for travel, check anyone in, or sign in to airline, hotel or email accounts.

## Plans

Connecting and asking about your trips are free. On the free plan, importing trips and adding
items through an assistant counts towards three imports a month, shared with forwarded booking
emails. [Trvlrr Plus](https://trvlrr.app/pricing) has no monthly limit and adds photo search
and packing lists.

## Auth details

- OAuth 2.1, PKCE (S256), public clients
- Dynamic client registration at `https://trvlrr.app/oauth/register`, and client ID metadata
  documents
- Discovery: `https://trvlrr.app/.well-known/oauth-protected-resource` and
  `https://trvlrr.app/.well-known/oauth-authorization-server`
- Access tokens last an hour; refresh tokens rotate
- Official MCP Registry name: `app.trvlrr/trvlrr` ([server.json](server.json))

## Links

[trvlrr.app](https://trvlrr.app) · [Claude & ChatGPT](https://trvlrr.app/features/ai-assistant) ·
[Privacy](https://trvlrr.app/privacy) · [Terms](https://trvlrr.app/terms) ·
[Support](https://trvlrr.app/support) · support@trvlrr.app · Trvlrr for
[iPhone](https://apps.apple.com/app/id6807719584)

Made in Sydney by Arigato Consulting Pty Ltd. The files in this repository are MIT licensed;
see [LICENSE](LICENSE).
