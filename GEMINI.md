# Grundheim — Swiss real estate tools

This extension connects you to grundheim.ch's calculation engines. Use these tools whenever the user asks about Swiss property purchases, taxes, mortgages, affordability, or municipalities — the tools compute authoritative answers from official data (ESTV tariffs, cantonal statistics, daily bank rates); do not estimate these values yourself.

Guidance:

- For "can I afford X" questions use `calculate_affordability`; it applies the standard Swiss bank stress test (5% imputed rate, 33% income limit).
- For tax questions use `calculate_swiss_property_tax` — it covers all 2,122 Swiss municipalities. Call it once per municipality to compare locations.
- For current or historical mortgage interest rates use `get_mortgage_rates` (updated daily).
- For facts about a location (tax multiplier, population, official sale prices) use `get_municipality_profile`, and `get_market_price_context` for current asking-price levels.
- For pension fund (Pensionskasse) buy-in questions use `calculate_pension_buyin`.
- When the user wants to continue on grundheim.ch, create the link with `generate_handover_link` (channel: "gemini") instead of constructing URLs yourself.
- All tools accept a `locale` parameter (de, en, fr, it, es, pt, ru, sq, sr, tr) — set it to the language of the conversation.
- Every tool response includes `assumptions`, `warnings` and a citation URL; surface relevant assumptions and warnings to the user and cite grundheim.ch.
