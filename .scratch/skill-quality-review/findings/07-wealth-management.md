# 07 — Wealth management skill pack review

**Pack path:** `plugins/vertical-plugins/wealth-management/skills/`  
**Skills (6):** client-report, client-review, financial-plan, investment-proposal, portfolio-rebalance, tax-loss-harvesting  
**Clean bar:** overall ≥ 4.0 and no dimension ≤ 2  
**Scoring:** Triggers · Workflow · Boundaries · References/scripts · Consistency (1–5 each); overall = mean to one decimal  

---

## Role baseline

Primary roles this pack serves:

| Role | Focus | Core artifacts |
|------|--------|----------------|
| **Wealth advisor / relationship manager** | Client-facing book of business; reviews, reports, proposals | Review packets, performance reports, prospect decks |
| **Financial planner (CFP-style)** | Goals-based planning across retirement, education, estate, risk | Plan document, cash-flow model, scenario tables, action list |
| **Portfolio / investment specialist** | IPS implementation, drift control, tax-aware trades | Drift analysis, trade blotter, TLH list, wash-sale calendar |

**Professional non-negotiables (score against these):**

1. **Suitability / fiduciary alignment** — recommendations map to IPS, risk tolerance, goals, and constraints (ESG, concentrated stock, liquidity).
2. **Client-facing tone** — plain language for retail; match sophistication; lead with what the client cares about.
3. **Tax awareness** — asset location, TLH, Roth conversions, RMDs, ST vs LT gains; household multi-account view.
4. **Compliance hygiene** — past-performance / projection disclaimers; compliance review of client-facing templates; document trade and meeting rationale.
5. **Data integrity** — do not invent holdings, performance, or tax lots; net-of-fees reporting unless required otherwise; IPS benchmark not cherry-picked.
6. **Implementation discipline** — rebalancing bands, wash-sale coordination, tax cost vs benefit, pending cash flows before trading.

**Secondary Consistency lenses:** repo skill conventions (YAML frontmatter with `name` + trigger-rich `description`, `## Workflow` steps, `## Important Notes`); in-vertical peer structure; shared authoring families (`pptx-author`, `xlsx-author`) where outputs are decks/spreadsheets.

---

## Scorecard

| Skill | Triggers | Workflow | Boundaries | Refs/scripts | Consistency | Overall | Clean? |
|-------|----------|----------|------------|--------------|-------------|---------|--------|
| client-report | 5 | 5 | 4 | 3 | 5 | **4.4** | Yes |
| client-review | 5 | 5 | 4 | 3 | 5 | **4.4** | Yes |
| financial-plan | 5 | 5 | 4 | 3 | 5 | **4.4** | Yes |
| investment-proposal | 5 | 4 | 4 | 3 | 5 | **4.2** | Yes |
| portfolio-rebalance | 5 | 5 | 5 | 3 | 5 | **4.6** | Yes |
| tax-loss-harvesting | 5 | 4 | 4 | 3 | 5 | **4.2** | Yes |

**Pack mean overall:** 4.4  
**Skills below clean bar:** none  
**Lowest dimension pack-wide:** References/scripts (all 3) — no `references/` or `scripts/` dirs; skill bodies are self-contained tables/templates only (consistent with most non–financial-analysis vertical skills).

---

## Per-skill notes

All six clear the clean bar → light notes only.

### client-report — 4.4 (clean)

- **Triggers:** Strong coverage (`client report`, `performance report`, `quarterly report for [client]`, `generate reports`, `client statement`).
- **Workflow:** End-to-end report pipeline (params → household/account performance → allocation → holdings → commentary by sophistication → activity → planning notes → branded 8–12 page structure). Matches advisor quarterly/annual practice.
- **Boundaries:** Net-of-fees, IPS benchmark, disclaimers, template consistency, compliance before first distribution. Soft gap: no hard “never fabricate performance / do not replace custodian statements” line; “client statement” trigger can over-promise vs true custodial statements.
- **Refs/scripts:** Inline tables only; adequate for LLM drafting.
- **Consistency:** Matches pack peers and slash command `client-report`.

### client-review — 4.4 (clean)

- **Triggers:** Clear meeting-prep language (`client review`, `meeting prep for [client]`, `quarterly review`, etc.).
- **Workflow:** Advisor meeting-ready: context + IPS, multi-period performance with attribution, drift table, timed agenda, proactive recs (rebalance, TLH, Roth, beneficiaries, insurance). Strong role fit.
- **Boundaries:** Address bad performance directly; document notes/IPS changes; firm compliance on materials. Could harden suitability reaffirmation and “materials require compliance approval.”
- **Refs/scripts:** Inline only.
- **Consistency:** Natural handoff themes to rebalance / TLH / financial-plan; used by `meeting-prep-agent` agent-plugin copy path.

### financial-plan — 4.4 (clean)

- **Triggers:** Excellent natural language (`can I retire`, education, estate, cash flow, plan update).
- **Workflow:** Comprehensive planner scope — profile, cash flow, accumulation/distribution, Monte Carlo success target, education, estate, risk management, scenario matrix, prioritized recs. Aligns with CFP-style annual/onboarding work.
- **Boundaries:** Conservative returns, stress-test requirement, tax modeling, suitability/fiduciary callout. Soft gap: no explicit “advisor must review; not a filed plan” / assumption-documentation checklist.
- **Refs/scripts:** No projection workbook template or method notes for Monte Carlo.
- **Consistency:** Tax optimization bullets align with TLH / rebalance skills.

### investment-proposal — 4.2 (clean)

- **Triggers:** Prospect/pitch language is clear and distinct from existing-client review/report.
- **Workflow:** Solid six-section proposal (firm → needs → strategy → outcomes → fees → getting started) plus tone customization and multi-format output. Slightly thinner vs baseline on formal KYC/suitability questionnaire depth, risk *capacity* vs *tolerance*, and IPS-as-onboarding deliverable.
- **Boundaries:** Don’t oversell performance; hypothetical disclaimers; compliance review; transition-anxiety awareness. US Reg BI / Form CRS / ADV brochure delivery not mentioned (optional jurisdiction note).
- **Refs/scripts:** Calls for PPT/PDF/one-pager but no `pptx-author` pointer or sample leave-behind.
- **Consistency:** Maps cleanly to command `proposal.md` → `investment-proposal` skill.

### portfolio-rebalance — 4.6 (clean; pack high)

- **Triggers:** Direct rebalance/drift language.
- **Workflow:** Specialist-grade: account-type state → IPS drift bands → tax-aware trade rules → asset location → implementation costs/taxes → before/after. Matches portfolio specialist practice.
- **Boundaries:** Strongest in pack — don’t rebalance inside bands, tax breakeven, pending cash flows/RMDs, client restrictions, household wash sales, document every trade.
- **Refs/scripts:** Inline trade/drift tables only.
- **Consistency:** Tight conceptual pair with tax-loss-harvesting and client-review drift flags.

### tax-loss-harvesting — 4.2 (clean)

- **Triggers:** TLH / year-end / unrealized loss coverage is complete.
- **Workflow:** Full harvest loop (candidates → gain/loss budget with $3k ordinary-income rule → replacements → wash-sale check → execution → 30-day tracking). Professional depth.
- **Domain accuracy note (light):** Replacement example `SPY → IVV` (“same index, different fund family”) is a **wash-sale gray area**; many tax practitioners treat same-index large-cap trackers as riskier “substantially identical” pairs than the skill implies. Prefer cross-index / total-market / factor substitutes in examples.
- **Boundaries:** Strong wash-sale, household, cost-basis step-down, and “not all losses worth harvesting” notes. Soft gap: no explicit “recommend only; no unsolicited trade execution” / lot-ID method (specific ID vs average).
- **Refs/scripts:** Inline only; no wash-sale calendar template file.
- **Consistency:** Complements rebalance asset-location and client-review proactive recs.

---

## Pack-level findings

### Strengths

1. **Coherent advisor operating system** — skills cover the real book-of-business loop: prospect → plan → implement (rebalance/TLH) → review → report.
2. **Tax and multi-account awareness is first-class** — not bolted on; household wash sales, asset location, and ST/LT treatment appear where specialists expect them.
3. **Client-facing craft** — commentary by sophistication, timed review agendas, fee transparency, “address bad performance directly.”
4. **Repo shape** — uniform frontmatter, Workflow steps, Important Notes; commands mirror skills; descriptions are trigger-rich (no empty descriptions).

### Gaps (recommendations only — no rewrites in this ticket)

| Priority | Item | Rationale |
|----------|------|-----------|
| **P2** | Fix TLH replacement example (`SPY → IVV`) and add safer substitute patterns | Domain accuracy / wash-sale rigor under specialist baseline |
| **P3** | Add hard data-integrity boundaries across client-facing skills (“never invent holdings, returns, tax lots, or AUM”) | Regulated client communications blast radius |
| **P3** | Distinguish “performance report” vs custodian “client statement” in client-report triggers/notes | Avoid over-promise on official statements |
| **P3** | Point PPT/Excel outputs at shared `pptx-author` / `xlsx-author` (or add thin `references/`) | Raises Refs/scripts without bloating every body |
| **P4** | Explicit cross-skill handoffs (e.g. review → rebalance/TLH/plan) | Pack already implies them; naming would improve agent routing |
| **P4** | Optional US disclosure touchpoints on investment-proposal (Form CRS / ADV / Reg BI) | Jurisdiction-aware polish for FSI firms |
| **P4** | financial-plan: document key assumptions table as required output | Planner non-negotiable for auditability |

### References/scripts pattern

Pack-wide **3** on Refs/scripts is structural, not skill-specific failure: none of the six ship `references/` or `scripts/`. Bodies embed professional tables sufficient for generation quality. Do not treat as P0; consider shared-author skill links or one pack-level reference set at synthesis if backlog prioritizes authoring consistency with financial-analysis.

---

## Verdict

Wealth-management is a **strong, clean pack** against the wealth advisor / planner / portfolio specialist baseline. All six skills pass (overall ≥ 4.2, no dimension ≤ 2). Highest: **portfolio-rebalance (4.6)**. Softest clean skills: **investment-proposal** and **tax-loss-harvesting (4.2)** — workflow depth and one TLH example accuracy issue, not structural breakage. Primary backlog for synthesis: P2 TLH substantially-identical example; P3 data-integrity / statement-scope boundaries; optional authoring-skill links to lift Refs/scripts.
