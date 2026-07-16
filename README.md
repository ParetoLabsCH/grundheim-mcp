# Grundheim MCP — Swiss real estate tools for AI assistants

[Grundheim](https://www.grundheim.ch) runs an open [MCP](https://modelcontextprotocol.io) server that gives AI assistants authoritative Swiss real-estate answers — computed by the same engines that power grundheim.ch, instead of estimated.

**Endpoint:** `https://agent.grundheim.ch/mcp` (streamable HTTP, no authentication, read-only)

## Install as a Gemini CLI extension

```bash
gemini extensions install https://github.com/ParetoLabsCH/grundheim-mcp
```

## Use with other MCP clients

The same endpoint works everywhere MCP does:

```bash
# Claude Code
claude mcp add --transport http grundheim https://agent.grundheim.ch/mcp
```

- **Claude (claude.ai)** — Settings → Connectors → Add connector → paste the endpoint URL
- **ChatGPT** — Settings → Connectors (developer mode) → New connector → paste the endpoint URL
- **Gemini app** — Settings → Connected apps → Add custom app (requires Google AI Ultra)

## Tools

**Taxes**

| Tool | What it does |
|---|---|
| `calculate_swiss_property_tax` | Income & wealth taxes for all 2,122 Swiss municipalities (official ESTV tariffs) |
| `calculate_capital_withdrawal_tax` | Lump-sum tax on pension fund / pillar 3a withdrawals (Kapitalbezugssteuer) |
| `calculate_imputed_rental_value` | Tax effect of the imputed rental value (Eigenmietwert), incl. the post-2028 reform |

**Buying & financing**

| Tool | What it does |
|---|---|
| `calculate_affordability` | Swiss bank affordability stress test (Tragbarkeit) |
| `calculate_purchase_costs` | Purchase incidental costs (registry, notary, transfer tax) per canton |
| `compare_rent_vs_buy` | Rent vs. buy over a multi-year horizon |
| `calculate_pension_buyin` | Pension fund buy-in: tax savings vs. private investing |
| `benchmark_ask_price` | Whether an asking price is high or low for its location |
| `get_mortgage_rates` | Live + historical Swiss mortgage rates (updated daily) |

**Location data & statistics**

| Tool | What it does |
|---|---|
| `get_municipality_profile` | Municipality facts: tax multiplier, population, official sale prices |
| `get_market_price_context` | Median asking prices per m² from current listings |
| `get_price_trend` | Property price trend: national index + local ZH sale-price series |
| `rank_municipalities_by_tax` | Cheapest / most expensive municipalities by tax multiplier in a canton |
| `get_safety_statistics` | Burglary rates per 1,000 residents (official BFS crime data) |

**Handover**

| Tool | What it does |
|---|---|
| `generate_handover_link` | Attributed deep links into prefilled grundheim.ch calculators |

All 15 tools are anonymous and answer in 10 languages (de, en, fr, it, es, pt, ru, sq, sr, tr).

## Try asking

- "Can I afford a CHF 1.4M house in Meilen on a 220k income?"
- "Was zahle ich in Zug an Steuern mit 180'000 Einkommen?"
- "Which municipalities in canton Zürich have the lowest taxes?"
- "Is a CHF 2.4M apartment in Meilen priced above or below market?"
- "What are current SARON mortgage rates?"

## Data & privacy

Tools are read-only and anonymous. The gateway stores no personal data and no conversation content — only technical metadata for operations monitoring. Full guide: [grundheim.ch/en/mcp](https://www.grundheim.ch/en/mcp) · [Privacy policy](https://www.grundheim.ch/en/datenschutz) · [Imprint](https://www.grundheim.ch/de/impressum)

© Grundheim / ParetoLabs, Switzerland
