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

| Tool | What it does |
|---|---|
| `calculate_swiss_property_tax` | Income & wealth taxes for all 2,122 Swiss municipalities (official ESTV tariffs) |
| `calculate_affordability` | Swiss bank affordability stress test (Tragbarkeit) |
| `compare_rent_vs_buy` | Rent vs. buy over a multi-year horizon |
| `calculate_pension_buyin` | Pension fund buy-in: tax savings vs. private investing |
| `get_mortgage_rates` | Live + historical Swiss mortgage rates (updated daily) |
| `get_municipality_profile` | Municipality facts: tax multiplier, population, official sale prices |
| `get_market_price_context` | Median asking prices per m² from current listings |
| `generate_handover_link` | Attributed deep links into prefilled grundheim.ch calculators |

All tools are anonymous and answer in 10 languages (de, en, fr, it, es, pt, ru, sq, sr, tr).

## Try asking

- "Can I afford a CHF 1.4M house in Meilen on a 220k income?"
- "Was zahle ich in Zug an Steuern mit 180'000 Einkommen?"
- "What are current SARON mortgage rates?"

## Data & privacy

Tools are read-only and anonymous. The gateway stores no personal data and no conversation content — only technical metadata for operations monitoring. Full guide: [grundheim.ch/en/mcp](https://www.grundheim.ch/en/mcp) · [Privacy policy](https://www.grundheim.ch/en/datenschutz) · [Imprint](https://www.grundheim.ch/de/impressum)

© Grundheim / ParetoLabs, Switzerland
