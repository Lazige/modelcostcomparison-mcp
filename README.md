# ModelCostComparison MCP

Measured by MCPmetrics:

[![MCPmetrics: measured MCP protocol support](https://mcpmetrics.io/badge/io.github.Lazige/modelcostcomparison/era.svg)](https://mcpmetrics.io/servers/io-github-lazige-modelcostcomparison)

Connect your AI client to the same pricing source and calculation engine used by [ModelCostComparison](https://modelcostcomparison.com).

[Install in Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=modelcostcomparison&config=eyJ1cmwiOiJodHRwczovL21vZGVsY29zdGNvbXBhcmlzb24uY29tL2FwaS92MS9tY3AifQ%3D%3D)

## Connect

Remote endpoint: `https://modelcostcomparison.com/api/v1/mcp`  
Transport: Streamable HTTP. No API key or local package required.

### Cursor

Use the install link above and confirm the server in Cursor. Alternatively, merge the contents of `mcp.json` into your Cursor MCP configuration, preserving existing servers. Enable ModelCostComparison in the agent's tools.

### Claude

Open Connectors, choose Add custom connector, name it ModelCostComparison and paste the endpoint above. Connect it and enable its tools for your conversation. Organization settings may require an administrator to add it.

### Other clients

Add a remote MCP server with the endpoint above and Streamable HTTP transport.

## Tools

| Tool | Purpose |
| --- | --- |
| `list_models` | Find model and exact tariff identifiers. |
| `get_model_pricing` | Get rates, sources and review dates. |
| `calculate_cost` | Calculate input, output and cached-input token costs. |
| `compare_model_costs` | Compare offers for the same token workload. |

## Try it

- “Use ModelCostComparison to list available OpenAI models and show pricing sources and review dates.”
- “Find reviewed offers for OpenAI, Anthropic and Google. Compare 1 million input tokens and 200,000 output tokens, with no cache and at most 8,000 input tokens per request.”
- “For the selected offer, estimate 1 million input tokens including 500,000 cached input tokens, plus 100,000 output tokens. Maximum input per request is 8,000 tokens.”

Start with model discovery; use the exact offer IDs returned by the service. Missing or ambiguous workload details should be clarified before calculating.

## Scope

Results are estimates of text-token subtotals in USD, not invoices or model-quality rankings. Cache writes, storage, tools, search and taxes are excluded. Expired or unreviewed offers cannot be calculated. Unsupported offers are reported separately in comparisons. Pricing is served from the website's reviewed deployment snapshot, not fetched from providers on every request.

The service is rate limited. On HTTP 429, wait for `Retry-After` before retrying. HTTP 503 indicates temporary unavailability. No provider credentials are needed, and tools do not call provider models.

This repository contains connection settings and documentation only. Pricing and calculations remain on the hosted service.

## References

- [Developer documentation](https://modelcostcomparison.com/developers#mcp)
- [Cursor install links](https://cursor.com/docs/mcp/install-links)
- [Claude custom connectors](https://support.claude.com/en/articles/11175166-get-started-with-custom-connectors-using-remote-mcp)

## Official MCP Registry

Published as `io.github.Lazige/modelcostcomparison`, version `1.0.0`. [Registry entry](https://registry.modelcontextprotocol.io/v0.1/servers/io.github.Lazige%2Fmodelcostcomparison/versions/1.0.0). The registry metadata lives in `server.json`.
