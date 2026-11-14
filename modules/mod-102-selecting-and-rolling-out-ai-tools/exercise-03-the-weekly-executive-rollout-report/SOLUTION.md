# Exercise 03 — The Weekly Executive Rollout Report — Solution

> Module: `mod-102-selecting-and-rolling-out-ai-tools`
> Exercise type: design / template + worked example
> Exercise brief: `lessons/mod-102-selecting-and-rolling-out-ai-tools/exercises/exercise-03-the-weekly-executive-rollout-report.md` (in the learning repo)

## 1. Solution overview

The weekly executive rollout report is the smallest unit of accountability the AI Enablement Lead owes an exec sponsor during a tool rollout. It is deliberately **thin**: five short sections, one page, same shape every week. Shape stability is the point — execs do not re-read a different document each week, they scan a familiar one for deltas.

The solution provides:

1. A reusable **template** (the shape).
2. A **worked example** for week 3 of the AI coding assistant rollout used across this module.
3. A **writer's playbook** covering two failure modes the template is designed to resist:
   - Report-as-narrative (feelings instead of status).
   - Report-as-telemetry-dump (dashboards instead of decisions).

The report pairs with exercise-06 (outcome metrics vs. usage telemetry) because the metrics section can only be filled in correctly if the learner has already thought through that distinction.

## Implementation

Apply this solution by freezing the template shape (§2 template), filling it each week from the metrics defined in exercise-06 and the charter in exercise-04, and sending it to the named distribution list on the same calendar day each week. Validate the finished report against section 3 and score against the rubric in section 4; section 5 lists the common failure modes the fixed-shape report is designed to resist.

## 2. Worked answer

### The template

> **Weekly AI Rollout Report — `[Tool Name]` — Week [N]**
> *From:* [AI Enablement Lead]  *To:* [Exec Sponsor + named governance council members]  *Date:* [YYYY-MM-DD]
>
> **1. Status (one sentence per line, max 3 lines)**
> - [Green / Amber / Red] — [state in one clause what is Green/Amber/Red and why].
> - Change from last week: [better / worse / same, in one clause].
> - Next decision needed from this group: [decision and by-when], or *none this week*.
>
> **2. What happened this week (max 5 bullets)**
> - Milestones hit or missed, each with one evidence pointer.
>
> **3. Metrics (fixed table, same every week)**
>
> | Metric | This week | Last week | Target | Source |
> |---|---|---|---|---|
> | Outcome metric #1 (from exercise-06) | | | | |
> | Outcome metric #2 (if any) | | | | |
> | Leading indicator #1 (usage, labeled as leading) | | | | |
> | Leading indicator #2 (usage, labeled as leading) | | | | |
> | Governance signal (e.g., open exception count) | | | | |
>
> **4. Risks / asks (max 3 items)**
> - Each item: *risk*, *owner*, *ask of this group*. No ask ⇒ do not list it.
>
> **5. Decisions to acknowledge (if any)**
> - Decisions made this week that this group should know were made (not approved).

### The worked example — Week 3

> **Weekly AI Rollout Report — [AI Coding Assistant] — Week 3**
> *From:* AI Enablement Lead  *To:* CTO (sponsor), CISO, General Counsel, VP Engineering, VP People
> *Date:* 2026-11-13
>
> **1. Status**
> - **Amber** — pilot is on track on adoption but a prompt-handling finding from Security is pending a vendor fix.
> - **Change from last week:** worse (was Green); scope has not changed.
> - **Next decision needed:** go/no-go to extend the pilot to a second team by 2026-11-20. Deciders: CTO + VP Engineering.
>
> **2. What happened this week**
> - Pilot team completed onboarding (18/18 engineers active). *Evidence:* enrollment dashboard.
> - Security identified a prompt-content handling finding during the Week-2 threat model walk-through. *Evidence:* finding `SEC-AI-00042`; see risks below.
> - Three exception requests reviewed; two approved, one declined. *Evidence:* exceptions log.
> - First outcome-metric reading taken (change-review cycle time); below target at Week 3 which is expected per exercise-06 timing. *Evidence:* metric sheet, week-3 row.
> - Policy `v1.0` published and acknowledged by 18/18 pilot engineers. *Evidence:* policy acknowledgment log.
>
> **3. Metrics**
>
> | Metric | Week 3 | Week 2 | Target (end of pilot) | Source |
> |---|---|---|---|---|
> | Median change-review cycle time (outcome) | [measured value] | [measured value] | [target from charter] | SDLC telemetry |
> | Reviewer-rated code quality on AI-assisted PRs (outcome) | [measured value] | [measured value] | ≥ baseline | PR review sampling |
> | Active users / enrolled (usage, leading) | 18 / 18 | 14 / 18 | n/a — coverage ≠ outcome | tool admin console |
> | Suggestions-accepted rate (usage, leading) | [value] | [value] | n/a — context only | tool admin console |
> | Open exceptions (governance) | 1 | 0 | ≤ 3 steady-state | exceptions log |
> | Open findings from Security (governance) | 1 | 0 | 0 to exit pilot | finding tracker |
>
> *Note:* usage rows are labeled "leading" and have no target. They are watched, not managed. See exercise-06.
>
> **4. Risks / asks**
> - *Risk:* `SEC-AI-00042` finding is not yet fixed; blocks pilot exit. *Owner:* AI Enablement Lead + CISO delegate. *Ask of this group:* none this week; status update next week.
> - *Risk:* second-team extension could be optimistic given the open finding. *Owner:* AI Enablement Lead. *Ask:* decide extend vs. hold at the 2026-11-20 governance checkpoint.
>
> **5. Decisions acknowledged**
> - Two exception requests approved under the §7 change-control clause of the use policy. No policy change required; decisions logged.

### Writer's playbook

A learner can return to these rules every week; they are what makes the report work as a steady signal rather than a weekly rewrite.

- **Status first, context later.** Execs read §1 and stop. If they only read §1, do they know what matters? If not, rewrite §1.
- **Deltas, not restatements.** Week 3 should not re-describe the project. The reader already knows what the project is.
- **No metric without a source column.** The source column is what stops dashboards from drifting into decoration.
- **Separate outcomes from usage.** Outcomes have targets. Usage rows are labeled "leading" and have none. This is the single most-corrected failure in review and is the link to exercise-06.
- **An "ask" without an addressee is not an ask.** Every bullet in §4 names the human whose action is wanted and the by-when.
- **A report that is always Green is broken.** If the report is Green for N weeks and then flips directly to Red, the reporting process failed, not just the project.
- **No new metrics mid-pilot without a note.** Changing the metrics mid-flight hides regressions. Add rows; do not delete them. If a metric is retired, leave the row with a dash and a footnote.

## 3. Validation steps

Reviewing a learner's submission, a reviewer should be able to answer **yes** to all of:

1. Is there both a reusable template **and** a filled-in worked example?
2. Is the report one page at a readable size?
3. Does §1 state the color, the change from last week, and the next decision needed?
4. Does §3 distinguish outcome metrics from usage telemetry, with usage rows labeled "leading" and without targets?
5. Does every metric row have a named source?
6. Does §4 name an owner and an ask for every risk, or state *no ask*?
7. Does §5 record decisions that were **made**, distinct from approvals being requested?
8. Is the shape identical in the template and the worked example (sections and ordering)?
9. Does the report **name the tool**, the **sponsor**, and the **distribution list**?

## 4. Rubric or review checklist

Scored out of 15. 11+ passes.

| # | Criterion | Max |
|---|---|---|
| 1 | One-page, consistent shape (template == worked example shape) | 2 |
| 2 | §1 hits color, delta, next decision | 2 |
| 3 | §2 bullets each cite evidence pointer | 1 |
| 4 | §3 separates outcomes from usage with explicit labeling | 3 |
| 5 | Every metric row has a source | 1 |
| 6 | §4 has owner + ask or "no ask" explicitly | 2 |
| 7 | §5 distinguishes decisions-made from decisions-requested | 1 |
| 8 | Named distribution list (not "the exec team") | 1 |
| 9 | Explicit governance signal row(s) in metrics | 1 |
| 10 | Clear link to exercise-06 for the outcome metric definition | 1 |

## 5. Common mistakes

- **Report-as-narrative.** Prose paragraphs about how the team is "really pushing hard." Rewrite as status + decisions.
- **Report-as-dashboard.** A screenshot of the tool admin console with no interpretation. Dashboards go in an appendix link; the report tells the exec what it means.
- **Vanity usage framing.** "95% adoption" as a headline in §1. Adoption is a leading indicator; the headline belongs to the outcome.
- **Color inflation.** Every week is Green because no one wants to be the bearer of Amber. Fix by stating the specific condition that would move to Green or Red; without that, the color is noise.
- **Drift.** Sections renamed or reordered week over week, so execs cannot scan. Freeze the shape.
- **Scope creep in §2.** Listing everything the enablement team did that week, including the newsletter. Keep §2 to milestones directly tied to the rollout.
- **Decision clutter in §5.** Listing every micro-decision. §5 is for decisions the recipient group should **know were made** because they affect scope, policy, or risk.

## 6. References

- NIST AI Risk Management Framework (AI RMF 1.0): <https://www.nist.gov/itl/ai-risk-management-framework> — the Measure and Manage functions motivate the metrics and governance-signal rows.
- OWASP Machine Learning Security Top 10: <https://owasp.org/www-project-machine-learning-security-top-10/> — risk rows for LLM-integrated rollouts should pattern-match to these categories where applicable.
- MITRE ATLAS: <https://atlas.mitre.org/> — for framing active-adversary risks surfaced during a rollout.
- Local context: `exercise-06-outcome-measurement-vs-usage-telemetry-drill` defines the outcome metrics referenced in §3. Companion module `mod-106-outcome-measurement-and-executive-reporting` deepens the executive-reporting craft. <!-- to-verify: confirm mod-106 reference in the learner's curriculum version. -->
