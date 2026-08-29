# GEOMETRY MCP

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](./LICENSE)
[![Official MCP Registry](https://img.shields.io/badge/Official_MCP_Registry-listed-2563eb)](https://registry.modelcontextprotocol.io/?q=app.geometry)
[![Glama Connector](https://img.shields.io/badge/Glama-Connector-00C853)](https://glama.ai/mcp/connectors/app.geometry.mcp/geometry)

Deterministic temporal reference data for AI builders — calendars, seasons, moon phases, planetary retrogrades, and traditional symbolic systems as stable JSON over [Model Context Protocol](https://modelcontextprotocol.io/).

**Same date → same bytes, every time.** No hallucinated dates. No wallet connect. No seed phrases.

This repository is the **public docs + listing face** for the hosted GEOMETRY MCP server. It is **not** the engine source, schema, or internal design docs.

| | |
|---|---|
| **MCP URL** | `https://mcp.geometry.app/mcp` |
| **Docs** | [docs.geometry.app](https://docs.geometry.app) |
| **Product** | [geometry.app](https://geometry.app) |
| **Pricing** | [geometry.app/pricing](https://geometry.app/pricing/) |
| **Company** | [Goqo Labs](https://goqo.com) · GitHub org [`goqolabs`](https://github.com/goqolabs) |
| **Official Registry** | [`app.geometry/mcp`](https://registry.modelcontextprotocol.io/?q=app.geometry) |
| **Glama** | [Connector listing](https://glama.ai/mcp/connectors/app.geometry.mcp/geometry) · [namespace search](https://glama.ai/mcp/connectors?query=namespace%3Aapp.geometry.mcp) |

**Namespaces:** Glama listing id `app.geometry.mcp` ≠ Official MCP Registry name `app.geometry/mcp`. Connect URL is always `https://mcp.geometry.app/mcp`.

### Repo layout

- `docs/` — Mintlify pages (MDX, tools, `llms.txt`)
- `docs/docs.json` — Mintlify config (content root = `/docs`)
- `logo/` — brand assets at repo root (favicon + light/dark)

## Try it (no account)

Paste the branded URL into your MCP client:

```
https://mcp.geometry.app/mcp
```

| Client | Auth |
|--------|------|
| Claude Desktop / Claude Code | Custom connector · plain URL |
| ChatGPT Plugins | Server URL · **Authentication = No Auth** (not OAuth) |
| Cursor / VS Code | HTTP MCP · plain URL |

### Cursor / VS Code (`mcp.json`)

No Auth try:

```json
{
  "mcpServers": {
    "geometry": {
      "url": "https://mcp.geometry.app/mcp"
    }
  }
}
```

Builders with a portal key (never commit a real `zpka_`):

```json
{
  "mcpServers": {
    "geometry": {
      "url": "https://mcp.geometry.app/mcp?key=YOUR_KEY"
    }
  }
}
```

Install walkthroughs: [geometry.app/tutorial](https://geometry.app/tutorial/) · [Quickstart](https://docs.geometry.app/quickstart).

Limits apply on the free try path — see [pricing](https://geometry.app/pricing/).

## Builders (Free / Starter key)

For a stable sandbox quota or paid volume, subscribe in the Developer Portal, then append your key:

```
https://mcp.geometry.app/mcp?key=YOUR_KEY
```

Same tools and fields on every plan — you pay for volume, not features. Checkout is the official Zuplo Developer Portal (`https://geometry-main-bf0a4d2.zuplo.site/pricing`), then Stripe — [Billing](https://docs.geometry.app/billing) · [Connect & keys](https://docs.geometry.app/connect-and-keys) · [Pricing](https://geometry.app/pricing/).

**Never** paste `zpka_…` keys into GitHub Issues or public chats.

## Tools

| Tool | Purpose | Docs |
|------|---------|------|
| `get_date` | Resolve one civil date to stable calendars, seasons, and card identity | [Date identity JSON](https://docs.geometry.app/tools/get-date) |
| `get_compatibility` | Compare two dates across shared symbolic systems | [Two-date compatibility](https://docs.geometry.app/tools/get-compatibility) |
| `get_name` | Map a name to cosmic cards plus ~100 Latin cipher sums | [Name → cosmic cards](https://docs.geometry.app/tools/get-name) |

Coverage focus: **1900–2100**. Ask examples: “What’s the birth card for 1985-03-15?” · “How compatible are 1990-05-14 and 1985-11-02?”

## Support

[docs.geometry.app/support](https://docs.geometry.app/support) · [GitHub Issues](https://github.com/goqolabs/geometry-mcp/issues) (paid plans)

## License

See [LICENSE](./LICENSE).

The MIT license applies to the documentation in this repository only. The GEOMETRY engine, schema, and hosted service are proprietary and are not included here.
