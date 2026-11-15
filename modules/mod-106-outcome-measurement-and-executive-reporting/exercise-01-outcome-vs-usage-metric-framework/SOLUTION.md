# Exercise 01 — Outcome vs. Usage Metric Framework — Reference Solution

> Module: `mod-106-outcome-measurement-and-executive-reporting`
> Exercise type: design / framework document
> Exercise brief: `lessons/mod-106-outcome-measurement-and-executive-reporting/exercises/exercise-01-outcome-vs-usage-metric-framework.md` (in the learning repo)

## 1. Solution overview

This exercise produces the **framework document** the enablement seat points to every time someone proposes a new metric for an AI program. It is deliberately a framework, not a dashboard — a dashboard changes with each tool; the framework does not. Its job is to make the same decision the same way across every pilot, every weekly scorecard, every quarterly review, and every ROI defence.

The framework carries four moves:

1. A **definitions block** — five metric types, each with an operational test the learner can run in under 30 seconds.
2. A **classification decision tree** — the exact questions a reader should run through to type any proposed metric.
3. A **shape-of-a-metric-row contract** — what fields every row must carry before it can appear on a report.
4. An **anti-pattern list** — the moves that look like outcomes but are usage, and the reverse.

The companion drill (`mod-102/exercise-06`) pressure-tests this framework against twelve candidate metrics. The weekly scorecard (`exercise-02` in this module) consumes its row contract. The quarterly board review (`exercise-03`) consumes its anti-pattern list. The ROI defence (`exercise-06`) consumes its attribution-honesty clause.

Posture checks the solution encodes:

- **Outcome metrics attach to a workflow that exists without the tool.** If the metric disappears when the tool is removed, it is usage.
- **Usage metrics are legitimate — but they are never the headline.** The framework does not demote usage; it refuses to let usage pose as outcome.
- **Every metric row carries attribution honesty.** The row says what the metric can and cannot tell you. The absence of that column is the single most common framework failure.
- **Governance signals are not outcomes and not usage.** They are their own class — floors/ceilings, not targets.
- **The framework is portable across tools.** It is written without reference to any specific vendor; vendor plugins into the framework happen in the scorecard and ROI artifacts.

## 2. Implementation — worked answer (`metric-framework.md`)

The artifact below is the document the enablement seat publishes to the governance council and distributes to any role (pilot owner, champion, FinOps partner) who proposes to put a metric on an exec-facing surface.

---

### AI Enablement Metric Framework — v1.0

**Owner:** AI Enablement Lead (this role).
**Audience:** governance council (consume), pilot owners and champions (apply before proposing a metric), FinOps partner (apply before proposing a cost or ROI metric).
**Scope:** every metric that reaches an exec-facing surface — weekly scorecard, quarterly board review, ROI memo, incident after-action. Operational signals that stay inside the enablement team (help-channel load, champion-roster size for routing) are out of scope.

---

#### 2.1 The five metric types

Every metric that reaches an exec-facing surface is exactly one of these five types. If a learner cannot type a proposed metric cleanly, that is the signal the metric is not yet well-defined.

**Type 1 — Outcome.** A measure of a work result the organization would care about even if the AI tool did not exist. Attaches to a named workflow with a pre-tool baseline. Carries a target. The 30-second test: *if we turned the tool off tomorrow, would we still measure this?* If no, it is not an outcome.

**Type 2 — Non-regression floor.** A paired outcome dimension the program must not lose while improving the primary outcome. Carries a floor (not a target). The 30-second test: *what outcome dimension would make us regret the gain in the primary outcome if it degraded?* That is the floor.

**Type 3 — Leading indicator (usage).** A measure of whether users are in a position to produce an outcome. Enrollments, activations, DAU/WAU, suggestion-acceptance rate, time-to-first-use. Carries an **action range**, not a target. The 30-second test: *if this number went to 100%, would the primary outcome move?* If the answer is "not necessarily," it is a leading indicator.

**Type 4 — Governance signal.** A measure of whether the governance posture is intact. Open exceptions, open security findings, incident counts, self-reported near-misses. Carries a **ceiling or floor direction** with an action trigger. The 30-second test: *does this metric describe a control, not a result?* If yes, it is a governance signal.

**Type 5 — Attribution-limit disclosure.** Not a metric *value* but a required row on every scorecard: one short line describing what the plan *cannot* attribute. The 30-second test: *could an informed exec correctly reconstruct what we claim the tool caused versus what merely coincided with the tool?* The attribution-limit row is how the honest answer is made visible.

**Not on an exec-facing surface:** operational signals (help-channel volume for staffing), vanity counts (training signups without competence evidence), and cost-per-user (belongs on the ROI artifact per `mod-107`, not the weekly scorecard — see Section 5).

---

#### 2.2 The classification decision tree

Run every proposed metric through this five-step tree, in order. The first "yes" assigns the type.

```
Q1. Does this metric describe a control, exception, incident, or policy-adjacent count?
    YES → Governance signal (Type 4). Assign ceiling/floor + action trigger. STOP.
    NO  → Q2.

Q2. Does this metric measure a work result that would still matter if the tool
    disappeared tomorrow, AND does a pre-tool baseline exist (or is one plannable)?
    YES → Outcome (Type 1) or Non-regression floor (Type 2).
          • If this is the dimension we are trying to improve: Outcome.
          • If this is a dimension we must not lose while improving the above: Non-regression floor.
          Assign baseline, target (Outcome) or floor (Non-regression), source, sampling plan.
          STOP.
    NO  → Q3.

Q3. Does this metric measure user activity, engagement, satisfaction with the tool,
    or compliance hygiene (policy acknowledgements, training completion)?
    YES → Leading indicator (Type 3). Assign action range, NOT a target. Label the
          scorecard row as "leading — not a success metric." STOP.
    NO  → Q4.

Q4. Is this metric a financial or cost measure (cost per user, cost per seat, cost per
    outcome unit)?
    YES → Not on this surface. Route to the ROI / FinOps artifact (mod-107). STOP.
    NO  → Q5.

Q5. Does this metric exist to help the enablement team run its own operations
    (help-channel load, champion-roster size, onboarding queue depth)?
    YES → Operational signal. Not on an exec-facing surface. Keep inside the team.
          STOP.
    NO  → The metric is not yet well-defined. Return to the proposer with the four
          failed questions above and ask for a tighter definition.
```

The decision tree is intentionally short and intentionally ordered. Governance signals are asked first because they are the easiest to misclassify as outcomes (an incident count "looks like a result"). Cost questions are asked fourth, not first, because they tempt the enablement seat to over-claim ROI before baselines exist.

---

#### 2.3 The metric-row contract

Every row that reaches an exec-facing surface must carry these fields. Rows missing any field are rejected back to the proposer.

| Field | Required content | Fail state |
|---|---|---|
| **Name** | Verb or noun phrase that names the thing measured and the unit. | "Productivity." "Impact." |
| **Type** | One of: outcome, non-regression floor, leading, governance signal. | Unlabeled; mixed types in the same row. |
| **Workflow** | The named business workflow the metric attaches to (for outcomes) or the control / usage surface it attaches to. | Not attached to any workflow or control. |
| **Baseline** | Measured value over a stated pre-tool window, or `<!-- author-to-confirm: baseline window and method to be measured in weeks -4 to 0 -->`. | Estimated in a meeting; no window stated. |
| **Target / range / direction** | Target (outcome), floor (non-regression), action range (leading), ceiling/floor + action trigger (governance). | A target on a leading indicator. A target on a governance signal. |
| **Source** | The specific system of record the number is read from. | "Dashboards." "The tool." |
| **Sampling plan** | Census or a named sampling procedure. | Review sample with no written procedure. |
| **Owner** | Named role who computes the metric and named role who signs it. | "The team." "Enablement." |
| **Cadence** | How often the value is refreshed (weekly, monthly, quarterly). | Refreshed when someone remembers. |
| **Attribution limit** | One short line: what this metric can and cannot support as a claim. | Missing. The row is rejected if this is missing. |

The **attribution-limit field** is the row contract's innovation over most vendor-provided dashboards. The field forces the author to write, in-line, what the metric can be used to claim. "Median change-review cycle time moved during the pilot window, from baseline X to current Y. This row does not support the claim that the tool caused the move — the plan does not include a controlled comparison." That is the honest shape of an outcome row.

---

#### 2.4 Anti-patterns

The framework is used against a standing list of anti-patterns. These are the moves to recognize at review time.

1. **Vanity outcome.** A usage metric dressed as an outcome by prefix. "Business adoption at 92%" is still adoption. If the metric fails Q2 of the decision tree, no prefix saves it.
2. **The composite dodge.** A single weighted index ("AI Health Score") mixing outcome, usage, and governance into one number. The composite always moves because *something* moved, and the exec cannot see which. Report the sub-metrics; refuse the composite.
3. **Three primary outcomes.** Collapsing under "we need to cover everything" and naming three primary outcomes. A pilot with three primary outcomes cannot fail.
4. **Missing non-regression floor.** The pilot "succeeds" on cycle time and a quality signal quietly degrades. The framework rejects any outcome row that is not paired with at least one explicit non-regression floor.
5. **Targets on leading indicators.** A target on "suggestion-acceptance rate" is a request to be gamed. Leading indicators get action ranges, not targets.
6. **Governance signals without action triggers.** A ceiling that is noted but not acted on is not a ceiling. Any governance row without an action trigger is rejected.
7. **Overclaimed causation.** "The tool reduced cycle time by X" when the plan does not support a causal claim. The framework rewrites this as "cycle time moved during the pilot window from X to Y; this is not a controlled comparison and does not support a causal claim."
8. **Cost on the rollout report.** Cost is a real metric but belongs on the ROI artifact per `mod-107`, not the rollout scorecard. Mixing them invites the exec to optimize cost against value prematurely.
9. **The retired-metric silence.** Dropping a metric that is going the wrong way. The framework requires: metrics are added; metrics are not deleted. A retired metric leaves a dash and a footnote.
10. **Scope-of-measurement drift.** The metric row name stays the same while the definition changes week to week. The framework requires that definition changes carry a version bump and a one-line change-note on the first report where they take effect.

---

### End of worked framework

## 3. Validation steps

Before publishing this framework to the governance council — and when grading a learner's submission — run it against this checklist.

1. **All five metric types present and defined.** Outcome, non-regression floor, leading indicator, governance signal, attribution-limit disclosure. If any of the five is missing, the submission is incomplete.
2. **Each type has a 30-second operational test.** Not a definition paragraph — a single testable question.
3. **Decision tree has five ordered questions.** The ordering is not arbitrary: governance first, outcome/non-regression second, leading third, cost fourth (route out), operational last. Reordering the tree breaks it.
4. **Decision tree has a STOP after each YES.** No branch should leave classification ambiguous.
5. **Metric-row contract has all ten fields.** Name, type, workflow, baseline, target/range/direction, source, sampling plan, owner, cadence, attribution limit.
6. **Attribution-limit field is required, not optional.** The fail state is "optional" because it will then be skipped.
7. **Anti-pattern list has at least eight entries.** Each written as a named move with the rewrite rule.
8. **Framework is tool-agnostic.** Grep the artifact for vendor names. If any appear, the framework has drifted into a measurement plan for a specific tool.
9. **Cross-exercise wiring is explicit.** The framework names which other exercises consume which parts (`exercise-02` the weekly scorecard consumes the row contract; `exercise-03` consumes the anti-pattern list; `exercise-06` consumes the attribution-limit clause; `mod-107` owns cost).
10. **No invented data.** Grep for `%`, dollar amounts, and specific minute/hour counts. Any that appear should be either clearly illustrative placeholders or marked `<!-- author-to-confirm: ... -->`.

Markdown-lint the file before publishing; the repo's `.markdownlint.jsonc` is the rule set.

## 4. Rubric / review checklist

Scored out of 100. Pass threshold: ≥ 80 and no R4/R5/R10 fail (those three are launch-gate equivalents).

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | All five metric types present and defined | 10 | Any of the five missing. |
| R2 | Each type carries a one-question 30-second operational test | 10 | Paragraph definitions without a test. |
| R3 | Decision tree is ordered and terminates on every branch | 10 | Non-terminating branches; ambiguous classifications. |
| R4 | Metric-row contract names all ten required fields | 15 | Any required field missing. |
| R5 | Attribution-limit row is required, not optional | 10 | Attribution-limit treated as "nice to have." |
| R6 | Anti-pattern list ≥ 8 entries, each named with rewrite rule | 10 | Vague anti-patterns without the rewrite. |
| R7 | Framework is tool-agnostic (no vendor names in the body) | 5 | Vendor name in the generic framework. |
| R8 | Cost / FinOps questions are routed out to `mod-107`, not answered here | 5 | Cost metrics defined in this framework. |
| R9 | Cross-exercise wiring to `exercise-02`, `-03`, `-06` is explicit | 10 | No pointer to downstream consumers. |
| R10 | No invented numeric claims; unknowns marked `<!-- author-to-confirm: ... -->` | 10 | Invented baselines, target numbers, or ROI figures. |
| R11 | Framework is written in operator-and-council voice, not vendor marketing voice | 5 | "AI-powered productivity insights." |

## 5. Common mistakes

- **Writing the framework as a glossary.** A glossary lists terms; a framework forces decisions. If the artifact has no decision tree and no row contract, it is a glossary and will not change behavior.
- **Letting cost creep into the framework.** Cost is a `mod-107` concern. Keeping it out of the metric framework is a deliberate scoping choice that prevents the weekly scorecard from becoming an ROI proxy.
- **Defining "AI Health Score" or similar composite.** Composites hide regressions. The anti-pattern list should name the composite dodge explicitly.
- **Making attribution-honesty optional.** It is the single field most often skipped when the framework is applied in practice. The row contract must list it as required.
- **Tying the framework to one vendor.** The framework governs across the portfolio. A framework that reads "measure Copilot adoption" is a Copilot measurement plan.
- **Omitting leading indicator action ranges.** "Activation" without a range is a number. "Activation below 50% at Week 2 ⇒ coaching intervention" is a decision rule.
- **Collapsing Type 2 (non-regression floor) into Type 1 (outcome).** They are measured the same way but consumed differently. The floor is what prevents "success at the cost of quality."
- **Overclaiming portability.** The framework is portable; the specific metrics inside a given scorecard are not. Writing "use these metrics for any AI tool" invites copying metrics across tools where baselines do not transfer.
- **No examples at all.** A framework with no illustrative row (even a placeholder) is hard to apply. Include at least one worked row — clearly marked as illustrative — so readers see the row-contract shape in use.

## 6. References

- **Official standards and frameworks:**
  - [NIST AI Risk Management Framework (AI RMF 1.0)](https://www.nist.gov/itl/ai-risk-management-framework) — the MEASURE function motivates the separation of performance measures, trustworthy characteristics, and risk-related measures that the five-type block builds on. The GOVERN function motivates the governance-signal class.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — governance signals around model abuse, data poisoning, and output handling map to several categories in this list.
  - [MITRE ATLAS](https://atlas.mitre.org/) — adversary-technique context motivating the governance-signal rows a scorecard should include (reconnaissance, input manipulation, model exfiltration).
- **Local context (same repo):**
  - `modules/mod-102-selecting-and-rolling-out-ai-tools/exercise-06-outcome-measurement-vs-usage-telemetry-drill/SOLUTION.md` — the twelve-metric classification drill that pressure-tests this framework.
  - `modules/mod-106-outcome-measurement-and-executive-reporting/exercise-02-the-weekly-executive-scorecard/SOLUTION.md` — consumes the row contract.
  - `modules/mod-106-outcome-measurement-and-executive-reporting/exercise-03-quarterly-board-ready-review-outline/SOLUTION.md` — consumes the anti-pattern list.
  - `modules/mod-106-outcome-measurement-and-executive-reporting/exercise-06-roi-numerator-and-denominator-defence/SOLUTION.md` — consumes the attribution-limit clause.
  - `modules/mod-107-budget-roi-and-build-vs-buy-at-org-scope/README.md` — owns cost and ROI metrics that this framework routes out of scope.
