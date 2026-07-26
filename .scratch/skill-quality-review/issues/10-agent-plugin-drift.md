# 10 — Agent-plugin skill drift spot-check

Type: research  
Status: resolved  
Blocked by:  

## Question

Spot-check whether `plugins/agent-plugins/<slug>/skills/` copies have **drifted** from their `plugins/vertical-plugins/` sources (repo rule: edit verticals, sync with `scripts/sync-agent-skills.py`).

1. Identify which agent bundles embed which skills (from layout / sync script).
2. Diff a representative sample: at least one shared skill across multiple agents (`xlsx-author` or `audit-xls`) and one unique skill per agent pack if feasible; expand if drift is found.
3. Report: clean vs drifted paths, nature of drift, recommendation (re-sync only vs fix-source-then-sync).
4. Write findings to `.scratch/skill-quality-review/findings/10-agent-plugin-drift.md`.

Do **not** re-score every copy as a unique skill.

## Answer

**No drift.** Full census of **51** bundled skill dirs (10 agents) are byte-identical (recursive) to vertical sources; 0 missing sources. Shared skills (`xlsx-author`×8, `audit-xls`×6, plus comps/pptx/models/sector) and all 23 unique-to-one-agent skills are CLEAN and inter-agent copies match. **No re-sync needed.** Keep edit-verticals → `sync-agent-skills.py`; `check.py` §4b already gates shallow drift. Details: [findings/10-agent-plugin-drift.md](../findings/10-agent-plugin-drift.md).
