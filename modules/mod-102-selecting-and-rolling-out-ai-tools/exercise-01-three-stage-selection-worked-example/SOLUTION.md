# Exercise 01 — Three-Stage Selection Worked Example — Solution

> Module: `mod-102-selecting-and-rolling-out-ai-tools`
> Exercise type: design / worked example
> Exercise brief: `lessons/mod-102-selecting-and-rolling-out-ai-tools/exercises/exercise-01-three-stage-selection-worked-example.md` (in the learning repo)

## 1. Solution overview

The three-stage selection pattern separates **discovery**, **evaluation**, and **decision** so that an AI Enablement Lead never promotes a tool past a stage it has not actually earned. This solution walks the pattern end-to-end for a single, deliberately mundane candidate — an **AI meeting-notes assistant** for a ~2,000-person services organization — and shows how the decision rationale is constructed from evidence captured at each stage rather than from vendor narrative.

Key design choices:

- Stage 1 (Discovery) ends with a **written shortlist and explicit non-goals**, not with a demo booked.
- Stage 2 (Evaluation) ends with a **structured risk/fit scorecard** keyed to functions governed by `nist-ai-rmf` (Govern, Map, Measure, Manage). The scorecard is the artifact, not the demo call.
- Stage 3 (Decision) ends with a **signed recommendation** that names the decision-maker, the reversal condition, and the committed owner for post-rollout monitoring.

The worked example below is deliberately generic so learners can adapt it to their own stack. Any claim that would require a specific vendor metric, benchmark, or customer reference is left as a blank with a bracketed instruction for the learner — these are flagged inline as **to-verify** notes where appropriate.

## Implementation

Apply this solution by working section 2 (Worked answer) in order — Discovery, then Evaluation, then Decision — gating progression on the stop/go artifact listed at the end of each stage. Validate the finished artifact against section 3 and score with the rubric in section 4; section 5 documents the common failure modes the three-stage shape is designed to resist.

## 2. Worked answer

### Scenario

- Organization: ~2,000-person professional services firm (multi-region, EU + US).
- Problem statement: senior consultants spend meaningful time each week writing meeting notes and follow-up emails. Leadership has asked the AI Enablement Lead to "figure out meeting-notes AI."
- AI Enablement Lead's standing mandate: never introduce a tool that cannot be mapped to an identified role, workflow, outcome, and owner.

### Stage 1 — Discovery

**Goal:** turn an executive ask into a scoped problem and a shortlist. Do **not** evaluate tools yet.

**Inputs collected:**

- Target users: client-facing consultants; initially 3 of ~12 practice areas.
- Workflow: notes captured during client meetings; some meetings are recorded, many are not; some clients explicitly forbid third-party processing of recordings.
- Existing systems: Microsoft 365 (Teams, Outlook, SharePoint); CRM; separate casework system.
- Data sensitivity: meeting content frequently contains client-confidential information; a subset is subject to sectoral confidentiality rules the firm already documents in its data-handling SOP. <!-- to-verify: confirm which specific sectoral rules apply to the learner's own org before quoting them. -->

**Outputs:**

1. **Problem statement** — one paragraph: "Reduce consultant time spent authoring client meeting notes and recap emails without changing what clients see, without routing client-confidential audio through third parties that have not been contractually cleared, and without creating a second source of truth outside Teams/SharePoint."
2. **Non-goals** — explicit:
   - Not an internal knowledge-base search tool.
   - Not a replacement for the existing CRM activity log.
   - Not a universal all-hands transcription tool for every meeting.
3. **Shortlist criteria** (hard gates before a vendor can be shortlisted):
   - Integrates with Teams **natively** (not via screen capture).
   - Contract terms permit **no training on tenant data by default**.
   - Processes **EU-origin meetings in the EU** or offers a documented region pin that the firm can verify.
   - Provides an administrator audit log of who recorded what.
4. **Shortlist** — three candidates named A/B/C in the artifact; shortlisting evidence is the vendor's documentation and procurement intake response, not a demo.

**Stop/go gate:** Legal, Security, and the Practice Area sponsor sign off on the problem statement and shortlist criteria **before** any demo is scheduled. This is the first place the exercise prevents the common failure of "vendor-led selection."

### Stage 2 — Evaluation

**Goal:** generate evidence that the shortlist can actually be scored against the criteria.

**Evaluation plan:**

- Form of evidence: a **risk/fit scorecard**, filled in from (a) vendor-supplied artifacts, (b) a short hands-on test with real but anonymized meeting content, and (c) answers to a written intake questionnaire. Demos are allowed but are a *support* source of evidence, not the primary one.
- Duration: time-boxed to 3 weeks per candidate, running in parallel.
- Exit: a scorecard per candidate plus a one-page narrative per candidate.

**Scorecard dimensions** (derived from `nist-ai-rmf` Core functions):

| Dimension | What is actually measured | Evidence source |
|---|---|---|
| Govern — contractual & data use | Training-on-tenant clause, retention, subprocessors, region pin, DPIA artifacts | Vendor paper, redlined MSA/DPA |
| Map — workflow fit | Fit with Teams and the existing recap-email workflow for the 3 practice areas | Hands-on test with anonymized content |
| Measure — quality & drift signals | Transcription accuracy on in-domain accents/terminology; hallucination rate on summaries; failure modes when audio quality is poor | Hands-on test logs; vendor self-reported numbers must be **labeled as vendor-reported**, not treated as independent evidence <!-- to-verify: the learner should re-measure in their own environment rather than quoting a vendor number. --> |
| Manage — operational readiness | SSO, SCIM, admin audit log, data deletion workflow, incident contact | Admin console walk-through, not slideware |
| Threat model fit | Candidate AI-specific abuse paths from `owasp-ml-top-10` (e.g., prompt injection via meeting content) and `mitre-atlas` techniques relevant to LLM-integrated apps | Threat modeling session with Security |

**Worked rollup (illustrative — numbers not to be quoted as real):**

Vendor A: strong Govern + Manage; weak Measure on accented speech; medium on threat model (outbound only, no plug-in ecosystem).
Vendor B: strong Measure but training-on-tenant off is a paid tier only; fails Govern gate.
Vendor C: medium across the board; no EU region pin; fails a hard Stage-1 gate — should have been dropped at Stage 1.

Vendor C is kept in the write-up as a **teaching artifact** to show that if a Stage-1 hard gate is unverifiable until Stage 2, the correct behavior is to retire the candidate and **update the Stage-1 criteria**, not to carry it forward.

**Stop/go gate:** the Security and Legal reviewers must sign **the scorecard they reviewed**, not a later edited version. The scorecard is version-controlled.

### Stage 3 — Decision

**Goal:** record a defensible decision with a committed owner and a committed exit condition.

**Decision record (one page):**

- **Decision:** proceed to pilot with Vendor A, scoped to a single practice area for 8 weeks.
- **Decision-maker:** named VP of the sponsoring practice area, counter-signed by the AI Enablement Lead.
- **Why A, not B or C:** two sentences referencing the scorecard, not the demo.
- **Reversal condition:** if the pilot does not reach the pre-committed outcome metric from exercise-06 (outcome, not usage), or if any one of the hard Govern gates fails during the pilot, the tool is rolled back per the enablement-side rollback plan. This is the link forward to `mod-109-ai-incident-response-and-enablement-side-rollback`. <!-- to-verify: confirm cross-module reference remains valid in the learner's version of the curriculum. -->
- **Owner for post-rollout:** named individual, not a team.
- **Review cadence:** attached to the executive rollout report cadence from exercise-03.

### Decision rationale summary

The decision is **defensible** because every claim it rests on points back to a scorecard row backed by an evidence source. The decision is **reversible** because the exit condition and the owner are named before rollout rather than negotiated during an incident.

## 3. Validation steps

A learner's submission is validated if, reading only their artifact and not asking them any questions, a reviewer can answer **yes** to all of the following:

1. Is there a written problem statement **with explicit non-goals**?
2. Does the shortlist have **hard gates** that could, in principle, exclude any vendor — including a favored one?
3. Is there a scorecard whose columns name **evidence sources** rather than vendor claims?
4. Are at least one `nist-ai-rmf` function and at least one AI-specific threat model reference (`owasp-ml-top-10` or `mitre-atlas`) mapped to scorecard rows?
5. Is the decision **signed** (named decision-maker + co-signer)?
6. Is the reversal condition **pre-committed**, not described in the abstract?
7. Is a post-rollout owner named by individual, not by team?
8. Is at least one candidate dropped or demoted on evidence from the scorecard, to demonstrate the gates can actually bite?

## 4. Rubric or review checklist

Scored out of 20. 14+ passes; below 10 is a rework.

| # | Criterion | Max |
|---|---|---|
| 1 | Problem statement + non-goals are both present and specific | 2 |
| 2 | Stage-1 hard gates are enforceable (verifiable from vendor paper, not demo) | 2 |
| 3 | Shortlist evidence source is named for each gate | 2 |
| 4 | Scorecard dimensions are mapped to `nist-ai-rmf` functions | 2 |
| 5 | At least one row references `owasp-ml-top-10` or `mitre-atlas` | 2 |
| 6 | Vendor-supplied numbers are labeled as vendor-reported | 1 |
| 7 | At least one candidate is dropped or demoted on evidence | 2 |
| 8 | Decision record names a decision-maker and co-signer | 2 |
| 9 | Pre-committed reversal condition exists and is specific | 2 |
| 10 | Post-rollout owner is an individual | 1 |
| 11 | Clear link forward to the pilot charter (exercise-04) | 1 |
| 12 | Clear link forward to the outcome metric (exercise-06), not usage telemetry | 1 |

## 5. Common mistakes

- **Vendor-led selection.** Letting the demo come before the Stage-1 gates. The symptom is a scorecard whose dimensions match the vendor's slide deck.
- **Treating vendor-supplied benchmarks as independent evidence.** They are inputs to the scorecard, labeled as such, not conclusions.
- **Dropping the non-goals section** because "it's obvious." Non-goals are the only thing that keeps scope creep out of Stage 2.
- **Picking the "winner" from a tie.** If two candidates score the same, that is a sign the scorecard dimensions are not discriminating. Fix the scorecard, do not break the tie by preference.
- **Owner = team.** "The CoE owns it" is not an owner. A named individual is the owner.
- **Reversal condition is vague.** "If it's not working" is not a reversal condition. A pre-committed outcome metric threshold, or a specific governance failure, is.
- **Confusing the pilot decision with the rollout decision.** Stage 3 here authorizes a pilot, not production. The production decision belongs to the pilot charter exit gate in exercise-04.

## 6. References

- NIST AI Risk Management Framework (AI RMF 1.0): <https://www.nist.gov/itl/ai-risk-management-framework> — the Govern / Map / Measure / Manage functions are the backbone of the Stage-2 scorecard.
- OWASP Machine Learning Security Top 10: <https://owasp.org/www-project-machine-learning-security-top-10/> — used in the threat-modeling row of the Stage-2 scorecard.
- MITRE ATLAS: <https://atlas.mitre.org/> — used for adversary technique framing when the candidate is LLM-integrated.
- Local context: companion exercises in this module — `exercise-04-pilot-charter-and-decision-criteria` (pilot gating) and `exercise-06-outcome-measurement-vs-usage-telemetry-drill` (outcome metric). Cross-module: `mod-109-ai-incident-response-and-enablement-side-rollback` for the reversal pathway.
