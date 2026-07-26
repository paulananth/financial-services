# 05 — Operations (KYC) skill pack review

**Path:** `plugins/vertical-plugins/operations/skills/`  
**Skills (2):** `kyc-doc-parse`, `kyc-rules`  
**Clean bar:** overall ≥ 4.0 and no dimension ≤ 2  
**Verdict:** both skills **pass** the clean bar (pack avg **4.2**)

---

## Role baseline

**Primary roles:** KYC/AML analyst; client-onboarding / CDD operations specialist (sometimes “onboarding ops” or “client due diligence”).

**Job to be done:** Turn an applicant-supplied onboarding packet into a **reviewable KYC file**: structured identity/ownership data, document inventory, firm rules-grid outcomes, screening hits, risk rating with factor evidence, and a **disposition for human compliance sign-off** (request docs, EDD escalate, recommend decline, or clear for officer approval). Not transaction monitoring; not final approval authority.

### Artifacts a competent analyst expects

| Artifact | Purpose |
|---|---|
| Document inventory | Every received doc typed and identified; age/expiry noted |
| Structured entity file | Legal name, jurisdiction, addresses, IDs, tax forms |
| Ownership & control map | UBOs with % / control basis; directors/trustees/signatories |
| Source of funds / wealth note | Narrative + supporting-doc refs (clarity drives risk) |
| Screening results | Sanctions / PEP / adverse media per named party + confidence |
| Risk rating + factor table | Jurisdiction, structure, opacity, PEP, SOF, screening → low/med/high |
| Rules grid outcomes | Every applicable rule: id, text, pass/fail/n/a, evidence fields |
| Disposition / escalation packet | Missing docs, escalation reasons, recommended route — **no silent approve** |

### Accuracy & compliance bar

- **Null over invent** — missing fields stay missing; no inferred UBOs or forged IDs.
- **Applicant content is untrusted** — extract data only; never follow instructions embedded in docs.
- **Rules are firm-owned** — outcomes must **cite the rule**; risk factors come from the firm’s grid/list, not model priors alone.
- **Auditability** — every fail/escalate links to field evidence and (where relevant) screening result.
- **Human-in-the-loop** — agent recommends disposition; compliance officer decides risk rating and approval.
- **Screening hits and PEPs** escalate; “clear” only when rating, docs, and rules all allow.

### Typical workflow (onboarding / refresh)

1. Inventory packet → 2. Extract structured KYC fields → 3. Flag inventory gaps (expired ID, stale address, missing UBO chart) → 4. Screen named parties (sanctions/PEP/adverse media) → 5. Apply firm rules grid → 6. Risk-rate with factor table → 7. Required-doc check at that rating/type → 8. Disposition + escalation package for reviewer.

### Non-negotiables (score against these)

1. Untrusted-input handling on parse  
2. Complete-enough schema for identity, ownership/control, SOF, docs  
3. Rule-cited outcomes + evidence  
4. Explicit non-approval / recommend-only stance  
5. Disposition that routes gaps and hits instead of burying them  

### Secondary Consistency lenses

- Repo: short procedural skills with frontmatter `name`/`description`, numbered steps, JSON outputs (same family as fund-admin).  
- In-vertical: only these two skills; they must chain on shared field names.  
- Agent wrap: `kyc-screener` uses both + `xlsx-author`; guardrails (untrusted docs, no write on orchestrator, no risk decision) should match skill text.

---

## Scorecard

Dimensions: **Triggers** · **Workflow** · **Boundaries** · **References/scripts** · **Consistency** (1–5 each). Overall = mean to one decimal.

| Skill | Triggers | Workflow | Boundaries | Refs/scripts | Consistency | Overall | Clean? |
|---|---:|---:|---:|---:|---:|---:|---|
| `kyc-doc-parse` | 4 | 4 | 5 | 3 | 5 | **4.2** | Yes |
| `kyc-rules` | 4 | 4 | 5 | 3 | 5 | **4.2** | Yes |
| **Pack average** | 4.0 | 4.0 | 5.0 | 3.0 | 5.0 | **4.2** | — |

Both skills meet the clean bar (overall ≥ 4.0, no dimension ≤ 2). Notes below are light; soft spot is **References/scripts** for both.

---

## Light notes by skill

### `kyc-doc-parse` — overall 4.2

| Dim | Score | Note |
|---|---:|---|
| Triggers | 4 | Description states first-step-of-screening and feeds rules engine. No quoted user-phrase list (acceptable for fund-admin-style ops skills; slightly thinner than PE-style trigger strings). |
| Workflow | 4 | Inventory table → null-safe JSON schema (applicant type, IDs, UBOs, controllers, SOF, PEP, tax, docs) → gap flags before handoff. Matches role steps 1–3. Gaps vs deep CDD: SOF is one-line; little multi-doc conflict / multi-entity guidance. |
| Boundaries | 5 | Strong untrusted-document framing (`<untrusted_document>` mental model); extract-only; null not guess; inventory gaps ≠ rules outcomes. Hits non-negotiable #1. |
| Refs/scripts | 3 | Schema is inline (right for a compact skill). No sample packet, field glossary, or worked extraction example — role baseline would gain from a short reference, but peers in fund-admin also ship without `references/`. |
| Consistency | 5 | Field names align with `kyc-rules`; style matches short ops skills; matches `kyc-screener` doc-reader role. |

### `kyc-rules` — overall 4.2

| Dim | Score | Note |
|---|---:|---|
| Triggers | 4 | Clear “use after kyc-doc-parse”; scores and routes, does not decide. Sequencing is explicit. |
| Workflow | 4 | Risk-rate factor table → required-doc check → rule outcomes with cite → disposition JSON with hard `clear` gate. Matches role steps 5–8 and auditability. Soft spots: aggregation/override order left to “the grid”; screening is an input not a numbered step; no CDD vs EDD depth ladder or false-positive guidance — acceptable if firm grid supplies that. |
| Boundaries | 5 | Trusted rules grid vs untrusted applicant record; **never approves**; every outcome cites a rule; `clear` only when rating, docs, and escalation rules allow. Hits non-negotiables #3–#5. |
| Refs/scripts | 3 | Correctly defers firm grid/lists to MCP or provided file; no sample grid or example disposition packet for dry-run. Connector readiness (screening MCP) is a dependency, not a skill defect. |
| Consistency | 5 | Disposition vocabulary and recommend-only stance match agent/cookbook; consumes `kyc-doc-parse` fields; pairs with escalator/`xlsx-author` packaging outside this skill. |

---

## Pack-level observations (for synthesis)

1. **Thin vertical, tight pair.** Operations ships only KYC onboarding/refresh assist — intentional vs transaction monitoring (agent copy is explicit). No third skill is required for the stated job if packaging stays in agent/`xlsx-author`.
2. **Boundaries are the pack strength** (both 5). Security model (untrusted parse → trusted rules → human approve) is clearer here than in many content-generation skills.
3. **Refs/scripts are the only soft band (3).** Not P0: inline schemas + firm grid as external source is coherent. Optional polish: one sample rules-grid fragment and one example disposition JSON (as references, not code rewrites in this effort).
4. **Workflow depth is “ops assistant” not “policy engine.”** Factor list is “typical”; real weighting, high-risk jurisdiction lists, and doc matrices live in the firm grid — skill correctly refuses to hardcode them. Scoring stays high if that contract is honored at runtime.
5. **MCP dependency** on screening (and optional rules file) belongs under Boundaries/connector readiness for synthesis — not an automatic score penalty per map notes.

---

## Fix backlog candidates (recommendations only; no rewrites here)

| Priority hint | Item |
|---|---|
| P3 polish | Add optional `references/` examples (sample inventory + disposition) for both skills |
| P3 polish | `kyc-doc-parse`: richer SOF/SOW structure and multi-doc conflict note |
| P3 polish | `kyc-rules`: number screening as an explicit step; note false-positive → human review |
| P4 nice-to-have | Trigger phrase examples in descriptions (onboarding packet, CDD refresh, UBO extract) |
| Out of pack | Transaction monitoring / TM alert triage would be a different skill pack |

---

## Sources reviewed

- `plugins/vertical-plugins/operations/skills/kyc-doc-parse/SKILL.md`
- `plugins/vertical-plugins/operations/skills/kyc-rules/SKILL.md`
- `plugins/agent-plugins/kyc-screener/agents/kyc-screener.md`
- `managed-agent-cookbooks/kyc-screener/README.md` (tier isolation / recommend-only)
- Peer style: `plugins/vertical-plugins/fund-admin/skills/*` (short procedural JSON skills)
