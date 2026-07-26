# 02 — Financial analysis skill pack review

**Pack:** `plugins/vertical-plugins/financial-analysis/skills/`  
**Skills reviewed:** 13  
**Date:** 2026-07-24  
**Method:** Role baseline first; score Triggers / Workflow / Boundaries / References-scripts / Consistency (1–5); overall = average to one decimal. Clean bar: overall ≥ 4.0 **and** no dimension ≤ 2.

---

## Role baseline (IB / PE / ER modeling analyst + presentation ops)

### Primary job roles

| Role | Typical artifacts | Non-negotiables |
|------|-------------------|-----------------|
| **IB / ER financial modeling associate** | 3-statement models, DCF, trading comps, supporting schedules | Formulas over hardcodes; BS balances every period; CF ending cash = BS cash; RE rolls; blue input / black formula / green cross-sheet convention; source comments on every hardcoded input; units ($mm) consistent; scenario toggle where material |
| **PE associate / deal ops** | LBO templates, sources & uses, debt schedule, IRR/MOIC, entry/exit sensitivity | Template fidelity; S&U balance; cash sweep waterfall; beginning-balance interest to break circs; returns cash-flow signs; odd-dimension sensitivity with base-case center cell |
| **Presentation / pitch ops** | Pitch decks, board books, quarterly refreshes, QC reports | Number consistency across slides; narrative–data alignment; IB register (no casual language); source footnotes; preserve existing template formatting on refresh |

### Workflow shape these skills must support

1. **Scope & inputs** — confirm template vs build, data sources (MCP > filings > estimates), peer set, audience.
2. **Structure first** — tabs/sections/layout locked before formulas.
3. **Section checkpoints** — never end-to-end dump; verify IS → BS → CF (or S&U → OpModel → Debt → Returns) with user.
4. **Integrity** — master checks (balance, cash tie, RE, no `#REF!`/`#DIV/0!`); recalc before delivery when headless.
5. **Documentation** — cell comments / notes with source, period, methodology.
6. **Presentation ops** — plan before edit; flag derived numbers; QC before client send.

### Accuracy / compliance bar

- Institutional data hierarchy when available (MCP / FactSet-class > EDGAR > web).
- No silent hardcodes in projection or multiple cells.
- Client-ready formatting: minimal blue/grey fills; professional number formats; borders where IB models expect them.
- Read-only QC skills must not mutate decks without request.

### Secondary consistency lenses

- Repo progressive-disclosure norms (`skill-creator`: SKILL body lean; details in `references/`; scripts for fragile ops).
- Shared-skill families: `xlsx-author`, `audit-xls`, `pptx-author` (and peer `clean-data-xls`) used across many agent plugins — family drift has high blast radius.
- In-pack modeling peers should share: Office JS vs openpyxl env fork, formulas-over-hardcodes, blue/black/green fonts, blue/grey fills, step-by-step user verify.

---

## Score table

| Skill | Triggers | Workflow | Boundaries | Refs/scripts | Consistency | Overall | Clean bar |
|-------|:--------:|:--------:|:----------:|:------------:|:-----------:|:-------:|:---------:|
| 3-statement-model | 5 | 5 | 4 | 5 | 4 | **4.6** | Pass |
| audit-xls | 5 | 5 | 4 | 3 | 5 | **4.4** | Pass |
| clean-data-xls | 5 | 5 | 4 | 3 | 4 | **4.2** | Pass |
| competitive-analysis | 5 | 5 | 4 | 4 | 4 | **4.4** | Pass |
| comps-analysis | 4 | 4 | 4 | **2** | 3 | **3.4** | **Fail** |
| dcf-model | 5 | 5 | 4 | 3 | **2** | **3.8** | **Fail** |
| deck-refresh | 5 | 5 | 5 | 3 | 5 | **4.6** | Pass |
| ib-check-deck | 5 | 5 | 5 | 5 | 5 | **5.0** | Pass |
| lbo-model | 4 | 4 | 4 | **1** | 3 | **3.2** | **Fail** |
| ppt-template-creator | 5 | 5 | 5 | 3 | 4 | **4.4** | Pass |
| pptx-author | 4 | 3 | 5 | **2** | 3 | **3.4** | **Fail** |
| skill-creator | 5 | 5 | 4 | 5 | 3 | **4.4** | Pass |
| xlsx-author | 4 | 3 | 5 | **2** | 4 | **3.6** | **Fail** |

**Pack summary:** 8 / 13 pass clean bar. Mean overall ≈ **4.1**. Weakest cluster is **missing/broken assets** (LBO, comps) and **shared headless authors** (xlsx/pptx) plus **DCF consistency/bloat**.

---

## Per-skill notes

### Pass (light notes)

**3-statement-model (4.6)** — Strong template-completion skill: env fork, formulas-over-hardcodes, statement-by-statement user gates, integrity matrix, optional margin/credit/scenario sections. References (`formulas.md`, `formatting.md`, `sec-filings.md`) are substantial and role-aligned. Minor: `formatting.md` allows green/yellow/red check styling while body insists on “blues & greys only” for fills — mild internal tension. Depends on external `recalc.py` (not bundled).

**audit-xls (4.4)** — Best-in-class shared QA skill. Scope ladder (selection/sheet/model), model-type bug lists (DCF/LBO/merger/3-stmt), severity report, “report first / fix on request.” No bundled script (acceptable; pure procedure). High blast radius — keep as family canonical.

**clean-data-xls (4.2)** — Clear prep skill: profile → propose → confirm → formula helpers over in-place overwrite. Matches modeling-analyst data hygiene needs. Could later add a small script for common transforms; not required for pass.

**competitive-analysis (4.4)** — Excellent deck workflow: scope with `ask_user_question`, outline approval gate, source hierarchy, comparability rules, moat synthesis, investment optional path. `frameworks.md` is thin (axis pairs only) but correctly progressive. Design rules align with presentation-ops baseline.

**deck-refresh (4.6)** — Exemplar presentation-ops skill: mapping intake, variant hunting ($M vs $0.485B), approval gate, flag derived YoY/share, surgical edits, post-report. Boundaries section is crisp.

**ib-check-deck (5.0)** — Highest quality in pack. Four-dimension QC; `extract_numbers.py --check` with unit normalization; `report-format.md` + `ib-terminology.md`; read-only boundary explicit. Matches “final pass before client send” baseline.

**ppt-template-creator (4.4)** — Meta skill correctly scoped (“creates SKILLS, not presentations”); strong placeholder/content-area measurement guidance; self-contained generated SKILL template. Depends on `skill-creator` for init/package.

**skill-creator (4.4)** — Solid meta tooling (init/package/validate scripts, progressive disclosure doctrine). Consistency ding only because it lives in an FSI vertical and its own “&lt;500 line body” rule is violated by sibling skills (esp. DCF/comps) it does not enforce.

---

### Fail clean bar (deeper write-up)

#### comps-analysis — overall 3.4 (Refs/scripts = 2)

**What works:** Institutional intent (operating metrics + multiples + quartiles), MCP-first data hierarchy, formulas-over-hardcodes, step checkpoints, industry metric frameworks, “5–10 rule,” notes/methodology requirements, clear “Not ideal for” list in description.

**Gaps vs baseline:**

1. **Broken reference asset:** SKILL cites `examples/comps_example.xlsx` as structural guide — **directory/file does not exist** under the skill. That is a hard failure for References/scripts.
2. **Length / progressive disclosure:** ~661-line monolithic body (layout ASCII art, formula encyclopedia, human time estimates like “Gather data 60–90 minutes”). Violates pack’s own skill-creator norms; hard for agents to hold as procedure.
3. **Formatting defaults:** Times New Roman as default is off-market for many modern IB/tech shops (template-first is stated, but default still steers).
4. **Data-source policy tension:** Forbids web as primary (good for institutional comps) while sibling `dcf-model` allows web for prices/beta — agents may confuse policies across valuation pack.

**Fix recs:** Ship or drop the example xlsx; split Section 8–11 into `references/`; align font default with 3-statement/DCF blue-grey system; add one-liner cross-link to `audit-xls` for post-build model scope.

#### dcf-model — overall 3.8 (Consistency = 2)

**What works:** Best substantive DCF methodology in pack — CAPM/WACC, mid-year convention, unlevered FCF build, TV sanity, EV→equity bridge, Bear/Base/Bull + consolidation INDEX pattern, 5×5 centered sensitivity, cell-comment mandate, Office JS merged-cell pitfall, TROUBLESHOOTING.md, `validate_dcf.py` intent.

**Gaps vs baseline:**

1. **Size:** ~1,263-line SKILL.md — far above progressive-disclosure target; correct/wrong patterns duplicated with structure sections.
2. **Color convention contradiction:** Body mandates blue font for inputs and minimal blue/grey fills; WACC sheet structure still labels inputs as **“[Yellow input]”** (legacy). Agents will paint yellow.
3. **Validator vs architecture:** SKILL requires sensitivity tables **at bottom of DCF sheet** (two sheets: DCF + WACC). `scripts/validate_dcf.py` recommends/looks for a separate **`Sensitivity` sheet** — false warnings or wrong mental model.
4. **External `xlsx` / `recalc.py` dependency:** Heavily couples to a non-packaged “xlsx skill” path; headless path should explicitly compose with in-pack `xlsx-author` or document where `recalc.py` lives in this repo/runtime.
5. **validate_dcf not wired into delivery checklist** as first-class (checklist emphasizes `recalc.py` only).

**Fix recs:** Split methodology / correct_patterns / common_mistakes / sheet layouts into `references/`; replace Yellow with blue/grey; fix validator required sheets to `['DCF','WACC']` and scan DCF bottom for sensitivity; one composition paragraph with `xlsx-author` + `audit-xls`.

#### lbo-model — overall 3.2 (Refs/scripts = 1)

**What works:** Template-first discipline, Office JS vs Python fork, formulas-over-hardcodes, section-by-section user gates (S&U → OpModel → Debt → Returns → Sensitivity), common problem areas (plug, circs, sweep, IRR signs, odd sensitivity grids), verification checklist.

**Gaps vs baseline:**

1. **Critical missing asset:** Instructs “Copy `examples/LBO_Model.xlsx`” when no user template — **examples/ does not exist**. Skill cannot fulfill its default path.
2. **Non-portable recalc path:** `python /mnt/skills/public/xlsx/recalc.py model.xlsx` is Claude-runtime-specific, not this repository.
3. **Color family drift:** Introduces **purple (same-tab links)** in addition to blue/black/green. Peers (`xlsx-author`, `3-statement-model`, `dcf-model`, `audit-xls`) use three-color fonts only. Shared-family inconsistency.
4. **Less domain depth than DCF:** Relies on template labels + “standard practice” rather than explicit PE mechanics (sources/uses taxonomy, PIK, management rollover, preferred, sponsor fees). Acceptable if template ships; without template, underspecified for PE associate baseline.
5. **Frontmatter quirk:** Body opens with an extra `---` horizontal rule immediately after YAML — harmless but sloppy vs peers.

**Fix recs:** Add `examples/LBO_Model.xlsx` (or remove “standard template” path and require user template); portable recalc instruction; align font colors with pack (drop purple or document as LBO-template-only override); optional `references/lbo-mechanics.md` for when template is thin.

#### pptx-author — overall 3.4 (Refs/scripts = 2, Workflow = 3)

**Intent:** Headless CMA fallback — write `./out/<name>.pptx` via `python-pptx` when live PowerPoint MCP unavailable.

**Gaps vs presentation-ops baseline:**

1. **Stub workflow:** No slide QC, no number-trace checklist beyond a one-liner, no IB language/visual rules (points at non-pack `pitch-deck` skill).
2. **Template path assumption:** `./templates/firm-template.pptx` not guaranteed in vertical.
3. **Family thinness:** Shared across pitch/market-research/meeting-prep agents — low depth means every headless deck run reinvents standards that `competitive-analysis` / `deck-refresh` / `ib-check-deck` already encode for live mode.

**Fix recs:** Add short mandatory checklist (one idea/slide, source footnotes, units, call `ib-check-deck` patterns or “run visual verify”); document composition with competitive-analysis / deck-refresh content skills; keep file thin but raise floor for client-ready headless output.

#### xlsx-author — overall 3.6 (Refs/scripts = 2, Workflow = 3)

**Intent:** Headless CMA fallback for `.xlsx` under `./out/`; mirrors `audit-xls` color rules in one paragraph.

**Gaps vs modeling baseline:**

1. **Stub only:** No Checks-tab pattern detail, no recalc step, no pointer to `dcf-model` / `3-statement-model` / `lbo-model` / `comps-analysis` as content skills that should own domain structure.
2. **Shared-family blast radius:** Copied into model-builder, valuation-reviewer, statement-auditor, earnings-reviewer, month-end-closer, gl-reconciler, kyc-screener, pitch-agent, etc. Thinness is amplified.
3. **“mirror audit-xls”** but does not mention purple-free vs LBO purple, or composition with `audit-xls` post-build.

**Fix recs:** Expand slightly (not to DCF size): output contract + blue/black/green + Checks tab skeleton + “after build, run audit-xls model scope” + “domain structure from 3-statement/dcf/lbo/comps skills” + recalc when available. Keep under ~80–100 lines.

---

## Shared-skill family flags (systemic)

| Family skill | Canonical path | Agent-plugin copies (sample) | Issues |
|--------------|----------------|------------------------------|--------|
| **xlsx-author** | `financial-analysis/skills/xlsx-author` | model-builder, valuation-reviewer, statement-auditor, earnings-reviewer, month-end-closer, gl-reconciler, kyc-screener, pitch-agent | Stub; no Checks/recalc/composition; high blast if left weak |
| **audit-xls** | `financial-analysis/skills/audit-xls` | model-builder, statement-auditor, earnings-reviewer, month-end-closer, gl-reconciler, pitch-agent, valuation-reviewer | Strong; keep canonical; ensure sync-agent-skills stays green |
| **pptx-author** | `financial-analysis/skills/pptx-author` | pitch-agent, market-researcher, meeting-prep-agent | Stub; no QC floor; mirrors non-local “pitch-deck” |
| **skill-creator** | `financial-analysis/skills/skill-creator` | (meta; also used by ppt-template-creator) | Pack placement is odd for pure FSI consumers; quality OK |
| **clean-data-xls** | this vertical only (not widely copied) | — | Pass; optional future shared utility |

**Cross-family consistency problems (candidates for synthesis P1):**

1. **Font color scheme split:** LBO purple same-tab vs everyone else blue/black/green only.
2. **Fill vs check colors:** “minimal blues/greys” vs formatting.md / credit thresholds / DCF yellow labels.
3. **recalc.py location:** variously `recalc.py`, `python recalc.py`, `/mnt/skills/public/xlsx/recalc.py`, “from the xlsx skill” — no single portable contract for this monorepo.
4. **Headless vs live:** Strong live skills (Office JS / MCP) vs thin `*-author` headless twins — capability gap for CMA cookbooks.
5. **Missing examples/** for template-dependent skills (LBO, comps) breaks default workflows.

---

## Systemic candidates (for ticket 11 synthesis)

| ID | Theme | Severity hint | Skills |
|----|--------|---------------|--------|
| S1 | Missing/broken `examples/` assets | P0 | lbo-model, comps-analysis |
| S2 | Headless author stubs under-spec vs live peers | P1 | xlsx-author, pptx-author |
| S3 | DCF monolith + internal contradictions (Yellow, Sensitivity sheet) | P1 | dcf-model (+ validate_dcf.py) |
| S4 | Color convention drift (purple / yellow / “no accent” vs RAG checks) | P1 | lbo-model, dcf-model, 3-statement formatting.md |
| S5 | Non-portable / external recalc + “xlsx skill” coupling | P1 | dcf-model, lbo-model, 3-statement-model |
| S6 | Progressive-disclosure violations (bodies ≫ 500 lines) | P2 | dcf-model, comps-analysis |
| S7 | Data-source policy inconsistency (web OK in DCF, forbidden primary in comps) | P2 | dcf-model, comps-analysis |
| S8 | Meta skills in FSI vertical (skill-creator, ppt-template-creator) | P3 | clarity of packaging only |

---

## Fix recommendations (prioritized, no rewrites applied)

### P0 — broken defaults

1. **lbo-model:** Provide `examples/LBO_Model.xlsx` or remove standard-template path and require user attachment; fix recalc path.
2. **comps-analysis:** Provide `examples/comps_example.xlsx` or delete the reference.

### P1 — high blast / consistency

3. **xlsx-author / pptx-author:** Raise workflow floor (checks, composition, QC); these are multi-agent shared.
4. **dcf-model:** Fix Yellow→blue; align `validate_dcf.py` with 2-sheet architecture; split references out of SKILL.md.
5. **Pack-wide:** Single **color convention** note (blue/black/green fonts; blue/grey fills; RAG only for check status cells) and reconcile LBO purple.
6. **Pack-wide:** Document **recalc contract** (where script lives in Cowork vs CMA vs this repo).

### P2 — usable but gappy

7. **comps-analysis / dcf-model:** Progressive disclosure splits; human time estimates → agent steps.
8. Harmonize MCP/web source hierarchy language across valuation skills.
9. **dcf-model:** Wire `validate_dcf.py` into delivery checklist after recalc.

### P3 — polish

10. **skill-creator** location note or cross-vertical reuse policy.
11. **3-statement formatting.md** vs “no green/yellow fills” wording.
12. **lbo-model** frontmatter double-`---` cleanup; richer PE mechanics reference if templates stay optional.

---

## Paths reviewed

| Skill | Primary | Bundled extras |
|-------|---------|----------------|
| 3-statement-model | `.../3-statement-model/SKILL.md` | `references/{formulas,formatting,sec-filings}.md` |
| audit-xls | `.../audit-xls/SKILL.md` | — |
| clean-data-xls | `.../clean-data-xls/SKILL.md` | — |
| competitive-analysis | `.../competitive-analysis/SKILL.md` | `references/{frameworks,schemas}.md` |
| comps-analysis | `.../comps-analysis/SKILL.md` | **missing** `examples/comps_example.xlsx` |
| dcf-model | `.../dcf-model/SKILL.md` | `TROUBLESHOOTING.md`, `scripts/validate_dcf.py`, `requirements.txt` |
| deck-refresh | `.../deck-refresh/SKILL.md` | — |
| ib-check-deck | `.../ib-check-deck/SKILL.md` | `scripts/extract_numbers.py`, `references/{report-format,ib-terminology}.md` |
| lbo-model | `.../lbo-model/SKILL.md` | **missing** `examples/LBO_Model.xlsx` |
| ppt-template-creator | `.../ppt-template-creator/SKILL.md` | — |
| pptx-author | `.../pptx-author/SKILL.md` | — |
| skill-creator | `.../skill-creator/SKILL.md` | `scripts/*`, `references/*`, `LICENSE.txt` |
| xlsx-author | `.../xlsx-author/SKILL.md` | — |

Absolute pack root:  
`/Users/aneenaananth/projects/financial-services/plugins/vertical-plugins/financial-analysis/skills/`
