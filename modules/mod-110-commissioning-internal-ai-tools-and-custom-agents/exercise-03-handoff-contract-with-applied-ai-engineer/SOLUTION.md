# Exercise 03 — Handoff Contract with Applied AI Engineer — Reference Solution

> Module: `mod-110-commissioning-internal-ai-tools-and-custom-agents`
> Exercise type: design / worked example
> Exercise brief: [`lessons/mod-110-commissioning-internal-ai-tools-and-custom-agents/exercises/exercise-03-handoff-contract-with-applied-ai-engineer.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-110-commissioning-internal-ai-tools-and-custom-agents/exercises/exercise-03-handoff-contract-with-applied-ai-engineer.md) (in the learning repo)

## 1. Solution overview

The deliverable is a **handoff contract** between the AI Enablement Lead and the Applied AI Engineer assigned to the commissioning engagement. The contract is the one-page written agreement that turns the commissioning brief (Exercise 01) into a jointly operated engagement. Without this artifact, the brief is a one-sided handoff; with it, the engagement has named decision rights, named artifact ownership, named gate choreography, and named escalation.

Posture checks this solution encodes:

- **Decision rights are explicit and asymmetric.** Enablement owns the outcome and the user-facing posture; Applied AI Engineering owns the implementation and the engineering posture. Neither function owns the other's territory. The council owns go/no-go at the sensitive-data and GA gates.
- **Artifact ownership is one-to-one.** Every artifact that crosses the function boundary has exactly one owner (Driver) and exactly one approver (A). No artifact has two Drivers.
- **Gate choreography is pre-agreed.** The brief's gates are the canonical gates; this contract names who presents what at each gate and who signs the gate-pass memo.
- **SLAs are two-way.** Enablement commits to availability for user-posture review and operator-language validation; Applied AI Engineering commits to engineering lead time, eval-harness cadence, and incident-response availability.
- **Role-name addressing throughout.** The contract survives personnel changes.
- **Exit is planned at entry.** The contract names when the engagement ends (success, kill, or hand-back) and what the inheritance posture is for the artifact after exit.

## 2. Implementation — worked answer (`enablement-ai-engineer-handoff-contract.md`)

```
AI Enablement ↔ Applied AI Engineering — Handoff Contract
Engagement:      Billing-Dispute Triage Agent (BDTA) — brief ID BDTA-FY<YYYY>Q<N>-01
Effective:       <!-- org-specific: effective date -->
Signatories:     AI Enablement Lead (this role), Applied AI Engineer (named at role level),
                 head-of-ai-governance (L60) for the DACI rows marked A to council
Next review:     End of commissioning window, or off-cycle per Section 7 trigger
```

---

### Section 1 — Purpose

This contract names how the AI Enablement function and the Applied AI Engineering function jointly operate the commissioning engagement scoped by the attached brief. It is paired one-to-one with a specific brief; multi-engagement partnership arrangements use separate contracts. It does not supersede the organisation's engineering standards, the governance council charter, or the data-handling policy. Where this contract and a corporate policy differ, the corporate policy wins and the contract is amended within 30 days.

### Section 2 — Decision rights (DACI)

| Decision | Enablement Lead | Applied AI Engineer | Governance council | Business sponsor |
|---|---|---|---|---|
| Problem framing and user-facing scope (ratifies brief Section 1 / 2) | A | C | I | C |
| Technical architecture (retrieval topology, inference provider, prompt structure, guardrails) | C | D/A | I | I |
| Data-handling implementation (classification propagation, retention, audit log) | C | D | A | I |
| Eval-harness design (test set composition, metrics, drift monitor) | C | D/A | I | I |
| User experience / integration points in the operator console | D/A | C | I | C |
| Training content and SOP co-authoring (per mod-103 / mod-104) | D/A | C | C | C |
| Rollout cohort selection (which users at which gate) | D/A | C | C | A |
| Go / no-go at POC gate | C | D | I | A |
| Go / no-go at limited-GA gate | C | C | A | A |
| Go / no-go at general-availability gate | C | C | A | A |
| Incident response during the commissioning window | C | D | C | I |
| Kill / sunset on the commissioning engagement | D | C | A | A |
| Exit posture at engagement end (steward-of-record, platform ownership, etc.) | D | C | C | C |

The Applied AI Engineer is Driver on the engineering decisions and Driver on the POC gate; the Enablement Lead is Driver on the user-facing posture and Driver on the kill decision. The two drivers remain distinct across the full table.

### Section 3 — Artifact ownership and crossing points

Every artifact that crosses the function boundary has exactly one Driver (D) and exactly one Approver (A).

| Artifact | Driver | Approver | Downstream consumers |
|---|---|---|---|
| Commissioning brief (Exercise 01) | Enablement Lead | Business sponsor | Applied AI Engineering, Security, Legal, governance council |
| Threat model note (OWASP ML Top 10 + MITRE ATLAS mapping) | Applied AI Engineer | Security | Governance council |
| Technical design document | Applied AI Engineer | Engineering area lead `<!-- org-specific -->` | Enablement Lead, Security |
| Data-handling implementation plan | Applied AI Engineer | Governance council | Legal / privacy, Security |
| Eval-harness and test-set spec | Applied AI Engineer | Applied AI Engineering area lead | Enablement Lead (consumes the ongoing results) |
| User-facing SOP and training materials | Enablement Lead | Business sponsor | Operators, L&D |
| Rollout cohort plan | Enablement Lead | Business sponsor | Applied AI Engineer, L&D |
| Gate-pass memos (POC, limited-GA, GA) | Co-authored | Per DACI row in Section 2 | Executive scorecard per mod-106 |
| Incident runbook (per mod-109) | Applied AI Engineer (technical) + Enablement Lead (operator-facing) | Governance council | Operators, SecOps |
| Measurement plan (Exercise 04) | Enablement Lead | Business sponsor (metrics), Applied AI Engineering area lead (instrumentation) | Executive scorecard, Finance |
| Exit / inheritance plan | Enablement Lead | Applied AI Engineering area lead | Platform ownership `<!-- org-specific -->` |

### Section 4 — Gate choreography

Three gates in sequence. Per gate the contract names who presents, who signs, and what the attached artifacts are.

| Gate | Presenter | Attached artifacts | Signatories on the gate-pass memo | Kill-criterion check |
|---|---|---|---|---|
| Proof-of-concept (POC) | Applied AI Engineer | Technical design, threat model note, eval-harness results on the POC test set | Applied AI Engineer (D), Enablement Lead (C), Engineering area lead (A) | Faithfulness threshold; prompt-injection resilience spot-check |
| Limited-GA (shadow / opt-in pilot) | Enablement Lead presents user-facing posture; Applied AI Engineer presents eval + incident readiness | User-facing SOP, rollout cohort plan (small), eval-harness results on production-like data, incident runbook | Enablement Lead (D), Applied AI Engineer (C), governance council (A), business sponsor (A) | All brief Section 4 leading indicators trending correctly; no Sev-2+ incidents; CSAT ≥ baseline − 2 |
| General-availability (GA) | Enablement Lead presents outcome results; Applied AI Engineer presents operational readiness | Updated SOP, full rollout cohort plan, eval-harness cadence commitment, measurement plan (Exercise 04) | Enablement Lead (D), Applied AI Engineer (C), governance council (A), business sponsor (A) | All brief Section 4 targets met or within tolerance; any miss > 20% triggers kill per brief Section 10 |

Gate-pass memos are one page. They name the attached artifacts, the gate decision, the next gate's date (or the exit date), and the incident route in force during the next phase.

### Section 5 — Service-level commitments (two-way)

**Enablement Lead commits to:**

| SLA | Target | Source / assumption |
|---|---|---|
| Availability for user-posture review during the commissioning window | ≥ 4 hours/week dedicated | — |
| Operator-language validation on SOP and UI copy | Within 3 business days of a draft | — |
| Rollout cohort list for limited-GA | ≥ 2 weeks before the gate | Allows L&D to prepare the cohort per mod-104 |
| Post-incident retrospective lead within the commissioning window | ≤ 5 business days after incident close | Per mod-109 retrospective cadence |
| Scorecard-ready monthly operator-side metrics | ≤ 5 business days after month close | Per mod-106 |

**Applied AI Engineer commits to:**

| SLA | Target | Source / assumption |
|---|---|---|
| Engineering lead time from brief acceptance to POC gate | ≤ `<!-- org-specific: engineering lead-time standard -->` weeks | — |
| Eval-harness cadence during the commissioning window | Weekly against the spot-check sample; daily against drift monitors | Per brief Section 4 row 5 |
| Incident response during the commissioning window | On-call rotation covering business hours in the operator's region, with a Sev-2+ escalation route to the Applied AI Engineering area lead | Per mod-109 on-call posture |
| Threat-model note refresh | At each gate, and on any material architecture change in between | Per `nist-ai-rmf` MEASURE function cadence |
| Technical-design document and data-handling plan | Delivered ≥ 2 weeks before the limited-GA gate | — |

**Joint commitments:**

- Co-author the incident runbook (per mod-109) before the limited-GA gate; neither party ships without it.
- Co-author the measurement plan (per Exercise 04) before the limited-GA gate; the plan is a condition of entry to the gate, not an output of the gate.
- Use role-name addressing in all written communications, per mod-103 posture.
- Share information that would materially change the other function's work within 2 business days of learning it.
- Keep the artifact set in a single engagement workspace; no artifact-of-record lives outside that workspace.

### Section 6 — Escalation

Escalation path (in order):

1. The two signatories convene a 30-minute working session within 2 business days of the flagged escalation.
2. If unresolved, the Applied AI Engineering area lead and the business sponsor are briefed jointly within 3 business days.
3. If still unresolved, the governance council receives a written pre-read (not live debate) at the next scheduled council session, or the session is re-scheduled to within 5 business days if the escalation is time-critical.
4. CISO and CFO offices are briefed on any incident-driven escalation at step 2 or beyond, per mod-109.

The council is the ratification venue, not the debate venue. Escalations arrive with a proposed resolution.

### Section 7 — Reversibility and exit

The contract has three exit paths; all three are named here so that end-of-engagement is not a renegotiation.

- **Success exit — GA.** At the GA gate, the contract hands off to the ongoing-operations posture named in the exit / inheritance plan (Section 3). Enablement remains the user-facing owner; Applied AI Engineering hands off operational ownership per the named platform ownership. The contract archives.
- **Kill exit.** On any brief Section 10 kill criterion, the contract terminates. The Applied AI Engineer leads an orderly sunset of the technical artifacts (deprovision credentials, archive logs, remove integrations); the Enablement Lead leads the operator-facing communications and the mod-109 incident retrospective where applicable. A one-page post-engagement memo is filed and both signatories sign.
- **Hand-back exit.** If the engagement is paused or returns to the Exercise 02 decision (e.g., the prototype is inherited lightweight instead of productionised), the contract is amended to the lighter commitment set or archived with a referenced successor contract.

**Contract-revisit triggers (off-cycle):**

- Either signatory's role scope changes materially.
- An incident at this tool, or a peer tool, surfaces patterns (per mod-109 retrospective) that argue for a change in posture.
- A regulatory or policy change invalidates a load-bearing clause of Section 3 or Section 5.
- The brief itself is revised beyond a 25% scope change.
- Two consecutive gate reviews show variance > 20% between plan and actual.

### Section 8 — Signatures

| Role | Signatory `<!-- org-specific: name -->` | Date | Version |
|---|---|---|---|
| AI Enablement Lead | <!-- org-specific --> | <!-- org-specific --> | 1.0 |
| Applied AI Engineer (named at role level, with area lead ratification) | <!-- org-specific --> | <!-- org-specific --> | 1.0 |
| Business sponsor | <!-- org-specific --> | <!-- org-specific --> | 1.0 |

### End of contract

---

### 2.1 Decision rationale — why this shape, not another

- **Why DACI and not RACI.** The failure mode of RACI is that Enablement and Applied AI Engineering both get listed as Responsible-and-Accountable on everything, which is RACI's way of saying "no decision rights have been assigned." DACI's Driver / Approver split names the asymmetry: the user-facing Driver and the engineering Driver are distinct, and the contract keeps them distinct across the table.
- **Why artifact-level ownership is one-to-one.** Every two-Driver artifact becomes a scheduling meeting. Giving each artifact one Driver and one Approver is what makes the artifact pipeline flow without a steering committee.
- **Why the contract is paired one-to-one with a brief.** A multi-engagement partnership contract is a different shape (closer to the mod-107 Exercise 04 Procurement / Finance contract). The per-engagement contract keeps gate choreography, SLAs, and exit posture specific to the engagement; multi-engagement averages lose the specificity that makes the contract reviewable at gates.
- **Why exit is designed at entry.** The three exit paths (Success-GA, Kill, Hand-back) are the only three; naming them at entry prevents the end of the engagement from becoming a renegotiation under pressure. Kill-at-entry is particularly important because the kill decision happens at the moment of lowest institutional appetite for killing.
- **Why two-way SLAs.** One-way SLAs (Enablement commits to Engineering only, or Engineering commits to Enablement only) breed asymmetry. The function with no reciprocal commitment becomes the silent bottleneck.
- **Why role-name addressing.** The contract must survive a re-org. Names expire; roles don't.
- **Why the eval-harness cadence is in Section 5, not Section 3.** The eval-harness spec is an artifact (Section 3); the cadence under which it runs is an operational commitment (Section 5). Conflating the two leaves the cadence unspecified when the spec is updated.

## 3. Validation steps

1. **Eight numbered sections** in the order shown (Purpose, Decision rights, Artifact ownership, Gate choreography, SLAs, Escalation, Reversibility and exit, Signatures).
2. **DACI table in Section 2** with ≥ 13 decisions. Every row has a Driver and an Approver, and they are not the same role. Enablement is not Driver on engineering decisions; Applied AI Engineering is not Driver on user-facing decisions.
3. **Artifact ownership table in Section 3** names ≥ 10 crossing-point artifacts with one Driver and one Approver per artifact.
4. **Gate choreography table in Section 4** names three gates with presenter, attached artifacts, signatories, and kill-criterion check per gate.
5. **Two-way SLAs in Section 5.** Both sides and joint commitments present. A one-way contract fails.
6. **Escalation path is numbered** and routes the governance council as a pre-read, not a live debate.
7. **Section 7 names three exit paths** (Success-GA, Kill, Hand-back) and ≥ 5 contract-revisit triggers.
8. **Role-name addressing throughout.** Grep for personal names and personal pronouns.
9. **No vendor product names** in any section.
10. **`org-specific` tags** on specific numbers (lead times, availability hours, cohort sizes, platform-ownership destinations, signatory names).
11. **Explicit cross-references** to Exercise 01 (brief), Exercise 02 (decision artifact feeding this engagement), Exercise 04 (measurement plan), mod-103 (role-name discipline, SOP co-authoring), mod-104 (training-cohort cadence), mod-106 (scorecard cadence), mod-109 (incident runbook and retrospective cadence).

## 4. Rubric / review checklist

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | Eight numbered sections in the order shown | 5 | Missing or re-ordered. |
| R2 | DACI table has ≥ 13 decisions with Driver and Approver distinct per row | 15 | Collapsed roles or missing decisions. |
| R3 | Artifact ownership table has one Driver and one Approver per artifact | 10 | Two-Driver rows, or artifacts missing. |
| R4 | Three gates with presenter, attached artifacts, signatories, and kill-criterion check per gate | 15 | Any gate missing presenter/artifacts/kill-check. |
| R5 | Two-way SLAs (Enablement + Engineering + joint) with concrete targets | 15 | One-way SLAs, or vague targets. |
| R6 | Escalation routes council as a pre-read, not live debate | 5 | Escalation path missing or routes council as live debate. |
| R7 | Three exit paths named and ≥ 5 off-cycle revisit triggers | 10 | Fewer than three exit paths, or fewer than five triggers. |
| R8 | Role-name addressing throughout | 10 | People names used in load-bearing clauses. |
| R9 | Cross-references to Exercise 01 / 02 / 04 and mod-103 / 104 / 106 / 109 | 5 | No cross-references. |
| R10 | `org-specific` tags on specific numbers and role assignments | 5 | Unmarked quoted numbers. |
| R11 | No vendor product names; no commercial terms baked in | 5 | Vendor names or commercial terms embedded. |

**Pass threshold:** ≥ 85/100 and no R2 / R4 / R5 fail. R2 (DACI integrity), R4 (gate choreography with kill-checks), and R5 (two-way SLAs) are the three discriminators between a contract that holds up at gates and a contract that quietly becomes an "Enablement owns everything" asymmetry.

## 5. Common mistakes

- **Collapsing DACI into RACI.** Enablement gets listed as both Responsible and Accountable for user-facing work *and* engineering work. The contract reads as one function owning two scopes, which is how the engineering function politely disengages.
- **Writing the contract as a one-way SLA on Engineering.** Engineering commits lead times and incident response; Enablement commits nothing. At the first slipped lead time the contract has no counter-commitment to fall back on and the relationship frays.
- **Two Drivers on one artifact.** The technical design doc with Enablement and Engineering both named as Drivers is an artifact that never ships. One Driver per artifact; the other side is Consulted.
- **Omitting exit paths.** End-of-engagement becomes a renegotiation under pressure if the three exit paths are not named up-front. The kill exit is especially important to pre-commit, because killing is hardest in the moment the pilot indicators turn mixed.
- **Scheduling the council as a live debate.** The council ratifies; it does not debate. Escalations arrive as a pre-read with a proposed resolution.
- **Addressing the contract to people names.** The contract expires with the next re-org. Use role names.
- **Eval-harness cadence left unspecified.** The spec is in Section 3; the cadence is in Section 5. Both must be named or the spec will be built once and never re-run.
- **Promising general availability at contract-signing time.** GA is a decision at the GA gate. Contracts that pre-commit GA bypass the gate structure and route around the council's approval row in Section 2.
- **Not pairing the contract to a specific brief.** A generic multi-engagement partnership contract loses the specificity that makes each gate reviewable.
- **Embedding commercial terms.** The handoff contract is a working-relationship artifact. Commercial terms (inference-provider pricing, platform-ownership chargebacks) belong in the mod-107 Exercise 04 partnership contract and in vendor-specific agreements, not here.

### 5.1 Stretch — standing templates attached to the contract

For a mature program, each contract carries a short appendix of standing templates so that the engagement does not re-author documents at each gate. The appendix is kept in the engagement workspace, not inlined into the contract, so the contract stays one page:

- Template: **gate-pass memo** (one page, three variants — POC, limited-GA, GA).
- Template: **threat-model note** (OWASP ML Top 10 rows × MITRE ATLAS techniques × mitigation posture).
- Template: **eval-harness results pack** (weekly spot-check sample, drift-monitor readouts).
- Template: **incident runbook skeleton** (per mod-109, tailored to the operator cohort).
- Template: **post-engagement memo** (one page, for Kill and Hand-back exits).

Each template is one page with a stable structure. The engagement does not re-invent its paperwork; it fills known shapes.

## 6. References

- **Learning material (local):**
  - [Exercise 01 — Commissioning Brief Drill](../exercise-01-commissioning-brief-drill/SOLUTION.md) — the brief this contract pairs with.
  - [Exercise 02 — Prototype Inheritance and Productionise Decision](../exercise-02-prototype-inheritance-and-productionise-decision/SOLUTION.md) — the upstream decision artifact that routes the engagement into this contract.
  - [Exercise 04 — Commissioned Tool Measurement Plan](../exercise-04-commissioned-tool-measurement-plan/SOLUTION.md) — the measurement plan that Section 3 lists as an artifact crossing the boundary.
  - [mod-103 — Policy Co-authoring with Governance](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-103-policy-co-authoring-with-governance) — role-name addressing and SOP co-authoring disciplines.
  - [mod-104 — Training Programs and AI Literacy Curriculum](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-104-training-programs-and-ai-literacy-curriculum) — training-cohort lead-time informing the Section 5 Enablement SLA on rollout cohort timing.
  - [mod-106 — Outcome Measurement and Executive Reporting](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-106-outcome-measurement-and-executive-reporting) — the scorecard cadence feeding the monthly operator-metrics SLA.
  - [mod-107 — Budget, ROI, and Build-vs-Buy at Org Scope](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-107-budget-roi-and-build-vs-buy-at-org-scope) — the Procurement / Finance partnership contract pattern this per-engagement contract complements.
  - [mod-109 — AI Incident Response and Enablement-Side Rollback](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-109-ai-incident-response-and-enablement-side-rollback) — the incident runbook, on-call posture, and retrospective cadence referenced across Sections 3, 5, and 7.
- **Official standards and frameworks:**
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — the GOVERN function underpins the asymmetric decision rights; MEASURE function underpins the eval-harness cadence.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — threat posture lens for the Section 3 threat-model note.
  - [MITRE ATLAS](https://atlas.mitre.org/) — adversarial-technique lens alongside OWASP for the threat-model note and the gate kill-criterion check.
