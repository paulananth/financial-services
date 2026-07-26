# 06 — Private equity skill pack review

Type: research  
Status: resolved  
Blocked by:  

## Question

For the **private-equity** vertical (`plugins/vertical-plugins/private-equity/skills/`, 10 skills: ai-readiness, dd-checklist, dd-meeting-prep, deal-screening, deal-sourcing, ic-memo, portfolio-monitoring, returns-analysis, unit-economics, value-creation-plan):

1. Research domain and job roles (PE associate, operating partner, IR/portfolio ops) for a **role baseline**.
2. Score each skill 1–5 on the five dimensions against that baseline.
3. Write findings to `.scratch/skill-quality-review/findings/06-private-equity.md`.

## Answer

Findings: [`.scratch/skill-quality-review/findings/06-private-equity.md`](../findings/06-private-equity.md)

**Role baseline:** PE associate (source→screen→DD→IC), operating partner (VCP, 100-day, cross-portco prioritization), portfolio ops (packs, variance, covenants). Non-negotiables: numbers tie and are source-backed; bull+bear; no unapproved external outreach; don’t invent mandate/covenant thresholds; BOTE returns vs full LBO handoff.

**Clean bar:** overall ≥ 4.0 and no dimension ≤ 2.

| Skill | T | W | B | R | C | Overall | Clean |
|-------|---|---|---|---|---|-------:|:-----:|
| ai-readiness | 5 | 5 | 4 | 4 | 5 | 4.6 | Pass |
| dd-checklist | 5 | 4 | 3 | 4 | 5 | 4.2 | Pass |
| dd-meeting-prep | 5 | 5 | 4 | 4 | 5 | 4.6 | Pass |
| deal-screening | 5 | 3 | 3 | 2 | 4 | 3.4 | **Fail** |
| deal-sourcing | 5 | 4 | 5 | 3 | 4 | 4.2 | Pass |
| ic-memo | 5 | 5 | 4 | 3 | 4 | 4.2 | Pass |
| portfolio-monitoring | 5 | 3 | 3 | 2 | 4 | 3.4 | **Fail** |
| returns-analysis | 5 | 5 | 4 | 4 | 3 | 4.2 | Pass |
| unit-economics | 5 | 5 | 4 | 4 | 4 | 4.4 | Pass |
| value-creation-plan | 5 | 5 | 4 | 4 | 5 | 4.6 | Pass |

**Result:** 8/10 pass. Failures: `deal-screening` and `portfolio-monitoring` (both overall 3.4, Refs/scripts 2) — thin workflows relative to highest-frequency associate/ops work; missing examples, underwriting/covenant depth, portfolio rollup. Pack strengths: triggers, OP skills (`ai-readiness`, `value-creation-plan`), meeting prep. Systemic: no `references/`/`scripts/`; soft boundaries; no lifecycle handoffs; plugin.json description is sourcing-only. No skill rewrites applied.
