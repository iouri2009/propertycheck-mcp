# AQL PropertyCheck — Physical check of one exact address

[![AQL PropertyCheck MCP connector – tool definition quality and endpoint health on Glama](https://glama.ai/mcp/connectors/ai.alphaquantlabs/propertycheck/badges/score.svg)](https://glama.ai/mcp/connectors/ai.alphaquantlabs/propertycheck)

**Gold Coast & Brisbane — the building, the street at its door and the everyday context around one exact address.**

One street address in. Get the building, the street and frontage context and the everyday context around it — from source-backed data, with source, status, date and limitations where available.

PropertyCheck is the last-mile check for a shortlisted property: search / listing / AVM → shortlist → PropertyCheck → decide.

Give one Gold Coast or Brisbane street address and get physical and daily-life evidence that listings and generic risk APIs often leave out:

• The street and frontage context — which street serves the property and how the road edge relates to it. Brisbane, where verified: the frontage street(s) and dual frontage, with nearby bridges and lanes excluded where the State cadastre shows they are not the frontage, and the road reserve stated boundary to boundary, never as the sealed road. Gold Coast: mapped frontage context and Council carriageway width where published. Gold Coast: Council parking-sign data and nearest registered parking area where available. Brisbane: kerb and parking context, including parking signs, meters, permit areas and clearways where available.

• The building and its neighbours — Gold Coast, where supported: building footprint, site coverage, open-lot area and the gap to the nearest separate building. Brisbane, where verified: parent-building height, high-rise status and building-level surroundings by side (N/E/S/W).

• Getting around — Brisbane: routed journeys to the CBD and four universities by walking, bus, train and ferry, including multimodal journeys with legs and transfers (scheduled timetable, never live), a free-flow driving time and any identified toll facilities on the driving route (never a toll price), plus the nearest hospitals and stops. Gold Coast: nearest public-transport stops.

Results include source, status, date and limitations where available. If the property identity cannot be verified safely, no paid report is offered.

Free: check_address — registered identity, coverage and a short source-backed summary.
Full Agent JSON (get_full_report): A$1.39 incl. GST via x402, or A$4.95 incl. GST by card after the human agrees.

Supporting due-diligence evidence also included where available: flood, bushfire and other mapped hazards, planning, school catchments, traffic, police-division context and infrastructure.

Building-level and site-level facts only — not a view from a specific apartment, and not a valuation.

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
