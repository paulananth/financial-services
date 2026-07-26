# 03 — Fund admin skill pack review

**Pack:** `plugins/vertical-plugins/fund-admin/skills/`  
**Skills (6):** accrual-schedule, break-trace, gl-recon, nav-tieout, roll-forward, variance-commentary  
**Clean bar:** overall ≥ 4.0 and no dimension ≤ 2  
**Verdict:** Pack **passes** the clean bar on all six skills. Light notes only (no deep dives).

## Role baseline

**Primary roles:** fund accountant; middle-/back-office recon analyst; controller support (month-end close preparer); statement auditor (pre-distribution LP capital-account check).

**Artifacts they produce**

| Artifact | Skill |
|---|---|
| Accrual schedule + draft JEs (support-cited) | accrual-schedule |
| BS roll-forward with GL ties and foot check | roll-forward |
| Flux commentary (vs prior / budget) for close package | variance-commentary |
| GL ↔ subledger break report + classification | gl-recon |
| Break root-cause with owner / action / clear date | break-trace |
| LP statement vs NAV pack line-level tie-out | nav-tieout |

**Accuracy / compliance bar**

- Every material number has a **support citation** (GL query, document id, NAV-pack field, policy formula).
- **No silent plugs** — unexplained deltas are surfaced, not forced to foot.
- **No ledger posting** from the agent path — drafts and diagnostics only; controller / human posts or distributes.
- Recon at the right grain (position/transaction), with explicit **tolerances** and **break taxonomy**.
- Untrusted outsider extracts (custodian, invoices, generated statements) are treated as **data**, not instructions.
- Month-end package is staged for **sign-off**, not auto-closed.

**Typical workflow**

1. **Daily / period recon:** pull GL + subledger → match → classify breaks → root-cause material ones → exception report for sign-off (`gl-recon` → `break-trace`).
2. **Month-end close:** accruals with draft JEs → roll-forwards → variance commentary → close package (`accrual-schedule`, `roll-forward`, `variance-commentary`).
3. **Investor reporting gate:** recompute LP capital from NAV pack → flag statement mismatches → pass/hold (`nav-tieout`).

**Non-negotiables (score against these)**

- Audit trail on every schedule line.
- JE is draft-only.
- Breaks diagnosed before adjusted; skill does not post.
- NAV pack is SoT for LP statements under test.
- Drivers explained from activity, not restated as percentages.

**Secondary consistency lenses:** compact ops-style skills (`operations/kyc-*`); agent wrappers `gl-reconciler`, `month-end-closer`, `statement-auditor`; shared consumers `audit-xls` / `xlsx-author` (not in this vertical).

## Scorecard

Dimensions: **T**riggers · **W**orkflow · **B**oundaries · **R**eferences/scripts · **C**onsistency · **Avg** (1 decimal).

| Skill | T | W | B | R | C | Avg | Clean? |
|---|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| accrual-schedule | 5 | 4 | 5 | 3 | 5 | **4.4** | yes |
| break-trace | 5 | 5 | 5 | 3 | 5 | **4.6** | yes |
| gl-recon | 5 | 5 | 4 | 3 | 5 | **4.4** | yes |
| nav-tieout | 5 | 5 | 5 | 3 | 5 | **4.6** | yes |
| roll-forward | 5 | 4 | 4 | 3 | 5 | **4.2** | yes |
| variance-commentary | 5 | 4 | 4 | 3 | 5 | **4.2** | yes |

**Pack average overall:** 4.4  
**Weakest dimension pack-wide:** References/scripts (uniform 3) — no `references/`, no `scripts/`, no vertical `.mcp.json`; MCPs named inline only (`internal-gl`, `subledger`, `nav`).

## Per-skill notes (light)

### accrual-schedule — 4.4
- **Triggers:** Description pins month-end use and “draft for controller approval, not a posting.”
- **Workflow:** Policy-list row model (basis → period portion → already booked → this-period) plus reversing-memo convention is right for close preparers.
- **Boundaries:** Untrusted invoices/vendor statements + explicit “Do not post.”
- **R gap:** Relies on “firm’s accrual policy list” and `internal-gl` without a reference sample policy or MCP catalog in-pack.
- **Consistency:** Matches `month-end-closer` skill set and guardrails.

### break-trace — 4.6
- **Triggers:** Correct handoff “after gl-recon has classified a break.”
- **Workflow:** Dual-side pull → attribute diff → single-sentence cause form → structured JSON (`owner`, `expected_clear_date`, `action`) is strong recon discipline.
- **Boundaries:** Diagnoses only; resolver posts/adjusts.
- **R gap:** Same MCP-name-only pattern; example causes are excellent inline substitutes for a short reference taxonomy.

### gl-recon — 4.4
- **Triggers / Workflow:** Normalize → full-outer-join buckets (matched / amount / quantity / timing / GL-only / subledger-only) → likely-cause set → break report + summary. Matches fund-ops recon practice.
- **Boundaries:** Untrusted subledger/custodian extracts called out; “don’t post” is implied via handoff rather than stated as baldly as in break-trace (minor).
- **Consistency:** Explicit hand to `break-trace` and to resolver — best-in-pack pairing.

### nav-tieout — 4.6
- **Triggers:** Pre-distribution LP statement check — correct control point.
- **Workflow:** Independent capital-account recompute, 0.01 tolerance, ownership-drift diagnostic, sum-of-LPs = fund NAV, commitment-register checks.
- **Boundaries:** Generated statement under test; NAV pack SoT; do not edit statement.
- **R gap:** Waterfall/carry called as single line; complex PE special allocations / side letters not expanded (acceptable at skill length; reference would help edge cases).
- **Consistency:** Aligns with `statement-auditor`.

### roll-forward — 4.2
- **Triggers:** Close packages and audit support — correct.
- **Workflow:** Classic BB + activity − reversals ± reclass/FX = EB with mandatory foot; “surface unexplained, don’t plug” is the right non-negotiable.
- **Boundaries:** Strong on no-plug; lighter on untrusted external inputs (mostly GL-native, so acceptable).
- **R gap:** No sample account-type patterns (accrued exp, prepaid, deferred fees) — workflow is general enough to stand alone.

### variance-commentary — 4.2
- **Triggers:** Close package + management reporting.
- **Workflow:** Materiality threshold + always-comment list; “why not what” driver rule; escalate unclear drivers instead of inventing.
- **Boundaries:** Anti-hallucination on drivers is clear; no untrusted-extract callout (GL/budget assumed internal).
- **Consistency:** Fits `month-end-closer`; slightly corporate-ops flavor (“headcount cost”) still valid for management company / fund P&L close.

## Pack-level findings

1. **Strengths**
   - Descriptions are trigger-rich and role-accurate (when to use + what not to do in one sentence).
   - Audit-trail and no-post discipline appear in every skill that drafts or diagnoses.
   - Skill graph is coherent: recon pipeline (`gl-recon` → `break-trace`); close package (`accrual-schedule` + `roll-forward` + `variance-commentary`); investor gate (`nav-tieout`).
   - Output shapes are concrete (tables, JE drafts, JSON root-cause, pass/fail lines).
   - Length is intentional and consistent with the compact ops skill style (~33–53 lines).

2. **Systemic gap (References/scripts = 3 everywhere)**
   - Vertical has **no** `.mcp.json`, `commands/`, `hooks/`, or per-skill `references/` / `scripts/`.
   - MCPs (`internal-gl`, `subledger`, `nav`) are named in body and in agent tool grants, but the vertical does not declare connectors (unlike e.g. financial-analysis).
   - Not a body-quality failure; synthesis may treat as **P2/P3 infrastructure** (MCP stub catalog + short recon taxonomy / close-package checklist references) rather than P0 skill rewrites.

3. **Minor polish candidates (none drop a skill below clean bar)**
   - `gl-recon`: state “no post / no adjust” as explicitly as `break-trace`.
   - `roll-forward` / `variance-commentary`: optional one-line untrusted/internal-source assumptions for symmetry.
   - `nav-tieout`: optional reference for multi-class / side-letter allocation edge cases.
   - Pack has no slash commands; agents own invocation — fine for current design.

## Clean-bar summary

| Skill | Overall | Min dim | Result |
|---|:-:|:-:|---|
| accrual-schedule | 4.4 | 3 (R) | pass |
| break-trace | 4.6 | 3 (R) | pass |
| gl-recon | 4.4 | 3 (R) | pass |
| nav-tieout | 4.6 | 3 (R) | pass |
| roll-forward | 4.2 | 3 (R) | pass |
| variance-commentary | 4.2 | 3 (R) | pass |

**No skill rewrites in this ticket.** Findings and recommendations only.
