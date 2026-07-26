# 05 — Operations (KYC) skill pack review

Type: research  
Status: resolved  
Blocked by:  

## Question

For the **operations** vertical (`plugins/vertical-plugins/operations/skills/`, 2 skills: kyc-doc-parse, kyc-rules):

1. Research domain and job roles (KYC/AML analyst, onboarding ops) for a **role baseline** (risk rating, rules grid, auditability).
2. Score each skill 1–5 on the five dimensions against that baseline.
3. Write findings to `.scratch/skill-quality-review/findings/05-operations.md`.

## Answer

**Findings:** [`.scratch/skill-quality-review/findings/05-operations.md`](../findings/05-operations.md)

**Role baseline:** KYC/AML analyst / onboarding CDD ops — inventory → extract (null over invent) → screen → firm rules grid with cited outcomes → risk rating + factor table → disposition for human sign-off; never final-approve; untrusted applicant docs.

**Scores (Triggers / Workflow / Boundaries / Refs / Consistency → overall):**

| Skill | T | W | B | R | C | Overall | Clean (≥4.0, no dim ≤2)? |
|---|---:|---:|---:|---:|---:|---:|---|
| kyc-doc-parse | 4 | 4 | 5 | 3 | 5 | **4.2** | Yes |
| kyc-rules | 4 | 4 | 5 | 3 | 5 | **4.2** | Yes |

**Pack average: 4.2.** Soft spot only: References/scripts (3) — inline schemas, no sample packet/grid. Boundaries are the strength (5). No skill rewrites performed.
