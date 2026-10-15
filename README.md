# AgentDeck

Turn AI-chat web sessions (DeepSeek, Z.ai, ...) into agents on your own VPS.

> Paste the login session of an AI chat account you own -> it becomes a live agent
> on your VPS, driven through a real (automated) browser, streamed into your own
> chat website. No API keys, no billing.

## Components

- `install-agentdeck-bridge.sh` — self-contained installer for the **AgentDeck MCP Bridge**:
  a zero-dependency MCP server (Streamable HTTP, JSON-RPC 2.0) that runs on the VPS at
  `127.0.0.1:3117` behind your own cloudflared tunnel. Features: Bearer-token auth,
  command denylist (fork bombs / disk wipes / docker prune / power control), output caps,
  background job model, full audit log.

## Install (on your VPS)

```bash
curl -fsSL -o /tmp/adbridge.sh https://raw.githubusercontent.com/belugaburgers513-bot/agentdeck/main/install-agentdeck-bridge.sh
bash /tmp/adbridge.sh
```

Then expose `http://localhost:3117` through your cloudflared tunnel and use any
MCP-compatible client (or plain curl JSON-RPC) to drive the box.
