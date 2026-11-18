# Exercise 04 — Commissioned Tool Measurement Plan — Reference Solution

> Module: `mod-110-commissioning-internal-ai-tools-and-custom-agents`
> Exercise type: design / worked example
> Exercise brief: [`lessons/mod-110-commissioning-internal-ai-tools-and-custom-agents/exercises/exercise-04-commissioned-tool-measurement-plan.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-110-commissioning-internal-ai-tools-and-custom-agents/exercises/exercise-04-commissioned-tool-measurement-plan.md) (in the learning repo)

## 1. Solution overview

The deliverable is a **commissioned-tool measurement plan**: the written artifact that extends the commissioning brief's Section 4 metrics into a lifecycle instrumentation plan, a review cadence, and a kill-or-grow decision structure. It is the artifact Finance can audit, the artifact governance can review for continued risk posture, and the artifact the business sponsor uses to decide — at a pre-committed cadence — whether the tool continues, is widened, is narrowed, or is sunset.

The plan sits one layer below the executive scorecard (mod-106) and one layer above the engineering eval harness (owned by Applied AI Engineering per Exercise 03). It is the Enablement-owned artifact that stitches engineering-side instrumentation to business-side outcomes.

Posture checks this solution encodes:

- **Every indicator is defined as a tuple of five properties** — name, direction, baseline, target, instrumentation owner — and nothing less. An indicator without a baseline or an instrumentation owner is a wish.
- **Leading, lagging, safety, and cost indicators are all present.** A plan with only one family is a plan that will either under-detect quality regression (no safety), under-detect do-no-harm violations (no lagging), under-detect cost blowouts (no cost), or over-react to short-term noise (no lagging + no safety).
- **Instrumentation ownership is explicit per row.** Engineering-side (eval harness, drift monitor) and Enablement-side (adoption telemetry, user-reported incidents) ownership is named at the indicator grain.
- **Review cadence is named at three tempos** — weekly eval, monthly operational, quarterly strategic — with attendees and decisions per tempo.
- **Kill-or-grow thresholds are pre-committed.** Decisions ride on signals the plan already said would cause them.
- **Drift and safety monitors are first-class.** Per `nist-ai-rmf` MEASURE and MANAGE, `owasp-ml-top-10`, and `mitre-atlas`.
- **The plan is reversible.** A trigger list names when the plan itself (not just the tool) is revisited.

## 2. Implementation — worked answer (`commissioned-tool-measurement-plan.md`)

### 2.1 Worked scenario context

The plan is instantiated against the Exercise 01 worked example — the Billing-Dispute Triage Agent (BDTA). The measurement plan is agreed at the limited-GA gate (per Exercise 03 Section 4) and is a condition of entry to that gate, not an output of it.

### 2.2 Indicator families

Four families; every indicator in the plan sits in exactly one family.

- **Adoption (leading).** Does the tool reach the operators it was commissioned for, and do those operators actually use it? Adoption is the *first* leading signal — a tool with no adoption has no other indicators worth measuring.
- **Outcome (leading and lagging).** Does the tool move the business outcome the brief named? The commissioning brief's Section 4 outcome rows live here, with leading proxies and lagging confirmations.
- **Safety and quality (leading, with lagging incident counts).** Does the tool do its job without harm — no hallucinations in load-bearing fields, no prompt-injection susceptibility, no silent drift, no user-reported incidents over Sev-3?
- **Cost (leading, with monthly reconciliation).** Does the tool stay inside its envelope — per-operator-per-month cost, inference cost per transaction, infrastructure cost, and human-side cost for the ongoing training and support?

### 2.3 Indicator table

Every row has {name, family, direction, baseline, target, review tempo, instrumentation owner, source}.

| # | Indicator | Family | Direction | Baseline | Target | Review tempo | Instrumentation owner | Source / notes |
|---|---|---|---|---|---|---|---|---|
| 1 | Addressable-operator reach (% of 120 operators active ≥ 1x/week) | Adoption | ↑ | 0% pre-launch | ≥ 80% by month 3 of GA | Monthly | Enablement (operator-console session log) | `<!-- org-specific: addressable-operator count and the week-active definition must be calibrated to the learner's workforce-management rhythm -->` |
| 2 | Draft-adoption rate (% of generated drafts adopted with ≤ moderate edit) | Outcome (leading) | ↑ | n/a (new tool) | ≥ 50% at month 3; ≥ 60% at month 6 | Monthly | Applied AI Engineering (telemetry on edit-distance) | Brief Section 4 row 2 |
| 3 | Median triage-prep time per case | Outcome (lagging) | ↓ | 14 min <!-- org-specific --> | ≤ 10 min at month 3; ≤ 8 min at month 6 | Monthly | Enablement (workforce-management + console telemetry) | Brief Section 4 row 1 |
| 4 | Customer satisfaction (CSAT) on first reply | Outcome (lagging — do no harm) | ↔ | Current CSAT baseline | Within ±2 points | Monthly | Enablement (CSAT survey) | Brief Section 4 row 3 |
| 5 | First-contact resolution rate | Outcome (lagging) | ↑ | Current FCR baseline | ≥ baseline | Monthly | Enablement (CRM report) | Brief Section 4 row 4 |
| 6 | Faithfulness on structured-fact fields (spot-check sample n ≥ 200/week) | Safety / quality (leading) | ↑ | 95% at POC | ≥ 95% sustained | Weekly | Applied AI Engineering (eval harness) | Brief Section 4 row 5 + `nist-ai-rmf` MEASURE |
| 7 | Prompt-injection resilience (red-team adjacent probe set) | Safety / quality (leading) | ↑ | Set at limited-GA gate | ≥ 95% refusal / contain | Monthly | Applied AI Engineering (eval harness) | `owasp-ml-top-10` (LLM-adjacent) + `mitre-atlas` |
| 8 | Drift indicator — rolling-window divergence on faithfulness and output-schema conformance | Safety / quality (leading) | Alarm at threshold | Set at limited-GA gate | ≤ 2σ on the rolling window | Daily (automated); summarised weekly | Applied AI Engineering (drift monitor) | `nist-ai-rmf` MEASURE |
| 9 | User-reported incident rate (Sev-2+) | Safety / quality (lagging) | ↓ | 0 baseline | 0 Sev-2+; Sev-3 triaged ≤ 1 business day | Weekly | Enablement (mod-109 incident intake) | Brief Section 4 row 6 + mod-109 |
| 10 | Inference cost per transaction (blended input + output tokens) | Cost (leading) | ↓ or stable | Set at limited-GA gate | Within `<!-- org-specific: budget envelope not-to-exceed, per Exercise 01 Section 7 -->` | Weekly | Applied AI Engineering (provider billing) | `<!-- org-specific: provider billing granularity -->` |
| 11 | Monthly cost per active operator (fully loaded: licenses + inference + enablement ops allocation) | Cost (leading → lagging) | ≤ envelope | Set at limited-GA gate | ≤ `<!-- org-specific: per-operator envelope, per Exercise 01 Section 7 -->` | Monthly | Enablement + Finance (cost-model reconciliation per mod-107 Exercise 01) | — |
| 12 | Training reach (% of addressable operators who have completed the BDTA SOP walkthrough) | Adoption (leading) | ↑ | 0% pre-launch | ≥ 95% by month 2 of GA | Monthly | Enablement + L&D (LMS report) | Per mod-104 training-reach cadence |
| 13 | Champion-network sentiment and field-report count | Adoption / safety (leading, qualitative) | n/a (signal) | 0 pre-launch | ≥ 1 field report per champion per month | Monthly | Enablement (per mod-105 champion pattern) | Qualitative signal; feeds the retrospective at the quarterly review |

### 2.4 Review cadence

Three tempos; one incident-triggered off-cycle path.

| Cadence | Attendees (role names) | Standing agenda | Decisions in scope |
|---|---|---|---|
| **Weekly eval review** (30 min) | AI Enablement Lead, Applied AI Engineer, Enablement operations analyst | Indicator 6 / 7 / 8 / 9 / 10 readouts; prompt-injection probe-set status; drift-monitor alarms | Hold / investigate / pause-and-triage |
| **Monthly operational review** (60 min) | Weekly attendees + business sponsor + L&D partner + Security intake partner | Full indicator pack; adoption cohort progress; cost reconciliation (indicator 10 / 11); CSAT and FCR trend (indicators 4 / 5) | Scope changes, rollout cohort widening, kill-criterion check |
| **Quarterly strategic review** (half-day) | Monthly attendees + `head-of-ai-governance` (L60) + Finance partner + Procurement AI-sourcing lead | Quarterly trend review across all 13 indicators; champion-network field reports (indicator 13) as qualitative signal; renewal / consolidation / expansion decision; measurement-plan amendments | Continuation / widening / narrowing / sunset; renewal and consolidation decisions (feeds mod-107 exercises) |
| **Off-cycle — incident path** | Convened by the Enablement Lead within 1 business day of Sev-2+ | Scope-restricted to the incident, per mod-109 | Pause / rollback per mod-109 rollback playbook |

Weekly and monthly reviews are **standing** — they happen whether or not there is new data, so the absence of signal is itself a signal. Quarterly reviews are **decision-bearing** — a kill, widen, narrow, or hold decision is recorded at each one.

### 2.5 Kill-or-grow decision thresholds

Thresholds are pre-committed. Decisions ride on signals the plan already said would cause them.

**Kill thresholds (sunset per brief Section 10):**

- Indicator 6 (faithfulness) < 85% for two consecutive weekly reviews, or any single week < 75%.
- Indicator 7 (prompt-injection resilience) < 90% at any monthly review.
- Indicator 9 (user-reported Sev-2+ incidents) > 0 within the commissioning window, or sustained > 2 Sev-3 per month across two months.
- Indicator 4 (CSAT) regression > 2 points for two consecutive months.
- Indicator 11 (cost per active operator) > 25% over envelope for two consecutive months with no reconciling explanation.
- Any regulatory or policy change that invalidates the brief Section 3 data-handling posture without a feasible remediation path.

**Narrow thresholds (restrict cohort, hold expansion):**

- Indicator 1 (reach) < 50% by month 3 — restrict to the engaged cohort; do not expand until adoption is understood.
- Indicator 2 (draft-adoption rate) < 30% at month 3 — restrict and investigate; adoption without use is a maintenance liability.
- Indicator 8 (drift) alarms > 1 per month sustained — hold expansion until the drift root cause is understood.

**Grow thresholds (widen cohort or widen scope):**

- Indicators 2, 3, and 5 (draft adoption, triage time, FCR) all meeting target for two consecutive months AND indicators 4, 6, 7, 9 (CSAT, faithfulness, prompt-injection resilience, incidents) at or inside their targets AND indicator 11 (cost per operator) at or under envelope — widen cohort by the next planned increment, or widen scope to an adjacent case family.
- Grow decisions are ratified at the quarterly strategic review, not at a monthly review. Monthly reviews can *recommend* a grow; they do not *ratify* one.

### 2.6 Instrumentation inventory

Listed once so that the operational reviews know where to look when a number is missing or disputed.

| Instrument | Owner | Grain | Retention | Notes |
|---|---|---|---|---|
| Operator-console session log | Applied AI Engineering | Per session, per operator, per case | Per telemetry retention policy | Feeds indicators 1, 2, 3 |
| Edit-distance telemetry on adopted drafts | Applied AI Engineering | Per draft | Same as above | Feeds indicator 2 |
| CRM report (FCR, CSAT) | Enablement (consumes), CRM team (owns) | Per interaction | Per CRM retention | Feeds indicators 4, 5 |
| Eval harness (faithfulness, prompt-injection probe set) | Applied AI Engineering | Per weekly run, per test-set version | Per eval retention policy | Feeds indicators 6, 7 |
| Drift monitor (rolling-window divergence) | Applied AI Engineering | Daily, rolling 14-day window `<!-- org-specific -->` | Per telemetry retention policy | Feeds indicator 8 |
| Incident intake (mod-109 path) | Enablement | Per incident | Per incident policy | Feeds indicator 9 |
| Provider billing export | Applied AI Engineering + Finance | Per billing cycle | Per Finance retention | Feeds indicators 10, 11 |
| LMS report | L&D | Per course completion | Per LMS retention | Feeds indicator 12 |
| Champion-network field-report log | Enablement | Per field report | Per working-folder retention | Feeds indicator 13 |

### 2.7 Decision rationale — why this shape, not another

- **Why four families (adoption, outcome, safety, cost).** Any plan with only one family is a plan that under-detects at least one failure mode. Adoption without outcome tracks activity but not value; outcome without safety tracks value but not harm; safety without cost tracks harm but not sustainability; cost without the others tracks nothing at all. The four together are the minimum spanning set.
- **Why leading *and* lagging.** Leading-only misses do-no-harm regressions (CSAT, FCR). Lagging-only misses early kill signals (faithfulness drops, drift alarms). The plan carries both and names the family on each row so reviewers do not confuse one for the other.
- **Why instrumentation ownership on every row.** A plan without named owners has one of two failure modes: the number is not instrumented (and the review becomes anecdotal), or it is instrumented twice and the two numbers disagree. Naming the owner prevents both.
- **Why three review tempos.** A single tempo runs at the wrong pace — weekly is too frequent for cost reconciliation; quarterly is too slow for drift alarms. The three tempos match the three timescales the indicators operate on.
- **Why kill thresholds are pre-committed.** Committing kill thresholds in the middle of a pilot under mixed signals is near-impossible. Committing them in advance, when there is no sunk cost, is the only moment they can be set honestly.
- **Why champion-network field reports are a first-class indicator (row 13).** Quantitative indicators miss the qualitative signals (operators are using the tool as directed vs. are routing around it). The champion-network field-report cadence from mod-105 is the mechanism that surfaces those signals without a survey.
- **Why drift monitoring is a daily automated signal, not a monthly review item.** Drift is a trailing-edge signal of model, data, or input-distribution change; by the time a monthly review catches it, the downstream outcome indicators have already moved. Daily automated monitoring with weekly summarisation keeps the loop tight.

## 3. Validation steps

1. **Thirteen indicators present** (or more, if the learner's engagement warrants), spanning the four families (adoption, outcome, safety, cost).
2. **Every indicator has five properties populated**: name, direction, baseline, target, instrumentation owner. A row missing any of the five is a fail.
3. **Both leading and lagging indicators present in the Outcome and Safety families.** A leading-only or lagging-only plan is a fail.
4. **Three review tempos named** (weekly, monthly, quarterly) with attendees, agenda, and decisions-in-scope per tempo.
5. **Incident off-cycle path defined** and anchored to mod-109.
6. **Kill thresholds pre-committed** and tied to specific indicators with specific numeric thresholds and persistence conditions ("two consecutive weeks," "> 25% for two months").
7. **Narrow and grow thresholds also pre-committed.** A plan with kill-only thresholds is incomplete — the plan's job is also to tell the engagement when to widen.
8. **Instrumentation inventory populated** with owner, grain, and retention per instrument.
9. **Named references to `owasp-ml-top-10`, `mitre-atlas`, `nist-ai-rmf`** on the safety-family rows and the drift row.
10. **Cross-references** to Exercise 01 (brief Section 4), Exercise 03 (handoff contract Section 5), mod-104 (training-reach cadence), mod-105 (champion-network cadence), mod-106 (scorecard tempo), mod-107 (cost-model reconciliation), mod-109 (incident intake, rollback).
11. **Role-name addressing throughout.** No people names in load-bearing clauses.
12. **`org-specific` tags** on baselines, cohort counts, cost envelopes, and drift-window parameters that are not instrumented in the learner's org.
13. **No vendor product names.**

## 4. Rubric / review checklist

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | Four families represented (adoption, outcome, safety, cost) with ≥ 2 indicators each | 10 | Any family absent or underweight. |
| R2 | Every indicator has the five properties (name, direction, baseline, target, instrumentation owner) | 20 | Any row missing any property. |
| R3 | Both leading and lagging indicators in the Outcome and Safety families | 10 | Leading-only or lagging-only. |
| R4 | Three review tempos named with attendees, agenda, decisions per tempo | 10 | Fewer than three or any tempo under-specified. |
| R5 | Incident off-cycle path anchored to mod-109 | 5 | No off-cycle path. |
| R6 | Kill thresholds pre-committed per indicator, with persistence conditions | 15 | Thresholds vague or absent, or not pre-committed. |
| R7 | Narrow and grow thresholds pre-committed (not only kill) | 10 | Kill-only thresholds. |
| R8 | Instrumentation inventory with owner, grain, retention | 5 | Inventory absent or underspecified. |
| R9 | Safety / drift rows cite `owasp-ml-top-10`, `mitre-atlas`, and `nist-ai-rmf` by name | 5 | Generic risk language. |
| R10 | Cross-references to Exercise 01, Exercise 03, mod-104 / 105 / 106 / 107 / 109 | 5 | No cross-references. |
| R11 | Role-name addressing; `org-specific` tags on unverifiable specifics | 5 | People names in load-bearing clauses or unmarked quoted numbers. |

**Pass threshold:** ≥ 85/100 and no R2 / R6 / R7 fail. R2 (five-property rows), R6 (pre-committed kill thresholds), and R7 (narrow / grow thresholds, not kill-only) are the three discriminators between a plan that drives decisions and a plan that reports numbers.

## 5. Common mistakes

- **Indicators without baselines.** An indicator without a baseline is a wish. At month 3 the review has no basis for saying whether the number is good or bad. Set baselines at the limited-GA gate; mark `<!-- org-specific -->` any baseline not yet measured.
- **Only outcome indicators, no safety or cost.** A plan without safety misses faithfulness drops and prompt-injection regressions until users report them. A plan without cost tracks nothing about sustainability. Both failure modes compound.
- **Only lagging indicators.** By the time CSAT regresses, the engagement is already in trouble. Leading indicators (faithfulness, drift, cost per transaction) surface the trouble weeks earlier.
- **Shared instrumentation ownership.** If two functions own the same indicator, the two numbers will disagree and the review will debate instrumentation rather than decisions. Name one owner per row.
- **Review tempo mismatched to signal timescale.** Monthly review of drift misses the signal; quarterly review of cost misses the overrun window. Each row belongs to the tempo whose decisions it informs.
- **Kill thresholds added late or left vague.** "We'll sunset if things go badly" is not a kill threshold. Pre-commit numeric thresholds with persistence conditions.
- **No grow thresholds.** A plan that only names kill thresholds under-widens on a working tool because every grow decision is re-litigated case-by-case.
- **Drift monitor as a monthly review item.** Drift is daily; monthly is the wrong tempo. Alarms are automated; summarisation is weekly; decisions are at the monthly or off-cycle review.
- **Qualitative signals discarded because they are qualitative.** Champion-network field reports are a first-class indicator (row 13); they surface signals the quantitative instruments miss (operator workarounds, UI confusion, scope drift).
- **Plan not tied to the brief.** The plan's indicators must trace back to the brief Section 4 targets. A plan with indicators the brief did not promise is a plan that moved the goalposts.
- **Promising instrumentation that is not feasible.** If the operator console does not log edit-distance, the draft-adoption indicator is aspirational. Flag instrumentation whose feasibility is not yet confirmed with an `<!-- org-specific: confirm operator-console telemetry supports edit-distance capture -->` tag; do not quote the indicator as live until the instrumentation is verified.

### 5.1 Stretch — rolling three-engagement view

For a mature program, the measurement plan is instantiated per engagement, but a **rolling three-engagement view** lives alongside the per-engagement plans. The rolling view:

- Reports the same indicator families across all active commissioned tools so the quarterly strategic review can see pattern-level signals (e.g., three different tools all tripping the drift alarm in the same month suggests a platform-level issue, not per-tool).
- Feeds the mod-106 executive scorecard at a consistent grain.
- Feeds the mod-107 Exercise 05 consolidation decision at the quarterly cadence by surfacing tools whose cost-per-operator is drifting above the consolidation threshold.
- Feeds the mod-109 incident retrospective cadence by letting the retrospective see whether an incident at one tool shares patterns with signals at a peer tool.

The rolling view is one page, with one row per engagement and one column per indicator family (adoption / outcome / safety / cost) at a traffic-light grain. The per-engagement plan is the source of truth; the rolling view is the pattern-detection instrument.

## 6. References

- **Learning material (local):**
  - [Exercise 01 — Commissioning Brief Drill](../exercise-01-commissioning-brief-drill/SOLUTION.md) — the brief Section 4 metrics that this plan extends and instruments.
  - [Exercise 02 — Prototype Inheritance and Productionise Decision](../exercise-02-prototype-inheritance-and-productionise-decision/SOLUTION.md) — the decision that routes an artifact into a full-grain or minimum-viable measurement plan.
  - [Exercise 03 — Handoff Contract with Applied AI Engineer](../exercise-03-handoff-contract-with-applied-ai-engineer/SOLUTION.md) — the contract that names the measurement plan as a condition of entry to the limited-GA gate and names the eval-harness ownership that feeds the safety family.
  - [mod-104 — Training Programs and AI Literacy Curriculum](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-104-training-programs-and-ai-literacy-curriculum) — training-reach cadence feeding indicator 12.
  - [mod-105 — Champion Networks and Change Management](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-105-champion-networks-and-change-management) — champion-network field-report pattern feeding indicator 13.
  - [mod-106 — Outcome Measurement and Executive Reporting](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-106-outcome-measurement-and-executive-reporting) — the executive scorecard that consumes the monthly indicator pack.
  - [mod-107 — Budget, ROI, and Build-vs-Buy at Org Scope](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-107-budget-roi-and-build-vs-buy-at-org-scope) — the cost-model reconciliation feeding indicator 11, and the consolidation decision that consumes the rolling three-engagement view.
  - [mod-109 — AI Incident Response and Enablement-Side Rollback](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-109-ai-incident-response-and-enablement-side-rollback) — the incident intake path, severity scale, and rollback playbook anchoring indicator 9 and the off-cycle cadence.
- **Official standards and frameworks:**
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — the MEASURE function underpins the safety-family rows and the drift-monitor indicator; the MANAGE function underpins the pre-committed kill, narrow, and grow thresholds.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — threat posture lens behind indicator 7 (prompt-injection resilience).
  - [MITRE ATLAS](https://atlas.mitre.org/) — adversarial-technique lens alongside OWASP for indicator 7 and the red-team-adjacent probe set.
