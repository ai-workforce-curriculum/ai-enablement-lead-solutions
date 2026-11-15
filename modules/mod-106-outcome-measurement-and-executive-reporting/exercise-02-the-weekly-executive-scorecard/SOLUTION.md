# Exercise 02 — The Weekly Executive Scorecard — Reference Solution

> Module: `mod-106-outcome-measurement-and-executive-reporting`
> Exercise type: design / template + worked example
> Exercise brief: `lessons/mod-106-outcome-measurement-and-executive-reporting/exercises/exercise-02-the-weekly-executive-scorecard.md` (in the learning repo)

## 1. Solution overview

The weekly executive scorecard is the portfolio-level cousin of the per-rollout weekly report from `mod-102/exercise-03`. Where the rollout report covers one tool, the scorecard covers the full AI enablement portfolio — every tool in GA, every active pilot, every governance posture change, every incident. It is the artifact the CTO, General Counsel, and (where applicable) the Chief Risk Officer scan every Monday to know what moved.

The scorecard is deliberately **one page, fixed shape, same every week**. Shape stability is the entire point: execs do not re-read a different document each week, they scan a familiar one for deltas. The scorecard trades expressive range for readability.

The solution provides:

1. A reusable **template** (the shape).
2. A **worked example** for a mid-cycle week at a 3,000-person US bank that runs one GA'd tool (a coding assistant) and one active pilot (a customer-support agent).
3. A **writer's playbook** — the rules that keep the scorecard honest over 50+ weeks of use.

The scorecard consumes the row contract defined in `exercise-01`. Every metric that appears here was typed through that framework first. The scorecard does not define metrics; it reports them.

Posture checks the solution encodes:

- **One page. One shape. Every week.** A scorecard that is four pages in week one and two in week ten has already failed as a signal.
- **Outcome rows have targets; usage rows do not.** The scorecard uses visual labels to make the distinction unmistakable to a scanning reader.
- **The attribution-limit line appears every week.** Not just when outcomes move. The exec sees the honest claim boundary every single week.
- **Governance and incident signals share space with outcomes.** They are not an appendix. An exec who reads §1 and §3 should see posture and results in the same scan.
- **A missing week is a red flag, not an administrative detail.** The scorecard's cadence is part of its integrity. Skipped weeks require a one-line note on the next scorecard.

## 2. Implementation — worked answer

### 2.1 The template (`scorecard-template.md`)

```markdown
Weekly AI Enablement Scorecard — Week [N] of [YYYY]
From: AI Enablement Lead (this role)
To:   CTO (chair), General Counsel, CISO, head-of-ai-governance (L60),
      CRO (where applicable), head-of-engineering-enablement (L55)
Cc:   governance-council distribution
Date: YYYY-MM-DD
```

**§1. Headline (3 lines, max)**

- **Posture color:** [Green / Amber / Red] — one clause stating what is G/A/R and why.
- **Change from last week:** [better / worse / same] — one clause.
- **Decision needed from this group this week:** [decision + by-when], or *none this week*.

**§2. Portfolio status (one row per in-scope tool)**

| Tool | Stage | Users (active / enrolled) | Outcome trend | Non-regression trend | Governance / incidents | Posture |
|---|---|---|---|---|---|---|
| [Tool A] | GA | X / Y | ↑ / ↓ / → vs. last week | ↑ / ↓ / → vs. last week | [open findings / exceptions] | G / A / R |
| [Tool B] | Pilot W [n] | X / Y | — (pre-baseline) | — | [open findings / exceptions] | G / A / R |

**§3. Outcomes this week (one line per primary outcome, portfolio-wide)**

| Outcome | Tool | Workflow | This week | Last week | Target | Source |
|---|---|---|---|---|---|---|

- *Each row typed per `exercise-01` as a Type 1 outcome.*

**§4. Non-regression floors (one line per floor, portfolio-wide)**

| Floor | Tool | This week | Last week | Floor value | Source |
|---|---|---|---|---|---|

**§5. Leading indicators (labeled, no targets)**

| Indicator | Tool | This week | Last week | Action range |
|---|---|---|---|---|

- *Rows explicitly labeled "leading — not a success metric" per `exercise-01`.*

**§6. Governance posture**

- Open high-severity findings: [count], by tool. Triage path: [owner, SLA].
- Open exception requests past SLA: [count], by tool.
- Incidents this week: [count], severity breakdown, status.
- Policy changes ratified this week: [count], with one-line descriptors.

**§7. Risks and asks (max 3)**

- Each item: *risk*, *owner*, *ask of this group* (named addressee + by-when). No ask ⇒ do not list it.

**§8. Decisions acknowledged (if any)**

- Decisions made this week that this group should know were made (not approved).

**§9. Attribution-limit line (required every week)**

- One sentence stating what the scorecard supports as a claim and what it does not. Pattern: "Movements in §3 coincide with the pilot/GA window; this scorecard does not support causal claims without the controlled-comparison line (see `mod-106/exercise-06`)."

---

### 2.2 Worked example — Week 17 of 2026

Running archetype: 3,000-person US bank (same archetype as `mod-103`). One GA'd tool (coding assistant), one active pilot (customer-support agent, Pilot Week 4).

```markdown
Weekly AI Enablement Scorecard — Week 17 of 2026
From: AI Enablement Lead (this role)
To:   CTO (chair), General Counsel, CISO, head-of-ai-governance (L60),
      CRO, head-of-engineering-enablement (L55)
Cc:   governance-council distribution
Date: 2026-04-27
```

**§1. Headline**

- **Posture: Amber** — Pilot of the customer-support agent paused mid-week pending vendor response to an output-handling finding (see §6).
- **Change from last week:** worse (was Green). Coding-assistant program unchanged.
- **Decision needed:** confirm or redirect the pilot-pause duration; recommendation from this role is 14 calendar days. Decider: CTO + General Counsel. By: 2026-04-30.

**§2. Portfolio status**

| Tool | Stage | Users (active / enrolled) | Outcome trend | Non-regression trend | Governance / incidents | Posture |
|---|---|---|---|---|---|---|
| Coding assistant | GA | <!-- author-to-confirm: current active / enrolled counts from the admin console --> | → vs. last week | → | 0 open high findings; 2 exceptions within SLA | Green |
| Customer-support agent | Pilot W4 | <!-- author-to-confirm: W4 active / enrolled --> | — (pre-baseline, by plan) | — | 1 open high finding (`SEC-AI-00117`); pilot paused | Amber |

**§3. Outcomes this week**

| Outcome | Tool | Workflow | This week | Last week | Target | Source |
|---|---|---|---|---|---|---|
| Median change-review cycle time (hours) on AI-assisted PRs | Coding assistant | SDLC code review | <!-- author-to-confirm: current median from SDLC telemetry --> | <!-- author-to-confirm: week-16 median --> | <!-- author-to-confirm: charter-committed target --> | SDLC telemetry |
| Reviewer-rated code quality on AI-assisted PRs (0–5 rubric) | Coding assistant | SDLC code review | <!-- author-to-confirm: current sample mean --> | <!-- author-to-confirm: week-16 sample mean --> | ≥ baseline | PR review sampling (n=20/week) |

- *Customer-support-agent pilot is pre-baseline by plan; no outcome rows yet. See the pilot charter for the baseline-window schedule.*

**§4. Non-regression floors**

| Floor | Tool | This week | Last week | Floor value | Source |
|---|---|---|---|---|---|
| Post-merge defect rate on AI-assisted PRs | Coding assistant | <!-- author-to-confirm: current rate --> | <!-- author-to-confirm: week-16 rate --> | ≤ baseline rate | Incident/defect system |
| CI first-push pass rate on AI-assisted PRs | Coding assistant | <!-- author-to-confirm: current rate --> | <!-- author-to-confirm: week-16 rate --> | ≥ baseline rate | CI system |

**§5. Leading indicators (not success metrics)**

| Indicator | Tool | This week | Last week | Action range |
|---|---|---|---|---|
| Activation (active / enrolled) | Coding assistant | <!-- author-to-confirm --> | <!-- author-to-confirm --> | < 50% at ≥ W8 ⇒ coaching |
| Suggestion-acceptance rate | Coding assistant | <!-- author-to-confirm --> | <!-- author-to-confirm --> | > 90% ⇒ sample for over-acceptance |
| Policy acknowledgement coverage | Both | <!-- author-to-confirm --> | <!-- author-to-confirm --> | < 100% in-scope ⇒ outreach |

**§6. Governance posture**

- Open high-severity findings: 1 (`SEC-AI-00117`, customer-support-agent output-handling). Owner: CISO delegate + this role. Vendor ETA: `<!-- author-to-confirm: vendor-stated ETA from the open ticket -->`.
- Open exception requests past SLA: 0.
- Incidents this week: 0 declared. 1 near-miss self-reported under amnesty (coding assistant; no customer data involved; routed to the data-handling SOP accident path).
- Policy changes ratified this week: 0.

**§7. Risks and asks**

- *Risk:* paused pilot risks slipping past the quarterly-review window; *owner:* this role; *ask of this group:* decide pause duration by 2026-04-30 (CTO + General Counsel).
- *Risk:* coding-assistant exception approvals trending up over four weeks; *owner:* `head-of-ai-governance` (L60); *ask:* 30-minute review slot in Week 18 to check whether the policy's approved-uses list (`mod-103/exercise-01`) needs a redline cycle.

**§8. Decisions acknowledged**

- Customer-support agent pilot paused by this role under the standing pause authority in the charter; CTO notified same-day by direct message.

**§9. Attribution-limit line**

Movements in §3 coincide with the coding-assistant GA window and the customer-support-agent pilot window; this scorecard does not support causal claims. See the quarterly review (`exercise-03`) for the controlled-comparison discussion and the ROI defence (`exercise-06`) for the attribution-honesty frame.

---

### 2.3 Writer's playbook

Return to these rules every week. They are what makes the scorecard work as a steady signal rather than a weekly rewrite.

- **Posture-first.** Execs read §1 and stop. If they only read §1, do they know what matters? If not, rewrite §1.
- **Deltas over restatement.** Week 17 does not re-describe the program. The reader already knows what the program is.
- **No metric without a source column.** The source column is what stops dashboards from drifting into decoration.
- **Outcomes have targets. Usage rows do not.** This is the single most-corrected failure in review. Enforce via visual separation (§3 vs. §5) and the "not a success metric" row label.
- **An ask without an addressee is not an ask.** Every bullet in §7 names the human whose action is wanted and the by-when.
- **A scorecard that is always Green is broken.** If the scorecard is Green for N weeks and then flips directly to Red, the reporting process failed, not just the program.
- **No new metrics mid-flight without a note.** Add rows; do not delete them. A retired metric leaves a dash and a footnote.
- **§6 governance and §3 outcomes coexist on the same page.** The temptation to hide §6 in an appendix is the governance-silence failure.
- **§9 attribution-limit line is non-negotiable.** Copy-paste it if unchanged; the exec sees it anyway. The scorecard loses the line *only* when a controlled comparison starts providing causal evidence (and then the line is rewritten to describe the new claim boundary — not removed).

## 3. Validation steps

A reviewer should be able to answer **yes** to all of:

1. Is the artifact one page at a readable rendering?
2. Does §1 state posture color, delta, and the next decision needed?
3. Does §2 cover every in-scope tool (every active pilot, every tool in GA)?
4. Are §3 outcome rows typed per `exercise-01` (Type 1, with target, source, workflow attachment)?
5. Are §4 non-regression floors present with a direction (≤ or ≥ baseline)?
6. Are §5 leading indicators explicitly labeled "not a success metric" and given action ranges, not targets?
7. Does §6 surface open findings, exceptions past SLA, incidents, and policy changes in one scan?
8. Does every item in §7 name owner + addressee + by-when?
9. Does §8 record decisions that were **made**, distinct from approvals being requested?
10. Is §9 the attribution-limit line present and specific to what the scorecard does and does not support?
11. Are unknown numbers marked `<!-- author-to-confirm: ... -->` rather than invented?
12. Is the shape identical in the template and the worked example (sections and ordering)?

Markdown-lint the file (`markdownlint scorecard-week-NN.md`) before sending.

## 4. Rubric / review checklist

Scored out of 100. Pass threshold: ≥ 80 and no R2/R4/R6/R10 fail (those four are the launch-gate equivalents).

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | One page at a readable rendering; shape identical to template | 5 | Spills past one page, or sections reordered between template and example. |
| R2 | §1 states posture color, delta, and next decision | 10 | Missing any one of the three. |
| R3 | §2 has a row for every in-scope tool | 5 | Portfolio under-coverage. |
| R4 | §3 outcome rows typed per `exercise-01` with target, source, workflow | 15 | Row missing target or source; or outcome not attached to a workflow. |
| R5 | §4 non-regression floors present, with direction | 10 | No floors, or targets written in place of floors. |
| R6 | §5 leading indicators labeled "not a success metric", action ranges only | 15 | Target on a leading indicator. |
| R7 | §6 surfaces findings, exceptions, incidents, policy changes in one scan | 10 | Governance hidden in appendix; or §6 missing a class. |
| R8 | §7 asks each name owner + addressee + by-when | 5 | Any item missing owner or addressee. |
| R9 | §8 records decisions made (distinct from decisions requested) | 5 | §8 merged with §7. |
| R10 | §9 attribution-limit line present and specific | 10 | Missing or generic placeholder. |
| R11 | Unknowns marked `<!-- author-to-confirm: ... -->`; no invented numbers | 10 | Invented percentages or hour counts. |
| R12 | Named distribution list (not "the exec team") | 5 | Vague recipient. |

## 5. Common mistakes

- **Scorecard-as-dashboard.** A screenshot of the admin console with no interpretation. The scorecard tells the exec what it means; dashboards live behind the source column.
- **Scorecard-as-narrative.** Prose paragraphs about how the team is "really pushing." Rewrite as status + decisions + rows.
- **Vanity usage framing in §1.** "92% adoption" as the headline. Adoption is a leading indicator; the headline belongs to the outcome or the posture.
- **Color inflation.** Every week Green because no one wants to deliver Amber. Fix by stating the specific condition that would move to Green or Red; without that, the color is noise.
- **Drift.** Sections renamed or reordered week over week. Freeze the shape. If a redesign is needed, publish a versioned v2 scorecard and name the version.
- **Governance silence.** §6 gets dropped the week nothing changed. Keep the section; write "no change" on quiet weeks. A section that disappears reads as a section that is being selectively surfaced.
- **Decision clutter in §8.** Listing every micro-decision. §8 is for decisions the recipient group should **know were made** because they affect scope, policy, or risk.
- **Attribution-limit line removed when outcomes look good.** The line is removed only when the plan starts supporting causal claims — not when the result is flattering. Removing it mid-cycle is the single most dangerous move on this surface.
- **Portfolio under-coverage.** Scorecard lists only the pilot, not the GA'd tool, because the pilot is "the news." §2 must cover the whole portfolio or an exec cannot see where risk is concentrated.
- **Invented numbers in the worked example.** Specific minute counts, user counts, and percentages must be real measurements or marked `<!-- author-to-confirm: ... -->`. Invented numbers in the template teach the wrong habit.

## 6. References

- **Official standards and frameworks:**
  - [NIST AI Risk Management Framework (AI RMF 1.0)](https://www.nist.gov/itl/ai-risk-management-framework) — the MEASURE function (performance measures, trustworthy characteristics, risk-related measures) and the MANAGE function (risk response and recovery) motivate §3–§6 of the scorecard. The GOVERN function motivates the §6 structure and the escalation path for incidents.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — categories map to specific governance-posture rows in §6 (prompt-injection, output handling, model exfiltration).
  - [MITRE ATLAS](https://atlas.mitre.org/) — adversary-technique context for the incident and near-miss rows in §6.
- **Local context (same repo):**
  - `modules/mod-106-outcome-measurement-and-executive-reporting/exercise-01-outcome-vs-usage-metric-framework/SOLUTION.md` — defines the metric-row contract every row here is typed against.
  - `modules/mod-106-outcome-measurement-and-executive-reporting/exercise-03-quarterly-board-ready-review-outline/SOLUTION.md` — consumes trends from this scorecard across a quarter.
  - `modules/mod-106-outcome-measurement-and-executive-reporting/exercise-04-metric-miss-narrative-drill/SOLUTION.md` — the drill applied when a §3 row misses target.
  - `modules/mod-106-outcome-measurement-and-executive-reporting/exercise-06-roi-numerator-and-denominator-defence/SOLUTION.md` — carries the attribution-honesty frame referenced in §9.
  - `modules/mod-102-selecting-and-rolling-out-ai-tools/exercise-03-the-weekly-executive-rollout-report/SOLUTION.md` — the per-rollout cousin of this portfolio scorecard.
  - `modules/mod-102-selecting-and-rolling-out-ai-tools/exercise-06-outcome-measurement-vs-usage-telemetry-drill/SOLUTION.md` — the drill version of the typing logic the row labels rely on.
  - `modules/mod-109-ai-incident-response-and-enablement-side-rollback/README.md` — the incident flow that feeds §6.
