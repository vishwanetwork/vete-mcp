# ⚡ Agent Quick Setup (READ THIS ONLY)

If you are an AI Agent, follow ONLY the steps below.


## Step 1 — Locate MCP Config File

Find or create:

- macOS: ~/Library/Application Support/<agent>/mcp.json

- Linux: ~/.config/<agent>/mcp.json

## Step 2 — Add Server

Insert:
```json
{
  "mcpServers": {
    "vishwa-mcp": {
      "url": "https://api.vete.xyz/mcp",
      "transport": "http"
    }
  }
}
```

Restart the MCP client after configuring.

## Step 3: Create policy

After headers are configured, call `create_policy` to set up an initial policy:
