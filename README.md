# AQL PropertyCheck: Gold Coast property data for AI agents

Official open-government data for **one point in the City of Gold Coast, Queensland, Australia**, served to AI agents over **MCP**, **A2A** and **REST**. Agents can pay per lookup in USDC over **x402** without an account, or use prepaid credits.

**What one lookup returns**

- Planning zone
- Flood, bushfire and transport-noise overlays, plus major electricity infrastructure
- Land use
- State school catchments
- Nearest public transport
- Measured traffic
- Police division

**Rules the answer follows**

- Every block is `has_value`, `checked_absent` or `not_checked`. `not_checked` is never a statement that a risk is absent.
- Every block carries its source, its Creative Commons Attribution licence and its date. The attribution travels with the data.
- A point outside the Gold Coast is refused with a 404 and never charged. Our own failures are refunded.
- Open government data only. No Google Maps content.

## Connect

| Door | Address |
|---|---|
| MCP (streamable HTTP) | `https://agents.alphaquantlabs.ai/v1/mcp` |
| MCP Registry | `ai.alphaquantlabs/propertycheck` |
| A2A Agent Card | `https://agents.alphaquantlabs.ai/.well-known/agent-card.json` |
| OpenAPI 3.1 | `https://agents.alphaquantlabs.ai/openapi.json` |
| x402 discovery | `https://agents.alphaquantlabs.ai/.well-known/x402` |
| Agent instructions | `https://agents.alphaquantlabs.ai/llms.txt` |
| Live catalogue and prices | `https://agents.alphaquantlabs.ai/v1/blocks` |

`initialize`, `tools/list` and the free `propertycheck_catalogue` tool work without a key. Lookups need a key, or an x402 payment on REST.

### MCP client configuration

```json
{
  "mcpServers": {
    "propertycheck": {
      "url": "https://agents.alphaquantlabs.ai/v1/mcp",
      "headers": { "Authorization": "Bearer <api_key>" }
    }
  }
}
```

A free key (0 credits) comes from this call:

```bash
curl -s -X POST https://agents.alphaquantlabs.ai/v1/accounts \
  -H 'content-type: application/json' \
  -d '{"email":"you@example.com","label":"my agent"}'
```

### Pay per call with x402 (no account)

```bash
curl -i 'https://agents.alphaquantlabs.ai/v1/property?lat=-27.9675&lng=153.4136'
# -> 402 with a PAYMENT-REQUIRED header (USDC on Base). Retry with PAYMENT-SIGNATURE.
```

## Tools

| Tool | Cost | Key |
|---|---|---|
| `propertycheck_lookup` (latitude, longitude) | 1 credit | required |
| `propertycheck_catalogue` | free | not needed |
| `propertycheck_account` | free | required |

## Prices (AUD, incl. GST)

- Pay per call: A$1.39 over x402
- Credit packs: 25 for A$29, 100 for A$89, 500 for A$345, 2000 for A$980

The live price table is always at `/v1/blocks`.

## About

This repository holds the public listing: this README and `server.json`. The service itself is hosted and operated by AlphaQuant Labs. For people rather than agents, the consumer product is at https://property.alphaquantlabs.ai.
