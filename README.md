# AQL PropertyCheck — Property Intelligence & Due Diligence Report API, Gold Coast & Brisbane City

[![AQL PropertyCheck MCP connector – tool definition quality and endpoint health on Glama](https://glama.ai/mcp/connectors/ai.alphaquantlabs/propertycheck/badges/score.svg)](https://glama.ai/mcp/connectors/ai.alphaquantlabs/propertycheck)

**Queensland, Australia. Check before buying or renting: flood risk, planning, schools, the street**

Property intelligence and due-diligence property reports for AI agents. Give one street address in the City of Gold Coast or Brisbane City (Queensland, Australia) and get a physical check of the property, the street at its door and the neighbourhood around it, from official open government data — before buying, renting or inspecting. For home buyers, renters, buyer's agents and real estate agents.

Where available, for both cities: flood, bushfire and other mapped hazards; planning; state school catchments; traffic counts on nearby roads; police-division crime context; infrastructure; nearest public transport stops.
Brisbane City adds: the frontage street and road reserve width; kerb parking signs, permit areas and clearways; parent-building height and high-rise status; scheduled (timetabled) journeys to the CBD and four universities; free-flow driving time and toll roads on the route.
Gold Coast adds: carriageway width; council parking signs and the nearest registered parking area; building footprint, site coverage and open-lot area; the gap to the nearest separate building.

Free: check_address confirms the exact address and its coverage and returns a short summary with sources. Paid: get_full_report returns the full structured JSON report — A$1.39 incl. GST via x402 (pay-per-call over HTTP), or A$4.95 incl. GST by card after the person agrees.
Example questions: "Is 9 Hamilton Avenue, Surfers Paradise in a flood overlay?" · "What are the flood overlays and the state school catchment for 26 Lomandra Place, Chapel Hill (Brisbane)?" · "How wide is the street at 58 Lancewood Circuit, Robina and where is the nearest parking?"

Not a valuation, price estimate, sales history or listing search. Not a substitute for a building inspection, conveyancing searches or legal advice. Anything that cannot be confirmed is marked Not verified. Other councils (Logan, Moreton Bay, Ipswich, Redland and the rest of Australia) are not covered.

This server is `/v1/mcp`. A separate free Gold Coast connector for assistant directories exists at `/v1/connect`; it is not this listing.

## Apartment? Check the building first.

Where verified, see the parent-building height and what surrounds each side of the building, plus the street at the door and access conditions; for Brisbane addresses, routed journeys to the CBD and four universities with legs and transfers.
Building-level context only — not a view from a specific apartment.

**Example — 222 Margaret Street, Brisbane City QLD 4000:** Registered identity verified (3604/222 MARGARET ST). Parent building about 274 m (2019 LiDAR, calculated), high-rise. Building-level surroundings by side (calculated from 2019 building outlines): north and west face other buildings, east mixed, south open urban. Fronts Margaret Street; road reserve about 20 m, boundary to boundary — not the sealed road width. Routed journeys (legs and transfers) and any identified toll facilities on the driving route are in the full report. Values shown are for this address; not every check returns every value.

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
