# AQL PropertyCheck for Claude

Check a City of Gold Coast or Brisbane City (Queensland, Australia) street address before you sign a lease or make an offer: flood, bushfire and other mapped hazards, planning zone, unit in a complex, the street, schools and public transport, and in Brisbane parking rules and public-transport time to the CBD, each from official open data with its source.

## What is in this plugin

- **One skill**, `check-address-before-you-rent-or-buy`: tells Claude when to check an address and how to report the result honestly (status and source of every finding; "not verified" never means "safe").
- **One remote MCP server**, `aql-propertycheck`, at `https://agents.alphaquantlabs.ai/v1/connect?via=claude` - the same server as the AQL PropertyCheck connector. Two read-only tools: `check_property(address)` and `about_propertycheck`.

## What it sends and where

- The plugin runs no code on your computer and has no hooks, commands or scripts.
- When Claude calls `check_property`, the **street address** you asked about is sent to `agents.alphaquantlabs.ai` (operated by TTM369 Pty Ltd). The server looks it up in the Queensland Government address register and official open data from the City of Gold Coast, Brisbane City Council, the Queensland Government, Translink, the Queensland Police Service and the ABS.
- Nothing else is sent: no conversation, name, email or files. No account, sign-in, key or payment. Nothing is bought, charged or stored about you. Request counters for abuse protection are kept briefly; see the privacy policy.
- Each answer includes a link to the page for that address on https://property.alphaquantlabs.ai.

## Limits

Coverage is the City of Gold Coast and Brisbane City only; other addresses are reported as outside coverage. Council overlays are mapping, not a guarantee about a single property. Not a valuation, survey, legal or financial advice.

## Links

- Documentation: https://agents.alphaquantlabs.ai/v1/connect
- Support: https://property.alphaquantlabs.ai/contact
- Privacy: https://property.alphaquantlabs.ai/privacy
- Terms: https://property.alphaquantlabs.ai/terms
