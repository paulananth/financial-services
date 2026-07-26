# 10 — Agent-plugin skill drift spot-check

**Status:** complete  
**Date:** 2026-07-24  
**Scope:** `plugins/agent-plugins/*/skills/*` vs `plugins/vertical-plugins/*/skills/*`  
**Verdict:** **No drift.** All 51 bundled skill directories are byte-identical to their vertical sources (recursive). No re-sync required.

---

## Sync model (from repo)

| Piece | Role |
|-------|------|
| `plugins/vertical-plugins/<vertical>/skills/<name>/` | **Source of truth** — edit here |
| `plugins/agent-plugins/<slug>/skills/<name>/` | **Vendored copy** — full tree `shutil.copytree` from vertical |
| `scripts/sync-agent-skills.py` | Rebuilds every agent bundle from vertical by skill **name** |
| `scripts/check.py` §4b | Fails if any bundle differs from vertical (`filecmp.dircmp`; top-level only) |

Sync indexes vertical skills by directory name only (first/last write wins if two verticals shared a name — **none do today**). Bundles with no matching vertical name are errors.

---

## Bundle map (10 agents → 51 skill dirs)

| Agent | Bundled skills | Vertical origin(s) |
|-------|----------------|--------------------|
| `earnings-reviewer` | audit-xls, earnings-analysis, earnings-preview, model-update, morning-note, xlsx-author | financial-analysis + equity-research |
| `gl-reconciler` | audit-xls, break-trace, gl-recon, xlsx-author | financial-analysis + fund-admin |
| `kyc-screener` | kyc-doc-parse, kyc-rules, xlsx-author | operations + financial-analysis |
| `market-researcher` | competitive-analysis, comps-analysis, idea-generation, pptx-author, sector-overview | financial-analysis + equity-research |
| `meeting-prep-agent` | client-report, client-review, investment-proposal, pptx-author | wealth-management + financial-analysis |
| `model-builder` | 3-statement-model, audit-xls, comps-analysis, dcf-model, lbo-model, xlsx-author | financial-analysis |
| `month-end-closer` | accrual-schedule, audit-xls, roll-forward, variance-commentary, xlsx-author | fund-admin + financial-analysis |
| `pitch-agent` | 3-statement-model, audit-xls, comps-analysis, dcf-model, deck-refresh, ib-check-deck, lbo-model, pitch-deck, pptx-author, sector-overview, xlsx-author | financial-analysis + equity-research + investment-banking |
| `statement-auditor` | audit-xls, nav-tieout, xlsx-author | financial-analysis + fund-admin |
| `valuation-reviewer` | ic-memo, portfolio-monitoring, returns-analysis, xlsx-author | private-equity + financial-analysis |

**Shared skills (multi-agent):**

| Skill | Agents | Vertical source |
|-------|--------|-----------------|
| `xlsx-author` | 8 | `financial-analysis/skills/xlsx-author` |
| `audit-xls` | 6 | `financial-analysis/skills/audit-xls` |
| `comps-analysis` | 3 | `financial-analysis/skills/comps-analysis` |
| `pptx-author` | 3 | `financial-analysis/skills/pptx-author` |
| `3-statement-model` | 2 | `financial-analysis/skills/3-statement-model` |
| `dcf-model` | 2 | `financial-analysis/skills/dcf-model` |
| `lbo-model` | 2 | `financial-analysis/skills/lbo-model` |
| `sector-overview` | 2 | `equity-research/skills/sector-overview` |

**Unique-to-one-agent skills:** 23 (one pack each) — all resolve to a single vertical source.

**Missing vertical source:** 0  
**Duplicate skill names across verticals:** 0

---

## Diff method

1. Built name → vertical path index (same as `sync-agent-skills.py` / `check.py`).
2. For every `agent-plugins/*/skills/*` dir: recursive file inventory + byte compare vs vertical.
3. Expanded beyond the ticket’s sample to a **full census** (51 dirs) because the pass was cheap and definitive.
4. Recursive `filecmp.dircmp` (deeper than `check.py`’s shallow top-level compare).
5. Inter-agent identity check for all 8 shared skills.
6. Multi-file inventory samples for skills with references/scripts.

---

## Results

### Shared sample (required)

| Skill | Result |
|-------|--------|
| `xlsx-author` × 8 agents | **CLEAN** — all identical to vertical and to each other |
| `audit-xls` × 6 agents | **CLEAN** — all identical to vertical and to each other |

### Other shared skills

| Skill | Result |
|-------|--------|
| `comps-analysis` × 3 | CLEAN |
| `pptx-author` × 3 | CLEAN |
| `3-statement-model` × 2 | CLEAN |
| `dcf-model` × 2 | CLEAN |
| `lbo-model` × 2 | CLEAN |
| `sector-overview` × 2 | CLEAN |

### Unique skills (one agent each) — all CLEAN

`accrual-schedule`, `break-trace`, `client-report`, `client-review`, `competitive-analysis`, `deck-refresh`, `earnings-analysis`, `earnings-preview`, `gl-recon`, `ib-check-deck`, `ic-memo`, `idea-generation`, `investment-proposal`, `kyc-doc-parse`, `kyc-rules`, `model-update`, `morning-note`, `nav-tieout`, `pitch-deck`, `portfolio-monitoring`, `returns-analysis`, `roll-forward`, `variance-commentary`

### Multi-file inventories (spot sample; source ≡ bundle)

| Skill (agent) | Files matched |
|---------------|---------------|
| `earnings-analysis` (earnings-reviewer) | SKILL.md + 3 references |
| `dcf-model` (model-builder) | SKILL.md, TROUBLESHOOTING.md, requirements.txt, scripts/validate_dcf.py |
| `pitch-deck` (pitch-agent) | SKILL.md + 4 reference/* |
| `3-statement-model` (pitch-agent) | SKILL.md + 3 references |
| `competitive-analysis` (market-researcher) | SKILL.md + 2 references |
| `ib-check-deck` (pitch-agent) | SKILL.md + 2 references + scripts/extract_numbers.py |

### Summary counts

| Category | Count |
|----------|------:|
| Bundled skill dirs checked | 51 |
| CLEAN (byte-identical recursive) | **51** |
| DRIFTED | **0** |
| MISSING_SOURCE | **0** |

**Drifted paths:** none.  
**Nature of drift:** N/A.

---

## Recommendation

| Action | Needed? |
|--------|---------|
| **Re-sync only** (`python3 scripts/sync-agent-skills.py`) | **No** — trees already match |
| **Fix-source-then-sync** | **No** for drift; content quality is out of this ticket |
| Ongoing process | Keep editing only under `vertical-plugins/`; run sync after skill edits; rely on `check.py` §4b / pre-commit |

### Process notes (not failures)

1. **`check.py` dircmp is shallow** (top-level files/dirs only). Nested-only drift would not trip §4b. This census used recursive compare and still found zero issues; consider recursive compare in `check.py` later if nested assets grow.
2. **Sync is name-global.** Two verticals must never ship the same skill directory name, or the last indexed source wins for every agent that bundles that name. Today: no collisions.
3. **Do not score agent copies as unique skills** in synthesis — quality lives once at the vertical; agent packs are mirrors.

---

## Out of scope (per ticket)

- Skill rewrites / content scoring  
- Treating each agent copy as a separate skill  
- Partner-built plugins  
- Managed-agent cookbook YAML  
