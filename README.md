# Grundheim MCP — Swiss real estate tools for AI assistants

[Grundheim](https://www.grundheim.ch) runs an open [MCP](https://modelcontextprotocol.io) server that gives AI assistants authoritative Swiss real-estate answers — computed by the same engines that power grundheim.ch, instead of estimated.

**Endpoint:** `https://agent.grundheim.ch/mcp` (streamable HTTP, no authentication, read-only)

## One-click install

- **ChatGPT**: [Grundheim in the ChatGPT plugin directory](https://chatgpt.com/plugins/plugin_asdk_app_6acb3c7ce3d8819188911ef4a4ce3818), choose «Add»
- **Claude (claude.ai)**: [Add Grundheim as a connector](https://claude.ai/customize/connectors?modal=add-custom-connector&connectorName=Grundheim&connectorUrl=https%3A%2F%2Fagent.grundheim.ch%2Fmcp) (dialog opens prefilled, confirm it)

Step-by-step guides: [grundheim.ch/en/integrationen/claude](https://www.grundheim.ch/en/integrationen/claude) · [grundheim.ch/en/integrationen/chatgpt](https://www.grundheim.ch/en/integrationen/chatgpt)

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

- **Claude (claude.ai)** — use the install link above, or Settings → Connectors → Add custom connector → paste the endpoint URL
- **ChatGPT** — use the directory listing above; without directory plugins: Settings → Security and login → Developer mode, then Plugins → «+» → paste the endpoint URL
- **Cursor / VS Code** — one-click links on [grundheim.ch/en/mcp](https://www.grundheim.ch/en/mcp#clients)
- **Gemini app** — Settings → Connected apps → Add custom app (requires Google AI Ultra)

## Tools

**Taxes**

| Tool | What it does |
|---|---|
| `calculate_swiss_income_and_wealth_tax` | Income & wealth taxes for all 2,122 Swiss municipalities (official ESTV tariffs) |
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
| `calculate_mortgage_costs` | What a mortgage costs per month, how to split it into tranches, and how a rate rise hits |
| `estimate_break_penalty` | Penalty for exiting a fixed mortgage early, and the rate that would justify it |
| `evaluate_forward_mortgage` | Whether locking a rate in advance beats waiting until renewal |
| `compare_amortization_strategies` | Paying down the second mortgage directly vs. via pillar 3a |
| `compare_tranche_structures` | 10-year fixed / 5-year fixed / SARON splits under six SNB rate paths over ten years (Tranchen-Planer) |
| `get_mortgage_rates` | Live + historical Swiss mortgage rates (updated daily) |

**Location data & statistics**

| Tool | What it does |
|---|---|
| `get_municipality_profile` | Municipality facts: tax multiplier, population, official sale prices |
| `get_market_price_context` | Median asking prices per m² from current listings |
| `get_price_trend` | Property price trend: national index + local ZH sale-price series |
| `rank_municipalities_by_tax` | Cheapest / most expensive municipalities by tax multiplier in a canton |
| `get_safety_statistics` | Burglary rates per 1,000 residents (official BFS crime data) |

**Renovation**

| Tool | What it does |
|---|---|
| `search_tradespeople` | Craft and construction companies (~35 trades) near a Swiss place, from the commercial register; free-text need in DE/FR/IT/EN |

**Handover**

| Tool | What it does |
|---|---|
| `generate_handover_link` | Tracked, attributed short links to continue on grundheim.ch (by-location tax/Nebenkosten, municipality profiles, rate comparison, registration). The calculation tools already return prefilled continue-links for their own calculators. |

All 21 tools are anonymous and answer in 10 languages (de, en, fr, it, es, pt, ru, sq, sr, tr).

## Try asking

- "Can I afford a CHF 1.4M house in Meilen on a 220k income?"
- "Was zahle ich in Zug an Steuern mit 180'000 Einkommen?"
- "Which municipalities in canton Zürich have the lowest taxes?"
- "Is a CHF 2.4M apartment in Meilen priced above or below market?"
- "What are current SARON mortgage rates?"
- "Fix or SARON? Compare tranche structures for a CHF 1 million mortgage."
- "Find a plumber near Winterthur, water in the basement."
- "What would a CHF 1.2M mortgage cost me per month, and should I fix or go SARON?"
- "Lohnt es sich, meine Festhypothek vorzeitig aufzulösen?"

## Data & privacy

Tools are read-only and anonymous. The gateway stores no personal data and no conversation content — only technical metadata for operations monitoring. Full guide: [grundheim.ch/en/mcp](https://www.grundheim.ch/en/mcp) · [Privacy policy](https://www.grundheim.ch/en/datenschutz) · [Imprint](https://www.grundheim.ch/de/impressum)

© Grundheim / ParetoLabs, Switzerland

> `calculate_swiss_income_and_wealth_tax` was called `calculate_swiss_property_tax` until October 2026; the old name still works for existing clients.
