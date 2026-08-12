---
name: geometry
description: Deterministic date & name reference data over MCP — Cosmic cards, calendars, moon phases, seasons, retrogrades, and ~30 symbolic systems on 1900–2100. Use when an app or agent needs fixed, structured JSON for a Gregorian date or a name (birthdays, events, holidays, compatibility, name ciphers) instead of guessing.
---

# GEOMETRY

Deterministic reference data for date- and name-keyed questions. Same input -> same JSON. GEOMETRY returns structured data; interpretation belongs to the host app.

## Connect

- MCP URL (the only URL to teach): `https://mcp.geometry.app/mcp`
- With a key: `https://mcp.geometry.app/mcp?key=<zpka_...>`. A key comes from any Developer Portal plan (metered Free or paid) — a key is not the same as "paid".
- Prefer Claude (Claude Code / Claude Desktop): enable once, then ask in natural language.
- ChatGPT: type `@geometry Call get_date for ...` (name the tool). If the tool drops mid-thread, start a new chat — normal behavior, not an outage.

## Tools — pick one

| Question | Tool | Status |
|---|---|---|
| Any single-date fact — Cosmic card, moon, season, retrograde, calendars, weekday, leap year, `day_ruler` | `get_date` | Production |
| Two dates — compatibility score + cross-wheel aspects | `get_compatibility` | Production |
| A name -> Cosmic cards + Latin cipher suite | `get_name` | Beta |

Inputs are a bare `YYYY-MM-DD` (or a name). Resolve natural language to a date before calling. There is no `full=true` flag — MCP/HTTP always returns the complete object.

## Always / never (the mistakes agents make)

- NEVER retype rare Unicode glyphs from memory. Paste the tool's bytes unchanged. `alchemical_symbol` (U+1F700–U+1F77F) and planetary glyphs corrupt into lookalike emoji (e.g. U+1F70A -> water wave). That is an LLM serialization hazard, not a GEOMETRY defect. Verify by codepoint.
- Missing scalars are typed sentinels, never `null`: `0` / `"none"` / `""` / `[]`. One exception: `day_ruler.norse.deity` is `null` on Saturdays (laugardagr has no deity). `_no` fields are non-negative.
- `_no` fields are opaque catalog ids for tracing — key on names and slugs, never on `_no`. Tradition-number exceptions that DO carry meaning: `card_no`, `tarot_no`, `iching_no`, `atomic_no`, `chakra_no`, `house_no`, `pada_no`.
- Sort `planetary_spread` by `spread_pos` (1–14: sun…phoenix), not by JSON key order.
- Cosmic card = birth card = life card = sun card — one identity (aliases under `cosmic.also_called` / `planetary_spread.sun`).
- Two date families, unlabeled in the JSON. Sky events (`moon_phase.*_anchor_dt`, `season.*_anchor_dt`, `retrogrades_active.retro_start_dt`/`retro_end_dt`/`cazimi_dt`) are GMT days. Cultural years (`lunar.year_no`, `calendar_years.*`) use each tradition's own civil timezone. A one-day difference from another library is usually this — check the family before calling it a bug.
- The five `astro_wheels` (tropical, vedic_rasi, fagan_bradley, sidereal_iau, sidereal_true) disagree by design. Match the wheel your source uses; default `sidereal_true`. Not a bug.
- On `get_compatibility`, each side is `cosmic_card_a` / `cosmic_card_b`, each the same profile shape as `get_date`.

## More context

Full page directory: /llms.txt · Site: https://geometry.app · Bugs (paid plans only): https://github.com/goqolabs/geometry-mcp/issues
