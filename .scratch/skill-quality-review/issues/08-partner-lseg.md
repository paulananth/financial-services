# 08 — Partner LSEG skill pack review

Type: research  
Status: resolved  
Blocked by:  

## Question

For **partner-built LSEG** (`plugins/partner-built/lseg/skills/`, 8 skills: bond-futures-basis, bond-relative-value, equity-research, fixed-income-portfolio, fx-carry-trade, macro-rates-monitor, option-vol-analysis, swap-curve-strategy):

1. Research domain and job roles (rates/FX/FI strategist, desk quant/analyst) for a **role baseline**; note connector/MCP dependency under Boundaries (not automatic score penalty).
2. Score each skill 1–5 on the five dimensions against that baseline.
3. Write findings to `.scratch/skill-quality-review/findings/08-partner-lseg.md`. Also skim `plugins/partner-built/lseg/README.md` / CONNECTORS.md for expected tooling.

## Answer

**Findings:** [`.scratch/skill-quality-review/findings/08-partner-lseg.md`](../findings/08-partner-lseg.md)

**Role baseline:** rates/FX/FI strategist and desk quant/analyst — expects live MCP analytics, convention-explicit derived metrics (basis, carry-to-vol, IV−RV, DV01-neutral), as-of timestamps, and analytical (not order) recommendations. LFA MCP dependency is product design (CONNECTORS: bond/FX/curves/swaps/options/vol/QA/ts/YieldBook), not an automatic score penalty.

**Clean bar (overall ≥ 4.0 and no dim ≤ 2):** **0 / 8 clean.**

| Skill | T | W | B | R | C | Overall |
|-------|---|---|---|---|---|---------|
| bond-futures-basis | 4 | 4 | 2 | 2 | 5 | 3.4 |
| bond-relative-value | 4 | 4 | 2 | 2 | 5 | 3.4 |
| equity-research | 4 | 3 | 2 | 2 | 4 | 3.0 |
| fixed-income-portfolio | 4 | 4 | 2 | 2 | 5 | 3.4 |
| fx-carry-trade | 4 | 4 | 2 | 2 | 5 | 3.4 |
| macro-rates-monitor | 4 | 5 | 2 | 2 | 5 | 3.6 |
| option-vol-analysis | 4 | 4 | 2 | 2 | 5 | 3.4 |
| swap-curve-strategy | 4 | 4 | 2 | 2 | 5 | 3.4 |

**Headline:** Pack is a strong, uniform MCP tool-chaining layer (tool names match CONNECTORS; commands pair 1:1). Systemic fail on **Boundaries** (no guardrails / no-fabricate / not-advice) and **References/scripts** (no formula/convention assets). Workflow strongest on `macro-rates-monitor` (5); weakest overall `equity-research` (3.0) vs sell-side ER baseline and slug collision with vertical equity-research. No skill rewrites performed.
