# Stork plugin for Cursor

Connects Cursor's agent to the Stork MCP server (Streamable HTTP) at
`https://mcp.stork.ai/mcp`.

With it the agent can:

- **Make a talking-photo video**: one photo says your text or lip-syncs your audio (`stork_talking_photo_estimate`, `_create`, `_status`, `_voices`).
- **Make a singing video**: one photo performs a song (`stork_singing_video_estimate`, `_create`, `_status`).
- **Find AI tools and MCP servers**: search, compare and get install configs from the Stork directory (`stork_search`, `stork_tools_search`, `stork_get_install_config` and others).
- **Look up LLM prices** (`stork_llm_prices`).

## Install

Open **Customize** in Cursor, search for **Stork** and click **Install**.

## Configuration

The directory and price tools work with no setup.

The video tools need a Stork API key:

1. Create a key at https://www.stork.ai/dashboard/api. It starts with `sk_stork_`.
2. Open the plugin's settings in Cursor and set `STORK_API_KEY`.

The key is sent as an `Authorization: Bearer` header to `mcp.stork.ai` only.
Talking photo has a free tier (videos carry a Stork logo). Paid videos and every
singing video are paid from prepaid Stork credits; the agent can call the
estimate tools first to see the price. Current prices:
https://www.stork.ai/developers

## Use it without the plugin

Add this to `.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "stork": {
      "type": "http",
      "url": "https://mcp.stork.ai/mcp",
      "headers": { "Authorization": "Bearer ${env:STORK_API_KEY}" }
    }
  }
}
```

## Links

- API docs: https://www.stork.ai/developers
- Official MCP registry name: `ai.stork/mcp`
- Support: support@stork.ai
- Terms: https://www.stork.ai/terms
- Privacy: https://www.stork.ai/privacy

## License

MIT
