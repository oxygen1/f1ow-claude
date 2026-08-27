# f1ow — Claude Code plugin

Crypto market data and research inside Claude Code: price, derivatives,
on-chain, sentiment, news, and catalysts. 30 read-only tools served by f1ow's
hosted MCP server at `https://mcp.f1ow.com/mcp`.

Nothing runs locally. This repository is the plugin manifest and the MCP server
address — the tools execute on f1ow's servers.

## Install

```bash
claude plugin marketplace add anthropics/claude-plugins-community
```

```bash
claude plugin install f1ow@claude-community
```

Or install straight from f1ow without the community marketplace:

```bash
claude plugin marketplace add https://www.f1ow.com/marketplace.json
```

```bash
claude plugin install f1ow@f1ow-connectors
```

Then authenticate:

```bash
claude mcp login plugin:f1ow:f1ow
```

Claude Code discovers f1ow's OAuth authorization server from the 401 challenge,
registers itself via Dynamic Client Registration, and opens the f1ow consent
page — sign in with MetaMask, Google, or GitHub and approve. No API key, no
client ID to paste.

Tool calls need an active f1ow subscription. Buy one at
[www.f1ow.com](https://www.f1ow.com).

## Other Claude surfaces

Claude Desktop and claude.ai connect to the same server without this plugin:
**Settings → Connectors → Add custom connector**, URL `https://mcp.f1ow.com/mcp`,
leaving the OAuth client fields empty.

Use `https://mcp.f1ow.com/mcp`, not the bare origin. The server publishes one
canonical resource identifier, and a client pointed at `https://mcp.f1ow.com/`
rejects the mismatch before it can start the OAuth flow.

## What the tools do

Read-only market and research tools only — no trade-execution or asset-transfer
tools are exposed. Categories: research, market data, derivatives, on-chain,
sentiment, news, catalysts, risk. The live list, with endpoints and auth models,
is at
[`https://mcp.f1ow.com/.well-known/mcp.json`](https://mcp.f1ow.com/.well-known/mcp.json).

## Privacy

f1ow's [privacy policy](https://www.f1ow.com/privacy) and
[terms](https://www.f1ow.com/terms) apply. The plugin sends your tool arguments
to `mcp.f1ow.com` over HTTPS carrying an OAuth access token issued by
`www.f1ow.com`. It stores nothing on your machine beyond the token your client
holds. Revoke access any time from the connected-apps list in your f1ow
dashboard.

## Support

[www.f1ow.com](https://www.f1ow.com)

---

`plugin.json` and `.mcp.json` here are copies of `plugins/f1ow/` in f1ow's
private site repository, which is also where the Codex build of this plugin
lives. Change them there first, then mirror.
