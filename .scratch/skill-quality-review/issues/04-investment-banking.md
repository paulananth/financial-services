# 04 — Investment banking skill pack review

Type: research  
Status: resolved  
Blocked by:  

## Question

For the **investment-banking** vertical (`plugins/vertical-plugins/investment-banking/skills/`, 9 skills: buyer-list, cim-builder, datapack-builder, deal-tracker, merger-model, pitch-deck, process-letter, strip-profile, teaser):

1. Research domain and job roles (M&A analyst/associate, coverage banker) for a **role baseline**.
2. Score each skill 1–5 on the five dimensions against that baseline.
3. Write findings to `.scratch/skill-quality-review/findings/04-investment-banking.md`.

## Answer

Findings written to [`.scratch/skill-quality-review/findings/04-investment-banking.md`](../findings/04-investment-banking.md).

**Role baseline:** M&A analyst/associate + coverage banker — sell-side marketing materials, process ops, A/D models, strip profiles, template population; bar requires clear triggers, process-faithful workflows, legal/client gates, bank-format artifacts, and handoffs to data terminals / authoring skills / legal.

**Pack result:** mean overall ~**3.8**. Clean bar (overall ≥ 4.0, no dim ≤ 2): **pitch-deck (4.6)**, **datapack-builder (4.0)**. Remaining seven fail clean bar mostly on soft Boundaries + light References; **strip-profile (2.8)** is the only skill with dimensions ≤ 2 (Refs=2, Consistency=2).

| Skill | T | W | B | R | C | Overall | Clean? |
|-------|---|---|---|---|---|---------|--------|
| buyer-list | 5 | 4 | 3 | 3 | 4 | 3.8 | No |
| cim-builder | 5 | 4 | 3 | 3 | 4 | 3.8 | No |
| datapack-builder | 4 | 5 | 4 | 4 | 3 | 4.0 | Yes |
| deal-tracker | 5 | 4 | 3 | 3 | 4 | 3.8 | No |
| merger-model | 5 | 4 | 3 | 3 | 4 | 3.8 | No |
| pitch-deck | 4 | 5 | 5 | 5 | 4 | 4.6 | Yes |
| process-letter | 5 | 4 | 3 | 3 | 4 | 3.8 | No |
| strip-profile | 3 | 4 | 3 | 2 | 2 | 2.8 | No |
| teaser | 5 | 4 | 3 | 3 | 4 | 3.8 | No |

**Top systemic issues:** (1) two-tier pack (heavy production vs thin process skills); (2) Boundaries mostly soft Important Notes; (3) authoring dep names (`xlsx` / `PPTX` vs `xlsx-author` / `pptx-author`); (4) strip-profile name `fsi-strip-profile` vs folder/command `strip-profile` + missing Nike example + mixed Python/JS; (5) datapack PE/IC framing inside IB vertical; (6) no documented sell-side skill chain or cross-plugin pitch-book routing.

No skill rewrites applied.
