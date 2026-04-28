---
name: vishwa-tee-mcp
description: Guide users to connect to the Vishwa TEE MCP server. Trigger when the user mentions "install vishwa", "configure vishwa MCP", "initialize TEE", "setup transaction verification", or needs the MCP server address.
---

# Vishwa TEE MCP Quick Setup

## MCP Server Address

Vishwa TEE MCP HTTP server: `https://mcp.test.vetagate.com/`

## Step 1: Call init

After connecting to the MCP server, **first** call the `init` tool:

```json
{
  "agentId": "User's Agent ID"
}
```

Agent ID format: `vishwa:veta:agentid:xxxx`

## Step 2: Configure headers from init response

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

## Step 3: Create policy

After headers are configured, call `create_policy` to set up an initial policy:

```json
{}
```

(All parameters optional — defaults will be used.)

Once the policy is created, `verify`, `prepare_transfer`, and other tools are ready to use.

## Tool Reference

- `init` - Initialize session (no auth required)
- `create_policy` - Create transaction policy
- `get_policy` - Query current policy
- `update_policy` - Update policy constraints
- `verify` - Verify transaction against policy
- `prepare_transfer` - Build transfer transaction
- `markets_match` - Search Polymarket prediction markets
