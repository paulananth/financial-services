# 01 — Equity research skill pack review

**Pack:** `plugins/vertical-plugins/equity-research/skills/`  
**Skills (9):** catalyst-calendar, earnings-analysis, earnings-preview, idea-generation, initiating-coverage, model-update, morning-note, sector-overview, thesis-tracker  
**Date:** 2026-07-24  
**Clean bar:** overall ≥ 4.0 and no dimension ≤ 2 → light notes only; else deeper write-up  

**Scoring dimensions (1–5):**  
- **T** Triggers (frontmatter + when/when-not)  
- **W** Workflow (steps, artifacts, role fit)  
- **B** Boundaries (scope, accuracy, compliance, do-nots)  
- **R** References/scripts (depth of supporting materials)  
- **C** Consistency (repo / in-vertical peers / shared-skill families)  
- **Overall** = average of five dims, one decimal  

---

## Role baseline

### Primary roles
Sell-side **equity research associate** and **analyst** (and senior analyst / coverage lead) covering a sector universe for institutional clients. Day-to-day work also overlaps buy-side research associates who consume the same artifacts, but this pack’s product language (ratings, price targets, morning meetings, initiation format) is **sell-side-first**.

### Typical workflow (calendar + event-driven)
1. **Daily:** overnight scan → **morning note** (actionable take for PMs/sales) → coverage events list.  
2. **Pre-event:** **earnings preview** / catalyst prep; model checks; consensus/whisper context.  
3. **Post-event (earnings):** flash/quick take (often morning note) → **model update** (plug actuals, revise estimates/PT) → full **earnings analysis** note (8–12 pp within 24–48h) → **thesis tracker** update.  
4. **Ongoing:** **catalyst calendar** maintenance; **thesis** reviews on material news; **idea generation** screens for new longs/shorts.  
5. **Major product:** **initiating coverage** (multi-week; research + model + valuation + charts + long-form report); **sector overview** for franchise/thematic pieces.

### Core artifacts
| Artifact | Typical form | Role purpose |
|----------|--------------|--------------|
| Initiation report | 30–50+ pp DOCX + full Excel model | Franchise coverage launch; rating + PT + full thesis |
| Earnings update | 8–12 pp DOCX (fast turn) | Beat/miss, estimate revisions, thesis impact |
| Earnings preview | 1-pager / short note | Positioning ahead of print |
| Morning note | ≤1 page email/Slack | 7am meeting; opinionated, actionable |
| Financial model | Live Excel (formulas, scenarios, DCF/comps) | Living estimate book; valuation engine |
| Catalyst calendar | Spreadsheet + weekly preview | Prioritize attention / risk around events |
| Sector overview | Deck or long note + data appendix | Landscape, comps context, thematic map |
| Idea sheets | Shortlist + one-pagers | Pipeline of new coverage / pitches |
| Thesis tracker | Living scorecard + update log | Position rationale integrity over time |

### Accuracy / compliance bar (non-negotiables)
- **Numbers match primary sources:** company releases, 10-Q/10-K, call transcripts; beat/miss uses **pre-print** consensus with as-of date.  
- **Estimates vs actuals labeled** (A/E); GAAP vs adjusted called out; share count/dilution handled for EPS.  
- **Citations with dates (and links where public)** on figures, tables, and key claims; subscription data noted as such.  
- **Freshness:** never rely on model training cutoffs for “latest earnings”; verify release/transcript dates.  
- **Rating / PT / thesis consistency** across model, note, and tracker; material estimate moves usually force PT revisit.  
- **Compliance culture (sell-side):** no use of MNPI; research independence from banking where applicable; clear investment **opinion vs fact**; distribution-appropriate disclaimers. Pack skills barely mention this layer today (gap).  
- **Timeliness:** post-earnings product within ~24–48 hours or labeled delayed; morning notes timed for open.  
- **Falsifiable theses** with explicit invalidation triggers (not narrative only).

### What “good skill design” means for this pack
Skills should map to the real product cadence above; enforce data freshness and citation for anything that becomes client-facing prose; hand off cleanly (preview → print → model → thesis); and for modeling, either own IB-grade Excel standards or **delegate to** `financial-analysis` skills (`dcf-model`, `comps-analysis`, `xlsx-author`, `audit-xls`).

---

## Score table

| Skill | T | W | B | R | C | Overall | Clean? |
|-------|---|---|---|---|---|---------|--------|
| catalyst-calendar | 4 | 4 | 3 | 2 | 3 | **3.2** | No |
| earnings-analysis | 5 | 5 | 5 | 5 | 4 | **4.8** | Yes |
| earnings-preview | 4 | 4 | 3 | 2 | 3 | **3.2** | No |
| idea-generation | 4 | 4 | 3 | 2 | 3 | **3.2** | No |
| initiating-coverage | 3 | 4 | 3 | 5 | 3 | **3.6** | No |
| model-update | 4 | 4 | 3 | 2 | 3 | **3.2** | No |
| morning-note | 5 | 4 | 3 | 2 | 3 | **3.4** | No |
| sector-overview | 4 | 4 | 3 | 2 | 3 | **3.2** | No |
| thesis-tracker | 4 | 4 | 3 | 2 | 3 | **3.2** | No |

**Pack average overall:** ~3.4  
**Clean skills:** 1/9 (`earnings-analysis` only)

---

## Clean skill (light notes)

### earnings-analysis — 4.8
Gold standard in this pack. Frontmatter + **When to Use / Do NOT use**, institutional page/word/table/chart budgets, mandatory citations with clickable hyperlinks, training-data freshness protocol, five-phase workflow, and three solid references (`workflow.md`, `report-structure.md`, `best-practices.md`). Explicit contrast table vs initiation length/scope.

**Light polish only:**
- Explicit handoff to `model-update` / `thesis-tracker` after delivery (today optional XLS is buried).  
- Clarify flash/quick-take vs full 8–12 pp path (points to “different format” but does not name `morning-note`).  
- Consistency: C=4 mainly because peer lightweight skills do not share its citation/freshness discipline (pack-level issue, not a defect of this skill).

---

## Per-skill notes (non-clean)

### catalyst-calendar — 3.2
**Strengths:** Clear universe/horizon framing; rich catalyst taxonomy (earnings, corporate, industry, macro); calendar table + weekly preview format matching desk practice; practical notes on date drift, pre-announce risk, conference attendance, archival outcomes.

**Gaps vs role baseline:**
- **R=2:** No `references/` (sample calendar workbook schema, recurring-event templates, impact rubric definitions).  
- **B=3:** No “verify against IR/Bloomberg before distribution” as a hard step; no compliance note on positioning language (“Our Positioning Long/Short”) as research opinion vs trade instruction; no MNPI caution for non-public event intel.  
- **C=3:** Duplicates catalyst tables inside `thesis-tracker` without cross-skill ownership rules; “Optional: Google Calendar” is aspirational with no integration path.

**Role fit:** Correct artifact class for associates; needs executable data discipline and pack-level calendar-of-record ownership.

---

### earnings-preview — 3.2
**Strengths:** Pre-print workflow matches real desk prep; sector-specific operating metrics; bull/base/bear with stock-reaction framing; catalyst checklist; consensus date + whisper + options-implied move notes.

**Gaps:**
- **R=2:** No templates for preview one-pager, no historical reaction methodology reference, no link pack to post-print skills.  
- **B=3:** No When-not-use (vs morning-note or full earnings-analysis); no hard “do not use post-release consensus” rule for scenario setup; silent on whisper-number sourcing ethics/limits.  
- **W:** Trading-setup / implied-move step is good but underspecified (how to fetch IV, what to do if unavailable).  
- Missing explicit bridge: *after print → earnings-analysis + model-update*.

---

### idea-generation — 3.2
**Strengths:** Parameter intake (direction, style, geo, theme); multi-style screen frameworks including shorts and special sits; thematic value-chain sweep; idea card with thesis/risks/next steps; honest “screens surface candidates, not conclusions.”

**Gaps:**
- **R=2 / executability:** Screens are criterion lists only—no data source hierarchy (MCP, web, user book), no runnable screen recipe, no ownership/crowding data procedure. Fixed thresholds (e.g. FCF yield >5%, P/B <1.5x) are one-size-fits-all and can mislead by sector.  
- **B=3:** No compliance framing for short ideas / market rumors; no “not a recommendation / for internal idea pipeline” boundary; no anti-hallucination rule when screen data is unavailable (risk of inventing metrics).  
- **C=3:** Does not hand off winners to `initiating-coverage`, `thesis-tracker`, or FA comps/DCF skills; command is `/screen` but skill does not document command pairing.

---

### initiating-coverage — 3.6
**Strengths:** Deepest structural skill after earnings-analysis: five-task pipeline, strict prerequisites, deliverable-only policy, rich `references/task1–5` + valuation methodologies + assets (template, quality checklist). Matches institutional initiation artifact (long report + model + charts). Word/page/chart minimums and “no shortcuts” culture align with accuracy bar for franchise product.

**Gaps (why not clean):**
- **T=3:** Frontmatter description is pipeline-oriented, not natural-language trigger rich; heavy “ask which task” UX can frustrate “just write an initiation” users (documented intentionally, but still a product friction).  
- **B=3:** Almost **zero sell-side compliance** (disclaimers, rating scale definitions, independence). “JPMorgan/Goldman/Morgan Stanley format” claims without firm-specific rating taxonomy.  
- **Internal inconsistencies (hurt W/C):**
  - Task 2 / refs: **6 essential model tabs** vs `assets/quality-checklist.md`: **15+ tabs**.  
  - Font: SKILL default **Times New Roman** vs checklist/template/task5: **Calibri/Arial**.  
  - File tree example shows Task3 valuation as **`.pdf`** while deliverable is **`.md`**.  
  - Task 4 dependency prose varies (needs Task 1 for company charts vs older “Tasks 2 & 3” notes).  
- **C=3:** Does not reuse `financial-analysis` `dcf-model` / `comps-analysis` / `xlsx-author` / `audit-xls` (parallel standards diverge: FA skill has formula-over-hardcode + `recalc.py`; initiation task2 is structure-heavy but thinner on live-formula discipline).  
- **R=5** is real, but conflicting checklist content reduces effective quality of those references.

---

### model-update — 3.2
**Strengths:** Trigger taxonomy (earnings, guidance, macro, event); actuals plug table; forward estimate revision; valuation/PT decision; consensus compare; GAAP vs adjusted / share-count notes—core associate workflow after a print.

**Gaps:**
- **R=2:** No model schema, no worked example, no validation script, no link to FA modeling stack.  
- **B=3:** Soft on “if no existing model, stop and build via initiating-coverage / dcf-model first”; no mandatory cross-check that DOCX note numbers match Excel after update; no versioning/audit trail pattern for revision history (mentioned as good practice, not required).  
- **W:** Valuation methods table assumes DCF + multiples exist; silent if user only has a simple estimate sheet.  
- **C=3:** Peer of lightweight ER skills; orphaned from `earnings-analysis` optional XLS path and from `xlsx-author` color/formula conventions.

---

### morning-note — 3.4
**Strengths:** Best trigger fit for daily ritual; 2-minute readability constraint; opinionated “Top Call” structure; earnings quick-take table; explicit “no news is valid”; credibility culture (“if wrong, own it”). Matches 7am meeting artifact well.

**Gaps:**
- **R=2:** No sample notes, sector-specific variants, or distribution checklist.  
- **B=3:** No MNPI / selective-disclosure / communication-policy boundary; no rule that material rating/PT changes may require full note or compliance review before morning blast; thin accuracy protocol (where numbers come from).  
- **C=3:** Overlap with post-earnings flash vs full `earnings-analysis` not formalized (when is a morning note enough?).

---

### sector-overview — 3.2
**Strengths:** Scope/depth/angle intake; TAM + structure + trends; competitor profile table; valuation context; investment implications; source-TAM and freshness notes.

**Gaps:**
- **R=2:** No report/deck outline with page budgets, no chart catalog, no peer-matrix template files.  
- **B=3:** Depth “5–10 vs 20–30 pages” optional without enforcement; DOCX vs PPTX choice vague (no `pptx-author` handoff); no citation mandate comparable to earnings-analysis despite client-facing use.  
- **C=3:** Competitive section overlaps FA `competitive-analysis` / `comps-analysis` without reuse; thematic path overlaps `idea-generation` without handoff.

---

### thesis-tracker — 3.2
**Strengths:** Pillars + risks + catalysts + stop-loss; update log with conviction; scorecard; falsifiability and disconfirming-evidence culture—aligned with professional portfolio hygiene (sell-side coverage theses and buy-side books).

**Gaps:**
- **R=2:** No schema (JSON/YAML/md frontmatter), no multi-name portfolio template, no example filled scorecard.  
- **B=3:** “Store thesis data in a structured format so it can be referenced across sessions” is aspirational—no storage contract, no path convention, no conflict resolution when user has multiple versions.  
- **C=3:** Catalyst sub-table duplicates `catalyst-calendar`; no automatic update step after `earnings-analysis` or `model-update`.  
- Weak multi-position review workflow beyond a single sentence.

---

## Candidate systemic issues for this pack

1. **Quality bifurcation (P1):** Two institutional skills (`earnings-analysis`, `initiating-coverage`) vs seven lightweight “Workflow + Important Notes only” skills. Same vertical, wildly different accuracy bars.  
2. **Citation & freshness not pack-wide (P1):** Only earnings-analysis (and initiation task prose) enforce dated sources and anti-training-data rules. Previews, morning notes, sector pieces, idea screens can invent or stale numbers.  
3. **Missing compliance layer (P1):** Across all nine skills, essentially no disclaimers, rating-scale definitions, MNPI, research independence, or “opinion vs fact” rules—non-negotiable for real sell-side ER.  
4. **No cross-skill orchestration map (P1):** Real cycle is preview → print → model → thesis → calendar. Skills are siloed; commands exist 1:1 but skills do not name successors/predecessors.  
5. **Modeling stack fork (P1/P2):** Initiation/model-update invent Excel standards in-vertical while `financial-analysis` already owns DCF, comps, xlsx-author, audit-xls with scripts—duplicate effort and inconsistent quality.  
6. **initiating-coverage internal contradiction (P0 within that skill):** 6 tabs vs 15+ tabs; Times vs Calibri; PDF vs md in file tree—agents will fail quality checklists inconsistently.  
7. **References desert for 7 skills (P2):** R=2 across lightweight set; no assets/schemas/examples.  
8. **No scripts anywhere in ER pack (P2):** Contrast FA `dcf-model` / `ib-check-deck` scripts. ER is pure prose SOP.  
9. **Persistence underspecified (P2):** Thesis tracker, catalyst calendar, coverage universe lack durable file contracts for multi-session work.  
10. **“Firm format” marketing without specification (P3):** JPM/GS/MS name-drops without rating taxonomies, page-1 house styles, or disclosure blocks—overclaims institutional fidelity.

---

## Concrete fix recommendations (not applied)

### Pack-level
1. Add a vertical **README or `_pack-conventions.md`** (or skill-shared reference) covering: citation standard, data freshness checklist, rating/PT vocabulary, disclaimer boilerplate, and skill handoff graph.  
2. Add **When to use / When not to use** blocks to every lightweight skill, mirroring `earnings-analysis`.  
3. Document the **canonical cycle:** `earnings-preview` → (`morning-note` flash) → `earnings-analysis` → `model-update` → `thesis-tracker` (+ `catalyst-calendar` maintenance).  
4. **Wire modeling** to FA: `initiating-coverage` Task 2/3 and `model-update` should require or strongly recommend `xlsx-author` + `dcf-model` / `comps-analysis` / `audit-xls` patterns (formulas, blue inputs, cell comments, recalc).  
5. Lift **earnings-analysis citation + freshness protocol** into a shared reference consumed by morning-note, earnings-preview, sector-overview, idea-generation.  
6. Define **file conventions** for multi-session artifacts, e.g. `coverage/{ticker}/thesis.md`, `coverage/calendar.xlsx`, `coverage/{ticker}/model.xlsx`.

### Per skill (priority-ish)
7. **initiating-coverage (P0):** Resolve tab-count (pick 6-core vs 15+ full book and align Task2 + quality-checklist); unify font policy; fix Task3 file-tree extension; align Task4 prerequisite text; soften or automate one-task UX for managed-agent contexts; drop or qualify bank-name claims; add disclosure section to Task5.  
8. **earnings-analysis (P3 polish):** Name `morning-note` for flash path; post-delivery prompt to run `model-update` + `thesis-tracker`.  
9. **model-update (P1):** Add prerequisite gate (existing model path); output contract (delta summary + versioned xlsx); require number reconcile to source release; optional `audit-xls` pass.  
10. **earnings-preview (P2):** Add one-page template asset; historical reaction method; explicit “stop if post-print—use earnings-analysis”; data source list for consensus/IV.  
11. **morning-note (P2):** Sample notes asset; materiality threshold for escalating to full earnings note; compliance line on distribution.  
12. **catalyst-calendar (P2):** Excel column schema asset; impact scoring rubric; ownership vs thesis-tracker catalysts (“coverage calendar is master; thesis embeds subset”).  
13. **thesis-tracker (P2):** YAML/md schema + example; portfolio review workflow; hooks after model/earnings updates.  
14. **idea-generation (P2):** Data-source priority; sector-relative thresholds; anti-fabrication rule when metrics unavailable; handoff to initiation/thesis for advanced ideas.  
15. **sector-overview (P2):** Choose default artifact (DOCX vs PPTX) with page budget; mandatory sources section; optional call into `comps-analysis` / `competitive-analysis`.  
16. **All lightweight skills (P2):** Raise R by adding at least one of: `references/workflow.md`, output template asset, or quality checklist—target overall ≥4.0 without changing product intent.

### Out of scope reminders
- Do not rewrite skills in this research ticket.  
- Agent-plugin skill copies are sync targets (`scripts/sync-agent-skills.py`); edit vertical sources only when fixes are applied later.  
- Partner MCP readiness not scored here.

---

## Sources consulted (this review)
- Pack skills under `plugins/vertical-plugins/equity-research/skills/*/SKILL.md` and nested `references/` / `assets/` for earnings-analysis and initiating-coverage.  
- Vertical commands under `plugins/vertical-plugins/equity-research/commands/`.  
- Repo `Claude.md` (vertical source-of-truth, sync workflow).  
- Peer modeling skill `plugins/vertical-plugins/financial-analysis/skills/dcf-model/SKILL.md` (shared-skill consistency lens).  
- Industry practice baseline: sell-side associate/analyst product cadence, initiation vs earnings note economics, estimate/citation/timeliness norms (domain knowledge cross-checked against skill-stated institutional standards).
