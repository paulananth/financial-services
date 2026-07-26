# 09 — Partner S&P Global skill pack review

**Pack:** `plugins/partner-built/spglobal/skills/`  
**Skills (3):** `earnings-preview-beta`, `funding-digest`, `tear-sheet`  
**Also skimmed:** `plugins/partner-built/spglobal/README.md`, `.mcp.json`, `.claude-plugin/plugin.json`  
**Clean bar:** overall ≥ 4.0 and no dimension ≤ 2  
**Outcome:** All three skills clear the clean bar. Light notes only.

---

## Role baseline

**Domain:** Capital IQ–grounded research and document generation for public/private companies — earnings setup, company profiles, and venture/funding deal flow.

**Primary job roles**

| Role | Typical artifacts | Non-negotiables |
|------|-------------------|-----------------|
| Sell-side / buy-side equity research associate–analyst | Pre-earnings notes, one-page tear sheets, peer valuation, transcript-backed thesis | Correct fiscal labels; consensus vs estimate framing; LTM/NTM nomenclature; no fabricated numbers; source traceability |
| IB / M&A associate | Pitchbook company profiles, trading comps, M&A activity tables | Deal values when known; NTM multiples with peers; private-company handling; page budget |
| Corp Dev | Target profiles, strategic fit, integration risks | Acquirer-lens synthesis; concentration/risk flags; no stale management bios |
| Capital markets / VC coverage / research ops | Weekly funding digests, deal tables with CIQ links | Correct entity resolution; subsidiary/parent awareness; announced vs closed dates |
| Sales / BD (secondary on tear-sheet) | Meeting prep one-pagers | Plain language; conversation starters tied to specific company facts |

**Accuracy / compliance bar**

- Financial facts from S&P Capital IQ / Kensho tooling only — not training knowledge gap-fill.
- AI-generated analysis labeled; outputs are informational, not investment advice.
- Arithmetic and period consistency (fiscal vs calendar; common return base dates).
- Verbatim management quotes when presented as quotes.

**Typical workflow pattern (baseline)**

1. Resolve entity / audience / period.  
2. Pull structured CIQ data (and Kensho grounding where allowed).  
3. Persist intermediates → calculate/validate derived metrics.  
4. Render audience-specific artifact (HTML / DOCX / PPTX) with disclaimer and source path.

### Boundaries note — Kensho / Capital IQ MCP

Hard runtime dependency (not scored as automatic penalty):

- Plugin MCP: `https://kfinance.kensho.com/integrations/mcp` (`.mcp.json` server `spglobal`).
- README requires Capital IQ Pro and/or **S&P Global LLM-ready API (Kensho)** subscription; skills name tools such as `get_*_from_identifiers`, funding round APIs, and Kensho `search`.
- Without authenticated MCP, all three skills fail closed on data collection — by design.
- Connector readiness annotation: **required** for any pack-level synthesis (see map “Not yet specified”).

---

## Score table

Dimensions: **Triggers | Workflow | Boundaries | References/scripts | Consistency** (1–5). Overall = mean to one decimal.

| Skill | Path | Triggers | Workflow | Boundaries | Refs/scripts | Consistency | Overall | Clean? |
|-------|------|:--------:|:--------:|:----------:|:------------:|:-----------:|:-------:|:------:|
| earnings-preview-beta | `.../earnings-preview-beta/` | 4 | 5 | 5 | 5 | 3 | **4.4** | Yes |
| funding-digest | `.../funding-digest/` | 5 | 5 | 4 | 5 | 4 | **4.6** | Yes |
| tear-sheet | `.../tear-sheet/` | 5 | 5 | 5 | 5 | 4 | **4.8** | Yes |

**Pack mean overall:** 4.6

---

## Light notes by skill

### earnings-preview-beta (overall 4.4)

Frontmatter `name: earnings-preview-single`; folder `earnings-preview-beta`. Matches sell-side pre-earnings artifact well: thesis + consensus table + themes/news + figures + hyperlinked appendix.

| Dim | Score | Note |
|-----|:-----:|------|
| Triggers | 4 | Description clear for single-company earnings preview; thinner trigger-phrase list than pack peers / vertical `earnings-preview`. |
| Workflow | 5 | Phases 1–8, write-after-query, calc pass, blocking file verification, mandatory Chart.js helpers — production-grade. |
| Boundaries | 5 | Zero-exception Kensho + `kfinance` only; no web fallback; fiscal-quarter, quote, LTM/NTM, hyperlink, AI-disclaimer rules. |
| Refs/scripts | 5 | `report-template.md` (~1.2k lines): full HTML/CSS, chart helpers, appendix patterns. |
| Consistency | 3 | Name/folder/`-beta` mismatch; README “Earnings Previews” vs skill name; figure renumber noise in template “Implementation Notes”; path/output conventions differ from siblings. |

### funding-digest (overall 4.6)

Weekly one-slide deal-flow PPTX for funding rounds — strong capital-markets / VC-coverage fit. Entity-resolution rules are best-in-pack operational hardening.

| Dim | Score | Note |
|-----|:-----:|------|
| Triggers | 5 | Rich description + When to Use phrases (deal flow, weekly recap, roundup, CM update). |
| Workflow | 5 | Coverage → universe (seeds + competitors) → rounds → highlights → logos → PPTX → markitdown/visual QA. |
| Boundaries | 4 | AI disclaimer; deep error handling (subsidiaries, wrong `role`, empty results). Less absolute “no other tools” banner than earnings-preview; financial claims still CIQ-bound. |
| Refs/scripts | 5 | `references/sector-seeds.md` validated seeds, exclusions, brand→legal aliases + `company_id`s. |
| Consistency | 4 | README markets “Industry Transaction Summaries” (M&A language) while skill is funding-round digest; output paths (`/home/claude/…`) differ from tear-sheet/earnings-preview. |

### tear-sheet (overall 4.8)

Strongest skill in pack. Four audience templates (ER, IB/M&A, Corp Dev, Sales/BD) with page budgets, cut orders, docx factory functions, intermediate SSoT, and integrity rules including no management from training data.

| Dim | Score | Note |
|-----|:-----:|------|
| Triggers | 5 | Tear sheet / one-pager / profile / snapshot + audience language; asks if audience missing. |
| Workflow | 5 | Inputs → audience ref → MCP + write-after-query → derived metrics/validation → file verify → DOCX. Private-company branch. |
| Boundaries | 5 | Data Integrity Rules 1–10; content quality rules; required footer (“not investment advice”). |
| Refs/scripts | 5 | Four reference files + embedded createHeaderBanner/createTable/… enforcement JS. |
| Consistency | 4 | Audience refs use NL query plans vs earnings-preview’s explicit `kfinance` function names; still aligned with bank one-pager convention and shared intermediate-file pattern. |

---

## Pack-level observations (for synthesis)

1. **MCP dependency is structural** — annotate connector readiness; do not treat as quality defect.  
2. **Naming hygiene** — align folder `earnings-preview-beta`, frontmatter `earnings-preview-single`, and README labels; rename README “Industry Transaction Summaries” toward funding/deal-flow digest.  
3. **Within-pack path/convention drift** — intermediate roots and final output locations differ (`/tmp/…`, cwd HTML, `/home/claude/…`, `/mnt/user-data/outputs/`).  
4. **Quality ceiling** — pack is among the strongest reviewed sources for workflow depth and data integrity; Consistency is the main soft spot, not Workflow/Boundaries.  
5. **Scope vs vertical peers** — partner skills are MCP-bound production pipelines; vertical `equity-research/earnings-preview` is lighter and web-oriented — different product, not a direct peer fail.

### Suggested prioritization (no rewrites this ticket)

| Priority | Item |
|----------|------|
| P3 | Normalize earnings-preview name / drop or justify `-beta` |
| P3 | README skill names/descriptions match `funding-digest` / `tear-sheet` / earnings skill |
| P4 | Harmonize intermediate/output path conventions across the three skills |
| P4 | Optional: make funding-digest Boundaries as explicit zero-exception as earnings-preview |

---

## README skim

- Positions skills as starting points; **always verify LLM outputs**.  
- Lists Tearsheets, Industry Transaction Summaries, Earnings Previews — maps roughly to the three skills with naming drift on transactions vs funding-digest.  
- Setup: Claude Cowork plugin + S&P auth; MCP docs link for LLM-ready API.  
- License Apache-2.0; author Kensho Technologies; plugin version `1.0.1`.
