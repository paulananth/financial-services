# Skill data requirements & outputs

**Date:** 2026-07-24  
**Scope:** Unique skills under `plugins/vertical-plugins/` and `plugins/partner-built/` (66). Agent-plugin copies mirror verticals — same I/O.  
**Companion:** [REVIEW.md](./REVIEW.md) (quality scores)

**How to read**

| Column | Meaning |
|--------|---------|
| **Data required** | What the user or systems must supply (or the skill must fetch) before a good run |
| **Sources** | Where that data typically comes from |
| **Outputs** | Primary artifacts the skill is designed to produce |

Legend for sources: **User** · **Files** · **MCP/API** · **Web** · **Session** (prior skills in chat)

---

## Equity research (9)

| Skill | Data required | Sources | Outputs |
|-------|---------------|---------|---------|
| **catalyst-calendar** | Coverage universe (tickers/names); sector focus; whether to include macro events; time horizon | User; company IR; calendars (Bloomberg-class / web) | Excel calendar (sortable); weekly preview note (markdown); optional calendar export |
| **earnings-analysis** | Company + latest quarter; earnings release; transcript; consensus; guidance; model/thesis if covered | Files/MCP/web (freshness mandatory); prior initiation | **DOCX** 8–12 pp earnings update (`[Co]_Q[q]_[yr]_Earnings_Update.docx`) + charts |
| **earnings-preview** | Company + quarter; consensus (rev/EPS/segments); earnings date/time; prior guidance; recent price/options move | User; web/consensus; IR | **1-page preview**: consensus table, metrics-to-watch, bull/base/bear, catalyst checklist, trading setup |
| **idea-generation** | Screen params (factors, universe, long/short, themes); optional sector focus | User; market data / web screens | Shortlist of **5–10 ideas** with one-pagers (thesis, mispricing, catalyst, falsifiers); optional deep-dive queue |
| **initiating-coverage** | Ticker/company; sector; rating scale; model assumptions; filings; comps set | User; SEC/filings; market data; multi-task verification | Full **initiation package**: Excel model + charts + long-form report (DOCX/PDF per task policy) |
| **model-update** | Existing model file; new actuals/guidance/macro drivers; which lines to revise | **Files** (model); earnings/release; User assumptions | Updated **Excel model**; estimate-change summary (md/docx); revised PT derivation |
| **morning-note** | Overnight news / events on coverage names; ratings/PTs to reiterate or change | News/web; coverage list; User view | **≤1 page** morning note (email/Slack-ready): take + stock impact + coverage bullets |
| **sector-overview** | Sector/subsector definition; purpose (client/pitch/internal); depth; geography | User; industry data; company filings | **Word or PPT**: market size, competitive map, company comparison table, themes |
| **thesis-tracker** | Existing theses / positions; new data points or catalysts; invalidation triggers | User; prior notes; news/fundamentals | Updated **thesis scorecard** + change log (what moved, still valid?) |

---

## Financial analysis (13)

| Skill | Data required | Sources | Outputs |
|-------|---------------|---------|---------|
| **3-statement-model** | Template or build scope; historical IS/BS/CF; drivers (growth, margins, WC, capex); scenario flags | User; **Files** template; SEC/MCP | Populated **3-statement Excel** with integrity checks (BS balances, cash ties, RE roll) |
| **audit-xls** | Workbook (or range/sheet); model type if known (DCF/LBO/3-stmt/merger) | **Files** | Severity-ranked **audit report** (errors/warnings); fix only on request |
| **clean-data-xls** | Messy sheet/range; clean rules (trim, types, casing, dups) | **Files**; User confirm | Cleaned range/sheet; transform notes (prefer formulas over silent overwrite) |
| **competitive-analysis** | Scope (market, competitors, audience); positioning axes; data hierarchy preference | User; MCP/filings/web; outline approval | **Competitive landscape deck** (positioning, deep-dives, moat synthesis) |
| **comps-analysis** | Peer set (or sector to build set); metrics list; valuation date; data source policy (MCP-first) | User; MCP (S&P/FactSet-class) / filings | **Comps Excel**: operating metrics, multiples, quartiles, notes/methodology |
| **dcf-model** | Company; historical financials; WACC inputs (rf, beta, ERP, size, debt); projections; terminal method | User; SEC/MCP; market data | **DCF workbook** (WACC, projections, sensitivity); optional validation script path |
| **deck-refresh** | Existing PPTX; new numbers map (source → slides); period label | **Files** deck + data; User mapping | Updated **PPTX** with surgical edits + change/flag report (derived YoY etc.) |
| **ib-check-deck** | Client-ready deck; optional unit conventions | **Files** PPTX | **QC report** (number consistency, terminology, visual/IB language); read-only by default |
| **lbo-model** | LBO template or structure; entry EV/EBITDA; debt schedule; ops assumptions; exit; fees | User; **Files** template | Completed **LBO Excel** (S&U, debt, returns, sensitivity) |
| **ppt-template-creator** | Source branded PPTX template; skill name/scope for generated skill | **Files**; User | **New skill package** that encodes that template (not a presentation) |
| **pptx-author** | Content outline / numbers; branding constraints; path to write | User; Session | Headless **`.pptx` on disk** |
| **skill-creator** | Intent for new/updated skill; optional existing skill path | User | Scaffolded **skill** (SKILL.md, refs, package/validate tooling) |
| **xlsx-author** | Structure/content for workbook; formulas vs values; path | User; Session | Headless **`.xlsx` on disk** |

---

## Fund admin (6)

| Skill | Data required | Sources | Outputs |
|-------|---------------|---------|---------|
| **accrual-schedule** | Period-end date; accrual list or GL balances; supporting invoices/contracts | User; **Files**/GL extract | **Accrual schedule** + draft JEs with support citations |
| **break-trace** | Break row(s) from recon; access to GL/subledger/trade detail | **Files**/systems; gl-recon output | **Root-cause trace** to source tx/posting; evidence chain |
| **gl-recon** | GL extract + subledger extract (same entity/asset class/date); match key; tolerance policy | **Files** (untrusted extracts) | **Break report** (bucket + likely cause) + summary % matched → handoff to break-trace |
| **nav-tieout** | LP statement; fund NAV pack / capital account components | **Files** | **Tie-out** recomputing LP capital vs NAV; flagged line differences |
| **roll-forward** | Account; beginning balance; period activity & reversals; ending GL | GL / **Files** | **Roll-forward schedule** (beg + activity − reversals = end) with support |
| **variance-commentary** | Current vs prior period (and vs budget) P&L and BS; materiality threshold | GL/trial balance; budget **Files** | **Flux commentary** for lines over threshold (period and budget) |

---

## Investment banking (9)

| Skill | Data required | Sources | Outputs |
|-------|---------------|---------|---------|
| **buyer-list** | Target description; sector; deal size; strategic vs financial mandate; any exclusions | User; market knowledge/web | **Buyer universe** table (strategic/financial, rationale, priority) |
| **cim-builder** | Company narrative; financials; market; team; process positioning | User; data room/CIM materials | Structured **CIM draft** (sections ready for bank formatting) |
| **datapack-builder** | Source materials (CIM, OM, filings, models); pack type/audience | **Files**; User | Professional **data pack** (structured Excel/tabs from sources) |
| **deal-tracker** | Live deals; milestones; owners; deadlines; status updates | User; prior tracker | **Pipeline view** + milestone/action status + overdue surfaces |
| **merger-model** | Acquirer & target financials; offer price/mix; synergies; financing; share count | User; models/filings | **A/D analysis** (pro forma EPS, synergy sensitivity, purchase accounting outline) |
| **pitch-deck** | PPT template; source data files; slide population map | **Files** template + data | Populated **pitch PPTX** with validation against sources |
| **process-letter** | Process stage (IOI/final); timeline; contact; bid instructions; NDA status | User; process calendar | **Process letter** / bid instruction draft (Word) |
| **strip-profile** (folder) / **fsi-strip-profile** | Company; 1 vs multi-slide; focus topics; financials & market data | User; filings; CapIQ/Bloomberg-class | **1–4 strip profile slides** (dense IB company profile) |
| **teaser** | Anonymous highlights; sector; key metrics; selling points; **no identity leak** | User (sanitized) | **1-page teaser** DOCX/PDF (optional single-slide PPT) |

---

## Operations — KYC (2)

| Skill | Data required | Sources | Outputs |
|-------|---------------|---------|---------|
| **kyc-doc-parse** | Onboarding packet (IDs, formation, UBO, address, SOF, tax forms) | **Files** (untrusted applicant docs) | **JSON KYC record** (identity, ownership, control, SOF, doc inventory) + gap flags → feeds kyc-rules |
| **kyc-rules** | Parsed KYC JSON; firm **rules grid** / risk factors; screening results if any | Session (parse output); User firm policy | **Rule-by-rule outcomes**, risk rating + factors, **disposition recommendation** (request docs / EDD / decline / clear for officer) — not final approve |

---

## Private equity (10)

| Skill | Data required | Sources | Outputs |
|-------|---------------|---------|---------|
| **ai-readiness** | Portfolio materials (quarterlies, board decks, financials) for one or many portcos | MCP/files/uploads | **1-page OP memo**: top 5 AI opportunities, replays, go/wait, explicitly not doing |
| **dd-checklist** | Target; deal type; size/complexity; key concerns; timeline | User | **DD checklist Excel** (workstream tabs) + % complete dashboard + weekly status format |
| **dd-meeting-prep** | Meeting type; attendees; topic focus; known materials; concerns | User; CIM/data room | **1-page prep**: objectives, prioritized questions, benchmarks, red flags, follow-ups |
| **deal-screening** | CIM / teaser / broker materials; **fund investment criteria** | **Files**; User criteria | **1-page screen memo** (metrics, fit, red flags, pass/advance) |
| **deal-sourcing** | Sector focus; revenue/EBITDA range; geo; ownership type; firm intro for outreach | User; web; CRM if available | **Target shortlist** + (after approval) **draft founder outreach** emails — never send unapproved |
| **ic-memo** | Business; market; financials 3–5y; management; terms; DD findings; VCP; returns | User; Session from other skills | **IC memo DOCX** (recommendation, risks, financials/returns tables) |
| **portfolio-monitoring** | Monthly/quarterly package; **budget/plan**; optional covenants | **Files**; User | KPI extract; variance vs plan; flags; monitoring summary (single-co oriented today) |
| **returns-analysis** | Entry EBITDA/multiple/EV; net debt; equity check; fees; leverage; growth/margin/exit/hold | User | **Returns Excel** (assumptions, IRR/MOIC, sensitivities, scenarios) + IC one-pager |
| **unit-economics** | Revenue model type; ARR/cohorts or unit P&L; CAC/LTV inputs; retention | User; **Files** | **UE Excel** (ARR bridge, cohorts, dashboard) + summary slide + red flags |
| **value-creation-plan** | Current rev/EBITDA; org; ops metrics; mgmt gaps; diligence quick wins | User; DD | **VCP doc/PPT** (EBITDA bridge, levers, 100-day plan, KPIs, owners) + backing Excel |

---

## Wealth management (6)

| Skill | Data required | Sources | Outputs |
|-------|---------------|---------|---------|
| **client-report** | Client/household; period; accounts; benchmark; branding/disclaimers; holdings & returns | User; custodian/portfolio data **Files** | **PDF/Word** 8–12 pp performance report (+ optional Excel appendix) |
| **client-review** | Client; account types; AUM; **IPS**; life stage; last meeting / open items; performance | User; portfolio data | **1-page review pack**: performance, allocation vs target, actions, agenda |
| **financial-plan** | Demographics; income; accounts; expenses; liabilities; goals; assumptions (retirement age, SS, etc.) | User | **Plan doc** 15–25 pp + **cash-flow Excel** + charts + scenarios + action checklist |
| **investment-proposal** | Prospect; situation; assets; goals; risk; constraints; fees/approach | User | **12–15 slide PPT** + PDF leave-behind + 1-page email summary |
| **portfolio-rebalance** | Per-account holdings + MV; **cost basis** (taxable); target allocation / bands | User; portfolio systems | Drift table; **trade list Excel**; tax impact; before/after allocation |
| **tax-loss-harvesting** | Taxable lots: security, basis, MV, holding period; gains to offset; wash-sale history | User; **Files** | Harvest list Excel; execution sheet; wash-sale calendar; tax savings estimate; replacements |

---

## Partner — LSEG (8)

All require **LSEG / LFA MCP connectivity** and market identifiers (RIC/ISIN/CUSIP as applicable). User supplies **instrument or portfolio identifiers** and analysis focus; tools supply market data.

| Skill | Data required (user + MCP) | Outputs (desk tables) |
|-------|----------------------------|------------------------|
| **bond-futures-basis** | Futures contract RIC; optional repo context | Future summary, CTD analytics, gross/net basis, implied vs market repo, historical percentile, trade assessment |
| **bond-relative-value** | Bond ID(s); curve context; stress scenarios | Spread decomposition (G / credit / residual); scenario P&L; RV assessment |
| **equity-research** (LSEG) | Equity RIC/ticker | Consensus table; financials summary; price history context; macro overlay snapshot |
| **fixed-income-portfolio** | Bond list / portfolio IDs; optional benchmark | Portfolio summary vs benchmark; composition; cashflow profile; scenario stress |
| **fx-carry-trade** | Currency pair(s); tenors | Carry profile; vol surface summary; carry-to-vol; RR/BF; trade framing |
| **macro-rates-monitor** | Country/region focus; indicator set | Macro summary table; yield curve snapshot; inflation/swap context; narrative dashboard |
| **option-vol-analysis** | Underlying RIC or FX pair; option specs | Vol surface; Greeks; IV vs RV comparison; assessment |
| **swap-curve-strategy** | Currency/index template; tenors | Swap curve table; spreads vs govt; curve metrics; trade ideas (DV01-neutral framing) |

---

## Partner — S&P Global / Kensho (3)

All require **Kensho LLM-ready API / Capital IQ MCP** (`kfinance`). Numbers from CIQ only.

| Skill | Data required | Sources | Outputs |
|-------|---------------|---------|---------|
| **earnings-preview-beta** (`earnings-preview-single`) | Single company/ticker; target earnings period | Kensho: company info, transcript, financials (8Q), segments, estimates, peers | Intermediate CSVs/txt under temp path → **4–5 page HTML** earnings preview (+ charts) |
| **funding-digest** | Sectors and/or company list / watchlist; time window | Kensho funding/deal tools; sector seeds | **One-page PPTX** digest of recent funding rounds + logos/QA |
| **tear-sheet** | Company/ticker; **audience** (ER / IB-M&A / Corp Dev / Sales-BD) | Kensho company + financials | **DOCX tear sheet** (1–2 pp) per audience template + intermediate SSoT files |

---

## Cross-skill data flows (common pipelines)

```text
ER earnings cycle
  earnings-preview → (print) → model-update + earnings-analysis → thesis-tracker
  initiating-coverage → model-update / thesis-tracker / catalyst-calendar

Modeling / valuation
  clean-data-xls → 3-statement-model | dcf-model | lbo-model | comps-analysis
  → audit-xls → xlsx-author (headless) | deck-refresh | pitch-deck
  → ib-check-deck

Fund close
  gl-recon → break-trace
  accrual-schedule | roll-forward | variance-commentary  (period package)
  nav-tieout  (LP vs NAV)

KYC
  kyc-doc-parse → kyc-rules → human compliance officer

PE deal
  deal-sourcing → deal-screening → dd-checklist / dd-meeting-prep
  → unit-economics + returns-analysis + value-creation-plan → ic-memo
  portfolio-monitoring | ai-readiness  (post-close)

Wealth
  investment-proposal → financial-plan → portfolio-rebalance / tax-loss-harvesting
  → client-review → client-report
```

---

## Data classes cheat sheet

| Data class | Skills that need it most |
|------------|--------------------------|
| **Company identity** (ticker, name, sector) | Almost all research/IB/PE/partner skills |
| **Financial statements / estimates** | ER, FA models, comps, DCF, LBO, merger, PE IC/returns, S&P |
| **Market prices / curves / vol** | LSEG pack; DCF WACC; comps trading multiples |
| **Existing model or deck file** | model-update, deck-refresh, pitch-deck, audit-xls, lbo/3-stmt templates |
| **GL / subledger / NAV / LP statement** | Fund admin pack |
| **Portfolio holdings + cost basis** | Wealth rebalance, TLH, client report/review |
| **IPS / goals / risk / household** | Wealth plan, proposal, review, rebalance |
| **Onboarding docs + rules grid** | KYC pair |
| **CIM / teaser / data room** | PE screen/DD/IC; IB CIM/teaser/datapack |
| **Fund criteria / mandate** | deal-screening, deal-sourcing, buyer-list |
| **MCP entitlements** | LSEG (LFA), S&P (Kensho/CIQ); optional FactSet-class for comps/DCF |

---

## Gaps (skills thin on explicit I/O contracts)

These work operationally but under-specify machine-checkable inputs/outputs in `SKILL.md` (also called out in the quality review):

- Several **ER lightweight** skills (preview, morning-note, thesis, idea, catalyst) — outputs described, data sources informal  
- **LSEG** — rich **outputs** and tool chains; weak **user input schema** and Boundaries  
- **xlsx-author / pptx-author** — generic file writers; domain data lives in caller skills  
- **deal-screening / portfolio-monitoring** — implied CIM/package inputs; thin formal schema  

---

*Inventory derived from skill bodies and frontmatter; partner MCP tool names as documented in each skill / CONNECTORS.md.*
