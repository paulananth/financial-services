# 09 — Partner S&P Global skill pack review

Type: research  
Status: resolved  
Blocked by:  

## Question

For **partner-built S&P Global** (`plugins/partner-built/spglobal/skills/`, 3 skills: earnings-preview-beta, funding-digest, tear-sheet):

1. Research domain and job roles (equity research, corp dev / IB, capital markets) for a **role baseline**; note Kensho/Capital IQ MCP dependency under Boundaries.
2. Score each skill 1–5 on the five dimensions against that baseline.
3. Write findings to `.scratch/skill-quality-review/findings/09-partner-spglobal.md`. Also skim pack README.

## Answer

Findings: [`.scratch/skill-quality-review/findings/09-partner-spglobal.md`](../findings/09-partner-spglobal.md)

**Role baseline:** Equity research (sell-/buy-side), IB/M&A, corp dev, capital markets/VC coverage (funding digests), plus sales/BD on tear-sheet. Artifacts: pre-earnings HTML, audience-specific DOCX tear sheets, one-slide funding PPTX. Non-negotiables: CIQ/Kensho-sourced numbers only, fiscal/period integrity, AI disclaimer, no fabricated deal values or management bios.

**MCP (Boundaries, not score penalty):** Hard dependency on Kensho LLM-ready API / Capital IQ via `.mcp.json` → `https://kfinance.kensho.com/integrations/mcp`. Skills unusable without authenticated S&P subscription.

**Scores (T / W / B / R / C → overall):**

| Skill | Scores | Overall | Clean bar |
|-------|--------|---------|-----------|
| earnings-preview-beta | 4 / 5 / 5 / 5 / 3 | **4.4** | Yes |
| funding-digest | 5 / 5 / 4 / 5 / 4 | **4.6** | Yes |
| tear-sheet | 5 / 5 / 5 / 5 / 4 | **4.8** | Yes |

All three clear clean bar (overall ≥ 4.0, no dim ≤ 2). Soft spots are Consistency (naming: folder `earnings-preview-beta` vs frontmatter `earnings-preview-single`; README “Industry Transaction Summaries” vs `funding-digest`) and pack path-convention drift. tear-sheet is strongest; pack mean overall **4.6**.
