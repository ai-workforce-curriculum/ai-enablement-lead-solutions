# Exercise 03 — Intake Questionnaire Co-Author — Reference Solution

> Learning file: [`exercise-03-intake-questionnaire-co-author.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-103-policy-co-authoring-with-governance/exercises/exercise-03-intake-questionnaire-co-author.md)

## 1. Solution overview

Two artifacts, both enablement-runner-side work: a completed intake submission (Deliverable A) and a 1-page schema-refinement memo to `senior-ai-governance-architect` (Deliverable B). The exercise is where the **schema vs. runner** distinction from Chapter 06 and the **route-out discipline** from Chapter 07 become concrete.

The whole posture is: you fill out the fields, you surface what the pre-review surfaced, you flag policy touchpoints — you do **not** classify the tool, and in the memo you do **not** redesign fields. The memo frames evidence for the architect; it does not propose the fix.

The worked artifacts below continue the "coding assistant at a 3,000-person US bank" archetype from Exercises 01 and 02 — same classification scheme, same escalation path, same SOP references.

## 2. Implementation — worked answer

### 2.1 Deliverable A — `intake-submission.md`

```
Status-tag history (from top):
  pre-intake (2026-10-12)
  intake-in-progress (2026-10-22, after pre-review session)
  schema-complete (2026-11-04) ← current
  awaiting-council-decision (target 2026-11-18)
```

> **Pre-review session summary (3 sentences).**
> The raw submission framed the request as "developer productivity improvements," but the 20-minute pre-review surfaced that the sponsoring BU is the Consumer Lending engineering group, meaning the tool will be used (at least in part) inside code paths that touch GLBA-regulated and MRM-managed decisioning. The requester had not considered that an approved use in the AUP ("explain unfamiliar code") would, in Consumer Lending, routinely require pasting repository code that includes Restricted-class identifiers in test fixtures — a policy touchpoint the raw submission missed. The pre-review therefore added an explicit "policy-touchpoints" entry proposing an AUP walking-redline conversation and a workflow carveout for Consumer Lending's test-fixture scrubbing before approval.

---

#### Tool identity

- Vendor: `<!-- org-specific: confirm vendor legal entity name as it appears on the DPA -->`.
- Product: Copilot-class coding assistant, Enterprise tier.
- Product version: `<!-- org-specific: confirm current GA minor version at submission date -->`.
- Deployment model: SaaS multi-tenant, bank's Enterprise tenant.
- Hosting jurisdiction: `<!-- org-specific: confirm primary US-region endpoint and any fallback region, same slot as AUP Section 1 / SOP Section 3 -->`.

#### Requester and business justification

- BU: Consumer Lending engineering, platform-services team.
- Named sponsor: `<!-- org-specific: confirm sponsor at L40+ (e.g., director-of-platform-engineering) — pre-review was with the engineering-manager-of-platform-services (L35), who confirmed the director-level sponsor exists but did not attend -->`.
- Target task: assist with code generation, code explanation, unit test authoring, and migration drafting for internal platform repositories (not the regulated-decision models themselves).
- Success criterion: 25% median reduction in the time engineers spend on boilerplate tickets (`<!-- org-specific: confirm the baseline metric source, likely the engineering ticket system -->`), measured at 90 days post-GA.
- Alternatives considered: stay on existing editor-only tooling without AI assist; pilot an alternative vendor from the mod-102 envelope; defer until after the Consumer Lending platform migration completes next year. The requester has not formally benchmarked the alternative vendor.

#### Data classes touched

Mapped to the classification scheme referenced in the AUP and SOP (`<!-- org-specific: confirm official scheme name — assumed "Information Classification Standard" with tiers Public / Internal / Confidential / Restricted / Regulated -->`):

- **Inputs:** Public and Internal expected routinely. Confidential possible when engineers paste draft design docs. Restricted and Regulated are AUP-forbidden; a policy touchpoint exists if the test-fixture scrubbing in Consumer Lending is incomplete.
- **Outputs:** Public and Internal expected. External-disclosure path only via human-reviewed commits to customer-facing products (AUP Section 3.4).
- **Vendor training data:** Not used on this tenant (confirmed path per SOP Section 2; DPA clause slot `<!-- org-specific: confirm DPA §X -->`).
- **Vendor logging data:** Abuse-monitoring retention at vendor side `<!-- org-specific: confirm window, same slot as SOP Section 2 -->`. Metadata-only retention at bank side per records schedule `<!-- org-specific: confirm schedule reference -->`.

#### External disclosure

- Outputs reaching customers: Only after human review and commit (AUP Section 3.4). Not direct.
- Outputs reaching partners: Same path as customers.
- Outputs reaching regulators: Only via artifacts prepared through `<!-- org-specific: confirm name of the bank's regulator-facing artifact pipeline, likely MRM or Compliance Communications -->`; the tool is not directly in that pipeline.
- Inputs including third-party confidential data: Possible if an engineer pastes a vendor SDK snippet; champion-level guidance is to summarize rather than paste.

#### Cohort size and reach

- Named populations: Consumer Lending engineering (Phase 1 cohort, size `<!-- org-specific: confirm Phase 1 roster size, approximately 180 engineers per pre-review -->`); then expansion to the two other engineering divisions after a 60-day Phase 1 evaluation (combined expansion `<!-- org-specific: confirm expansion cohort size, approximately 650 engineers -->`).
- Role mix: Software engineers (SWE I–III), staff engineers, engineering managers who read code. No non-engineering roles in Phase 1.
- Geography: US (primary), with `<!-- org-specific: confirm whether any off-shore engineering vendor team is in-scope for Phase 1 — pre-review flagged a Hyderabad-based contracted team that may or may not be included -->`.

#### Risk-classification prompt inputs

Collected for the architect's schema. No classification proposed below — these are inputs only.

- Does the tool make or support a decision that affects a customer, employee, or third party? Support-side only; no customer-facing automated decision uses this tool. Regulated-decision code path (MRM-managed models) is out of scope per AUP Section 3.3.
- Is a human reviewer required before any tool output is used? Yes, per AUP Sections 2 (approved uses) and 3.4 (external-facing output). Reviewer is the engineer committing the code.
- Does the tool operate in a regulated domain? Partial. Phase 1 cohort is in Consumer Lending engineering; code they write touches regulated domains, but the tool itself is not being used inside the regulated-decision code path.
- Does the tool train on organizational data? No, per SOP Section 2 (tenant on no-training path).
- Is there a kill-switch / rollback mechanism documented? Yes — per rollout artifact set (mod-102 artifact 7; operated per mod-109).

#### Envelope check

Envelope status: In envelope. The tool was admitted to the approved-tooling envelope in `<!-- org-specific: confirm envelope-admission date -->` with legal, security, and privacy reviews already complete at the envelope level. Tool-specific (non-envelope) work for this request: AUP touchpoint review (see below) and cohort-specific training plan.

#### Policy touchpoints

Enablement-side reading on which AUP sections and which data-handling SOP sections may need revision because of this tool:

- **AUP Section 2 (approved uses):** No new approved use required for Phase 1; existing five approved uses cover the cohort's expected workflows.
- **AUP Section 3 (prohibited uses):** Walking-redline conversation proposed. Specifically, 3.1 (customer PII prohibition) may need an operator-voice note on test-fixture scrubbing in Consumer Lending repositories — the fixtures are the known paste-mistake risk surface. Propose at the next walking-redline slot; no re-ratification needed if the operator-voice note is additive.
- **AUP Section 4 (data classes):** No change proposed.
- **SOP Section 4 (accident path):** No change proposed; the current five-step path covers the paste-mistake shape for this tool.
- **SOP Section 1 (data classes with examples):** Propose adding one Consumer-Lending-specific example under Restricted at the next SOP walking-redline — the current examples are generic. Additive; privacy sign-off is enough (not a re-ratification).

#### Enablement-side submission note

This submission is complete. The enablement-side read is that classification inputs are collected; the risk-classification output is `senior-ai-governance-architect`'s call under `head-of-ai-governance`'s ratification. The runner recommends council treat this as a `schema-complete` item at the next cycle.

---

### 2.2 Deliverable B — `intake-schema-refinement-memo.md`

```
To:     senior-ai-governance-architect (L50)
Cc:     head-of-ai-governance (L60)
From:   AI Enablement Lead (this role)
Date:   <!-- org-specific: confirm memo date -->
Re:     Two intake-schema observations from the last two intake cycles — evidence for your consideration
```

Over the last two intake cycles I have run the runner side of the intake questionnaire at scale and have noticed two patterns the current field set surfaces imperfectly. Both are **evidence for your consideration** — I am not proposing a redesigned field, a new value enumeration, or a control mapping. Those are your call.

**Observation 1 — The "external disclosure" grouping is read inconsistently when the disclosure is indirect.**

The current external-disclosure fields capture direct output paths (output reaches customer / partner / public / regulator) well. Where they read inconsistently is on **indirect** paths — where the tool's output is committed to a repository that itself feeds a customer-facing product, with one or more human review gates in between. Over the last two cycles, submissions INT-2026-087 (Consumer Lending), INT-2026-091 (Cards engineering), and INT-2026-096 (Wealth advisory tooling) each filled the external-disclosure fields differently for substantively similar indirect paths — one marked "no," one marked "yes," one marked "ask the architect." The pre-review sessions caught it each time, but the schema-complete submissions still read inconsistently. The shape of a refinement that would close this: some way to distinguish direct from indirect disclosure without collapsing them into one field. *The specific shape and value enumeration are your call.* Cost/benefit if adopted: the runner side (pre-review script, champion briefings) would need to update within the same cycle; existing submissions INT-2026-063 through INT-2026-098 may need a backfill pass to re-read their external-disclosure fields against the refined field.

**Observation 2 — The risk-classification prompt input "does the tool operate in a regulated domain?" collapses two questions the architect may want separated.**

The current "regulated-domain" prompt input returns a yes/no/partial answer. In practice, over the last two cycles, "partial" has been used to mean two different things: (a) the tool is not itself in a regulated code path, but the cohort using it is a regulated BU (INT-2026-087, INT-2026-094); and (b) the tool is used in both regulated and non-regulated workflows by the same cohort (INT-2026-089, INT-2026-093). The two cases carry different control implications, and the current single "partial" answer blurs the distinction. The shape of a refinement would be some way to separate "regulated-cohort using a non-regulated tool" from "tool used in mixed regulated/non-regulated workflows." *The architecturally right form of that distinction is your call.* Cost/benefit if adopted: training updates for champion network on how to field-coach requesters through the refined inputs; potentially a re-classification pass on any "partial"-tagged tools from the trailing four quarters.

These are **evidence for your consideration** — observations from the runner side that may or may not warrant a schema change, framed as inputs to your decision process, not as proposals to approve. I am available for a 30-minute walk-through at your convenience.

---

### End of worked artifacts

## 3. Validation steps

### For Deliverable A (`intake-submission.md`)

1. **All eight field groupings present** (tool identity; requester + justification; data classes touched; external disclosure; cohort; risk-classification inputs; envelope check; policy touchpoints).
2. **Pre-review session summary is exactly three sentences** and describes what the pre-review surfaced beyond the raw request (not a general description of the pre-review process).
3. **No risk classification proposed** anywhere in the submission. Grep for "high risk," "medium risk," "low risk," "limited risk," "tier 1/2/3" — any hit indicates the runner crossed into schema work. Rewrite as risk-classification inputs.
4. **Data classes map to the same scheme named in Exercise 01's AUP.** Scheme name match is non-negotiable.
5. **Policy touchpoints are the enablement-side read.** A submission that marks "no touchpoints" without a sentence of reasoning is weak; a submission that names specific AUP/SOP sections (even to say "no change proposed") is strong.
6. **`<!-- org-specific: ... -->` on every unknown, each naming the specific slot.** Sponsor identity, cohort size, DPA clause, envelope-admission date, records schedule, regulator-pipeline name.

### For Deliverable B (`intake-schema-refinement-memo.md`)

1. **One page.** Render; cut if it spills.
2. **Addressed to `senior-ai-governance-architect` (L50) with `head-of-ai-governance` (L60) on cc.** Role names, not people names.
3. **Exactly two refinements, both framed as evidence for consideration.** Grep for "propose adding a field," "the new field should be," "the schema should be updated to" — these indicate the memo crossed the schema-vs-runner line. Rewrite.
4. **Each refinement has three shaped components:** (a) 1–2 sentences on the general shape of change; (b) 2–3 sentences of field evidence with submission references (the references can be fabricated, but the evidence shape must be realistic — "three of twelve submissions in the last cycle" is realistic; "I have seen this a lot" is not); (c) 1 sentence on costs and benefits if adopted.
5. **Memo does not include a proposed field definition, a proposed value enumeration, or a proposed control mapping.** This is the single hardest rubric criterion to pass — review word by word.
6. **Two refinements are independent.** If both refinements argue different angles of the same field change, that is one refinement dressed as two.
7. **Carry-forward with Exercises 01/02.** The data-class scheme name matches; the AUP section references match; the SOP section references match.

Markdown lint both files.

## 4. Rubric / review checklist

### Deliverable A — completed questionnaire

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| A1 | All eight field groupings present | 15 | Any grouping missing. |
| A2 | Pre-review session summary is exactly 3 sentences and names what pre-review surfaced beyond the raw request | 10 | Wrong count, or generic process-describing text. |
| A3 | No risk classification proposed | 15 | Any explicit classification word used. |
| A4 | Data classes map to the Exercise 01 scheme (name match) | 10 | Scheme name mismatch. |
| A5 | Policy touchpoints are concrete (specific AUP/SOP sections named) | 10 | "No touchpoints" with no reasoning, or vague "may affect policy." |
| A6 | `<!-- org-specific: ... -->` on every unknown, with specific slots | 5 | Invented facts, or vague markers. |
| A7 | Carry-forward coherent with Exercises 01/02 (same tool, same scheme, same escalation path) | 5 | Any drift. |

### Deliverable B — memo

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| B1 | One page at normal body-text size | 5 | Spills. |
| B2 | Addressed to `senior-ai-governance-architect` with `head-of-ai-governance` cc (role names) | 2 | Named individuals, or missing cc. |
| B3 | Exactly two refinements | 3 | Wrong count. |
| B4 | Each refinement has 1–2 sentences on shape + 2–3 sentences of field evidence (with submission references) + 1 sentence on costs/benefits | 5 | Missing or malformed component. |
| B5 | Framed explicitly as evidence for architect's consideration | 5 | No "for your consideration" / "your call" framing; or framing contradicted by content. |
| B6 | **No proposed field definition, value enumeration, or control mapping** | 10 | Any of the three present. |
| B7 | Two refinements are independent | 3 | Both argue different angles of one change. |

**Pass threshold:** A total ≥ 85/100 and no A3 / B6 fail. B6 is the exercise's single most important discipline test.

## 5. Common mistakes

- **Proposing a risk classification in the questionnaire.** The submission says "we recommend tier-2 classification" or "likely low risk." Rewrite as inputs. Classification is `senior-ai-governance-architect`'s output under `head-of-ai-governance`'s ratification.
- **Writing the memo as a redesign proposal.** "I propose adding the following field: `external_disclosure_path: [direct | indirect | none]`." That is the architect's work. Rewrite as "some way to distinguish direct from indirect disclosure without collapsing them into one field; the specific shape is your call."
- **Vague pre-review summary.** "The pre-review session confirmed the submission is accurate." That is not a summary of what the session surfaced beyond the raw request. Rewrite to name the specific insight that the raw request would have missed.
- **Memo refinements that are not independent.** "Refinement 1: split external disclosure. Refinement 2: add a value for indirect disclosure." Those are one refinement, not two. Pick a different second observation.
- **Fabricating references without realistic shape.** "I have seen this a lot" is not evidence; "three of twelve submissions in the last cycle (INT-2026-087, INT-2026-091, INT-2026-096)" is evidence. The references can be fabricated for the exercise but the shape must look like real intake telemetry.
- **Drifting into architecture under the "cost/benefit" line.** Cost/benefit should describe runner-side and operating-model costs (training updates, re-classification passes, submission backfills), not proposed schema changes dressed up as "costs."
- **Scheme name mismatch with Exercise 01.** The three artifacts are a set. Mismatch is a visible coherence failure.
- **Classification-like vocabulary leaking into the "risk-classification prompt inputs" section.** "The tool is high-impact because…" — rewrite as the raw input ("the tool's outputs reach customer-facing products after human review") and let the architect's schema produce the impact rating.

## 6. Stretch — Slack nudge, agenda line, status-tag history, champion report-back

**Slack nudge to a requester whose submission is stalled** (at `intake-in-progress` for > 14 days):

> Hey — just checking in on INT-2026-091. It's been at `intake-in-progress` for about two weeks; the schema-complete handoff is waiting on the cohort-size and off-shore-contractor lines (fields D and E). If you can drop the number of in-scope engineers and whether the Hyderabad team is included by Thursday, I'll have it on the next council agenda. Shout if the delay is on our side.

**2-sentence agenda-line summary for the council pre-read** (Chapter 02 condensed format — carried forward to Exercise 04):

> **INT-2026-091 (Copilot-class coding assistant, Phase 1 Consumer Lending).** Schema-complete 2026-11-04; classification inputs attached; one AUP Section 3 touchpoint flagged for walking-redline before GA — **ask: council decision this cycle.**

**Status-tag history** (already included at the top of Deliverable A):

```
pre-intake                    2026-10-12
intake-in-progress            2026-10-22   (after pre-review session)
schema-complete               2026-11-04
awaiting-council-decision     2026-11-18   (target)
```

**Report-back-to-champions after council approval with conditions** (assume council approves with condition "AUP Section 3 walking-redline on test-fixture scrubbing must complete before Consumer Lending GA"):

> Council approved the coding-assistant tool for Phase 1 Consumer Lending with one condition: an AUP Section 3 walking-redline on test-fixture scrubbing before GA. For champions in Consumer Lending, that means (1) we need a short sync next Tuesday to walk through what "scrubbing" means at your team level, and (2) your engineers can expect a Section 3 update in the AUP within three weeks. The GA date moves accordingly; I'll share the new target by Friday. Non-Consumer-Lending engineering champions: no change for you yet — expansion decisions are post-Phase-1 evaluation.

## 7. References

- **Learning material (local):**
  - [Chapter 02 — The Governance Council Liaison Seat](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-103-policy-co-authoring-with-governance/02-the-governance-council-liaison-seat.md)
  - [Chapter 06 — The Intake Questionnaire](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-103-policy-co-authoring-with-governance/06-the-intake-questionnaire.md)
  - [Chapter 07 — What You Route Out](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-103-policy-co-authoring-with-governance/07-what-you-route-out-counsel-soc-architect.md)
  - [mod-102 Chapter 01 — The Three-Stage Selection Decision](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-102-selecting-and-rolling-out-ai-tools/01-the-three-stage-selection-decision.md)
  - Exercise 01 ([`SOLUTION.md`](../exercise-01-one-page-acceptable-use-policy-drill/SOLUTION.md)) and Exercise 02 ([`SOLUTION.md`](../exercise-02-data-handling-sop-for-an-ai-tool/SOLUTION.md)) — carried forward tool, scheme, and escalation path.
- **Official standards and frameworks** (for context on why these field groupings exist, not for citation inside the submission):
  - [NIST AI RMF](https://www.nist.gov/itl/ai-risk-management-framework) — MAP function; the intake questionnaire is a primary MAP artifact.
  - [NIST AI 600-1: Generative AI Profile](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf) — generative-AI-specific risk considerations relevant to the risk-classification prompt inputs.
