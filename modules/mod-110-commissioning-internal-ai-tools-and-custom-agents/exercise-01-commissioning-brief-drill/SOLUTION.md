# Exercise 01 — Commissioning Brief Drill — Reference Solution

> Module: `mod-110-commissioning-internal-ai-tools-and-custom-agents`
> Exercise type: design / worked example
> Exercise brief: [`lessons/mod-110-commissioning-internal-ai-tools-and-custom-agents/exercises/exercise-01-commissioning-brief-drill.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-110-commissioning-internal-ai-tools-and-custom-agents/exercises/exercise-01-commissioning-brief-drill.md) (in the learning repo)

## 1. Solution overview

The deliverable is a **commissioning brief**: a one-to-two-page written artifact the AI Enablement Lead hands to the Applied AI Engineering function to initiate work on an internal AI tool or custom agent. The brief is the contract that converts a business intuition ("we should build an X") into a scoped engagement with named outcomes, named decision rights, named risk posture, and named exit criteria. It is written *before* a single line of production code is cut.

The brief is distinct from three adjacent artifacts and must not be collapsed into any of them:

- It is **not a vendor intake questionnaire** (that is the mod-102 shape, used when the path is Buy).
- It is **not a product spec**. Applied AI Engineering will author the technical spec from the brief; the brief names what, for whom, and why — not how.
- It is **not a project plan**. The brief names gates; the PM artifacts (schedule, resourcing, RAID log) hang off the gates.

Posture checks this solution encodes:

- **Every brief is addressed to a named business outcome, not a technology enthusiasm.** The outcome is phrased in the operator's language ("reduce L2 support-ticket handling time for billing disputes") and ties to a measurable baseline.
- **The brief carries a risk posture section tied to `owasp-ml-top-10` and `mitre-atlas`.** Any brief that says "low risk" without naming the threats it has considered is not ready for engineering intake.
- **Decision rights are explicit and asymmetric.** The Enablement Lead owns the outcome; Applied AI Engineering owns the implementation; the governance council owns go/no-go on sensitive-data or high-impact scope. Nobody is Driver and Approver on the same decision.
- **A kill criterion exists.** The brief names at least one pre-committed condition under which the commissioning engagement is sunset rather than extended.
- **Data classification is named up-front.** Data domain, sensitivity tier, retention class, and cross-border posture are decided at brief time, not after the prototype is written.
- **The brief is reversible.** It is ratified, not signed-in-blood; a trigger list names when it is revisited.

## 2. Implementation — worked answer (`commissioning-brief.md`)

### 2.1 Worked scenario

- Requesting business unit: Customer Operations.
- Working problem: L2 support agents spend material time on billing-dispute triage — summarising prior-ticket history, pulling account context, and drafting the first-reply template — before the human judgement part of the work begins.
- Proposed capability: an internal retrieval-grounded agent that ingests the active case, prior-case history, and account context, and emits a structured triage summary + proposed first-reply draft, as a sidecar to the existing agent console.
- Build / Buy / Buy-plus-glue posture: TBD; brief feeds the Exercise 03 build-vs-buy matrix. The *brief* does not pre-decide the path.
- Commissioning window (brief validity): one quarter; revisited per the trigger list in Section 11.

### 2.2 The brief

```
Commissioning Brief — Billing-Dispute Triage Agent (BDTA)
Brief ID:        BDTA-FY<YYYY>Q<N>-01
Requesting BU:   Customer Operations
Enablement Lead: AI Enablement Lead (this role)
Engineering partner (Driver on implementation): Applied AI Engineer, Customer Operations platform area
Governance sponsor (Approver on sensitive-data scope): head-of-ai-governance (L60)
Brief date:      <!-- org-specific: brief date -->
Next review:     End of the commissioning window, or off-cycle per Section 11 trigger
```

#### Section 1 — Working problem

L2 billing-dispute triage currently takes a median of ~14 minutes per case before the agent begins the judgement portion of the work. <!-- org-specific: confirm the 14-minute baseline against the learner's actual call-centre workforce-management telemetry; do not quote this number if the baseline is not instrumented. --> The non-judgement portion — history summary, account context lookup, first-reply template selection — is the slice we propose to automate. Agent judgement (dispute resolution, discretionary credit, policy exception) stays with the human.

Operator phrasing: *"I spend the first half of each billing dispute putting the history in my own head. I'd like something that walks me through what the prior cases said and drafts the first paragraph I'm going to type anyway."*

#### Section 2 — Scope

**In scope:**

- Ingest the active case record, the prior-case thread for the same account (last 12 months), and the account-level billing context.
- Emit: (a) a structured triage summary, (b) a proposed first-reply paragraph, (c) a confidence band and a short "what I used" trace.
- Surface as a sidecar panel in the existing agent console; no autonomous action.

**Out of scope:**

- Auto-sending any reply to the customer.
- Issuing credits, refunds, or policy exceptions.
- Decisioning on fraud-flagged accounts (routes back to the human queue regardless of agent output).
- Cross-account inference (the agent sees one account at a time; it does not train on or cross-reference other accounts).

**User population (addressable):** ~120 L2 billing-dispute agents across two regions. <!-- org-specific: confirm from workforce-management -->

#### Section 3 — Data domain and sensitivity

| Data class | Sensitivity tier | Retention class | Cross-border posture |
|---|---|---|---|
| Account billing records | Confidential (PII + financial) | Per existing CRM retention policy | <!-- org-specific: confirm residency requirement; brief assumes same-region processing only --> |
| Prior case transcripts | Confidential (may contain PII) | Per existing CRM retention policy | Same-region |
| Agent-console session logs | Internal | Per telemetry retention policy | Same-region |
| Model prompts / completions | Confidential (derived from Confidential) | Logged for audit; retention matches CRM | Same-region |

**Hard constraints:**

- No data egress to a third-party inference provider that is not already in-scope for the current AUP and DPA. <!-- org-specific: confirm the approved-provider list from the mod-103 AUP -->
- No training/finetuning on account data without a separate mod-103 governance-council approval.
- Right-to-be-forgotten requests propagate into the retrieval index within the same SLA as CRM deletion.

#### Section 4 — Success metrics

Both leading and lagging; both baselined; both named with instrumentation ownership.

| Indicator | Direction | Baseline | Target (end of commissioning window) | Instrumentation owner |
|---|---|---|---|---|
| Median triage-prep time per case (leading) | ↓ | 14 min <!-- org-specific --> | ≤ 10 min | Workforce-management + agent console event log |
| Agent-adopted first-reply draft rate (leading) | ↑ | n/a (new) | ≥ 50% of drafts adopted with ≤ moderate edit | Agent console telemetry |
| Customer-satisfaction (CSAT) on first reply (lagging) | ↔ (do no harm) | Current CSAT baseline | Within ±2 points of baseline | Post-interaction CSAT survey |
| First-contact resolution rate (lagging) | ↑ | Current FCR baseline | ≥ baseline | CRM reporting |
| Hallucination / fabrication rate on structured-fact fields (leading, safety) | ↓ | n/a (new) | ≤ 1% on spot-check sample of 200/week | Applied AI Engineering eval harness |
| User-reported incident rate (leading, safety) | ↓ | 0 baseline | 0 serious; triaged within 1 business day | Enablement scorecard per mod-106 |

The commissioning window ends with a review against **all four target rows**. A win on the leading indicators and a drop on the lagging indicators is a kill signal, not a success signal.

#### Section 5 — Decision rights (DACI)

| Decision | Enablement Lead | Applied AI Engineer | Governance council | Business sponsor |
|---|---|---|---|---|
| Problem framing and scope at brief time | D | C | I | A |
| Technical architecture and implementation path | C | D/A | I | I |
| Data-handling posture and AUP fit | C | C | A | I |
| Go / no-go to proof-of-concept gate | D | C | C | A |
| Go / no-go to limited-GA gate | C | C | A | A |
| Go / no-go to general-availability gate | C | C | A | A |
| Scope change > 25% effort or new data class | C | C | A | A |
| Kill / sunset decision | D | C | A | A |

#### Section 6 — Risk posture

Threat context scoped against the official sources. The brief does not re-derive these risks; it names the ones the engagement commits to addressing.

| Threat / risk | Source | Mitigation posture |
|---|---|---|
| Prompt injection via case transcript fields | `owasp-ml-top-10` (LLM-adjacent) and `mitre-atlas` reconnaissance/evasion techniques | Structured-field extraction with allow-listed output schema; untrusted free-text is attributed and not treated as instruction |
| Output manipulation via adversarially crafted prior cases | `mitre-atlas` ML Model Access / Evasion techniques | Confidence-band gating; low-confidence outputs fall back to "no summary — prior cases inconclusive" rather than hallucinating |
| Data exfiltration via inference provider | `owasp-ml-top-10` (data-exposure patterns) | Same-region processing; no third-party egress outside the AUP-approved provider list |
| Model drift silently degrading outputs | `nist-ai-rmf` MEASURE function | Weekly eval harness run (see Section 4 row 5); regression → pause to limited-GA |
| Role creep (the sidecar becoming an authority) | `nist-ai-rmf` GOVERN function | UI copy, training content, and the SOP (co-authored per mod-103) make the agent-is-advisory posture explicit; audit flag on any first reply sent verbatim |

#### Section 7 — Budget envelope

| Envelope component | Amount (USD) | Source / assumption |
|---|---|---|
| Commissioning engineering effort (Applied AI Engineering FTE allocation) | <!-- org-specific --> | ≈ 0.5 FTE for the commissioning window |
| Consumption (inference + retrieval) during pilot | <!-- org-specific --> | Scoped to ~120 users × pilot usage profile |
| Enablement operations, training content, SOP co-authoring | <!-- org-specific --> | Per mod-104 training-design and mod-103 SOP-co-authoring patterns |
| Governance / assurance | <!-- org-specific --> | Red-team adjacent review per mod-109 incident-prep posture |
| **Not-to-exceed for the commissioning window** | <!-- org-specific --> | Approved at brief time; overrun > 25% returns to governance council per Section 5 row 7 |

The envelope is explicitly a **commissioning-window** envelope, not a lifetime envelope. Full-lifetime cost is modelled at the Exercise 04 measurement-plan gate if the tool proceeds beyond pilot.

#### Section 8 — Gate structure

Three gates in sequence; each gate is pre-committed to kill criteria as well as pass criteria.

1. **Proof-of-concept gate (POC).** Applied AI Engineering demonstrates the capability on a sandbox dataset. Pass: the structured-fact extraction is ≥ 95% faithful on a 100-item hand-labeled sample; the first-reply draft is coherent on spot-check. Kill: faithfulness < 85%, or inability to constrain outputs to the allow-listed schema.
2. **Limited-GA gate.** Shadow mode with ~10 opt-in agents for two weeks. Pass: leading indicators trend in the right direction; no Sev-2+ incidents; the per-case trace artifact is present and reviewable. Kill: any Sev-2+ incident; CSAT regression > 2 points on the shadowed subset.
3. **General-availability gate.** Rollout to the full addressable 120 agents gated on Section 4 targets being met. Kill: any Section 4 target missed by > 20% at the gate review.

#### Section 9 — Handoff to Applied AI Engineering

The handoff is governed by the separate **handoff contract** artifact (per Exercise 03), not re-litigated here. This brief provides the inputs the handoff contract requires: working problem (Section 1), scope (Section 2), data posture (Section 3), success metrics (Section 4), decision rights (Section 5), risk posture (Section 6), budget envelope (Section 7), gate structure (Section 8).

#### Section 10 — Kill criteria (explicit)

The engagement is sunset — not extended, not re-scoped — on any of:

- A Sev-2+ AI incident (per mod-109) traceable to the commissioned tool.
- Faithfulness < 85% at the POC gate.
- CSAT regression > 2 points on the shadowed subset at the limited-GA gate.
- Any Section 4 target missed by > 20% at the GA gate.
- A regulatory or policy change that invalidates the data-handling posture in Section 3 without a feasible remediation path inside the commissioning window.
- Loss of the business-unit sponsor's commitment (the commissioning brief is not Enablement's to run without the BU's backing).

#### Section 11 — Review triggers and reversibility

The brief is revisited (not just the engagement — the brief itself) on any of:

- Change in the addressable population by > 20%.
- Change in the data-sensitivity posture (new data class added, cross-border posture changed).
- Change in the approved-provider list under the mod-103 AUP.
- An AI incident at a peer tool, where the incident-review retrospective (per mod-109) surfaces patterns relevant to this engagement.
- A Build / Buy / Buy-plus-glue re-decision against the Exercise 03 matrix.
- Any signatory role change (role, not person).

### 2.3 Decision rationale — why this shape, not another

- **Why eleven sections, not three.** A three-section brief (problem / scope / plan) is what lets engineering intake politely reject the document. The eleven sections mirror the intake gates downstream functions already have (Security intake, Legal/privacy review, Procurement intake, governance-council review). Each downstream function finds its section and signs or redlines it. A brief that is not addressable section-by-section becomes a meeting.
- **Why risk posture ties explicitly to OWASP ML Top 10, MITRE ATLAS, and NIST AI RMF.** Those are the official sources the governance council, Security partner, and Applied AI Engineer are already using. Naming them by ID in Section 6 is what lets the three downstream functions converge on a shared threat model without re-negotiating it per engagement.
- **Why "kill criteria" are pre-committed at brief time.** Committing to the kill criteria *after* the pilot is underway is near-impossible — the sunk-cost pressure is at its peak when the first pilot indicators look mixed. Committing at brief time, when there is no sunk cost, is the moment to write them down.
- **Why the brief is addressed to the role names, not the people.** The brief survives a re-org; the same brief ratifies the same working relationship after a change in Applied AI Engineering leadership. This is the mod-103 role-name-addressing discipline carried forward.
- **Why the brief does not pre-decide Build / Buy / Buy-plus-glue.** That decision is the Exercise 03 matrix's output. The brief captures the *problem*; the matrix captures the *path*. Pre-deciding the path at brief time collapses the two and routes around Procurement.
- **Why the budget envelope is commissioning-window-scoped, not lifetime.** Lifetime scoping over-commits budget before the POC gate has demonstrated the tool is even feasible. Window-scoping keeps the first money reversible.

## 3. Validation steps

1. **Eleven sections present in order** (Working problem, Scope, Data domain, Success metrics, Decision rights, Risk posture, Budget envelope, Gate structure, Handoff, Kill criteria, Review triggers).
2. **Operator-language phrasing in Section 1.** A brief written in technology-vendor language (e.g., "LLM-powered intelligent agent") is a brief Customer Operations did not help write; reject and re-run with the operator.
3. **Scope has explicit out-of-scope bullets.** Without named out-of-scope, scope is implicit and expands silently.
4. **Data domain table has all four columns populated per row** (class, sensitivity tier, retention class, cross-border posture).
5. **Success metrics have both leading and lagging rows, each with baseline and instrumentation owner.** A metrics section without baselines is unreviewable at the gates.
6. **Decision rights are DACI, not RACI.** Every row has a Driver and an Approver, and they are not the same role.
7. **Risk posture section names OWASP ML Top 10, MITRE ATLAS, and NIST AI RMF by ID.** Generic "we considered risks" is not sufficient.
8. **Budget envelope has a not-to-exceed with a stated overrun-return clause** (overrun > X% routes back to the governance council per the DACI table).
9. **Gate structure is three gates with explicit pass *and* kill criteria per gate.** A gate with only pass criteria is not a gate.
10. **Section 10 (kill criteria) has ≥ 4 criteria** and includes at least one that is outside the engagement's control (regulatory change or sponsor withdrawal).
11. **Review triggers in Section 11 are concrete.** "As needed" is a failure.
12. **Role-name addressing throughout.** Grep for personal names and personal pronouns.
13. **No vendor product names** in Section 2 or Section 7.
14. **`org-specific` tags on specific baselines, budgets, addressable populations, and residency assumptions.** Unmarked quoted numbers are a hard fail.

## 4. Rubric / review checklist

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | Eleven sections in order | 5 | Missing section or re-ordered. |
| R2 | Operator-language problem statement with named baseline | 10 | Vendor-speak or baseline missing. |
| R3 | Scope has explicit in-scope and out-of-scope bullets | 5 | No out-of-scope bullets. |
| R4 | Data domain table populated across class / sensitivity / retention / cross-border | 10 | Missing columns or missing rows. |
| R5 | Success metrics: both leading and lagging; each with baseline and instrumentation owner | 15 | Only leading, only lagging, or baselines absent. |
| R6 | Decision rights are DACI with Driver + Approver distinct per row | 10 | RACI-blurring or missing decisions. |
| R7 | Risk posture names `owasp-ml-top-10`, `mitre-atlas`, and `nist-ai-rmf` with specific threat / mitigation rows | 10 | Generic risk list, or official sources not named. |
| R8 | Budget envelope with not-to-exceed and overrun-return clause | 5 | Envelope absent or no overrun routing. |
| R9 | Three gates with explicit pass + kill criteria each | 10 | Kill criteria missing on any gate. |
| R10 | Kill criteria section has ≥ 4 criteria including ≥ 1 outside engagement control | 5 | Fewer than four, or all engagement-controlled. |
| R11 | Review triggers named concretely in Section 11 | 5 | "As needed" / vague. |
| R12 | Role-name addressing throughout | 5 | People names used. |
| R13 | `org-specific` tags on unverifiable specifics (baselines, budgets, residency) | 5 | Unmarked quoted numbers. |

**Pass threshold:** ≥ 85/100 and no R5 / R6 / R7 / R9 fail. R5 (metrics), R6 (decision rights), R7 (risk sources), and R9 (gates with kill criteria) are the four discriminators between a brief engineering will take in and a brief engineering will send back.

## 5. Common mistakes

- **Vendor-speak in Section 1.** "LLM-powered agent to transform operations" is a brief Customer Operations did not help write. Section 1 is the operator's voice; if it does not sound like the operator, re-write with them.
- **Pre-deciding the Build / Buy / Buy-plus-glue path inside the brief.** That decision is the Exercise 03 matrix's output. Pre-deciding routes around Procurement and Finance.
- **Omitting out-of-scope.** Without explicit out-of-scope, the sidecar becomes an authority: it starts issuing credits because nobody wrote down that it does not.
- **Collapsing leading and lagging metrics into one row each.** Leading metrics catch early trajectory; lagging metrics catch do-no-harm. A brief with only one kind cannot be evaluated at the gates.
- **No kill criteria, or kill criteria added post-POC.** Committing to the kill criteria *after* the first results arrive is near-impossible under sunk-cost pressure. The brief is where they are pre-committed.
- **Lifetime budget envelope at brief time.** Scope the envelope to the commissioning window; model lifetime at the Exercise 04 measurement-plan gate if the tool proceeds beyond pilot.
- **Risk section with no sources.** "We considered prompt injection" is not reviewable; "prompt injection per `owasp-ml-top-10` LLM-adjacent, mitigation posture: structured-field extraction with allow-listed output schema" is.
- **People names in the signature block.** The brief is a role-name artifact. It survives re-orgs only if written that way.
- **Scope creep into training-and-finetuning without governance.** Training on account data is a mod-103 governance-council decision; a brief that assumes training is a brief that will not survive first contact with Legal/privacy review.
- **Promising general availability at brief time.** The GA gate is a decision at the gate, not a brief-time commitment.

### 5.1 Stretch — brief-to-handoff pack

For a mature program, the brief is paired with a short handoff pack that the Enablement Lead attaches to the engineering intake. The pack is three artifacts:

- The brief itself (this document).
- A one-page threat-model note that names the specific OWASP ML Top 10 rows, MITRE ATLAS techniques, and NIST AI RMF functions in scope, and is updated jointly with Applied AI Engineering at each gate.
- A one-page SOP outline (co-authored under mod-103) covering the agent-is-advisory posture, the audit flag on verbatim first-reply sends, and the user-reported-incident route into the mod-109 incident flow.

The three-artifact pack is what makes a commissioning engagement reviewable by any of the four downstream functions (Applied AI Engineering, Security, Legal/privacy, governance council) without a meeting.

## 6. References

- **Learning material (local):**
  - [mod-102 — Selecting and Rolling Out AI Tools](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-102-selecting-and-rolling-out-ai-tools) — the intake questionnaire the brief must *not* be collapsed into when the path is Build / Buy-plus-glue.
  - [mod-103 — Policy Co-authoring with Governance](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-103-policy-co-authoring-with-governance) — role-name addressing, governance-council pre-read posture, and the SOP co-authoring pattern.
  - [mod-104 — Training Programs and AI Literacy Curriculum](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-104-training-programs-and-ai-literacy-curriculum) — the training-design pattern supporting Section 7 training-content budget line.
  - [mod-106 — Outcome Measurement and Executive Reporting](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-106-outcome-measurement-and-executive-reporting) — the scorecard discipline the leading-indicator rows roll into.
  - [mod-107 — Budget, ROI, and Build-vs-Buy at Org Scope](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-107-budget-roi-and-build-vs-buy-at-org-scope) — Exercise 03's build-vs-buy matrix is what consumes Section 1 of this brief.
  - [mod-109 — AI Incident Response and Enablement-Side Rollback](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-109-ai-incident-response-and-enablement-side-rollback) — the incident-severity scale behind the Section 10 Sev-2+ kill criterion.
  - [Exercise 02 — Prototype Inheritance and Productionise Decision](../exercise-02-prototype-inheritance-and-productionise-decision/SOLUTION.md) — the decision artifact used when a bottom-up prototype predates the brief.
  - [Exercise 03 — Handoff Contract with Applied AI Engineer](../exercise-03-handoff-contract-with-applied-ai-engineer/SOLUTION.md) — the contract that governs the Section 9 handoff.
  - [Exercise 04 — Commissioned Tool Measurement Plan](../exercise-04-commissioned-tool-measurement-plan/SOLUTION.md) — the plan that extends Section 4 metrics into lifecycle instrumentation and review cadence.
- **Official standards and frameworks:**
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — Section 6 threat posture is scoped against this list by ID.
  - [MITRE ATLAS](https://atlas.mitre.org/) — adversarial-technique context for the Section 6 threat / mitigation rows.
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — the GOVERN function underpins the DACI structure in Section 5; the MEASURE function underpins the drift-monitoring row in Section 6.
