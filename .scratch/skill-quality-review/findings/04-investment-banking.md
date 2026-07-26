# 04 — Investment banking skill pack review

**Path:** `plugins/vertical-plugins/investment-banking/skills/`  
**Skills reviewed (9):** buyer-list, cim-builder, datapack-builder, deal-tracker, merger-model, pitch-deck, process-letter, strip-profile (`name: fsi-strip-profile`), teaser  
**Role baseline:** M&A analyst / associate + coverage banker (sell-side process, buy-side advisory support, coverage pitching)  
**Method:** Score 1–5 on Triggers, Workflow, Boundaries, References/scripts, Consistency. Overall = mean to 1 decimal.  
**Clean bar:** overall ≥ 4.0 and no dimension ≤ 2.  
**Scope:** Findings only — no skill rewrites.

---

## Role baseline

### Who uses these skills

| Role | Primary jobs these skills serve |
|------|----------------------------------|
| **M&A analyst** | Teaser/CIM drafting, buyer list research scaffolding, process letters, datapacks from CIM/filings, merger A/D models, strip profiles for books, deal milestone hygiene |
| **M&A associate** | Quality control of the above; prioritization of buyer universe; process design; weekly deal reviews; pitch template population; narrative that supports valuation/process strategy |
| **Coverage banker (MD/VP support)** | Sector company profiles for pitches; pipeline tracking; materials that survive client and legal review |

### Professional bar for deliverables

An associate-ready skill should:

1. **Trigger cleanly** on the phrases analysts actually type (“draft a teaser”, “accretion dilution”, “buyer universe”, “process letter for round 2”).
2. **Encode the real process order** (mandate → teaser + NDA → CIM → IOI letter → management meetings → final bid letter → SPA), not just a generic outline.
3. **Protect the bank and client** — confidentiality/anonymization, legal review gates, no accidental commitments, clear “not legal advice / not a fairness opinion” where relevant.
4. **Produce bank-format artifacts** — one-page teaser, CIM TOC, letter structure, Excel trackers/models with blue/black inputs, 4:3 pitch pages — with enough structure that a junior can execute without inventing firm standards.
5. **Know handoffs** — CapIQ/FactSet/Bloomberg for buyer research and market data; legal for disclaimers and process letter terms; xlsx/pptx authoring skills for file production; senior banker for valuation narrative and bid strategy.

### What this pack covers well vs. leaves to other verticals

| Covered here | Typically elsewhere (not scored as gaps if intentional) |
|--------------|--------------------------------------------------------|
| Sell-side marketing materials (teaser, CIM, process letter, buyer list) | Full comps / DCF / LBO (`financial-analysis`) |
| Deal ops tracker + simple A/D model | Fairness opinion, detailed SPA markup |
| Template **population** (pitch-deck) + strip profiles | Greenfield full pitch book storyboarding |
| CIM/filings → standardized datapack | Portfolio/IC PE memos (`private-equity`) |

---

## Pack scorecard

| Skill | Triggers | Workflow | Boundaries | Refs/scripts | Consistency | Overall | Clean? |
|-------|----------|----------|------------|--------------|-------------|---------|--------|
| buyer-list | 5 | 4 | 3 | 3 | 4 | **3.8** | No |
| cim-builder | 5 | 4 | 3 | 3 | 4 | **3.8** | No |
| datapack-builder | 4 | 5 | 4 | 4 | 3 | **4.0** | Yes* |
| deal-tracker | 5 | 4 | 3 | 3 | 4 | **3.8** | No |
| merger-model | 5 | 4 | 3 | 3 | 4 | **3.8** | No |
| pitch-deck | 4 | 5 | 5 | 5 | 4 | **4.6** | Yes |
| process-letter | 5 | 4 | 3 | 3 | 4 | **3.8** | No |
| strip-profile | 3 | 4 | 3 | 2 | 2 | **2.8** | No |
| teaser | 5 | 4 | 3 | 3 | 4 | **3.8** | No |

\*datapack-builder meets numeric clean bar; see notes on PE framing and `xlsx` skill name drift.

**Pack mean overall:** ~3.8  
**Clean skills:** pitch-deck; datapack-builder (borderline)  
**Weakest:** strip-profile (only skill with a dimension ≤ 2)

---

## Per-skill notes

### pitch-deck — 4.6 (clean)

**Path:** `plugins/vertical-plugins/investment-banking/skills/pitch-deck/SKILL.md`  
**Refs:** `reference/formatting-standards.md`, `slide-templates.md`, `xml-reference.md`, `calculation-standards.md`

| Dim | Score | Note |
|-----|-------|------|
| Triggers | 4 | Strong when-to + explicit **not for creating presentations from scratch**. Slightly template-centric; “build a pitch deck” without a template correctly routes away, but analysts often phrase that way. |
| Workflow | 5 | Decision tree, 5-phase checklist, validate→fix loop with cycle cap, error handling, final checklist. Associate-grade. |
| Boundaries | 5 | Anti-patterns (placeholder boxes, fake tables, contrast), LibreOffice rendering caveat, 3-cycle escalate, source-priority rules. Best-in-pack. |
| Refs/scripts | 5 | Four purpose-built references; commands to read them first. Gold standard for this dimension. |
| Consistency | 4 | Structure differs from thin sell-side peers (appropriate for complexity). Footnote widths cover 16:9 and 4:3; strip-profile forces 4:3 only — intentional specialization, minor pack friction. |

**Light notes only:** Keep as the pack’s quality reference. Future work is optional polish (more trigger synonyms for “populate / update book slides”).

---

### datapack-builder — 4.0 (clean, with framing caveats)

**Path:** `plugins/vertical-plugins/investment-banking/skills/datapack-builder/SKILL.md`

| Dim | Score | Note |
|-----|-------|------|
| Triggers | 4 | Good positive + negative (“Do not use for simple calculations or completed packs”). Fewer explicit phrase triggers than sell-side peers; PE/IC language may under-fire pure IB “build a VDR extract / CIM datapack.” |
| Workflow | 5 | Phased extract → normalize → 8-tab build → scenarios → QC → delivery. Industry adaptations (SaaS, industrial, RE, healthcare). Formula patterns and anti-patterns. |
| Boundaries | 4 | Accuracy zero-tolerance, checklist, conservative vs aggressive normalization. Less explicit on client/legal confidentiality of CIM extracts. |
| Refs/scripts | 4 | Self-contained standards + Python row-ref patterns; depends on external **xlsx** skill (name may not match repo `xlsx-author`). |
| Consistency | 3 | Length/style outlier vs thin IB peers; framing is multi-vertical PE/IB/AM; “investment committee-ready” and portco language sits oddly as an IB-vertical primary skill. |

**Notes (deeper):** Extremely usable for sell-side financial appendices and buy-side CIM transcription. For synthesis backlog: (1) IB-first description/triggers, (2) resolve skill dependency name (`xlsx` vs `xlsx-author`), (3) optional split or shared-skill home if PE also needs the same pack.

---

### buyer-list — 3.8

| Dim | Score | Note |
|-----|-------|------|
| Triggers | 5 | Explicit phrase list matches coverage language (“buyer universe”, “who would buy this”, “financial sponsors”). |
| Workflow | 4 | Strategics (competitor / adjacent / vertical / platform) + sponsors (platform / add-on / growth), A/B/C and Tier 1–3, contact mapping, Excel output. Missing: geography/cultural buyers, explicit research steps (CapIQ screens, prior M&A pulls), reverse-inquiry intake. |
| Boundaries | 3 | Antitrust flag and seller include/exclude — good. No MNPI/wall-crossing, no “not a substitute for firm BD CRM,” no compliance on cold outreach. |
| Refs/scripts | 3 | Embedded assessment tables sufficient as framework; no research playbook or sample workbook layout. |
| Consistency | 4 | Matches thin-skill house style (Workflow + Important Notes). |

---

### cim-builder — 3.8

| Dim | Score | Note |
|-----|-------|------|
| Triggers | 5 | CIM / OM / info memo / sell-side materials — excellent. |
| Workflow | 4 | Standard sell-side TOC (exec summary → industry → growth → customers → ops → financials → appendix), tone rules, 40–60 page target, docx + Excel appendix. Lighter on drafting sequence, redaction levels (pre- vs post-NDA), and public-company / carve-out variants. |
| Boundaries | 3 | Disclaimer, management review, don’t hide material issues — solid professional instincts. Thin on forward-looking statement discipline, what belongs only in data room, regulation considerations for public targets. |
| Refs/scripts | 3 | TOC is the reference; no sample disclaimer language file or formatting standard. |
| Consistency | 4 | Aligned with teaser / process-letter family. |

---

### teaser — 3.8

| Dim | Score | Note |
|-----|-------|------|
| Triggers | 5 | “Blind teaser”, “anonymous profile”, sell-side one-pager — on point. |
| Workflow | 4 | Header / description / highlights / financials / transaction overview + dedicated anonymization checklist. Fits associate bar for structure. |
| Boundaries | 3 | Client + legal review; anonymization is effectively a boundary section. Could be sharper on “never disclose identity-revealing exact metrics in small sectors.” |
| Refs/scripts | 3 | Structure is the template; no visual sample. |
| Consistency | 4 | Peer of cim-builder / process-letter. |

---

### process-letter — 3.8

| Dim | Score | Note |
|-----|-------|------|
| Triggers | 5 | IOI / final round / management meeting invite — maps to live process language. |
| Workflow | 4 | Letter types, IOI content list, final-bid extras (SPA markup, financing, exclusivity, antitrust), mgmt meeting logistics. Could add process calendar attachment and RWI/escrow items common in later-round letters. |
| Boundaries | 3 | Legal + client approval called out. Weak explicit “do not create binding commitments / legal advice.” |
| Refs/scripts | 3 | Section outlines serve as templates. |
| Consistency | 4 | Family match. |

---

### deal-tracker — 3.8

| Dim | Score | Note |
|-----|-------|------|
| Triggers | 5 | Pipeline / weekly deal review / “where are we on” — natural. |
| Workflow | 4 | Setup fields, full auction milestone table, action items, weekly review agenda, Excel multi-tab output. Deal-type field exists but milestones are classic sell-side auction-centric (financing/reorg/buy-side not expanded). |
| Boundaries | 3 | Hygiene (owners, dates, archive). Missing: “does not replace firm CRM / compliance deal log”; confidentiality of code names. |
| Refs/scripts | 3 | Milestone table is enough scaffolding. |
| Consistency | 4 | House style. |

---

### merger-model — 3.8

| Dim | Score | Note |
|-----|-------|------|
| Triggers | 5 | Accretion/dilution, merger consequences, pro forma EPS — coverage/M&A standard. |
| Workflow | 4 | Inputs → purchase price → S&U → PF EPS → synergy/premium and mix sensitivities → breakeven → Excel + one-pager. Gaps vs associate full A/D: fully diluted share count, fixed vs floating exchange ratio, contribution analysis, ownership %, stub year, private target without EPS, PPA step-up methodology beyond a note. |
| Boundaries | 3 | GAAP vs cash EPS, synergy phase-in — technical guardrails. Missing explicit “not a fairness opinion / not full 3-statement model; escalate valuation.” No pointer to `xlsx-author` / `3-statement-model`. |
| Refs/scripts | 3 | Tables encode formulas at outline level; no calculation-standards sibling like pitch-deck. |
| Consistency | 4 | Matches thin transaction skills; weaker dependency hygiene than datapack. |

---

### strip-profile (`fsi-strip-profile`) — 2.8 (**not clean**; only pack skill with dim ≤ 2)

**Path:** `plugins/vertical-plugins/investment-banking/skills/strip-profile/SKILL.md`  
**Frontmatter name:** `fsi-strip-profile` (folder and README/command say `strip-profile`)

| Dim | Score | Note |
|-----|-------|------|
| Triggers | 3 | Description is capability-only; **no** phrase triggers, **no** negative triggers. Command `/one-pager` loads `skill: "strip-profile"` while registered name is `fsi-strip-profile` — load/trigger risk. |
| Workflow | 4 | Strong IB strip craft: research sources, metrics list, 4:3 quadrant layout, slide-by-slide approval, soffice visual QA. Internal inconsistency: quadrant targets say 6–8 bullets vs layout table “4–5 bullets”; title size 18pt in example vs table 24pt. |
| Boundaries | 3 | User approval gates and density rules. Assumes Bloomberg/FactSet/CapIQ/BamSEC access without fallback. Weak MNPI/confidentiality for non-public names. |
| Refs/scripts | **2** | Points to `examples/Nike_Strip_Profile_Example.pptx` — **file not present** under the skill or vertical. Mixed **Python** (`pptx`/Inches) and **PptxGenJS** JavaScript in the same skill. Vague “reference the PPTX skill” (repo has `pptx-author`). |
| Consistency | **2** | Name ≠ folder ≠ command reference; different doc structure from sell-side peers; mixed authoring stacks; conflicts with pitch-deck’s template-population model (from-scratch PptxGenJS vs fill existing template). |

**Deeper write-up:** This is the highest-blast structural problem in the pack. Content quality of the layout guidance is actually high for coverage one-pagers, but identity/naming, broken example path, and dual-code-stack issues will cause skill loading failures and implementation thrash. Prioritize for synthesis backlog (likely P1 structural / P0 if skill invocation by name is broken in product).

---

## Systemic findings

### S1 — Two quality tiers in one vertical

| Tier | Skills | Character |
|------|--------|-----------|
| **Heavy / production** | pitch-deck, datapack-builder, strip-profile | Long, code/QC heavy, external deps |
| **Thin process** | buyer-list, cim-builder, teaser, process-letter, deal-tracker, merger-model | ~75–110 lines, Workflow + Important Notes, no refs |

Thin skills are **usable frameworks** for an analyst (strong Triggers, good Workflow skeletons) but consistently soft on **Boundaries** (compliance, legal, system-of-record) and **References** (samples, data-source playbooks, authoring skill links). They fail the clean bar together for the same reasons — not nine independent failures.

### S2 — Boundaries usually = “Important Notes,” not hard scope

Only pitch-deck (and partially datapack description) encode hard anti-patterns and do-nots. Sell-side materials that leave the bank (teaser, CIM, process letter) should systematically require:

- Client approval before external distribution  
- Legal on disclaimers / process terms  
- No identity leakage (teaser) / no undisclosed material issues (CIM)  
- “Not legal advice / not a fairness opinion” where relevant  

Today these appear as soft tips, not mandatory gates.

### S3 — Authoring skill dependency names are inconsistent

| Skill | Claims dependency | Likely canonical in repo |
|-------|-------------------|--------------------------|
| datapack-builder | “xlsx skill” | `xlsx-author` (financial-analysis) |
| strip-profile | “PPTX skill” | `pptx-author` |
| pitch-deck | LibreOffice + XML edit patterns | Self-contained + refs |
| merger-model / deal-tracker | (none) | Should likely call `xlsx-author` |

### S4 — strip-profile identity and asset breakage

- Frontmatter `name: fsi-strip-profile` vs directory `strip-profile` vs command `skill: "strip-profile"`  
- Missing `examples/Nike_Strip_Profile_Example.pptx`  
- Python vs PptxGenJS mixed instructions  

### S5 — datapack is PE-native content sitting in the IB pack

Description and scenarios emphasize investment committee, portfolio companies, LBO downside cases. Still valuable for IB diligence packs, but positioning and triggers should lead with M&A/CIM/filings use cases when the skill lives under investment-banking.

### S6 — Intentional product gap: greenfield pitch books

`pitch-deck` correctly refuses from-scratch decks; `strip-profile` only covers company profile pages. Coverage bankers still ask for full pitch narratives (situation overview, valuation summary, process recommendations). That may be OK if owned by other skills (`pptx-author`, `deck-refresh`, `ib-check-deck` in financial-analysis) — but the IB vertical README markets “Presentations” without pointing users there. Cross-plugin routing is undocumented in these skill bodies.

### S7 — Sell-side process chain is implicit

No skill states the standard sequence or handoffs:

`buyer-list` ↔ `teaser` → NDA → `cim-builder` / `datapack-builder` → `process-letter` (IOI) → meetings → final process letter → `deal-tracker` throughout; `merger-model` / strip profiles for **buy-side or coverage pitch** threads.

Associates would benefit from one-line “related skills” footers (consistency / workflow).

---

## Suggested fix backlog seeds (for ticket 11 synthesis; do not implement here)

| Priority seed | Item | Skills |
|---------------|------|--------|
| **P0 / P1** | Align skill `name`, folder, and `/one-pager` load string; fix or remove Nike example path | strip-profile |
| **P1** | Normalize authoring deps to `xlsx-author` / `pptx-author`; pick one PPT stack for strip-profile | strip-profile, datapack-builder, merger-model |
| **P1** | Add explicit Boundaries blocks (legal/client, MNPI, do-not) to all outbound materials skills | teaser, cim-builder, process-letter, buyer-list |
| **P2** | Enrich thin workflows with data-source steps and variant processes (buy-side, carve-out, public target) | buyer-list, cim-builder, deal-tracker, merger-model |
| **P2** | IB-first reframe of datapack description/triggers; optional shared ownership with PE | datapack-builder |
| **P3** | Cross-skill “process map” / related-skills lines; README pointer to financial-analysis for comps/DCF/full decks | pack-level |
| **P3** | Resolve bullet-count and font-size contradictions inside strip-profile | strip-profile |
| **P4** | Sample artifacts (teaser one-pager, process letter skeleton, buyer-list xlsx shell) as references | thin sell-side set |

---

## Evidence index (absolute paths)

| Skill | SKILL.md |
|-------|----------|
| buyer-list | `/Users/aneenaananth/projects/financial-services/plugins/vertical-plugins/investment-banking/skills/buyer-list/SKILL.md` |
| cim-builder | `/Users/aneenaananth/projects/financial-services/plugins/vertical-plugins/investment-banking/skills/cim-builder/SKILL.md` |
| datapack-builder | `/Users/aneenaananth/projects/financial-services/plugins/vertical-plugins/investment-banking/skills/datapack-builder/SKILL.md` |
| deal-tracker | `/Users/aneenaananth/projects/financial-services/plugins/vertical-plugins/investment-banking/skills/deal-tracker/SKILL.md` |
| merger-model | `/Users/aneenaananth/projects/financial-services/plugins/vertical-plugins/investment-banking/skills/merger-model/SKILL.md` |
| pitch-deck | `/Users/aneenaananth/projects/financial-services/plugins/vertical-plugins/investment-banking/skills/pitch-deck/SKILL.md` |
| process-letter | `/Users/aneenaananth/projects/financial-services/plugins/vertical-plugins/investment-banking/skills/process-letter/SKILL.md` |
| strip-profile | `/Users/aneenaananth/projects/financial-services/plugins/vertical-plugins/investment-banking/skills/strip-profile/SKILL.md` |
| teaser | `/Users/aneenaananth/projects/financial-services/plugins/vertical-plugins/investment-banking/skills/teaser/SKILL.md` |

Related non-skill paths cited:

- `/Users/aneenaananth/projects/financial-services/plugins/vertical-plugins/investment-banking/commands/one-pager.md` (loads `strip-profile`)
- `/Users/aneenaananth/projects/financial-services/plugins/vertical-plugins/investment-banking/README.md`
- Pitch-deck refs under `.../pitch-deck/reference/`

---

## Bottom line

Against an M&A analyst/associate and coverage banker baseline, the investment-banking pack is **directionally right and mostly mid-to-high usable**: sell-side process skills score consistently ~3.8 with excellent triggers and solid workflows, while **pitch-deck is the quality benchmark (4.6)** and **datapack-builder clears the clean bar on completeness**. The pack fails a clean overall assessment because **seven of nine skills sit just under 4.0** (shared soft Boundaries + light References pattern) and **strip-profile is a structural outlier (2.8)** with naming mismatch, broken example reference, Consistency ≤ 2, and Refs ≤ 2. No skill rewrites performed in this ticket.
