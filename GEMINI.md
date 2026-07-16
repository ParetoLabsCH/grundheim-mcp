# Grundheim — Swiss real estate tools

This extension connects you to grundheim.ch's calculation engines. Use these tools whenever the user asks about Swiss property purchases, taxes, mortgages, affordability, or municipalities — the tools compute authoritative answers from official data (ESTV tariffs, cantonal statistics, daily bank rates); do not estimate these values yourself.

Guidance:

Taxes
- For income & wealth tax questions use `calculate_swiss_property_tax` — it covers all 2,122 Swiss municipalities. Call it once per municipality to compare locations.
- For the one-time tax on a lump-sum pension fund / pillar 3a payout use `calculate_capital_withdrawal_tax` (Kapitalbezugssteuer).
- For the tax effect of owner-occupied imputed rent use `calculate_imputed_rental_value` (Eigenmietwert).

Buying & financing
- For "can I afford X" questions use `calculate_affordability`; it applies the standard Swiss bank stress test (5% imputed rate, 33% income limit).
- For the one-time closing costs of a purchase use `calculate_purchase_costs` (land registry, notary, transfer tax — varies by canton).
- For rent-versus-buy decisions use `compare_rent_vs_buy`.
- For pension fund (Pensionskasse) buy-in questions use `calculate_pension_buyin`.
- To judge whether a specific asking price is high or low for its location use `benchmark_ask_price` — lead with its `local_norm_verdict` (vs other asks nearby) and report the `confidence` level honestly.
- For current or historical mortgage interest rates use `get_mortgage_rates` (updated daily).

Location data & statistics
- For facts about a location (tax multiplier, population, official sale prices) use `get_municipality_profile`, and `get_market_price_context` for current asking-price levels.
- For price development over time use `get_price_trend` (national index + local ZH sale-price series).
- For "where are the lowest/highest taxes in canton X" use `rank_municipalities_by_tax`.
- For "how safe is X / burglary rates" use `get_safety_statistics`.

Handover
- When the user wants to continue on grundheim.ch, create the link with `generate_handover_link` (channel: "gemini") instead of constructing URLs yourself.

General
- All tools accept a `locale` parameter (de, en, fr, it, es, pt, ru, sq, sr, tr) — set it to the language of the conversation.
- Every tool response includes `assumptions`, `warnings` and a citation URL; surface relevant assumptions and warnings to the user and cite grundheim.ch.
