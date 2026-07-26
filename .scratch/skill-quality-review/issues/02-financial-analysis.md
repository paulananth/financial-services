# 02 — Financial analysis skill pack review

Type: research  
Status: resolved  
Blocked by:  

## Question

For the **financial-analysis** vertical (`plugins/vertical-plugins/financial-analysis/skills/`, 13 skills: 3-statement-model, audit-xls, clean-data-xls, competitive-analysis, comps-analysis, dcf-model, deck-refresh, ib-check-deck, lbo-model, ppt-template-creator, pptx-author, skill-creator, xlsx-author):

1. Research domain and job roles (IB/PE/ER modeling analyst, presentation ops) for a **role baseline**.
2. Score each skill 1–5 on the five dimensions against that baseline.
3. Write findings to `.scratch/skill-quality-review/findings/02-financial-analysis.md`.

Note: several skills here are **shared** across agents — flag family consistency issues for systemic findings.

## Answer

### Answer gist

Scored all 13 financial-analysis skills against an IB/PE/ER modeling + presentation-ops baseline (formulas-over-hardcodes, BS/cash/RE integrity, blue/black/green, source comments, section checkpoints, deck number QC).

**8/13 pass** the clean bar (overall ≥ 4.0 and no dim ≤ 2). Standouts: **ib-check-deck (5.0)**, **deck-refresh (4.6)**, **3-statement-model (4.6)**, **audit-xls (4.4)**.

**Fails:** **lbo-model (3.2)** and **comps-analysis (3.4)** — missing `examples/*.xlsx` assets they require; **dcf-model (3.8)** — consistency (Yellow inputs vs blue rule; `validate_dcf.py` expects Sensitivity sheet while skill puts sensitivity on DCF sheet; 1.2k-line monolith); **xlsx-author (3.6)** and **pptx-author (3.4)** — thin headless stubs with high multi-agent blast radius.

**Systemic flags:** shared `xlsx-author`/`pptx-author` under-spec; color drift (LBO purple); non-portable `recalc.py` paths; progressive-disclosure violations on DCF/comps.

### Findings path

`.scratch/skill-quality-review/findings/02-financial-analysis.md`
