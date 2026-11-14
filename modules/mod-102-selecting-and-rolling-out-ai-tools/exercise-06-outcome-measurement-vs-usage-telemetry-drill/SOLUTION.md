# Exercise 06 — Outcome Measurement vs. Usage Telemetry Drill — Solution

> Module: `mod-102-selecting-and-rolling-out-ai-tools`
> Exercise type: design / measurement plan + classification drill
> Exercise brief: `lessons/mod-102-selecting-and-rolling-out-ai-tools/exercises/exercise-06-outcome-measurement-vs-usage-telemetry-drill.md` (in the learning repo)

## 1. Solution overview

"80% of eligible users have activated the tool" is a usage number. It is not an outcome. Rolling it up as success is the single most common AI enablement reporting failure. The exercise builds the habit of asking, for every number on a report: **is this an outcome, or is this a leading indicator of possible outcome?**

This solution provides:

1. A **definitions block** — what counts as an outcome, what counts as a leading indicator, and why the distinction matters.
2. A **classification drill** — 12 candidate metrics, each classified with rationale.
3. A **measurement plan template** that an AI Enablement Lead can apply to any rollout.
4. A **worked measurement plan** for the running AI coding assistant pilot in this module.

The classification drill is the centerpiece. If a learner can correctly classify twelve mixed metrics and justify the classifications, they can design the metrics rows in exercise-03's weekly report and the success definition in exercise-04's charter without re-learning the pattern each time.

## Implementation

Apply this solution by working the classification drill in section 2 to internalize the four metric types, then filling the measurement plan template against the specific pilot — baselines first, primary outcome second, non-regression floor third, leading indicators and governance signals labeled last. Validate the finished plan against section 3 and score against the rubric in section 4; section 5 lists the common failure modes the outcome-vs-usage separation is designed to resist.

## 2. Worked answer

### Definitions

**Outcome metric.** A measure of a business or work result the organization would care about **even if the tool did not exist**. It attaches to a named workflow and a named baseline. It has a target and a source. Examples (at the pattern level): cycle time on a named workflow; quality signal on a named workflow; reduction in time-to-first-draft of a named deliverable; defect rate; customer response time. Outcomes are what pilots succeed or fail against.

**Leading indicator (usage telemetry).** A measure of *whether users are in a position to produce an outcome*. Enrollments, activations, DAU/WAU, suggestions-accepted rate. Leading indicators have no target that implies success; they have **ranges** that trigger action. "Activation below X% at Week N" triggers a coaching intervention, not a failure declaration.

**Governance signal.** A measure of whether the governance posture is intact. Open exceptions, open security findings, number of policy breaches reported, number of amnesty self-reports. Governance signals have **floors/ceilings**, not targets.

**Non-regression floor.** The outcome dimension you do not want to lose. The non-regression floor is as important as the primary outcome; a pilot that improves speed and degrades quality is not a success without an explicit decision that said so.

Why the distinction matters:

- **Reporting integrity.** Mixing usage with outcome inflates success. An exec who reads "92% adoption" infers value. An exec who reads "92% adoption, primary outcome tracking flat vs. baseline at Week 4" infers correctly.
- **Decision integrity.** Charter decisions (exercise-04) hinge on outcomes, not usage. If the success definition is usage, the pilot cannot fail on usage terms — adoption is almost always achievable with enough enablement effort, because enablement is paying for it.
- **Measurement cost.** Outcomes are expensive to measure. If you skip the work, you will end up optimizing the leading indicator because it is cheap to see.

### Classification drill

Each candidate metric is classified as **Outcome**, **Leading indicator (usage)**, **Governance signal**, or **Neither** (i.e., a metric that should not appear on the rollout report at all).

| # | Candidate metric | Classification | Rationale |
|---|---|---|---|
| 1 | Median change-review cycle time on AI-assisted PRs vs. baseline | Outcome | Attaches to an existing workflow (code review), has a baseline, and would be cared about even without the tool. |
| 2 | Number of engineers who have logged in at least once | Leading (usage) | Access ≠ value. Useful as an enablement input, useless as a success statement. |
| 3 | Suggestions-accepted rate | Leading (usage) | Can correlate with value but is also inflated by users who accept to be polite or to test; not an outcome. |
| 4 | Number of secret-paste incidents reported | Governance signal | A floor metric (want this near zero but also want the self-report channel exercised). Context-dependent on the amnesty clause. |
| 5 | Post-merge defect rate on AI-assisted PRs | Outcome (non-regression) | Classic non-regression floor; attaches to a long-standing quality signal. |
| 6 | Number of help-channel questions in week 1 | Neither — operational signal | Useful to size support load, not a success or governance metric; keep off the exec report. |
| 7 | NPS from pilot users on the tool itself | Leading (satisfaction) | Correlates with sustained adoption; is not an outcome because it does not measure the work result. |
| 8 | % of PRs that passed CI on first push | Outcome | Attaches to an existing workflow and measures work quality; usable as secondary outcome if baselined. |
| 9 | Number of exception requests open > SLA | Governance signal | Ceiling metric; signals policy/operational drift. |
| 10 | Cost per active user | Neither — financial, but off the rollout report | Belongs to the FinOps/ROI artifact (`mod-107-budget-roi-and-build-vs-buy-at-org-scope`), not to the rollout report. <!-- to-verify: confirm cross-module reference. --> |
| 11 | Number of policy acknowledgments collected | Leading (compliance hygiene) | Counts access entitlement + policy sign, not value. Needed to launch; not a success measure. |
| 12 | Reviewer-rated code quality on AI-assisted PRs (sample-based) | Outcome | Measures work result; sample-based is fine if the sampling plan is written down. |

The drill's lesson: of twelve plausible rollout metrics, only four are outcomes (one of which is a non-regression). The majority of what shows up on a dashboard is leading or governance, which is fine — provided it is labeled as such.

### Measurement plan template

> **Measurement plan — `[Tool Name]` — v1.0**
>
> **Scope:** which pilot, which teams, which workflows.
>
> **Baselines:** for each outcome, state *baseline method*, *baseline window*, *baseline value* (or "to be measured in weeks -4 to 0 before pilot start"). Baselines must be real, not estimated.
>
> **Primary outcome**
> - Name, source, baseline, target, sampling plan (if not census), who computes it, review cadence.
>
> **Secondary outcomes (≤ 2)**
> - Same shape.
>
> **Non-regression floors**
> - Name, source, baseline, floor. At least one.
>
> **Leading indicators**
> - Named with explicit "not a success metric" label. Each has an action range, not a target.
>
> **Governance signals**
> - Named with explicit ceiling/floor direction and the action triggered when they move.
>
> **Reporting**
> - Where the weekly report pulls these from (exercise-03), who writes them, who signs them, how they change.
>
> **Attribution honesty**
> - A short paragraph on what the plan *cannot* attribute. E.g., it cannot prove the tool caused improvement without a controlled comparison; it can show whether improvement coincided with rollout. This is required to be present.

### Worked measurement plan (AI coding assistant pilot)

- **Scope:** platform-infrastructure practice area pilot (18 engineers), as per the charter in exercise-04.
- **Baselines:** collected from SDLC telemetry over the four weeks before pilot start.
- **Primary outcome:** median change-review cycle time on AI-assisted PRs vs. baseline. Source: SDLC telemetry. Baseline: measured from historical PRs; sampling: census of eligible PRs. Target: pre-committed in exercise-04. Owner: AI Enablement Lead; computed by platform data team.
- **Secondary outcomes:**
  - Reviewer-rated code quality on AI-assisted PRs (sample of 20 PRs/week, two reviewers, blind rubric).
  - CI-first-push pass rate on AI-assisted PRs.
- **Non-regression floor:** post-merge defect rate, floor = baseline. Source: incident/defect system.
- **Leading indicators (labeled, no target):** enrolled, activated, suggestions-accepted rate, policy-acknowledgment coverage. Action ranges, not targets: e.g., activation below 50% at Week 2 ⇒ coaching; suggestions-accepted rate above 95% ⇒ sample for over-acceptance.
- **Governance signals:** open high-severity findings (ceiling 0 to exit pilot), open exceptions beyond SLA (ceiling: any one triggers escalation), self-reported incidents (floor, encouraged under amnesty).
- **Reporting:** weekly table in exercise-03 report; owner AI Enablement Lead; signed off weekly by Pilot Owner and Engineering lead before publication.
- **Attribution honesty:** this plan does not include a randomized comparison. It can show whether outcomes moved during the pilot and whether they moved with the tool switched off during the rollback drill; it cannot prove causation. Any claim of "the tool caused X" must be dropped from reports in favor of "X improved during the pilot window."

## 3. Validation steps

A reviewer should be able to confirm, from the learner's artifact:

1. The learner names and defines outcome, leading indicator, governance signal, and non-regression floor.
2. The classification drill covers at least 10 candidate metrics, each with rationale.
3. At least one "Neither" classification appears in the drill, to show the learner recognizes metrics that should not be on the rollout report.
4. The measurement plan has exactly one primary outcome.
5. Each outcome has baseline, source, sampling plan (if not census), target, and owner.
6. At least one non-regression floor is present.
7. Leading indicators are labeled as such and have action ranges, not targets.
8. Governance signals have ceilings/floors and defined action triggers.
9. An attribution-honesty statement is present and acknowledges what the plan *cannot* show.
10. The measurement plan is wired to the weekly report (exercise-03) and charter (exercise-04).

## 4. Rubric or review checklist

Scored out of 20. 14+ passes; below 10 is a rework.

| # | Criterion | Max |
|---|---|---|
| 1 | Definitions block names all four metric types with rationale | 2 |
| 2 | Classification drill ≥ 10 candidates with rationale | 3 |
| 3 | Drill includes at least one "Neither" classification | 1 |
| 4 | Single primary outcome with baseline/source/target/sampling/owner | 3 |
| 5 | At least one non-regression floor | 2 |
| 6 | Leading indicators labeled with action ranges, not targets | 2 |
| 7 | Governance signals with ceilings/floors and action triggers | 2 |
| 8 | Attribution honesty statement present | 2 |
| 9 | Plan wired to exercise-03 report and exercise-04 charter | 2 |
| 10 | At least one metric row references `nist-ai-rmf` Measure outcomes explicitly | 1 |

## 5. Common mistakes

- **Vanity outcomes.** Dressing up a usage metric as an outcome by prefixing it with "business." "Business adoption at 92%" is still adoption.
- **Three primary outcomes.** Collapsing under pressure to "cover everything" produces a measurement plan that nothing can fail.
- **No baseline, or a baseline guessed in a meeting.** Baselines must be measured. A missing baseline is a `<!-- to-verify: ... -->` row, not a stand-in.
- **Sampling plan hidden.** "Reviewer-rated quality" without a written sampling procedure drifts into cherry-picking.
- **No non-regression floor.** The pilot "succeeds" and a quality signal degrades below where it started.
- **Targets on leading indicators.** Setting a target for suggestions-accepted rate encourages gaming.
- **Governance signals without action triggers.** A ceiling that is noted but not acted on is not a ceiling.
- **Overclaiming causation.** Writing "the tool reduced cycle time by X" when the plan does not support a causal claim. Outcomes "moved during" the pilot — that is the honest frame.
- **Cost on the rollout report.** Cost is a real metric but belongs on the ROI artifact, not the rollout report. Putting it on the rollout report invites the exec to optimize cost against value prematurely.

## 6. References

- NIST AI Risk Management Framework (AI RMF 1.0): <https://www.nist.gov/itl/ai-risk-management-framework> — the Measure function directly motivates the separation of performance measures, trustworthy characteristics, and risk-related measures that this exercise builds on.
- OWASP Machine Learning Security Top 10: <https://owasp.org/www-project-machine-learning-security-top-10/> — governance signals around abuse paths map to several categories in this list.
- MITRE ATLAS: <https://atlas.mitre.org/> — adversary-technique context for the governance signals an LLM-integrated tool's measurement plan should include.
- Local context: `exercise-03` (weekly report) consumes these rows; `exercise-04` (charter) consumes the primary/secondary/non-regression definitions; `exercise-05` (artifact set) lists the measurement sheet as artifact #11. Cross-module: `mod-106-outcome-measurement-and-executive-reporting` deepens the measurement craft; `mod-107-budget-roi-and-build-vs-buy-at-org-scope` owns cost-side metrics. <!-- to-verify: confirm cross-module titles in the learner's version of the curriculum. -->
