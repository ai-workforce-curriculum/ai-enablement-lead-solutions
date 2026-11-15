# Exercise 06 — ROI Numerator and Denominator Defence — Reference Solution

> Module: `mod-106-outcome-measurement-and-executive-reporting`
> Exercise type: design / defence memo + anticipated-question drill
> Exercise brief: `lessons/mod-106-outcome-measurement-and-executive-reporting/exercises/exercise-06-roi-numerator-and-denominator-defence.md` (in the learning repo)

## 1. Solution overview

Every AI program will, at some point, be asked for its ROI number. The enablement seat is the person in the room who most needs that number to be defensible — because they are the one who will be asked to defend it when the CFO's team examines it, when the audit committee asks about it, or when a regulator asks how value was characterized.

This exercise produces the **ROI defence memo**: a short document that names, in advance, what the program counts in the numerator (value), what it counts in the denominator (cost), what it excludes from each, and the three to five questions a skeptical reader is most likely to ask. The memo pairs with the ROI numeric roll-up owned by FinOps in `mod-107`. The numeric roll-up is the artifact; the defence memo is why the numeric roll-up is credible.

The memo is explicitly **defensive in posture, not promotional**. Its job is to survive adversarial reading, not to sell the program. A memo that reads as an advocacy brief for the program has already failed on this exercise's terms.

The solution provides:

1. The **numerator contract** — what goes in, what stays out, with the reasoning for each.
2. The **denominator contract** — the same for cost.
3. The **attribution-honesty frame** — carried forward from `exercise-01`, extended into the ROI claim shape.
4. The **sensitivity analysis** — the two or three assumptions in the memo that would most change the number if revised, with the number's direction under each revision.
5. The **anticipated-question drill** — the five questions a skeptical CFO / audit-partner / regulator reader will ask, with the prepared answer and the one or two questions the memo *cannot* fully answer and why.
6. The **update cadence** — when the memo is refreshed and what triggers a mid-cycle rewrite.

Posture checks the solution encodes:

- **Numbers that cannot be defended are not in the memo.** If the program cannot show the work for a dollar number, the memo does not publish it.
- **The denominator is not just vendor spend.** Implementation cost, enablement-team salary, training time of pilot users, governance overhead — all belong in the denominator. A denominator that reads as only "subscription cost" is the memo's largest failure mode.
- **The numerator does not count the research literature's effect sizes.** The literature informed charter decisions (see `exercise-05`); it does not supply the program's own value claim.
- **The memo names what it cannot answer.** A memo with no unanswered questions is a memo that has not been pressure-tested.
- **The memo is not the ROI number.** It is the defence of whatever number FinOps publishes. The two artifacts are paired but not merged.

## 2. Implementation — worked answer (`roi-defence-memo.md`)

The worked memo below is written for the running archetype's coding-assistant program (3,000-person US bank, coding assistant at GA since Q3 2025). It is the memo attached to any quarterly review (`exercise-03`, §7) where an ROI question is on the agenda, and it is the document FinOps references when asked how the dollar numbers in the FinOps roll-up should be interpreted.

---

### ROI Defence Memo — AI Coding-Assistant Program — v1.0

**Author:** AI Enablement Lead (this role).
**Co-signer on the numerator:** FinOps partner.
**Co-signer on the denominator:** FinOps partner + VP Engineering (for engineer-hour accounting) + `head-of-ai-governance` (L60, for governance-overhead inclusion).
**Reviewers:** CFO delegate, CTO, head-of-ai-governance (L60).
**Memo date:** `<!-- author-to-confirm: confirm memo publication date -->`.
**Program in scope:** coding-assistant program at GA. Other tools (customer-support-agent pilot, drafting-tool evaluation) are out of scope; each carries its own memo when it reaches the ROI question.
**Paired artifact:** the FinOps numeric roll-up for the coding-assistant program at the same date (owned by `mod-107`).

---

#### 2.1 The claim shape

This memo defends the following **three statements** about the coding-assistant program at memo date. It does not defend a single ROI ratio because the plan does not support one.

**Statement A — spend is real and measured.** The program's cost side is measurable, bounded, and fully attributable to the program. See §2.3 (denominator) for the components. The denominator is a defensible number.

**Statement B — a program outcome has moved during the pilot and GA window.** Median change-review cycle time on AI-assisted PRs has moved from `<!-- author-to-confirm: baseline value -->` at pre-GA to `<!-- author-to-confirm: current value -->` at memo date, with the non-regression floor on post-merge defect rate intact. See §2.2 (numerator) for the claimed-value components.

**Statement C — a specific causal attribution from the tool to the observed movement is not currently defended.** The sampling plan does not include a controlled comparison. See `exercise-01` and `exercise-04`. The memo's §2.4 (attribution-honesty frame) is explicit on the claim boundary.

---

#### 2.2 The numerator — what counts as value

The numerator is the dollar translation of movement in defensible outcome and non-regression metrics, bounded by the attribution-honesty frame. The memo publishes the numerator as **a range, not a single number**, and names which assumption in the range would move it.

**Components in the numerator:**

| Component | What it is | How it is quantified | Defensibility |
|---|---|---|---|
| **N1 — Change-review cycle-time delta** | Median change-review cycle time on AI-assisted PRs vs. the measured pre-tool baseline, translated into engineer-hours per week. | Baseline cycle time × eligible AI-assisted PR volume − current cycle time × eligible AI-assisted PR volume; converted to engineer-hours. | Defensible as a *coincident* movement. Not defensible as a *caused* movement. The range's lower bound assumes 0% causal attribution; the upper bound assumes 100%. Both are explicit. |
| **N2 — Non-regression on post-merge defects** | The dollar-value of the absence of regression in post-merge defect rate. | Not quantified in the numerator. | **Explicitly not counted.** The non-regression floor prevents a negative contribution to the numerator; it is a floor, not a gain. Treating "we didn't break things" as dollar value overcounts. |
| **N3 — Avoided future hires** | Cost of engineers who would otherwise have been hired to meet the workload the AI-assisted workflow now absorbs. | Not quantified in the current memo. | **Explicitly excluded.** This is a *projection*, not a measurement. The memo flags the exclusion so a reader does not assume the number has been silently loaded. Projecting avoided hires turns the memo into advocacy; the program does not do it. |
| **N4 — Developer satisfaction** | Reported satisfaction with the tool, translated to a retention or productivity dollar value. | Not quantified. | **Explicitly excluded.** Developer satisfaction is a leading indicator (per `exercise-01` and `exercise-05`); translating it to dollars requires a causal chain the memo does not support. |
| **N5 — Research-literature effect sizes** | Numbers like "X% speedup" from published studies. | Not applied to the organization's cost base. | **Explicitly excluded.** The literature informed the charter (see `exercise-05`); it does not supply the program's value claim. |

**The numerator published in the memo:**

- A **range** derived from N1 alone, with the lower bound assuming 0% of the observed cycle-time movement is attributable to the tool and the upper bound assuming 100%.
- A footnote naming that N2 is not dollarized, and that N3, N4, N5 are excluded with the reasoning above.
- An explicit statement that any future additions to the numerator (adding N3 when a controlled comparison is in place, for example) will bump the memo version and will be called out in the quarterly review (`exercise-03`, §7).

---

#### 2.3 The denominator — what counts as cost

The denominator is intentionally broader than vendor spend. The memo's second-largest failure mode is a denominator that is "just the subscription." The memo lists every cost category the program incurs that would not exist if the program did not exist.

| Component | What it is | How it is quantified | Notes |
|---|---|---|---|
| **D1 — Vendor subscription** | Per-seat cost × active seats across the memo period. | From the FinOps roll-up. | The straightforward one. |
| **D2 — Vendor overage / excess usage charges** | Any costs above the committed plan. | From the FinOps roll-up. | Often small but non-zero; omitting it is the first sign of a lazy denominator. |
| **D3 — Implementation and integration cost** | Platform-engineering time to integrate the tool with the organization's identity, logging, and policy-enforcement surfaces. | Engineer-hours × fully-loaded rate, measured from the implementation project's time-tracking. | The audit committee will ask about this. Omitting it reads as hiding the setup tax. |
| **D4 — Enablement-team cost** | Fully-loaded cost of the AI enablement seat and dedicated supporting roles (champion network coordinator, trainer) during the memo period. | FTE-time × fully-loaded rate. | Co-signed with FinOps and VP Engineering to agree on allocation. |
| **D5 — Training time of pilot and GA users** | Hours spent by in-scope engineers completing training per `mod-104`. | Participant-hours × fully-loaded rate. | Often the single largest line item; omitting it drastically understates cost. |
| **D6 — Governance and policy overhead** | Time of `head-of-ai-governance` (L60), counsel, DPO, CISO delegate spent on this program's artifacts (policy, SOP, intake, incident). | Recorded in the redline log (`mod-103`), converted to hours and loaded. | Co-signed with `head-of-ai-governance`. |
| **D7 — Incident and near-miss response time** | Time spent by the enablement seat, champions, and (where applicable) the SOC on this program's incidents and near-misses. | From the after-action logs per `mod-109`. | Zero some quarters; non-zero and visible when it matters. |
| **D8 — Audit and regulatory-reporting support** | Time spent preparing responses to internal audit and (where applicable) regulators on questions about this program. | Logged against the program. | Often small per-quarter; cumulative over a year is not. |

**The denominator published in the memo:**

- A **single number** (not a range; cost accounting resolves to a single number by convention), with component-level breakdown in a FinOps appendix.
- An explicit statement that cost accounting conventions used are those of the organization (`<!-- author-to-confirm: confirm whether the organization uses direct cost or fully-loaded cost in this type of program-level roll-up -->`); the memo adopts whichever convention FinOps uses org-wide, and names the choice.

---

#### 2.4 The attribution-honesty frame

The memo carries forward the attribution-honesty discipline from `exercise-01` (row contract) and `exercise-04` (metric-miss narration), applied to the ROI claim.

**What the program can defend at memo date:**

- The denominator is accurate within the cost-accounting conventions named in §2.3.
- The outcome movement in N1 is real and measured against a real pre-tool baseline.
- The non-regression floor is intact.
- The program's design does not depend on the ROI number being a specific value; the charter's success criteria were defined in outcome terms, not in ROI terms.

**What the program cannot defend at memo date:**

- A specific causal attribution of the outcome movement to the tool. The sampling plan does not include a controlled comparison; the attribution-limit line in every weekly scorecard (`exercise-02`, §9) makes this bound continuously visible.
- A projected ROI for future periods. The memo is a point-in-time defence; projections require a controlled comparison plan (not currently in place) or a different, projection-labeled memo.
- A per-engineer productivity claim. Measurement is at workflow and cohort level (see `exercise-05`, declined moves).

**What would change what can be defended:**

- A **controlled comparison** between teams using the tool and a matched cohort not using it, run over a period long enough to detect a workflow-level effect, would allow a causal attribution claim with a confidence bound. The memo does not currently propose this; it names the condition under which it would.
- A **time-series design** with the tool switched off during a planned rollback drill (per `mod-109`) would allow a weaker causal claim bounded by the drill window. This is on the roadmap for `<!-- author-to-confirm: confirm whether a rollback drill is scheduled in the next two quarters per mod-109 -->`.

---

#### 2.5 Sensitivity analysis

Two or three assumptions in the memo, if revised, would most change the numerator. The memo names them explicitly so a reader can see where the number is most elastic.

**Assumption S1 — engineer fully-loaded hourly rate.**
The N1 translation from cycle-time delta to dollar value multiplies engineer-hours by a fully-loaded rate. The memo uses the rate FinOps publishes org-wide `<!-- author-to-confirm: confirm current fully-loaded rate used by FinOps for this engineering population -->`. If the rate were revised by ±20%, the numerator moves by approximately the same proportion. The memo does not advocate for a specific rate; it uses the FinOps-published rate and names the dependency.

**Assumption S2 — eligible PR volume used in N1.**
The volume of AI-assisted PRs eligible for the cycle-time improvement is bounded by the active-seat count and by whether the PRs actually used the assistant. The memo uses the operational signal of PRs tagged as AI-assisted (via `<!-- author-to-confirm: confirm the signal used — likely a commit trailer or a tool-admin-console identifier -->`). If the eligible volume is over- or under-counted by 25%, the numerator moves roughly proportionally.

**Assumption S3 — causal attribution fraction.**
The numerator range from §2.2 brackets 0%–100% attribution. Narrowing the range requires the controlled comparison in §2.4. The memo's choice to publish the full range is deliberate; narrowing it without the evidence would overclaim.

---

#### 2.6 Anticipated-question drill

The five questions a skeptical reader is most likely to ask, with the prepared answer. At least one answer is explicitly "we cannot answer this."

**Q1 — CFO delegate: "What is the ROI number?"**
*Prepared answer:* The program's position is that a single ROI ratio is not currently defensible. The memo publishes a numerator *range* (§2.2) and a denominator *number* (§2.3), which an informed reader can divide to produce a range of ROI values. The range's lower bound (zero causal attribution) is approximately `<!-- author-to-confirm: lower-bound ratio -->`; the upper bound (full causal attribution) is approximately `<!-- author-to-confirm: upper-bound ratio -->`. The range exists because the program has not run a controlled comparison; narrowing the range requires the plan described in §2.4.

**Q2 — Audit partner: "What is in the denominator beyond vendor spend?"**
*Prepared answer:* Seven additional components (D2–D8). The memo publishes the full breakdown; the FinOps roll-up carries the numbers. The specific items that most often surprise audit partners are D5 (training time of pilot users) and D6 (governance and policy overhead). Both are real; the memo is explicit about counting them.

**Q3 — Audit partner: "What is in the denominator that should not be?"**
*Prepared answer:* The memo's conservatism is on the numerator, not the denominator. Everything in §2.3 would exist as a cost even if the program were paused tomorrow; every component is attributable to this program's existence. The memo does not exclude any category to inflate the ratio; if a reviewer believes a category is over-counted, the specific challenge is welcome and the memo will revise.

**Q4 — Board member: "What about the productivity numbers from the papers everyone is citing?"**
*Prepared answer:* The literature-to-metric map (`exercise-05`) is explicit that published effect sizes are evidence for charter decisions, not inputs to the organization's value claim. The memo does not count N5 (literature effect sizes) in the numerator. A reader who wants to see what the research says should read the map; a reader who wants to see what this program claims about itself should read this memo.

**Q5 — Regulator (where applicable): "How is the program's value characterization made durable against being revised in a favorable direction over time?"**
*Prepared answer that is partially an acknowledgement:* The memo is versioned (`exercise-05` convention). A revision to the numerator or denominator bumps the version and carries a change-note; a revision that widens what can be defended (adding N3 after a controlled comparison, for example) is called out in the quarterly review (`exercise-03`, §7). **What the memo cannot promise:** the organization does not currently run an external audit of the memo's assumptions; the review is internal (FinOps + enablement + governance + audit committee). A regulator-facing version would need an external review step that is not currently in place; the memo flags this as a specific gap the program would need to close before publishing a regulator-facing ROI claim.

---

#### 2.7 Update cadence

- **Quarterly review.** The memo is reviewed at each quarterly review (`exercise-03`) and re-dated. Any changes to the numerator or denominator contracts are noted in a changelog at the memo's foot.
- **On major cost changes.** A vendor contract renewal, a material change in training hours per `mod-104`, or a change in the FinOps fully-loaded rate triggers a mid-cycle refresh of the denominator and S1/S2.
- **On a controlled-comparison plan.** If the program takes on a controlled-comparison measurement per §2.4, that is a major-version bump (v1.x → v2.0) and the attribution-honesty section is rewritten.

### End of worked memo

## 3. Validation steps

A reviewer should be able to confirm, from the learner's artifact:

1. **The memo publishes a range, not a single ratio.** Unless a controlled comparison exists, a single ROI number is unsupportable.
2. **The denominator has ≥ 6 components.** Subscription-only denominators fail.
3. **At least three numerator components are excluded with reasoning.** The memo's spine is what it refuses to count.
4. **The attribution-honesty section is explicit about what the program can and cannot defend.** No implicit causation.
5. **The sensitivity analysis names 2–3 assumptions and states direction of impact.** Sensitivity-free memos read as advocacy.
6. **The anticipated-question drill has at least five questions with prepared answers.** At least one answer is "we cannot answer this."
7. **The memo is versioned and dated.** Undated memos fail.
8. **The memo is explicit about its paired artifact (the FinOps roll-up) and does not duplicate it.** The defence memo defends; the roll-up computes.
9. **Co-signers are named and span FinOps, governance, and engineering.** A single-author memo fails the co-signer test.
10. **Unknowns are marked `<!-- author-to-confirm: ... -->`, not invented.** Invented ROI numbers survive worse than acknowledged gaps.

## 4. Rubric / review checklist

Scored out of 100. Pass threshold: ≥ 80 and no R1/R2/R4/R10 fail.

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | Numerator published as a range (unless controlled comparison exists); no single ROI ratio | 15 | Single ratio without controlled comparison. |
| R2 | Denominator has ≥ 6 named components (vendor, implementation, enablement team, training time, governance, incidents, audit, etc.) | 15 | Subscription-only or fewer than 6 components. |
| R3 | ≥ 3 numerator components explicitly excluded with reasoning | 10 | No excluded components; or exclusions without reasoning. |
| R4 | Attribution-honesty section explicit about what the program can and cannot defend | 15 | Implicit causation; or honesty section missing. |
| R5 | Sensitivity analysis names 2–3 assumptions with direction of impact | 10 | Missing or generic. |
| R6 | Anticipated-question drill: ≥ 5 questions with prepared answers, at least one honest "cannot answer" | 10 | Fewer than 5; or no "cannot answer" acknowledgement. |
| R7 | Versioned and dated, with update cadence named | 5 | No date / version / cadence. |
| R8 | Paired with FinOps roll-up; defence vs. computation clearly separated | 5 | Memo duplicates the roll-up or is merged with it. |
| R9 | Multi-party co-signers (FinOps + governance + engineering) named | 5 | Single-author memo. |
| R10 | Unknowns marked `<!-- author-to-confirm: ... -->`; no invented dollar numbers | 10 | Invented ratios, rates, or dollar amounts. |

## 5. Common mistakes

- **Publishing a single ROI ratio.** The single-ratio memo is the most common and most harmful failure. Unless the program has a controlled comparison, the single ratio is a conjecture, and once published it becomes the number everyone remembers.
- **Subscription-only denominator.** The second most common. It reads as either naive or dishonest, depending on the reader; neither helps the program.
- **Excluding governance and training overhead from the denominator.** Both are real costs, both are attributable to the program, both are often the first lines an auditor asks about. Exclude them and the memo loses credibility on the first question.
- **Counting literature effect sizes in the numerator.** The literature informs the charter; it does not supply the value claim. See `exercise-05`.
- **Counting projected avoided hires.** Projections belong in a different memo, clearly labeled as projection. Loading them into the current-period numerator is advocacy.
- **Counting developer satisfaction in the numerator.** Leading indicators (per `exercise-01`) do not carry a dollar value in this memo. Translating them requires a causal chain the memo does not support.
- **"We cannot answer this" absent from the Q&A.** A memo with every question answered is a memo that has not been pressure-tested. At least one honest gap is required.
- **Missing sensitivity analysis.** Without it, the reader cannot see which assumption is loading the number. This is where sophisticated readers break the memo most quickly.
- **Single-author memo.** The memo must be co-signed by FinOps (for cost accounting) and governance (for governance-overhead inclusion) and engineering (for engineer-hour accounting). A single-author memo looks like advocacy.
- **Advocacy voice.** Grep the draft for "transformative," "significant return," "clearly justifies." Any of these fails the defensive-posture test. Replace with measured prose.
- **Not naming the paired FinOps roll-up.** The memo defends numbers that live in the roll-up; omitting the pointer makes the memo seem self-contained when it is not.

## 6. References

- **Official standards and frameworks:**
  - [NIST AI Risk Management Framework (AI RMF 1.0)](https://www.nist.gov/itl/ai-risk-management-framework) — the MEASURE function's emphasis on documented methodology, uncertainty, and limitations motivates the attribution-honesty frame (§2.4) and the sensitivity analysis (§2.5).
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — context for the incident-response cost line (D7).
  - [MITRE ATLAS](https://atlas.mitre.org/) — adversary-technique context for the incident/near-miss response cost line (D7) and the operational overhead of maintaining governance signal (D6).
- **Local context (same repo):**
  - `modules/mod-106-outcome-measurement-and-executive-reporting/exercise-01-outcome-vs-usage-metric-framework/SOLUTION.md` — the metric framework whose attribution-limit clause the memo extends into an ROI claim.
  - `modules/mod-106-outcome-measurement-and-executive-reporting/exercise-02-the-weekly-executive-scorecard/SOLUTION.md` — the surface whose §9 attribution-limit line carries this memo's frame forward week to week.
  - `modules/mod-106-outcome-measurement-and-executive-reporting/exercise-03-quarterly-board-ready-review-outline/SOLUTION.md` — §7 of the quarterly review references this memo rather than re-deriving ROI.
  - `modules/mod-106-outcome-measurement-and-executive-reporting/exercise-05-ai-productivity-literature-to-metric-choice-map/SOLUTION.md` — the literature map's declined moves are the basis for the numerator's N5 exclusion.
  - `modules/mod-107-budget-roi-and-build-vs-buy-at-org-scope/README.md` — the FinOps roll-up this memo is paired with and defends.
  - `modules/mod-104-training-programs-and-ai-literacy-curriculum/README.md` — source for the D5 training-time denominator component.
  - `modules/mod-103-policy-co-authoring-with-governance/README.md` — source for the D6 governance-overhead denominator component (redline log hours).
  - `modules/mod-109-ai-incident-response-and-enablement-side-rollback/README.md` — source for the D7 incident/near-miss response denominator component.
