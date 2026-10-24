# AQL PropertyCheck — Physical check of one exact address

[![AQL PropertyCheck MCP connector – tool definition quality and endpoint health on Glama](https://glama.ai/mcp/connectors/ai.alphaquantlabs/propertycheck/badges/score.svg)](https://glama.ai/mcp/connectors/ai.alphaquantlabs/propertycheck)

**Gold Coast & Brisbane — the building, the street at its door and the everyday context around one exact address.**

Give one shortlisted street address in the City of Gold Coast or Brisbane City and get a source-backed physical check of the property and what surrounds it, where the underlying data supports the result. For buyers, renters and their AI assistants; not listing search or a valuation.

Where available, for both cities: flood, bushfire and other mapped hazards; planning; state school catchments; traffic counts on nearby roads; police-division crime context; infrastructure; nearest public transport stops.
Brisbane City adds: the frontage street and road reserve width; kerb parking signs, permit areas and clearways; parent-building height and high-rise status; scheduled (timetabled) journeys to the CBD and four universities; free-flow driving time and toll roads on the route.
Gold Coast adds: carriageway width; council parking signs and the nearest registered parking area; building footprint, site coverage and open-lot area; the gap to the nearest separate building.

Free: check_address confirms the exact address and its coverage and returns a short summary with sources. Paid: get_full_report returns the full structured JSON report — A$1.39 incl. GST via x402 (pay-per-call over HTTP), or A$4.95 incl. GST by card after the person agrees.
Example questions: "Is 9 Hamilton Avenue, Surfers Paradise in a flood overlay?" · "What are the flood overlays and the state school catchment for 26 Lomandra Place, Chapel Hill (Brisbane)?" · "How wide is the street at 58 Lancewood Circuit, Robina and where is the nearest parking?"

Not a valuation, price estimate, sales history or listing search. Not a substitute for a building inspection, conveyancing searches or legal advice. Anything that cannot be confirmed is marked Not verified. Other councils (Logan, Moreton Bay, Ipswich, Redland and the rest of Australia) are not covered.

This server is `/v1/mcp`. A separate free connector for assistant directories (ChatGPT app, Claude directory) exists at `/v1/connect`, for the same Gold Coast and Brisbane coverage; it is not this listing.

## Apartment? Check the building first.

Where verified, see the parent-building height and what surrounds each side of the building, plus the street at the door and access conditions; for Brisbane addresses, routed journeys to the CBD and four universities with legs and transfers.
Building-level context only — not a view from a specific apartment.

For an apartment, supply its exact unit number. A request for an entire building must not be presented as a verified match to an arbitrarily selected apartment; PropertyCheck refuses that mismatch before offering payment. Building-level context is supplied only where the address and underlying data support it.

## House or land? Check the space around it.

Where supported, see how much of the lot is built on, how close the next building is, which street fronts the property and what the road and parking context is. Gold Coast full report, where supported: footprint, site coverage, open lot, nearest-building gap, mapped frontage context, Council carriageway width where published, parking registers where available. Brisbane, where verified: the frontage street(s), road reserve and kerb and parking registers; the Gold Coast lot measurements are not claimed for Brisbane.

## Connect

| Surface | Address |
|---|---|
| MCP (streamable HTTP) | `https://agents.alphaquantlabs.ai/v1/mcp` |
| Official MCP Registry | `ai.alphaquantlabs/propertycheck` |
| A2A Agent Card | `https://agents.alphaquantlabs.ai/.well-known/agent-card.json` |
| OpenAPI | `https://agents.alphaquantlabs.ai/openapi.json` |
| x402 discovery | `https://agents.alphaquantlabs.ai/.well-known/x402` |
| Agent instructions | `https://agents.alphaquantlabs.ai/llms.txt` |

```json
{
  "mcpServers": {
    "propertycheck": { "url": "https://agents.alphaquantlabs.ai/v1/mcp" }
  }
}
```

No key is needed to connect or to run the free check.

## Tools

| Tool | What it does | Price |
|---|---|---|
| `check_address(address)` | Identity, coverage and a short source-backed summary for one Gold Coast or Brisbane street address. Never charges. | Free |
| `get_full_report(address)` | The full structured Agent JSON for the same address. x402: re-open the same report by `report_id` at no extra cost. Card: after card payment, retrieve using the returned `purchase_id` and `access_token`. | A$1.39 incl. GST via x402 (USDC on Base, Polygon or Solana), or A$4.95 incl. GST by card after the human agrees |

The A$17.95 PDF on https://property.alphaquantlabs.ai is a separate consumer product.

## Not for

Listing search, valuations or sale-price estimates, mortgages, national property search, price forecasts, live emergency warnings, generic suburb rankings, views from a specific apartment, or addresses outside the City of Gold Coast and Brisbane City.

## About

This repository holds the public listing only: this README and `server.json`. The service is hosted and operated by AlphaQuant Labs.
