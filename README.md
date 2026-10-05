# Synero AI Council MCP server

Ask GPT, Claude, Gemini and Grok the same question at once and get one consensus answer plus an agreement analysis: what the models agree on, and exactly where they split, with each model's position named.

This repo is the plugin package (Agent Plugins / Open Plugins format) for Synero's hosted remote MCP server. There is nothing to install or run: the server is hosted at

```
https://synero.ai/api/mcp
```

Streamable HTTP, OAuth 2.1 sign-in (dynamic client registration + PKCE), or `Authorization: Bearer sk_live_...` with a key from [synero.ai/app/api-keys](https://synero.ai/app/api-keys). Official MCP Registry name: `ai.synero/council`.

## Connect

| Client | How |
|---|---|
| ChatGPT | Plugins → Add → Create custom MCP server → paste the URL → OAuth → Continue to Synero → Allow. Then type `@Synero` in a chat. |
| Grok | grok.com Plugins (grok.com/connectors) → New Connector → Custom → paste the URL → Allow. Toggle it under + → Connectors. |
| claude.ai / Claude Desktop | Settings → Connectors → Add custom connector → paste the URL. |
| Claude Code | `claude mcp add --transport http synero https://synero.ai/api/mcp`, then `/mcp` to sign in. |
| Cursor / Windsurf | `{ "mcpServers": { "synero": { "url": "https://synero.ai/api/mcp" } } }` |

Full setup guide: [synero.ai/mcp](https://synero.ai/mcp). A local stdio proxy is also on npm: `npx -y @syneroai/mcp` (needs `SYNERO_API_KEY`).

## Tool: `query_council`

| Argument | What it does |
|---|---|
| `prompt` (required) | The question. |
| `preset` | `solo`, `duel`, `council` (default) or `deep`. |
| `models` | 1 to 4 model ids, one per provider. |
| `web_search` | Let the models search the web first. |
| `synthesis` | `false` for a cheaper raw mode: every answer, no consensus. |
| `parent_query_id` | Follow up on a previous result with full context. |

Results carry a consensus answer, the agreement analysis, and a link to the saved comparison on synero.ai.

## Pricing

Billed to your Synero credits like the app: 3 free queries for new accounts, then $10/month with $10 of usage included. [synero.ai/pricing](https://synero.ai/pricing)

## License

MIT
