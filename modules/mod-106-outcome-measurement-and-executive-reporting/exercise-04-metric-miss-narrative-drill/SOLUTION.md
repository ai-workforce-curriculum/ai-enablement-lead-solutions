# Exercise 04 — Metric Miss Narrative Drill — Reference Solution

> Module: `mod-106-outcome-measurement-and-executive-reporting`
> Exercise type: drill / before-and-after rewrites + rubric
> Exercise brief: `lessons/mod-106-outcome-measurement-and-executive-reporting/exercises/exercise-04-metric-miss-narrative-drill.md` (in the learning repo)

## 1. Solution overview

Every AI enablement program will miss a metric. The question is not whether, it is what the enablement seat says about it. This drill builds the **honest-narration** habit: a small, named structure the learner can apply in the moment when a primary outcome moves against plan.

The failure modes the drill is designed to resist are familiar from any bad status email:

- **Defensiveness** — explaining why the miss is not really the program's fault.
- **Catastrophizing** — treating a single miss as a program-level failure to signal seriousness.
- **Burying** — moving the miss from §1 of the weekly scorecard into a footnote or a §7 risk bullet.
- **Over-attributing** — claiming a specific external cause the plan cannot support.
- **Promising-the-fix-early** — committing in writing to a specific corrective action before the cause is understood.

The solution provides:

1. The **four-move narration structure** — *name the miss, name the cause with its uncertainty, name the ask, name the next observable*.
2. A **bank of five bad narrations** (each a realistic first-draft failure mode) with the rewrite and a note on what makes the rewrite work.
3. A **before-the-rewrite checklist** — the four questions the author answers in a notebook before they write the rewrite, so the rewrite is grounded.
4. A **rubric** for scoring a learner's rewrite against the four-move structure.

The drill assumes the metric framework from `exercise-01` and the scorecard shape from `exercise-02`. A narration is published in §7 (risks and asks) or §8 (decisions acknowledged) of the weekly scorecard, with a one-line reference in §1 that names the miss by metric and by magnitude.

Posture checks the solution encodes:

- **Honest narration ≠ confession.** The rewrite is not "we failed." It is a bounded, specific account of what moved and what the author can and cannot claim about it.
- **Uncertainty about cause is a feature.** A rewrite that names a specific cause with no evidence is worse than one that names two candidate causes and says "we are investigating which."
- **The ask is always specific.** The miss narration either asks for something or declares it does not. Vague "please support the team" does not belong on an exec-facing surface.
- **The next observable is in the artifact.** If the author writes "we expect X by Y date," the next scorecard checks against that. No next-observable means no accountability loop.

## 2. Implementation — worked answer

### 2.1 The four-move narration structure

A metric-miss narration is **four sentences** in §7 of the weekly scorecard. Not three; three leaves out the next observable. Not five; five becomes defense.

```
Move 1 — name the miss.
  One sentence. Metric name, baseline / prior week, current reading, magnitude
  of the miss (absolute or relative). No adjectives. No "unfortunately."

Move 2 — name the cause with its uncertainty.
  One sentence. The one or two credible candidate causes, with explicit
  uncertainty about which. If the author has identified a confirmed cause, the
  sentence names it with the evidence; if not, it names the top two candidates
  and the investigation path.

Move 3 — name the ask.
  One sentence. Either a specific ask (decision, resource, pause, escalation)
  with a named addressee and by-when, OR an explicit "no ask this week; status
  update next week."

Move 4 — name the next observable.
  One sentence. What specific signal the next scorecard will check against, by
  what date. "If activation does not return above Y by Week N+2, we will escalate
  to Z." The next observable is the accountability anchor.
```

The four moves are in this order deliberately. Naming the miss first prevents the reader from having to search for it; naming cause with uncertainty second prevents the ask from reading as a blame-shift; naming the ask third prevents the next observable from being read as a promise of the fix; naming the next observable last makes it the thing the next scorecard can check.

### 2.2 Before-the-rewrite checklist

Before writing the four moves, the author answers these four questions in a notebook — not in the scorecard. The answers inform the rewrite; they do not appear in it.

1. **What does the scorecard row actually say against the row-contract fields** (from `exercise-01`)? Name the metric, its type, its source, its sampling plan, its attribution-limit line. If any of these are missing, the row is under-defined and the "miss" might be a definition problem, not a program problem.
2. **How many data points is the miss based on?** One week of movement on a weekly cadence is not a trend; it is a reading. The narration should not overstate.
3. **What cause-candidates are actually credible given the evidence?** List the top three; cross out any that cannot be distinguished from the others without an experiment.
4. **What would turn this miss into something that warrants a §1 headline posture change?** The answer is the next-observable in Move 4.

### 2.3 Bad narration bank and rewrites

Each entry is a realistic first-draft the enablement seat will write under time pressure. The rewrite applies the four moves and the checklist. The commentary names what makes the rewrite work.

---

**Bad narration #1 — the apologia**

> Unfortunately, the activation rate missed target this week due to a number of factors outside our control, including a conflict with team quarterly planning and a short holiday. We are confident in the fundamentals of the rollout and will continue to drive adoption through additional outreach. We expect activation to recover.

*Rewrite (four moves):*

> **Activation for the coding-assistant pilot read `<!-- author-to-confirm: current activation rate -->` at Week 6, down from `<!-- author-to-confirm: Week 5 activation rate -->`.** The two credible candidate causes are the organization-wide quarterly-planning window the pilot cohort was in during this week and a two-day holiday that reduced the denominator of eligible working days; the week's reading is one data point and does not yet distinguish the two. **No ask this week; status update next week.** The next scorecard will check whether activation returns to or above the Week 5 reading; if it does not, we will treat Week 6 as the start of a trend and bring a coaching-intervention plan to the sponsor at Week 8.

*What makes the rewrite work:*

- "Unfortunately" removed; miss named with current and prior readings.
- Activation is a leading indicator (per `exercise-01`), so the rewrite does not treat the miss as a program-level failure.
- Two credible causes named; the uncertainty between them is explicit.
- The "we are confident / we will drive adoption" language is replaced with a specific next-observable.
- The ask is explicit ("no ask this week"), not implied.

---

**Bad narration #2 — the external-blame**

> The outcome regressed this week because the vendor shipped a backend change that affected suggestion quality. We have raised a ticket with the vendor and expect resolution next week. Once resolved, the outcome will return to plan.

*Rewrite:*

> **Reviewer-rated code quality on the sampled AI-assisted PRs this week averaged `<!-- author-to-confirm: current mean -->`, down from `<!-- author-to-confirm: prior mean -->`** against a baseline mean of `<!-- author-to-confirm: baseline mean -->`. The movement coincides with a vendor-reported backend change `<!-- author-to-confirm: vendor ticket ID -->`; the direction of the quality change is consistent with the vendor change, but the sample size (`<!-- author-to-confirm: n -->`) is not large enough to distinguish the vendor change from normal week-to-week variation. **Ask of the sponsor: confirm that we are authorized to pause the pilot's onboarding wave planned for next week until the vendor closes the backend ticket; recommended decider CTO by `<!-- author-to-confirm: date -->`.** The next scorecard will check two things: whether the reviewer-rated quality mean recovers, and whether the sampling-window mean on non-AI-assisted PRs moved in the same direction (which would argue against a tool-specific cause).

*What makes the rewrite work:*

- "The outcome regressed" is replaced with the specific metric, reading, prior reading, and baseline.
- The "the vendor did it" claim is replaced with a coincidence claim bounded by sampling-size honesty.
- The implicit "we promise recovery" is replaced with a specific ask (pause authority) and a specific next observable (the counterfactual check against non-AI-assisted PRs).

---

**Bad narration #3 — the catastrophe**

> This week's incident is a serious blow to the program. We have identified a systemic weakness in our rollout approach, and we are considering pausing the entire enablement effort pending a top-to-bottom review. This will significantly impact the roadmap.

*Rewrite:*

> **One high-severity finding (`SEC-AI-00117`) was opened this week against the customer-support-agent pilot, affecting the output-handling path.** The finding's cause is a vendor-side configuration default that the pilot's intake review did not catch; this is a specific gap in the intake questionnaire (per `mod-103/exercise-03`), not a systemic failure of the rollout approach. **Ask of the sponsor and head-of-ai-governance (L60): approve a 14-day pilot pause while the vendor delivers the fix, during which this role will re-run the intake questionnaire with the new field; decider CTO + General Counsel by `<!-- author-to-confirm: date -->`.** The next scorecard will check: vendor fix confirmed, intake questionnaire v2.2 ratified, and the single additional field added to the schema for future reviews.

*What makes the rewrite work:*

- The catastrophe voice ("serious blow," "top-to-bottom review") is replaced with the specific finding, specific cause, and specific scope ("this is a specific gap in the intake questionnaire").
- The implicit threat of pausing the whole program is replaced with a bounded, ask-shaped pause for the one affected pilot.
- The next-observable is three specific things, each check-able next week.

---

**Bad narration #4 — the buried signal**

> Overall the program is on plan this week. Activation is at `<!-- author-to-confirm: current rate -->`, suggestion-acceptance is at `<!-- author-to-confirm: current rate -->`, and we had a slight dip in reviewer-rated code quality that we are watching. See §7 for details.

*Rewrite:*

> §1 headline becomes: **Posture Amber — reviewer-rated code quality dipped in the Week-N sample from `<!-- author-to-confirm: prior mean -->` to `<!-- author-to-confirm: current mean -->`; see §7 for narration.** The §7 entry runs the four moves as in #2 above.

*What makes the rewrite work:*

- The dipping outcome does not stay buried in §7; it surfaces in §1 so the exec who only reads §1 sees it.
- The two leading indicators (activation and suggestion-acceptance) are reported in §5 per `exercise-02`, not used to drown out the outcome signal in §1.

---

**Bad narration #5 — the premature fix**

> Activation missed target this week. We have already implemented a new outreach plan with the champions, and we expect activation to recover by next week. This should not recur.

*Rewrite:*

> **Activation for the coding-assistant pilot read `<!-- author-to-confirm: current -->` at Week N against the action-range floor of `<!-- author-to-confirm: action-range floor from exercise-01 -->`.** The top two credible causes are an onboarding-queue bottleneck in the identity team and a cohort-specific morale factor; the week's reading does not yet distinguish them. **No ask this week.** The next scorecard will check: whether activation returns above the action-range floor **and** which of the two cause-candidates was addressed by the champion-led intervention running this week; if activation recovers and the identity-team-queue intervention was the one that landed, we will update the onboarding playbook (`mod-102`, artifact set) accordingly.

*What makes the rewrite work:*

- The "we have already implemented a fix" claim is replaced with "an intervention is running this week," which is observable in next week's scorecard.
- The "this should not recur" promise is removed; nothing has been learned yet that would support it.
- The next-observable explicitly separates "did the metric recover" from "did the attempted intervention cause the recovery," which is the attribution-honesty discipline from `exercise-01`.

---

### 2.4 Walkthrough — annotated rewrite of bad narration #2

To demonstrate the four moves against the checklist, this walkthrough shows how bad narration #2 is converted to its rewrite by running the four checklist questions first.

**Checklist answers (notebook, not scorecard):**

1. *Row-contract fields.* Metric: reviewer-rated code quality on AI-assisted PRs. Type: Outcome (per `exercise-01`). Source: PR review sampling. Sampling plan: `<!-- author-to-confirm: current sampling procedure — likely n=20 per week, blind rubric, two reviewers -->`. Attribution limit: "quality movements coincide with pilot; plan does not include a controlled comparison."
2. *Data points.* One weekly sample. Not a trend yet.
3. *Credible cause-candidates.* (a) vendor backend change (direction is consistent); (b) normal sampling variation (sample size too small to rule out); crossed out: (c) pilot-cohort-specific skill drift (would show in non-AI-assisted PRs too and does not).
4. *What would make this a §1 posture change?* A second consecutive weekly sample below baseline **or** a widening gap against the non-AI-assisted PR mean on the same sampling window.

**From the checklist to the rewrite:**

- Move 1 names the current reading, prior reading, and baseline — all read off the row contract in checklist answer 1.
- Move 2 uses the two credible candidates from checklist answer 3 and names the sample-size-limit honesty from checklist answer 2.
- Move 3 translates checklist answer 4's "what would make this a §1 posture change" into the specific ask (pause authority before that threshold is reached).
- Move 4 names the two checks (recovery and counterfactual on non-AI-assisted PRs) that distinguish the credible cause candidates.

## 3. Validation steps

A reviewer grading a learner's rewrite should confirm:

1. **Four sentences, in order.** Miss → cause-with-uncertainty → ask → next-observable. Not three; not five.
2. **The miss names metric, current reading, prior reading, and baseline** (or action-range for a leading indicator).
3. **The cause sentence names either one confirmed cause with evidence or two credible candidates with explicit uncertainty.** Three-plus candidates without ranking is a failure mode.
4. **The ask is either specific (decision + addressee + by-when) or an explicit "no ask this week."** Implicit asks fail.
5. **The next observable is check-able in a specific future scorecard.** "We will continue to monitor" is not a next-observable.
6. **No adjectives of catastrophe or defense.** Grep for: unfortunately, serious, systemic, disappointing, confident, drive, momentum.
7. **No premature-fix claim.** Grep for: we have already, we have implemented, this should not recur, we expect recovery.
8. **If the miss is on a leading indicator, the rewrite does not escalate its weight.** Activation below range is not a program-level failure. The rewrite uses `exercise-01`'s metric-type labels.
9. **Attribution-honesty is intact.** The rewrite does not claim the tool caused the observed movement if the plan does not support that claim.
10. **The rewrite names the §1 posture change condition** (even if the miss stays in §7 this week).

## 4. Rubric / review checklist

Scored out of 50. Pass threshold: ≥ 40 and no R2/R5/R6 fail.

| # | Criterion | Max | Fail state |
|---|---|---|---|
| R1 | Four moves present, in order | 5 | Any missing or reordered. |
| R2 | Miss named with current reading, prior reading, baseline (or action-range) | 10 | Metric unnamed; or readings vague. |
| R3 | Cause sentence names 1 confirmed cause w/ evidence OR 2 candidates w/ uncertainty | 10 | 3+ unranked candidates; or single cause claimed without evidence. |
| R4 | Ask is specific (decision + addressee + by-when) or explicit "no ask" | 5 | Implicit ask. |
| R5 | Next observable is check-able in a named future scorecard | 10 | "We will continue to monitor." |
| R6 | No catastrophe or defense adjectives; no premature-fix claims | 5 | Any of the listed grep-fail words present. |
| R7 | Metric type correctly applied; leading-indicator misses not over-weighted | 3 | Leading-indicator miss narrated as outcome miss. |
| R8 | Attribution-honesty intact — no causal claim the plan cannot support | 2 | Claims cause the sampling plan cannot distinguish. |

## 5. Common mistakes

- **Starting with "unfortunately" or "sadly."** The scorecard is not a letter. Cut the tone word; the number does the work.
- **Burying a §3 outcome miss in §7.** §1 points to §7; §7 narrates. The exec who only reads §1 should see the miss.
- **Catastrophizing a single reading.** One week is a reading, not a trend. Name the current and prior; let the narration say "one data point, not a trend."
- **Three-plus cause candidates.** The exec cannot act on a four-branch cause tree. Narrow to one or two, or say "the data does not yet distinguish."
- **"We have already fixed it."** A fix without confirmed cause is aspirational. Say "an intervention is running this week," and let the next scorecard check.
- **Promising the recurrence won't happen.** Not knowable yet. Replace with the next observable.
- **Blaming the vendor without the sample-size caveat.** The vendor may be the cause; the sample may be too small to tell; a narration that blames without that caveat will be walked back under scrutiny.
- **No ask when there is one.** If the narration implies the sponsor should do something, say so with a named addressee and by-when. Implicit asks do not get acted on.
- **Treating a leading-indicator miss as a program-level failure.** Activation below range triggers a coaching intervention, not a §1 posture change. The framework in `exercise-01` draws this line explicitly.
- **Removing the attribution-honesty line from §9.** Especially tempting in a bad week. Keep it; the honesty line applies whether the metric moved up or down.

## 6. References

- **Official standards and frameworks:**
  - [NIST AI Risk Management Framework (AI RMF 1.0)](https://www.nist.gov/itl/ai-risk-management-framework) — the MEASURE function's emphasis on documented uncertainty and limitations of measurements motivates Move 2 (cause with its uncertainty) and the attribution-honesty discipline.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — context for the incident-narration variant of this drill (bad narration #3).
  - [MITRE ATLAS](https://atlas.mitre.org/) — adversary-technique context for distinguishing a vendor-side cause from a program-side cause when both are credible.
- **Local context (same repo):**
  - `modules/mod-106-outcome-measurement-and-executive-reporting/exercise-01-outcome-vs-usage-metric-framework/SOLUTION.md` — defines the metric types this drill relies on to avoid over-weighting leading-indicator misses.
  - `modules/mod-106-outcome-measurement-and-executive-reporting/exercise-02-the-weekly-executive-scorecard/SOLUTION.md` — the surface the narration is published on (§1 pointer, §7 narration, §9 attribution-honesty line).
  - `modules/mod-106-outcome-measurement-and-executive-reporting/exercise-03-quarterly-board-ready-review-outline/SOLUTION.md` — the longer-horizon surface where a sequence of narrated misses rolls up into §3 attribution-honesty.
  - `modules/mod-109-ai-incident-response-and-enablement-side-rollback/README.md` — the incident-flow the narration form adapts to for high-severity findings.
