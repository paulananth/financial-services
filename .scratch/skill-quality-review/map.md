# Skill quality review map

Label: `wayfinder:map`

## Destination

A structured quality-review report at [`.scratch/skill-quality-review/REVIEW.md`](./REVIEW.md) covering all unique vertical-plugin and partner-built skills: per-skill scorecards (Triggers, Workflow, Boundaries, References/scripts, Consistency), domain/job-role baselines per pack, agent-plugin drift spot-check, systemic findings, and a prioritized (P0–P4) fix backlog. Findings and recommendations only — no skill rewrites in this effort.

**Status: DESTINATION REACHED** — [REVIEW.md](./REVIEW.md) delivered 2026-07-24.

## Notes

- **Domain:** Financial services Cowork / Claude plugins (`plugins/vertical-plugins/`, `plugins/partner-built/`). Canonical sources live in verticals; agent-plugin skills are synced copies.
- **Skills every session should consult:** this map; `Claude.md` (repo structure, edit-verticals-then-sync); each ticket's pack paths under `plugins/`.
- **Baseline rule:** For each pack, research the domain and job roles first, then score skills against that professional baseline. Secondary Consistency lenses: repo conventions, in-vertical peers, shared-skill families (`xlsx-author`, `audit-xls`, `pptx-author`, etc.).
- **Scoring:** Five dimensions × 1–5; overall = average to one decimal. Light notes only when overall ≥ 4.0 and no dimension ≤ 2; deeper write-up otherwise.
- **Prioritization (synthesis):** P0 broken/high-blast → P1 cross-cutting systemic → P2 usable-but-gappy → P3 polish → P4 nice-to-have; within band, worst overall first.
- **Out of execution for this map:** applying fixes, rewriting skills, scoring every agent-plugin copy as unique, M365 install skills.
- **Tracker:** local markdown under `.scratch/skill-quality-review/`.
- **Plan + research execution:** research tickets produce findings assets; synthesis ticket assembles `REVIEW.md`. Do not apply skill patches on this map.

## Decisions so far

- [Equity research skill pack review](./issues/01-equity-research.md) — Mean ~3.4; only earnings-analysis clean (4.8). Findings: [01](./findings/01-equity-research.md)
- [Financial analysis skill pack review](./issues/02-financial-analysis.md) — Mean ~4.1; 8/13 clean; P0 missing LBO/comps examples. Findings: [02](./findings/02-financial-analysis.md)
- [Fund admin skill pack review](./issues/03-fund-admin.md) — Pack clean (avg 4.4); R=3 pack-wide. Findings: [03](./findings/03-fund-admin.md)
- [Investment banking skill pack review](./issues/04-investment-banking.md) — Mean ~3.8; pitch-deck 4.6; strip-profile 2.8 weakest. Findings: [04](./findings/04-investment-banking.md)
- [Operations (KYC) skill pack review](./issues/05-operations.md) — Both clean at 4.2; Boundaries excellent. Findings: [05](./findings/05-operations.md)
- [Private equity skill pack review](./issues/06-private-equity.md) — 8/10 clean; deal-screening + portfolio-monitoring 3.4. Findings: [06](./findings/06-private-equity.md)
- [Wealth management skill pack review](./issues/07-wealth-management.md) — All clean; mean 4.4. Findings: [07](./findings/07-wealth-management.md)
- [Partner LSEG skill pack review](./issues/08-partner-lseg.md) — 0/8 clean; B=2 and R=2 pack-wide. Findings: [08](./findings/08-partner-lseg.md)
- [Partner S&P Global skill pack review](./issues/09-partner-spglobal.md) — All clean; mean 4.6. Findings: [09](./findings/09-partner-spglobal.md)
- [Agent-plugin skill drift spot-check](./issues/10-agent-plugin-drift.md) — No drift; 51/51 CLEAN. Findings: [10](./findings/10-agent-plugin-drift.md)
- [Synthesize skill quality REVIEW.md](./issues/11-synthesize-review.md) — Destination report written: [REVIEW.md](./REVIEW.md)

## Not yet specified

- Whether partner MCP-only skills should get a separate “connector readiness” annotation beyond Boundaries *(still optional post-report)*
- Post-report: process for turning backlog into PRs (out of this destination unless destination is redrawn)

## Out of scope

- Applying recommended fixes or rewriting `SKILL.md` files
- Full re-score of every `agent-plugins/*/skills/` copy (drift spot-check only)
- `claude-for-msft-365-install` skills (different product surface)
- Managed-agent cookbook YAML quality (agents, not skills)
- Marketplace / plugin.json versioning process
