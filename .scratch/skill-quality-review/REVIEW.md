# Skill quality review — financial-services

**Date:** 2026-07-24  
**Map:** [map.md](./map.md)  
**Scope:** Unique skills under `plugins/vertical-plugins/` (~55) and `plugins/partner-built/` (11), plus agent-plugin drift spot-check.  
**Method:** Domain/job-role baseline per pack → score Triggers / Workflow / Boundaries / References-scripts / Consistency (1–5) → overall = average. Clean bar: overall ≥ 4.0 **and** no dimension ≤ 2.  
**Out of scope of this report:** applying fixes, rewriting skills, M365 install skills, cookbook YAML.

**Source findings:** [findings/](./findings/) (one file per research ticket).

---

## 1. Executive summary

### Overall health

| Pack | Skills | Clean | Pack mean (approx) | Headline |
|------|-------:|------:|-------------------:|----------|
| equity-research | 9 | 1 | 3.4 | Gold-standard `earnings-analysis`; rest thin |
| financial-analysis | 13 | 8 | 4.1 | Strong modeling/QC core; broken examples + thin authors |
| fund-admin | 6 | 6 | 4.4 | Strong close/recon pack; light refs only |
| investment-banking | 9 | 2 | 3.8 | `pitch-deck` excellent; sell-side pack soft B/R |
| operations (KYC) | 2 | 2 | 4.2 | Boundaries exemplary; optional samples |
| private-equity | 10 | 8 | 4.2 | Lifecycle strong; screen + portco monitor weak |
| wealth-management | 6 | 6 | 4.4 | Coherent advisor loop |
| partner LSEG | 8 | 0 | 3.4 | Uniform desk templates; Boundaries/refs fail clean bar |
| partner S&P Global | 3 | 3 | 4.6 | Production partner quality |
| **agent-plugin drift** | 51 copies | n/a | n/a | **No drift** — all byte-identical to verticals |

**Rough global picture (~66 unique skills scored):** about **half clear the clean bar**. Quality is **bimodal**: fund-admin, operations, wealth, S&P, and much of PE/financial-analysis QC sit high; equity-research thin skills, LSEG pack-wide, and a few broken-asset modeling skills sit low.

### Top systemic issues (read this first)

1. **P0 — Broken or missing skill assets** — `lbo-model` and `comps-analysis` cite `examples/*.xlsx` that do not exist; `strip-profile` cites missing example PPTX and has naming contradictions.
2. **P1 — Thin shared headless authors** — `xlsx-author` / `pptx-author` are stubs with multi-agent blast radius (8 / 3 agents) while live peers (`ib-check-deck`, `deck-refresh`, `3-statement-model`) are excellent.
3. **P1 — Boundaries gap on partner LSEG** — all 8 skills score B=2 (no MCP-only / no-fabricate / not-advice / entitlement handling) while S&P partner pack shows the bar.
4. **P1 — Equity-research quality bifurcation** — one institutional skill (`earnings-analysis` 4.8) vs seven lightweight SOP skills without pack-wide citation/freshness/compliance.
5. **P1 — Missing cross-skill orchestration** — real job cycles (ER earnings path; PE source→IC; sell-side teaser→CIM) are siloed 1:1 skills without handoff contracts.
6. **P2 — Progressive-disclosure debt** — monoliths (`dcf-model`, `comps-analysis`, parts of `initiating-coverage`) violate the pack’s own `skill-creator` norms.
7. **Good news — sync health** — agent-plugin copies are clean; invest in **vertical source quality**, not re-sync forensics.

---

## 2. By vertical / partner pack

### 2.1 Equity research — mean ~3.4 · 1/9 clean

**Role baseline:** Sell-side ER associate/analyst — morning note → preview → post-print model + earnings note → thesis/calendar; franchise via initiation + sector.

| Skill | T | W | B | R | C | Overall | Clean |
|-------|---|---|---|---|---|---------|:-----:|
| catalyst-calendar | 4 | 4 | 3 | 2 | 3 | 3.2 | No |
| earnings-analysis | 5 | 5 | 5 | 5 | 4 | **4.8** | Yes |
| earnings-preview | 4 | 4 | 3 | 2 | 3 | 3.2 | No |
| idea-generation | 4 | 4 | 3 | 2 | 3 | 3.2 | No |
| initiating-coverage | 3 | 4 | 3 | 5 | 3 | 3.6 | No |
| model-update | 4 | 4 | 3 | 2 | 3 | 3.2 | No |
| morning-note | 5 | 4 | 3 | 2 | 3 | 3.4 | No |
| sector-overview | 4 | 4 | 3 | 2 | 3 | 3.2 | No |
| thesis-tracker | 4 | 4 | 3 | 2 | 3 | 3.2 | No |

**Non-clean focus:** Lift citation/freshness from `earnings-analysis` pack-wide; fix `initiating-coverage` internal contradictions (tab count, fonts, file tree); hand off modeling to `financial-analysis` where possible; add compliance layer.

Details: [findings/01-equity-research.md](./findings/01-equity-research.md)

---

### 2.2 Financial analysis — mean ~4.1 · 8/13 clean

**Role baseline:** IB/PE/ER modeling associate + presentation ops — formulas over hardcodes, integrity checks, blue/black/green, deck number QC.

| Skill | Overall | Clean | Note |
|-------|--------:|:-----:|------|
| ib-check-deck | **5.0** | Yes | Best-in-repo QC skill |
| deck-refresh | 4.6 | Yes | Exemplar refresh workflow |
| 3-statement-model | 4.6 | Yes | Strong template + refs |
| audit-xls | 4.4 | Yes | Canonical shared QA |
| competitive-analysis | 4.4 | Yes | |
| ppt-template-creator | 4.4 | Yes | |
| skill-creator | 4.4 | Yes | Meta |
| clean-data-xls | 4.2 | Yes | |
| dcf-model | 3.8 | **No** | Yellow vs blue; Sensitivity sheet mismatch; monolith |
| xlsx-author | 3.6 | **No** | Thin shared stub |
| comps-analysis | 3.4 | **No** | Missing `examples/comps_example.xlsx` |
| pptx-author | 3.4 | **No** | Thin shared stub |
| lbo-model | 3.2 | **No** | Missing `examples/LBO_Model.xlsx` (R=1) |

Details: [findings/02-financial-analysis.md](./findings/02-financial-analysis.md)

---

### 2.3 Fund admin — mean 4.4 · 6/6 clean

**Role baseline:** Fund accountant / recon analyst — audit-cited schedules, draft-only JEs, no silent plugs.

| Skill | Overall |
|-------|--------:|
| break-trace | 4.6 |
| nav-tieout | 4.6 |
| accrual-schedule | 4.4 |
| gl-recon | 4.4 |
| roll-forward | 4.2 |
| variance-commentary | 4.2 |

**Light notes only:** R=3 pack-wide (MCPs named, no `references/` / sample packs). Optional P3 polish.

Details: [findings/03-fund-admin.md](./findings/03-fund-admin.md)

---

### 2.4 Investment banking — mean ~3.8 · 2/9 clean

**Role baseline:** M&A analyst/associate + coverage — teaser → CIM → process → buyer universe; A/D models; strip profiles; template decks.

| Skill | Overall | Clean |
|-------|--------:|:-----:|
| pitch-deck | **4.6** | Yes |
| datapack-builder | 4.0 | Yes |
| buyer-list | 3.8 | No |
| cim-builder | 3.8 | No |
| deal-tracker | 3.8 | No |
| merger-model | 3.8 | No |
| process-letter | 3.8 | No |
| teaser | 3.8 | No |
| strip-profile | **2.8** | No |

**Weakest:** `strip-profile` — frontmatter `fsi-strip-profile` vs folder `strip-profile`; missing example PPTX; mixed Python/PptxGenJS; font contradictions (R=2, C=2).

Details: [findings/04-investment-banking.md](./findings/04-investment-banking.md)

---

### 2.5 Operations (KYC) — mean 4.2 · 2/2 clean

**Role baseline:** KYC/AML analyst — untrusted parse → rules grid → risk rating → human disposition (never silent approve).

| Skill | T | W | B | R | C | Overall |
|-------|---|---|---|---|---|---------|
| kyc-doc-parse | 4 | 4 | 5 | 3 | 5 | 4.2 |
| kyc-rules | 4 | 4 | 5 | 3 | 5 | 4.2 |

**Strength:** Boundaries. **Soft:** sample packet / rules-grid assets (P3).

Details: [findings/05-operations.md](./findings/05-operations.md)

---

### 2.6 Private equity — mean ~4.2 · 8/10 clean

**Role baseline:** PE associate (source→screen→DD→IC), operating partner (VCP), portfolio ops.

| Skill | Overall | Clean |
|-------|--------:|:-----:|
| ai-readiness | 4.6 | Yes |
| value-creation-plan | 4.6 | Yes |
| dd-meeting-prep | 4.6 | Yes |
| unit-economics | 4.4 | Yes |
| deal-sourcing | 4.2 | Yes |
| dd-checklist | 4.2 | Yes |
| ic-memo | 4.2 | Yes |
| returns-analysis | 4.2 | Yes |
| deal-screening | **3.4** | **No** |
| portfolio-monitoring | **3.4** | **No** |

**Fails:** `deal-screening` thin triage + empty criteria shell; `portfolio-monitoring` single-company body vs multi-portco triggers.

Details: [findings/06-private-equity.md](./findings/06-private-equity.md)

---

### 2.7 Wealth management — mean 4.4 · 6/6 clean

**Role baseline:** Advisor / planner / portfolio specialist — suitability, client tone, tax-aware multi-account work.

| Skill | Overall |
|-------|--------:|
| portfolio-rebalance | 4.6 |
| client-report | 4.4 |
| client-review | 4.4 |
| financial-plan | 4.4 |
| investment-proposal | 4.2 |
| tax-loss-harvesting | 4.2 |

**Light notes:** R=3 pack-wide; fix TLH substantially-identical example (P2); deepen investment-proposal KYC/suitability (P3).

Details: [findings/07-wealth-management.md](./findings/07-wealth-management.md)

---

### 2.8 Partner LSEG — mean ~3.4 · 0/8 clean

**Role baseline:** Rates/FX/FI strategist — live LFA MCP analytics, convention-explicit metrics, analytical (not order) recommendations. MCP dependency noted under Boundaries, **not** auto-penalized.

| Skill | Overall | B | R |
|-------|--------:|---|---|
| macro-rates-monitor | 3.6 | 2 | 2 |
| bond-futures-basis | 3.4 | 2 | 2 |
| bond-relative-value | 3.4 | 2 | 2 |
| fixed-income-portfolio | 3.4 | 2 | 2 |
| fx-carry-trade | 3.4 | 2 | 2 |
| option-vol-analysis | 3.4 | 2 | 2 |
| swap-curve-strategy | 3.4 | 2 | 2 |
| equity-research | **3.0** | 2 | 2 |

**Works:** uniform template, tool inventory matches CONNECTORS, desk vocabulary.  
**Fails clean bar systemically:** Boundaries=2 and References=2 pack-wide. `equity-research` slug collides with vertical name and overclaims buy/hold/sell depth.

Details: [findings/08-partner-lseg.md](./findings/08-partner-lseg.md)

---

### 2.9 Partner S&P Global — mean 4.6 · 3/3 clean

**Role baseline:** ER / IB / corp dev / capital markets with hard Kensho/CIQ dependency.

| Skill | Overall | Clean |
|-------|--------:|:-----:|
| tear-sheet | **4.8** | Yes |
| funding-digest | 4.6 | Yes |
| earnings-preview-beta | 4.4 | Yes |

**Polish only:** name normalization (`earnings-preview-beta` vs frontmatter `earnings-preview-single`); README “Industry Transaction Summaries” vs funding-round skill.

Details: [findings/09-partner-spglobal.md](./findings/09-partner-spglobal.md)

---

### 2.10 Agent-plugin drift — CLEAN

Full recursive census: **51/51** bundled skill dirs byte-identical to vertical sources. Shared skills match across agents. **No re-sync required.**

Details: [findings/10-agent-plugin-drift.md](./findings/10-agent-plugin-drift.md)

---

## 3. Systemic findings

| ID | Theme | Severity | Evidence packs |
|----|--------|----------|----------------|
| S1 | Missing/broken `examples/` (or cited assets) | **P0** | financial-analysis (LBO, comps); IB strip-profile |
| S2 | Shared headless authors under-spec vs live peers | **P1** | xlsx-author, pptx-author (high agent fan-out) |
| S3 | Partner LSEG missing Boundaries + formula refs | **P1** | all 8 LSEG skills |
| S4 | ER quality bifurcation + missing compliance/citation pack-wide | **P1** | equity-research |
| S5 | No lifecycle handoff contracts between skills | **P1** | ER, PE, IB sell-side |
| S6 | Internal contradictions / naming mismatches | **P1** | initiating-coverage; strip-profile; earnings-preview-beta; dcf-model validator |
| S7 | Progressive-disclosure / monolith debt | **P2** | dcf-model, comps-analysis, initiating-coverage |
| S8 | Modeling standards forked (ER/IB vs financial-analysis) | **P2** | equity-research model path vs dcf/comps/xlsx-author |
| S9 | Soft Boundaries on otherwise good sell-side skills | **P2** | IB buyer-list…teaser cluster |
| S10 | Light references on strong ops packs | **P3** | fund-admin, wealth, ops, PE |
| S11 | Agent drift | **None** | drift ticket clean |

**Gold standards to clone patterns from:**

- `ib-check-deck` — QC + scripts + terminology  
- `earnings-analysis` — citations, freshness, institutional report budgets  
- `tear-sheet` (S&P) — data-integrity rules 1–10 + audience templates  
- `deck-refresh` — surgical update + approval gates  
- `kyc-rules` / `kyc-doc-parse` — untrusted input + recommend-only disposition  
- `audit-xls` — shared QA family anchor  

---

## 4. Prioritized fix backlog

Ordered by map rule: P0 → P1 systemic → P2 → P3 → P4; within band, worst overall first.

### P0 — Broken / high-blast

| # | Item | Skills / location | Action (recommendation only) |
|---|------|-------------------|------------------------------|
| 1 | Missing LBO example template | `financial-analysis/skills/lbo-model` | Ship `examples/LBO_Model.xlsx` **or** require user template and remove broken path |
| 2 | Missing comps example | `financial-analysis/skills/comps-analysis` | Ship `examples/comps_example.xlsx` **or** drop the cite |
| 3 | strip-profile naming + missing example + toolchain | `investment-banking/skills/strip-profile` | Align frontmatter name with folder; fix or remove example PPTX; one authoring stack |
| 4 | initiating-coverage contradictions | `equity-research/skills/initiating-coverage` | One tab model (6 vs 15+); one font policy; fix file-tree extensions |

### P1 — Cross-cutting systemic

| # | Item | Scope | Action |
|---|------|-------|--------|
| 5 | Strengthen `xlsx-author` floor | Shared · 8 agents | Output contract, blue/black/green, Checks tab, compose with domain skills + `audit-xls` |
| 6 | Strengthen `pptx-author` floor | Shared · 3 agents | Client-ready checklist; compose with `ib-check-deck` / content skills |
| 7 | LSEG Boundaries pack-wide | All 8 LSEG skills | MCP-only numbers, as-of, no fabricate, entitlements, not-advice, proxy labels |
| 8 | LSEG references / conventions | All 8 LSEG | Pack-level `references/conventions.md` (basis, carry, IV−RV, DV01, roll-down) |
| 9 | ER citation + freshness pack-wide | 8 thin ER skills | Port `earnings-analysis` source/freshness rules |
| 10 | ER compliance layer | equity-research | Disclaimers, opinion vs fact, MNPI/independence notes |
| 11 | Cross-skill handoffs | ER, PE, IB | Explicit predecessor/successor skills in Workflow |
| 12 | dcf-model consistency | dcf-model | Blue inputs; align `validate_dcf.py` sheets; split references |

### P2 — Usable but gappy

| # | Item | Skills |
|---|------|--------|
| 13 | deal-screening workflow + sample memo / criteria | PE |
| 14 | portfolio-monitoring multi-portco + covenants | PE |
| 15 | ER lightweight skills R≥3 (one ref or template each) | catalyst-calendar, earnings-preview, idea-generation, model-update, morning-note, sector-overview, thesis-tracker |
| 16 | IB sell-side Boundaries tighten | buyer-list, cim-builder, deal-tracker, merger-model, process-letter, teaser |
| 17 | LSEG equity-research depth or rename | partner LSEG (slug collision with vertical) |
| 18 | TLH substantially-identical example fix | tax-loss-harvesting |
| 19 | Comps/DCF progressive disclosure splits | comps-analysis, dcf-model |
| 20 | Color/convention drift (LBO purple; data-source policy) | modeling pack |

### P3 — Polish

| # | Item |
|---|------|
| 21 | Fund-admin / wealth / ops optional sample assets |
| 22 | S&P earnings-preview name normalize; README label alignment |
| 23 | investment-proposal deeper suitability/KYC |
| 24 | Author-skill naming: skills cite `xlsx`/`PPTX` vs `xlsx-author`/`pptx-author` |
| 25 | PE plugin.json description broader than sourcing-only |

### P4 — Nice-to-have

| # | Item |
|---|------|
| 26 | Harmonize S&P intermediate/output path conventions |
| 27 | Optional deeper `check.py` recursive drift (already clean) |
| 28 | Gold-standard pattern library doc for new skills |

---

## 5. Suggested fix waves (execution is out of this map)

If a follow-on effort applies fixes:

1. **Wave A (P0 assets + contradictions)** — restore trust that skills’ cited files exist and checklists agree.  
2. **Wave B (shared authors + LSEG Boundaries/refs)** — maximum blast radius per line changed.  
3. **Wave C (ER pack lift + PE screen/monitor)** — role-cycle fidelity.  
4. **Wave D (polish)** — samples, naming, README.

Always: edit **vertical** (or partner) sources → `python3 scripts/sync-agent-skills.py` → `python3 scripts/check.py`.

---

## 6. Decision index (wayfinder)

| Ticket | Result |
|--------|--------|
| [01 Equity research](./issues/01-equity-research.md) | Mean ~3.4; 1/9 clean |
| [02 Financial analysis](./issues/02-financial-analysis.md) | Mean ~4.1; 8/13 clean |
| [03 Fund admin](./issues/03-fund-admin.md) | Mean 4.4; 6/6 clean |
| [04 Investment banking](./issues/04-investment-banking.md) | Mean ~3.8; 2/9 clean |
| [05 Operations](./issues/05-operations.md) | Mean 4.2; 2/2 clean |
| [06 Private equity](./issues/06-private-equity.md) | Mean ~4.2; 8/10 clean |
| [07 Wealth management](./issues/07-wealth-management.md) | Mean 4.4; 6/6 clean |
| [08 Partner LSEG](./issues/08-partner-lseg.md) | Mean ~3.4; 0/8 clean |
| [09 Partner S&P](./issues/09-partner-spglobal.md) | Mean 4.6; 3/3 clean |
| [10 Agent drift](./issues/10-agent-plugin-drift.md) | 51/51 CLEAN |
| [11 Synthesize REVIEW](./issues/11-synthesize-review.md) | This document |

---

*End of review. Recommendations only — no skill files were modified.*
