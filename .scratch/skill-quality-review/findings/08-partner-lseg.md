# 08 — Partner LSEG skill pack review

**Pack:** `plugins/partner-built/lseg/skills/` (8 skills)  
**Also skimmed:** `plugins/partner-built/lseg/README.md`, `CONNECTORS.md`, sibling `commands/*.md`  
**Clean bar:** overall ≥ 4.0 **and** no dimension ≤ 2  
**Result:** **0 / 8 clean.** Systemic shortfalls on **Boundaries** (2) and **References/scripts** (2); Workflow and Triggers are generally strong; internal Consistency is excellent.

---

## Role baseline (rates / FX / FI desk)

**Primary roles:** rates strategist, FX strategist, FI relative-value / basis trader support, desk quant/analyst, macro strategist; secondary: equity research associate for the single equity skill.

**Artifacts the desk expects**
- Structured tables (spreads, curves, CTD/basis, carry-to-vol, vol surface, portfolio KRD/DV01, scenario P&L) with **as-of timestamps** and identifier clarity (RIC / ISIN / CUSIP).
- Explicit **conventions** for derived metrics (gross/net basis, implied repo, annualized carry, realized vol estimator, swap-spread definition, DV01-neutral weights).
- Tool-sourced market data only; graceful handling of missing entitlements / empty baskets / failed two-phase curve calls.
- Analytical views framed as **desk research**, not order tickets; clear separation of market facts vs interpretation.

**Accuracy / non-negotiables**
- Never invent prices, yields, vols, or CTD identity.
- State when a quantity is a **proxy** (e.g. short-end curve as repo) vs observed market (GC/specials).
- Parallel-shift scenarios ≠ full curve/credit risk; label model limits.
- Buy/sell / long-basis language is **recommendation framing**, not executable advice — needs risk/disclaimer rails on a sell-side-style desk.

**Typical workflow**
1. Resolve instrument identifiers and market date.  
2. Pull live analytics via LFA MCP (pricing → curves/vol → history).  
3. Compute residual / risk-adjusted metrics the tools do not return directly.  
4. Present desk-standard tables + short thesis/risks.  

**Connector / MCP note (Boundaries annotation, not auto-penalty):**  
This pack is intentionally **LFA MCP–native**. README + CONNECTORS.md document one MCP server (bond pricing, FX, curves, swaps, options, vol, QA, time series, YieldBook). Skills list exact tool names that match CONNECTORS. Dependency on LSEG credentials/entitlements is expected product design — score only for how well skills **scope failure modes and non-use of training-data fillers**, not for requiring MCP.

---

## Scorecard

Dimensions: **T**riggers · **W**orkflow · **B**oundaries · **R**eferences/scripts · **C**onsistency · overall = mean to 1 decimal.

| Skill | T | W | B | R | C | Overall | Clean? |
|-------|---|---|---|---|---|---------|--------|
| bond-futures-basis | 4 | 4 | 2 | 2 | 5 | **3.4** | No |
| bond-relative-value | 4 | 4 | 2 | 2 | 5 | **3.4** | No |
| equity-research | 4 | 3 | 2 | 2 | 4 | **3.0** | No |
| fixed-income-portfolio | 4 | 4 | 2 | 2 | 5 | **3.4** | No |
| fx-carry-trade | 4 | 4 | 2 | 2 | 5 | **3.4** | No |
| macro-rates-monitor | 4 | 5 | 2 | 2 | 5 | **3.6** | No |
| option-vol-analysis | 4 | 4 | 2 | 2 | 5 | **3.4** | No |
| swap-curve-strategy | 4 | 4 | 2 | 2 | 5 | **3.4** | No |

**Pack averages:** T 4.0 · W 4.0 · B 2.0 · R 2.0 · C 4.9 · overall **~3.4**

---

## Cross-cutting findings

### Strengths
1. **Uniform partner template** — every skill: frontmatter `name`/`description`, Core Principles, Available MCP Tools, Tool Chaining Workflow (5–7 steps), desk-shaped Output Format tables. Highly teachable pack.
2. **Tool inventory fidelity** — tool names and two-phase patterns (list/search then calculate/price) align with `CONNECTORS.md`; no orphan tool references observed.
3. **Command ↔ skill pairing** — each of 8 commands points at the matching skill and reuses the same chain; skills add domain interpretation layer as README claims.
4. **Desk framing** — carry-to-vol, G/Z residual, CTD/BNOC, 2s10s / butterfly, IV−RV premium, MV-weighted portfolio metrics match strategist vocabulary.

### Systemic gaps (drive B=2 and R=2 pack-wide)
1. **No Boundaries / guardrails section** on any skill — no “MCP-only data / no fabricate,” no entitlement failure path, no “not investment advice,” no identifier/market-date requirements, no proxy-label rules (repo, benchmark). For a desk that issues rich/cheap and trade structures, this is the primary clean-bar fail.
2. **No `references/` or scripts** — formula sheets, RIC examples, convention notes, and mnemonic catalogs live only as thin inline prose. Peer partner pack (`spglobal`) uses deep `references/` extensively; formula-heavy skills (basis, carry, realized vol, roll-down) need the same.
3. **“Compute X” without explicit convention** — model is told to compute gross/net basis, implied repo, annualized carry, close-to-close RV, residual spread, DV01-neutral notionals, 3M carry/roll — without formulas, day-count, or quote units (ticks vs price). Raises desk-accuracy risk even when chaining is correct.
4. **Trade recommendation tone without compliance rails** — several skills end with long/short, buy/hold/sell, conviction, position sizing — appropriate for strategist drafts, incomplete without disclaimer + data-as-of + risk bullets as hard requirements.

### Secondary consistency notes
- Structure diverges from many **vertical-plugin** skills (those often use free-form workflow + web search; LSEG is MCP orchestration). Within partner-built, this is coherent product design — not scored down for “not looking like equity-research vertical.”
- **Name collision:** pack skill `equity-research` vs vertical `equity-research` (different product surface, same slug) — discovery/confusion risk for multi-plugin installs.

---

## Per-skill notes

All skills fail the clean bar on **Boundaries ≤ 2** and **References ≤ 2**. Deeper notes focus on skill-specific Workflow/Triggers/Consistency deltas and recommended fix themes (findings only — no rewrites here).

### bond-futures-basis — 3.4

| Dim | Score | Note |
|-----|-------|------|
| Triggers | 4 | Strong “Use when” (basis, CTD, implied repo, basis trades). Could add CTD switch / delivery option / BNOC. |
| Workflow | 4 | Correct chain: future → CTD bond → basis metrics → curve repo proxy → history → optional sovereign credit. Output tables desk-ready. Weak: no explicit basis/IRR formulas or tick conversion. |
| Boundaries | 2 | None. Critical: short-end curve ≠ specials/GC; delivery basket incompleteness; never invent CTD. |
| References | 2 | No CF/IRR/BNOC formula sheet; no sample RICs beyond command examples. |
| Consistency | 5 | Matches command `analyze-bond-basis` and CONNECTORS bond future tools. |

**Fix themes:** Boundaries (proxy repo, no fabricate CTD); references with gross basis / net basis / implied repo definitions and units; optional switch-option qualitative checklist.

---

### bond-relative-value — 3.4

| Dim | Score | Note |
|-----|-------|------|
| Triggers | 4 | Rich/cheap, spread decomp, scenarios covered. |
| Workflow | 4 | Sensible decomp: Z from `bond_price`, G via curve interp, residual vs credit curve, scenarios, optional history. OAS tool listed but not default-chained for callables — gap vs description’s RV depth. Residual = G − credit curve is a **heuristic**, not full OAS. |
| Boundaries | 2 | None. Issuer-type credit curve may mis-match single-name risk; scenario = parallel only. |
| References | 2 | No G/Z/ASW/OAS glossary or interpolation notes. |
| Consistency | 5 | Aligns with `analyze-bond-rv` and YieldBook/credit tools. |

**Fix themes:** When to require `fixed_income_risk_analytics` (callables); label residual as model residual; Boundaries on curve mismatch; spread definitions reference.

---

### equity-research — 3.0 (weakest)

| Dim | Score | Note |
|-----|-------|------|
| Triggers | 4 | Solid snapshot triggers; overlaps vertical ER language. |
| Workflow | 3 | Adequate **QA snapshot** (IBES + fundamentals + price + light macro). Against sell-side ER baseline it under-delivers: no peer/comps data path, valuation “vs sector/history” without sector tools, buy/hold/sell + fair value from thin inputs is overclaimed. |
| Boundaries | 2 | Highest risk skill for overconfident investment language without data-integrity / disclaimer rails. |
| References | 2 | No sector metric kits or estimate-interpretation notes. |
| Consistency | 4 | Internally matches pack template and `research-equity` command; **slug collision** with vertical equity-research; thinner than vertical peers and than S&P tear-sheet partner skill. |

**Fix themes:** Reposition as “equity data snapshot” not full investment case; or add comps/valuation data paths if tools exist; hard Boundaries (no fabricate estimates; N/A on missing; not advice); consider rename to reduce multi-plugin collision.

---

### fixed-income-portfolio — 3.4

| Dim | Score | Note |
|-----|-------|------|
| Triggers | 4 | Portfolio duration/DV01, cashflow waterfall, scenarios — clear. |
| Workflow | 4 | Price → MV-weight → reference composition → cashflows → scenarios → curve context. Strong aggregation focus. Benchmark column in output has no tool path when user doesn’t supply one; KRD via `fixed_income_risk_analytics` listed but not stepped for option-heavy books. |
| Boundaries | 2 | None. Batch ID failures, multi-currency aggregation, callable treatment not scoped. |
| References | 2 | No portfolio analytics conventions (YTW vs YTM blend, rating average method). |
| Consistency | 5 | Matches `review-fi-portfolio` and YieldBook tool set. |

**Fix themes:** Require user benchmark or mark “—”; multi-ccy FX conversion rule; when to pull KRD/OAS; Boundaries on partial pricing failures.

---

### fx-carry-trade — 3.4

| Dim | Score | Note |
|-----|-------|------|
| Triggers | 4 | Carry, forward curve, carry-to-vol well covered; G10/EM distinction only in README skill blurb, not skill body. |
| Workflow | 4 | Spot → tenor forward → full curve → vol surface → history is correct strategist chain. Carry-to-vol formula stated in principles; annualized carry from points not fully specified (quote convention / day count). Position sizing mentioned without risk budget framework. |
| Boundaries | 2 | None. EM convertibility, funding/cross-currency basis, short-vol nature mentioned lightly in principles only. |
| References | 2 | No pip/point convention or G10 vs EM checklist. |
| Consistency | 5 | Matches `analyze-fx-carry` and FX CONNECTORS tools. |

**Fix themes:** Explicit annualized carry formula; EM risk Boundaries; optional use of `interest_rate_curve` (listed but not in numbered steps).

---

### macro-rates-monitor — 3.6 (strongest Workflow)

| Dim | Score | Note |
|-----|-------|------|
| Triggers | 4 | Macro dashboard, curve shape, real rates, financial conditions. |
| Workflow | **5** | Best-in-pack: cycle → govt curve slopes → inflation/real → swap spreads → history → narrative. **Macro Search Patterns** (US/EZ/UK wildcards) is the only skill-level “reference-like” operational aid and materially raises Workflow quality. |
| Boundaries | 2 | None. Mnemonic mismatch / SA vs NSA / nowcast vs print not guarded. |
| References | 2 | Search patterns help but are not a full mnemonic catalog or release-calendar reference. |
| Consistency | 5 | Matches `macro-rates` command and QA/curve/swap tools. |

**Fix themes:** Boundaries on data vintage and revision; expand mnemonic reference file; policy-rate path vs front-end curve caveats.

---

### option-vol-analysis — 3.4

| Dim | Score | Note |
|-----|-------|------|
| Triggers | 4 | Surface, Greeks, IV vs RV, vol strategies. |
| Workflow | 4 | Surface-first → templates → `option_value` → history → RV windows is sound. RV method “close-to-close” named but not formula/annualization; equity vs FX surface quote differences noted lightly; strategy recommendations without hedge construction detail. |
| Boundaries | 2 | None. Model risk (SABR surface assumptions), American vs European, corporate events on RV. |
| References | 2 | No RR/BF sign convention sheet; no RV estimator reference. |
| Consistency | 5 | Matches `analyze-option-vol` and options/vol CONNECTORS tools. |

**Fix themes:** Realized vol formula + windows; RR sign convention (25d); Boundaries on event windows and missing surface points.

---

### swap-curve-strategy — 3.4

| Dim | Score | Note |
|-----|-------|------|
| Triggers | 4 | Swap curve, swap spreads, steepener/flattener/butterfly, cross-ccy. |
| Workflow | 4 | Template discovery → multi-tenor swaps → govt overlay → inflation/real → metrics → trade ideas with DV01-neutral and carry/roll **requested** but history tool listed without a step to ground slopes historically; carry/roll estimation method unspecified; cross-currency comparison in description not in workflow. |
| Boundaries | 2 | None. LIBOR vs RFR template selection, discounting assumptions, illustrative stops/targets. |
| References | 2 | No butterfly weight formulas or roll-down method. |
| Consistency | 5 | Matches `analyze-swap-curve` and swap/curve tools. |

**Fix themes:** Add historical slope step; DV01-neutral weight formula; Boundaries on index/template choice; optional multi-currency branch.

---

## Suggested priority themes (for synthesis backlog)

| Priority band | Theme | Skills |
|---------------|--------|--------|
| P1 systemic | Add **Boundaries** pack-wide: MCP-only numbers, as-of dates, no fabricate, entitlement/empty-result handling, not-advice, proxy labels | All 8 |
| P1 systemic | Add **references/** (or pack-level `references/conventions.md`) for derived metrics formulas and identifier examples | All; highest for basis, carry, vol, swap |
| P2 | Formula-explicit “compute” steps for desk-critical derived metrics | basis, fx-carry, option-vol, swap-curve, bond-RV residual |
| P2 | Soften or tool-back **investment recommendations** especially equity buy/hold/sell + fair value | equity-research; also basis/carry/swap trade boxes |
| P3 | Workflow completeness: history for curve metrics; KRD path; `interest_rate_curve` in fx-carry steps; callable OAS default | swap-curve, FI portfolio, fx-carry, bond-RV |
| P3 | Naming: disambiguate `equity-research` vs vertical slug | equity-research |
| P4 | Trigger phrase expansion (CTD switch, BNOC, EM carry, etc.) | various |

---

## Evidence paths (absolute)

- `/Users/aneenaananth/projects/financial-services/plugins/partner-built/lseg/skills/*/SKILL.md` (8)
- `/Users/aneenaananth/projects/financial-services/plugins/partner-built/lseg/README.md`
- `/Users/aneenaananth/projects/financial-services/plugins/partner-built/lseg/CONNECTORS.md`
- `/Users/aneenaananth/projects/financial-services/plugins/partner-built/lseg/commands/*.md` (8)
- Peer contrast: `/Users/aneenaananth/projects/financial-services/plugins/partner-built/spglobal/skills/tear-sheet/` (deep references + data-integrity Boundaries)
