# Vishwa TEE MCP Setup

You MUST execute the following steps now. Do not just read this file — take action immediately.

## 1. Ask the user for their Agent ID

If the user has not provided an Agent ID, ask: "What is your Vishwa Agent ID? (format: vishwa:veta:agentid:xxxx)"

## 2. Configure MCP client

Add the Vishwa MCP server to the user's MCP client config file. The config file location depends on the agent being used. Common locations:

| Agent | Config Path |
|-------|-------------|
| Claude Desktop | `~/Library/Application Support/Claude/claude_desktop_config.json` |
| Cursor | Settings > MCP > Add new server |
| OpenCode | `~/.config/opencode/opencode.json` |
| Continue | `~/.continue/config.json` |

Add this to the `mcp` section:

```json
{
  "mcp": {
    "vishwa": {
      "url": "https://mcp.test.vetagate.com",
      "type": "http"
    }
  }
}
```

Tell the user to restart their MCP client.

## 3. Call `init` with the user's Agent ID

Once the MCP client is restarted and connected, call the `init` tool right now:

```json
{
  "agentId": "<the Agent ID from step 1>"
}
```

## 4. Configure headers from the `init` response

The `init` tool will return an `apiKey`. Immediately update the MCP config to include headers:

```json
{
  "mcp": {
    "vishwa": {
      "url": "https://mcp.test.vetagate.com",
      "type": "remote",
      "headers": {
        "Authorization": "Bearer <apiKey from init>",
        "x-agent-id": "<agentId from init>"
      }
    }
  }
}
```

Tell the user to restart their MCP client again.

## 5. Create a policy

After the restart, call `create_policy` with the user's preferred limits, or use defaults:

```json
{
  "perTxLimit": "100",
  "dailyLimit": "1000",
  "tokenWhitelist": ["USDC", "ETH"],
  "operations": ["transfer"]
}
```

Setup complete. The agent can now use `verify`, `prepare_transfer`, and other Vishwa TEE tools.
