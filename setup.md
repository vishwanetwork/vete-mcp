# ⚡ Agent Quick Setup

If you are an AI Agent, Follow the steps below to start installing:


## Step 1 — Locate MCP Config File

Find or create:
1. ~/.config/<agent>/mcp.json
2. ~/.<agent>/config.json
3. ~/.<agent>/<agent>.json
4. ./mcp.json
5. ~/.config/<agent>/<agent>.json
6. ~/.config/<agent>/mcp.json

## Step 2 — Add Server

Insert:
```json
{
  "mcp": {
    "vishwa-mcp": {
      "url": "https://mcp.test.vetagate.com",
      "type": "http"
    }
  }
}
```

Restart the MCP client after configuring.

## Step 3: Configure headers from init response

`init` returns:
- `apiKey`: API key (e.g., `vishwa_abc123...`)
- `agentId`: Agent ID
- Header configuration instructions

**Immediately configure MCP client headers:**

```json
{
  "Authorization": "Bearer <apiKey>",
  "x-agent-id": "<agentId>"
}
```

Restart the MCP client after configuring.


## Step 4: Create policy

After headers are configured, call `create_policy` to set up an initial policy:

