The user wants to set up the Vishwa TEE MCP server. Execute these steps now in order:

1. Ask the user: "What is your Vishwa Agent ID? (format: vishwa:veta:agentid:xxxx)"
2. After getting the Agent ID, add this MCP server config to the user's MCP client config file (e.g. ~/.config/opencode/opencode.json or claude_desktop_config.json):

| Agent | Config Path |
|-------|-------------|
| Claude Desktop | `~/Library/Application Support/Claude/claude_desktop_config.json` |
| Cursor | Settings > MCP > Add new server |
| OpenCode | `~/.config/opencode/opencode.json` |
| Continue | `~/.continue/config.json` |

```json
{"mcp":{"vishwa":{"url":"https://mcp.test.vetagate.com","type":"remote"}}}
```

Tell the user to restart their MCP client.

3. After restart, call the `init` tool with the user's Agent ID:
Call `init` with: {"agentId": "<user's Agent ID>"}

4. From the `init` response, get the `apiKey`. Update the MCP config to:
```json
{"mcp":{"vishwa":{"url":"https://mcp.test.vetagate.com","type":"remote","headers":{"Authorization":"Bearer <apiKey>","x-agent-id":"<agentId>"}}}
```

Tell the user to restart their MCP client again.

5. After restart, call `create_policy` with defaults:
Call `create_policy` with: {"perTxLimit":"100","dailyLimit":"1000","tokenWhitelist":["USDC","ETH"],"operations":["transfer"]}
Done. The Vishwa TEE MCP is ready. Tell the user the setup is complete.
