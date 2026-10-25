---
name: check-address-before-you-rent-or-buy
description: Use when someone names a specific street address in the City of Gold Coast or Brisbane City (Queensland, Australia) that they may rent, buy, live in or move to, and wants to know what the property and its surroundings are like - flood, bushfire and other mapped hazards, planning zone, unit in a complex, the street, schools, public transport, and in Brisbane parking rules and transport time to the CBD.
---

# Check an address before you rent or buy (Gold Coast and Brisbane City)

## When to use
- The person names one street address in the City of Gold Coast or Brisbane City and is deciding whether to rent, buy, live there or move there.
- They ask about flooding, bushfire, zoning, the street, schools, transport or parking at that address.

Do not use it for listing searches, valuations, price forecasts, mortgage questions or suburb rankings, or for addresses outside these two councils.

## How
1. Get one full street address: street number, street name and suburb, and the unit number for an apartment ("27/50 Rotherham Street, Kangaroo Point").
2. Call the `check_property` tool of the AQL PropertyCheck connector with that address. One call per address.
3. Report what the tool returned, finding by finding, with each finding's status (verified, calculated or not verified) and its source.
4. Give the link the answer contains, so the person can open the page for that address.

## Say it honestly
- "Not verified" means the source could not be checked. It never means "no risk" or "safe".
- Council flood and bushfire maps are mapping, not a guarantee about one property. Say "mapped as" and "may", never "will" or "guaranteed".
- When the answer says UNIT_NOT_VERIFIED, the facts describe the building or complex, not the apartment itself. Say so.
- If the tool says the address could not be matched or is outside coverage, say that and ask for the exact address. Never guess another property.
- This is not a valuation, survey, legal or financial advice.

## Example
"We might rent 15 Winslow Court, Oxenford. Anything we should know?" -> call `check_property` with "15 Winslow Court, Oxenford QLD 4210" -> list the findings with their status and source -> give the link.
