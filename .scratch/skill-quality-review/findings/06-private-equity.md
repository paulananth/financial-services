# 06 — Private equity skill pack review

**Path:** `plugins/vertical-plugins/private-equity/skills/`  
**Skills (10):** ai-readiness, dd-checklist, dd-meeting-prep, deal-screening, deal-sourcing, ic-memo, portfolio-monitoring, returns-analysis, unit-economics, value-creation-plan  
**Reviewer lens:** PE associate, operating partner, portfolio ops  
**Clean bar:** overall ≥ 4.0 **and** no dimension ≤ 2  
**Scoring:** Triggers, Workflow, Boundaries, References/scripts, Consistency — each 1–5; overall = mean to one decimal  
**Scope note:** Findings and recommendations only; no skill rewrites in this ticket.

---

## Role baseline

### Primary roles

| Role | Core job | Typical artifacts | Non-negotiables |
|------|----------|-------------------|-----------------|
| **PE associate / deal team** | Source → screen → diligence → IC → close | Teaser/CIM screens, DD trackers, meeting prep, unit economics, BOTE / returns exhibits, IC memo | Numbers tie (S&U, bridges, IRR/MOIC); extract vs invent clearly labeled; bull **and** bear; use fund mandate; never send external outreach without approval; deal materials confidential |
| **Operating partner** | Post-close value creation, initiative prioritization | VCP / EBITDA bridge, 100-day plan, KPI owners, cross-portco opportunity ranking (incl. AI/ops) | Rank by dollars and speed, not narrative; management ownership required; hold-period realism; co-develop with mgmt |
| **Portfolio ops / portco monitoring** | Monthly/quarterly pack review, board prep, covenants | Flash/monthly packs, variance tables, RAG flags, covenant status, questions for mgmt | Actual vs budget **and** vs underwriting; don't invent covenant thresholds; escalate reds early; board-ready brevity |

### Lifecycle coverage expected of the pack

```
Source → Screen → DD (checklist + meetings) → Unit econ / Returns → IC memo
                                                      ↓
                              Value creation plan → Portfolio monitoring (+ AI readiness)
```

### Accuracy / compliance bar

- Financial outputs must be formula- or source-backed; assumptions explicit.
- Screening and IC materials must surface red flags, not bury them.
- External actions (email to founders, CRM writes) require explicit user approval.
- Sector-agnostic defaults OK if skill asks for mandate/sector KPIs rather than guessing.
- Full template LBO lives in `financial-analysis` (`lbo-model`); PE pack should do BOTE / IC exhibits and hand off for full models.

### Secondary Consistency lenses

- Repo: YAML frontmatter `name` + rich `description` with triggers; `## Workflow` + `## Important Notes`.
- In-vertical peers: same step depth and output specificity.
- Shared-skill families: `lbo-model`, `xlsx-author`, `comps-analysis` for heavy modeling — PE skills that emit Excel should not contradict those conventions.

---

## Scorecard

| Skill | Triggers | Workflow | Boundaries | Refs/scripts | Consistency | Overall | Clean bar |
|-------|:--------:|:--------:|:----------:|:------------:|:-----------:|:-------:|:---------:|
| ai-readiness | 5 | 5 | 4 | 4 | 5 | **4.6** | Pass |
| dd-checklist | 5 | 4 | 3 | 4 | 5 | **4.2** | Pass |
| dd-meeting-prep | 5 | 5 | 4 | 4 | 5 | **4.6** | Pass |
| deal-screening | 5 | 3 | 3 | 2 | 4 | **3.4** | **Fail** |
| deal-sourcing | 5 | 4 | 5 | 3 | 4 | **4.2** | Pass |
| ic-memo | 5 | 5 | 4 | 3 | 4 | **4.2** | Pass |
| portfolio-monitoring | 5 | 3 | 3 | 2 | 4 | **3.4** | **Fail** |
| returns-analysis | 5 | 5 | 4 | 4 | 3 | **4.2** | Pass |
| unit-economics | 5 | 5 | 4 | 4 | 4 | **4.4** | Pass |
| value-creation-plan | 5 | 5 | 4 | 4 | 5 | **4.6** | Pass |

**Pack summary:** 8/10 skills clear the clean bar. Two fail with overall **3.4** and References/scripts **2**: `deal-screening`, `portfolio-monitoring`. Mean overall across pack ≈ **4.18**. Triggers are uniformly strong; the weak dimensions pack-wide are Boundaries (thin invent/label/confidentiality rules) and Refs/scripts (no `references/` or `scripts/` trees anywhere in this vertical).

---

## Per-skill notes

### Pass band (light notes)

#### ai-readiness — 4.6

Best-in-pack craft for operating partner. Gate questions (data / owner / 30-day pilot), portfolio rank, replays, and explicit “what we’re NOT doing” match how good OPs allocate time. Triggers cover quarterly review and portco prioritization. Minor gap: no structured method for sizing “Est. EBITDA ($)” beyond FTE-hours heuristics; no confidentiality note on multi-portco data. No rewrite required for clean bar.

#### value-creation-plan — 4.6

Full associate/OP artifact: lever map → EBITDA bridge → 100-day plan → KPI owners. Important Notes correctly stress timing realism, mgmt buy-in, initiative-level P&L, Day-1 add-on pipeline. Light polish only: investment-vs-return per lever and risk of double-counting in the bridge.

#### dd-meeting-prep — 4.6

Strong meeting-type branching (mgmt / expert / customer), prioritized question banks, red-flag probe list, one-page prep output. Boundaries (open-ended, don’t lead, 15–20 max) are practical. Slightly odd “body language” note for an LLM copilot; benchmarks step assumes session context without sourcing rules.

#### unit-economics — 4.4

SaaS/recurring PE diligence standard: ARR bridge, cohorts, LTV/CAC, NDR vs gross retention, Rule of 40 / Magic Number benchmarks, revenue quality score. Notes correctly warn that NDR can mask gross churn and that services are not recurring. Scope is intentionally software-weighted (description says so); industrial unit econ is out of band.

#### deal-sourcing — 4.2

Only skill with hard external-action boundary (“Never send emails without explicit user approval”) plus shortlist-before-draft and quality-over-quantity. CRM step assumes Gmail/Slack rather than a real PE CRM (DealCloud, Salesforce, Affinity) — workable as fallback but should not be the only path. Discovery is generic web search; no sector source playbooks.

#### dd-checklist — 4.2

Covers financial / commercial / legal / ops / HR / IT / ESG workstreams with sector add-ons and status + red-flag tracking. Workflow is theme-level (“QoE report”) not a true request-list depth (line-item VDR requests). Boundaries weak on inventing findings and VDR confidentiality. Still clears bar as a living tracker scaffold.

#### ic-memo — 4.2

Classic IC outline (exec summary through recommendation) with tie-out and “don’t minimize risks” notes. Does not name sibling skills as inputs (`returns-analysis`, `value-creation-plan`, `dd-checklist`) or require source tags on figures. Default `.docx` is fine; no sample memo or firm-template placeholders.

#### returns-analysis — 4.2

Right job for BOTE / IC exhibits: entry stack, waterfall attribution, multi-way sensitivities, bull/base/bear, Excel + one-pager. Key Formulas section lifts Refs/scripts. Consistency drag: no handoff to `financial-analysis/lbo-model` for full debt schedule / circular interest / XIRR; IRR note is single-period simplified; attribution formulas are industry-rough, not a full bridge to MOIC. Still clean-bar for the skill’s stated “quick / back of the envelope” role.

---

### Below clean bar (deeper notes)

#### deal-screening — 3.4 (fail)

| Dim | Score | Rationale |
|-----|:-----:|-----------|
| Triggers | 5 | Clear CIM/teaser/triage language and phrases |
| Workflow | 3 | Four short steps; criteria table is empty shell; “3-part assessment” lists four parts; no sector screens, no data-quality checklist, no force-rank when stack of deals |
| Boundaries | 3 | Flags incomplete financials and asks for criteria; no extract-vs-invent rule, no CIM confidentiality, no “do not score without mandate” hard stop |
| Refs/scripts | **2** | No sample screening memo, no example mandate criteria, no sector red-flag library, no scoring rubric beyond empty Pass/Fail cells |
| Consistency | 4 | Matches pack skeleton; thinner than peers (`dd-checklist`, `ic-memo`) for a first-line associate workflow |

**Role-baseline gaps**

- Associates live in high-volume inbound triage. Skill stops at a single one-pager with no prioritization vs other live deals, no “why now / process dynamics,” no banker/process context, and no explicit “missing cell → fail or further diligence” rule.
- Pass/Fail grid does not encode common PE gates (e.g. max customer concentration, min growth, leverage headroom, platform vs add-on fit) even as optional defaults the user can override.
- No instruction to quote CIM page/source for extracted metrics — credibility risk when partners challenge numbers.

**Recommended fix direction (do not implement here)**

- Expand Step 2 with optional default ranges + “criteria unknown → ask, do not invent mandate.”
- Add data-quality checklist (growth vs EBITDA reconciliation, add-backs opacity, stub periods).
- One worked example screening memo under `references/`.
- Fix “3-part” labeling; add multi-deal stack rank output when user pastes several teasers.
- Boundary: never fabricate financials not in materials; mark estimates as estimates.

#### portfolio-monitoring — 3.4 (fail)

| Dim | Score | Rationale |
|-----|:-----:|-----------|
| Triggers | 5 | Monthly packs, “how is X performing,” covenant check, portfolio update |
| Workflow | 3 | Single-company ingest → basic KPIs → fixed 5%/15% RAG → optional multi-period trend; missing underwriting case, portfolio rollup, flash vs board pack, WC/debt detail |
| Boundaries | 3 | Asks for budget/plan and credit terms if missing; no invent-covenant ban; no “label one-time items” |
| Refs/scripts | **2** | No covenant formula definitions, no sector KPI packs, no sample dashboard/board one-pager |
| Consistency | 4 | Name/triggers imply portfolio-level; body is almost entirely single-portco |

**Role-baseline gaps**

- PE portfolio ops always compare **actual vs budget vs underwriting case** (and often prior year). Skill mentions underwriting only in the multi-period trend bullet.
- “Portfolio update” trigger should support multi-company scorecard (who is red, cash runway, leverage, value-creation progress). Body never builds a fund-level view.
- Covenant compliance is a header without calculation guidance (Net Debt / EBITDA definition, add-backs, springing covenants, cure rights).
- No link to `value-creation-plan` KPIs or initiative tracking — associates/OPs review ops metrics alongside financials.
- Fixed 5% / 15% bands ignore sector volatility and materiality (a 6% miss on a high-growth SaaS vs a stable industrial).

**Recommended fix direction (do not implement here)**

- Split outputs: (A) single-company board pack summary, (B) multi-portco portfolio dashboard when ≥2 packages or user asks “portfolio update.”
- Mandate underwriting-case column when available; ask once and persist.
- Add covenant math appendix (`references/covenant-calcs.md`) and sector KPI menus.
- Boundary: never invent covenant thresholds or “deemed” compliance; if credit agreement missing, status = Unknown.
- Cross-link value-creation KPIs and RAG on initiative delivery, not only P&L variance.

---

## Systemic findings (pack-level)

1. **Triggers are the strength.** Every skill has a non-empty, phrase-rich `description` with clear use-when language — no empty-description P0s in this pack.
2. **No `references/` or `scripts/` under any PE skill.** Acceptable for pure meeting-prep / memo scaffolding when body content is dense; material gap for screening templates, covenant math, and any Excel that should share conventions with `lbo-model` / `xlsx-author`.
3. **Boundaries are informal “Important Notes,” not hard gates.** Only `deal-sourcing` has a true external-action ban. Pack-wide missing: extract-vs-invent, confidentiality of CIM/VDR/portco data, “don’t invent mandate/covenants.”
4. **Lifecycle handoffs are implicit.** Skills form a natural funnel (source → screen → DD → returns → IC → VCP → monitor) but none name the next/previous skill. `returns-analysis` does not point at `lbo-model` for full LBOs.
5. **Plugin manifest under-describes the vertical.** `plugins/vertical-plugins/private-equity/.claude-plugin/plugin.json` description is sourcing-only (“company discovery, CRM integration, and founder outreach”) while 8/10 skills are diligence, IC, ops, and monitoring. Marketplace/UX consistency issue at pack level (not a per-skill score, but synthesis-relevant).
6. **`.mcp.json` is empty** (`mcpServers: {}`). Skills that mention MCP (ai-readiness, deal-sourcing CRM) assume user-connected tools; not a skill defect, but connector readiness is “none packaged.”
7. **Modeling dual-track risk.** Thin BOTE (`returns-analysis`) vs deep template LBO (`financial-analysis/lbo-model`) is the right product split **if** documented; currently associates may over-trust BOTE Excel for IC.

---

## Prioritization hints for synthesis (P-band only; no fixes applied)

| Priority hint | Item | Why |
|---------------|------|-----|
| P2 | `deal-screening` deepen workflow + refs | Highest-frequency associate task; below clean bar |
| P2 | `portfolio-monitoring` portfolio rollup + underwriting + covenants | Name/trigger mismatch; below clean bar |
| P3 | Cross-skill handoff one-liners + `lbo-model` pointer in returns | Consistency / dual-track risk |
| P3 | Pack-wide Boundaries block (invent, confidential, approval) | Systemic |
| P3 | plugin.json description align to full lifecycle | Manifest honesty |
| P4 | Sample memo / screening memo / covenant calc `references/` | Depth without changing core workflows |
| P4 | deal-sourcing CRM abstractions beyond Gmail/Slack | Real PE stack |

---

## Method notes

- Scored against PE associate / OP / portfolio-ops baseline first; Consistency secondarily vs in-pack peers and `lbo-model`.
- Refs/scripts scored on **embedded** frameworks when no `references/` tree exists: dense question banks / formulas / bridges can score 3–4; empty shells that need examples score 2.
- No agent-plugin drift check in this ticket (owned by ticket 10).
- No skill text was modified.
