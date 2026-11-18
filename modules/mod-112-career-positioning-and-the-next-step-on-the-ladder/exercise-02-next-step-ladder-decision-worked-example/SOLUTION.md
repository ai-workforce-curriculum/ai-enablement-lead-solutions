# Exercise 02 — Next Step Ladder Decision Worked Example — Reference Solution

> Module: `mod-112-career-positioning-and-the-next-step-on-the-ladder`
> Exercise type: design / worked example
> Exercise brief: [`lessons/mod-112-career-positioning-and-the-next-step-on-the-ladder/exercises/exercise-02-next-step-ladder-decision-worked-example.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-112-career-positioning-and-the-next-step-on-the-ladder/exercises/exercise-02-next-step-ladder-decision-worked-example.md) (in the learning repo)

## 1. Solution overview

The deliverable is a **worked example** of the AI Enablement Lead's next-step-on-the-ladder decision. The example walks through the decision end-to-end: how the options are enumerated, how they are scored against a transparent rubric, where the honest cuts fall, and how the final decision is written down so it can be defended under a hostile read (a future recruiter conversation, an exec sponsor's counter-offer, a mentor's pushback, the Lead's own second-guessing six months later).

The decision is **not** "which recruiter email do I reply to." It is the standing exercise of knowing, at any given moment, which of three or four plausible next moves the Lead would make if a concrete opportunity landed this week. A Lead who cannot answer that question has not run the exercise; a Lead who can is in a position to say yes or no to a surprise opportunity without six weeks of anxiety.

Posture checks this solution encodes:

- **Options first, scoring second.** Enumerating the real option space honestly (including "stay another 12-24 months") is more than half the work. Scoring a shortlist of two options the Lead already prefers is a tilted exercise.
- **The null option is a first-class option.** "Stay in the current role and deepen scope" is included as a named option with the same scoring treatment. Rejecting the null option by not listing it is a failure mode.
- **Scoring dimensions are stable across the exercise.** The dimensions are set *before* the Lead reads the specific options, to prevent scoring-dimensions drift ("I'll weight compensation highly this time because option A happens to be higher").
- **Weights are explicit.** A rubric without weights hides which dimension is actually driving the decision.
- **The decision writes down what would reverse it.** Decisions without a named reversal condition are not decisions; they are preferences. The exercise ends with "I would revisit this decision if X, Y, or Z happened in the next twelve months."
- **Attribution is honest.** The Lead's capability claims about themselves (what they can and cannot do in the next role) are bounded in the same way the mod-106 outcome claims are bounded.
- **Confidentiality holds.** The decision artifact is a personal operating artifact, not a shared document. Current-organisation specifics stay in it; they are not shared with any future employer during interview.
- **Framework-anchored posture extends to the Lead's own career.** The NIST AI RMF discipline of "state the posture, state the risks, state the controls" generalises to this decision: state the move, state the risks of the move, state the controls on each risk.
- **The exercise is re-run quarterly.** A one-time exercise goes stale fast. The quarterly portfolio review (mod-111 exercise-05) carries a 10-minute re-scoring pass.

## 2. Implementation — worked answer (`next-step-ladder-decision.md`)

### 2.1 Scope and framing

This artifact is the Lead's personal next-step decision worked once, end-to-end, for the archetype Lead at the archetype organisation (3,000-person regulated enterprise, 4 quarters into the role). The Lead is 36-42, mid-career, has one or two prior adjacent roles (head of L&D with AI specialty, head of productivity engineering, or a chief-of-staff role), and is not in financial-constraint mode.

The artifact is explicitly **not** a career plan for all time. It is a snapshot at today's date (`<!-- author-to-confirm: today's date in ISO format -->`) of what the Lead would do if a concrete option landed within the next ninety days.

### 2.2 Step 1 — Enumerate the option space (before any scoring)

Six options are enumerated. Each option is a role class, not a specific job posting. Specific postings are scored against the class.

| # | Option (role class) | Shape | Example title at a representative org |
|---|---|---|---|
| **O0** | **Stay and deepen** — remain as AI Enablement Lead at current org, expand scope by 1-2 BUs or regions over 12-18 months | Null option; same employer | AI Enablement Lead, expanded scope |
| **O1** | **Lateral at larger scope** — AI Enablement Lead at a larger-scope organisation (10x employee count, or multi-region, or sector-regulated-heavier) | Same role, larger domain | AI Enablement Lead, global; or Head of AI Enablement at a smaller company |
| **O2** | **Vertical in-org** — step up inside the current organisation to Head of / Director of AI Enablement, chief of staff for AI, or head of an AI Program Office | Current employer promotion | Head of AI Enablement; VP AI Programs |
| **O3** | **Vertical out-of-org** — Head of / Director of AI Enablement at a different organisation | New employer step-up | Head of AI Enablement at peer company |
| **O4** | **Adjacent — Governance/Risk** — Head of AI Governance, AI Risk Lead at a regulated enterprise, or AI-focused role inside a model-risk or audit function | Adjacent role, governance-heavy | Head of AI Governance; AI Risk Officer |
| **O5** | **Adjacent — Learning/Productivity** — Head of Learning & Development with AI specialty; Head of Workplace Engineering / Productivity | Adjacent role, learning / productivity | Head of L&D (AI-forward); Director of Workplace AI |
| **O6** | **External — Advisor/Founder** — Independent AI enablement advisor; join a vendor as a customer-advisory or field-CTO role; co-found an AI enablement product | External step | Principal, AI Enablement Advisory; Field CTO; Co-founder |

Option O0 (stay) must be scored with the same discipline as any external option. The Lead who skips scoring the null option is the Lead who leaves prematurely.

### 2.3 Step 2 — Fix the scoring rubric (before reading any option again)

Dimensions are set *now*, before the scoring step. Weights sum to 100. Each dimension is scored 1-5 per option (1 = strongly misaligned; 5 = strongly aligned).

| # | Dimension | Weight | What a 5 looks like | What a 1 looks like |
|---|---|---|---|---|
| **D1** | **Scope growth** — does the role materially expand scope vs. today (bigger org, more BUs, more regulatory surface, more complex stakeholder graph)? | 15 | Clear 2-3x scope increase on multiple axes | Scope lateral or narrower |
| **D2** | **Craft growth** — does the role grow the Lead's craft in dimensions they care about (governance depth, commissioning depth, measurement depth, change-management depth)? | 15 | New craft dimension explicitly in the role spec | Role is repetition of current craft |
| **D3** | **Operating altitude** — does the role sit at the altitude the Lead wants to operate at (operator vs. advisor vs. founder)? | 10 | Role is the altitude the Lead has named as their next step | Role conflicts with chosen altitude |
| **D4** | **Mission and sector fit** — does the role sit in a sector / mission the Lead is willing to carry publicly for 2-4 years? | 10 | High fit; Lead is comfortable advocating for the sector publicly | Low fit; sector conflicts with Lead's personal brand |
| **D5** | **Compensation and total-rewards** — base, variable, equity, benefits, geography-adjusted | 10 | Meaningful uplift at parity of risk; fair at adjusted-geography | Pay cut without compensating growth |
| **D6** | **Risk-adjusted longevity** — expected tenure in the role before it stops growing; likelihood the role survives a leadership change or re-org at the hiring org | 10 | 3+ years of growth available, low re-org risk | 12-18 months and then uncertain |
| **D7** | **Portfolio leverage** — does the role build the Lead's credentials portfolio (mod-111 ex-05) toward the subsequent step on the ladder? | 10 | Role produces the credentials needed for N+2 | Role produces credentials irrelevant to N+2 |
| **D8** | **Life fit** — geography, commute, travel, schedule, family and personal commitments | 10 | Materially compatible | Materially incompatible |
| **D9** | **Switching cost** — tax of departure (equity left on the table, in-flight incident / rollback owed, direct-reports mid-cycle, sponsor relationships mid-build) | 5 | Low switching cost; clean departure window | High switching cost; departure would leave the CoE under-staffed through a known risk window |
| **D10** | **Reversibility** — if the move is wrong, how reversible is it (can the Lead return to a role like today's within 12 months?) | 5 | Highly reversible; adjacent to current field | Low reversibility; off the AI enablement ladder entirely |

Weights sum to 100. The weights are the Lead's weights **today**; a Lead with a child entering school in 12 months might weight D8 higher; a Lead five years from a planned FI target might weight D5 higher. The weights are declared and defended before any option is scored.

### 2.4 Step 3 — Score each option against the rubric

Scoring the archetype Lead's six options. Scores are 1-5; weighted score is score × weight; option total is the sum.

| Dimension | Wt | O0 Stay | O1 Lateral+ | O2 Vert-In | O3 Vert-Out | O4 Governance | O5 L&D/Productivity | O6 Advisor/Founder |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| D1 Scope growth | 15 | 3 | 5 | 4 | 5 | 3 | 3 | 4 |
| D2 Craft growth | 15 | 3 | 4 | 4 | 4 | 5 | 3 | 5 |
| D3 Operating altitude | 10 | 4 | 4 | 5 | 5 | 3 | 3 | 2 |
| D4 Mission / sector fit | 10 | 5 | 4 | 5 | 4 | 4 | 4 | 3 |
| D5 Compensation | 10 | 3 | 4 | 4 | 5 | 4 | 3 | 2 |
| D6 Longevity | 10 | 4 | 4 | 3 | 4 | 4 | 3 | 2 |
| D7 Portfolio leverage | 10 | 3 | 4 | 5 | 5 | 5 | 3 | 4 |
| D8 Life fit | 10 | 5 | 3 | 5 | 3 | 4 | 4 | 4 |
| D9 Switching cost | 5 | 5 | 2 | 4 | 2 | 2 | 2 | 1 |
| D10 Reversibility | 5 | 5 | 4 | 4 | 4 | 3 | 3 | 2 |
| **Weighted total** | 100 | **3.75** | **3.95** | **4.25** | **4.20** | **3.95** | **3.15** | **3.15** |

(Weighted total shown on a 1-5 scale; equivalent 100-point totals: O0 = 375, O1 = 395, O2 = 425, O3 = 420, O4 = 395, O5 = 315, O6 = 315.)

The scores are illustrative for the archetype Lead and will differ for any specific person. The point is the method, not the specific answer. `<!-- org-specific: the Lead re-scores against their own weights; the illustrative numbers shift substantially per Lead -->`

### 2.5 Step 4 — Read the scoring honestly

- **The top two options** are O2 (vertical in-org, 425) and O3 (vertical out-of-org, 420). They are effectively tied inside the rubric's resolution.
- **O0 (stay) scores 375 — below the top two but within a credible range.** This is the honest read: staying is not a loss, but it is not the best score available. For the archetype Lead, "stay and deepen" is a serious option, not a default.
- **O1 (lateral+) at 395** is in the same band. A specific posting at a materially larger organisation would likely edge up with D1 and D7; the class-level 395 is the bar a specific posting must beat.
- **O4 (governance adjacent) at 395** scores well because D2 (craft growth) and D7 (portfolio leverage) are 5s. The weak spot is D6 (longevity) and D5 (compensation at some orgs).
- **O5 (L&D / productivity) and O6 (advisor / founder) at 315** are both underscored — the archetype Lead is not currently at the stage where either is the right move. They are preserved in the artifact as options, but they are not shortlisted this cycle.

The near-tie between O2 and O3 is where the Lead earns their money. Both are legitimately strong; the choice between them is governed by:

- **O2 upside:** continuity, intact sponsor relationships, intact operating scorecard, the Lead's attribution record in-org is strongest at the sponsor's own org, D9 (switching cost) is low.
- **O2 downside:** the role depends on the current sponsor and current scope. If the sponsor leaves in the next 12 months (not impossible at exec levels), O2 can disappear as a promotion opportunity and the Lead is left having waited.
- **O3 upside:** immediate scope increase; forces the Lead to rebuild the operating playbook in a new context, which is where the big craft gains live for mid-career operators; D7 (portfolio leverage) is strongest.
- **O3 downside:** D9 (switching cost) is highest; D6 (longevity) depends heavily on the new sponsor; the first 180 days are a period of maximum vulnerability.

### 2.6 Step 5 — Decision posture (this cycle)

The Lead's decision for this cycle, written down:

> **This cycle (dated `<!-- author-to-confirm: YYYY-MM-DD -->`) the Lead will prioritise O2 as the preferred next step, with O3 as a serious alternative and O1 as a floor. The Lead will:**
>
> 1. **Signal O2 intent** to the exec sponsor at the next scheduled 1:1, framed as a 9-15 month development conversation and not an ultimatum. Request a jointly-authored development plan with the sponsor on what evidence closes the gap from the current role to a named Head of / Director of role. Follow the mod-111 exercise-05 confidentiality posture — do not share the artifact itself.
> 2. **Decline inbound O3 opportunities with warmth, not finality.** If a concrete O3 posting arrives within 90 days and the sponsor is non-committal or absent on O2, re-score with the specific posting in the table above; proceed if the specific-posting total clears O2's score by ≥ 0.2 (weighted, on the 1-5 scale) **and** the first-180-day risk is acceptable.
> 3. **Hold O1 as a floor.** The Lead will not take an O1 role unless O2 is explicitly off the table and no viable O3 has landed within six months.
> 4. **Not pursue O4 / O5 / O6 this cycle.** The Lead will continue to build Family A credentials and Family B public artifacts that would support an O4 move in a later cycle, but the active pursuit stays on O2/O3.
> 5. **Re-run this exercise at the next quarterly portfolio review** (mod-111 exercise-05 §2.7) or on any of the off-cycle review triggers in §2.9 below.

### 2.7 Step 6 — Risks and controls on the chosen posture

| Risk | Likelihood | Impact | Control |
|---|---|---|---|
| Sponsor leaves or re-orgs before O2 materialises | Medium | High — O2 evaporates | Plan has 9-15 month horizon; if sponsor's own departure is signalled, re-evaluate immediately |
| Sponsor is positive but promotion is scope-constrained by org-level headcount freeze | Medium | Medium — O2 delayed | If delayed > 2 quarters past the plan date, re-open O3 pursuit |
| O3 inbound arrives at a tempting compensation level without sponsor on O2 | Medium | Medium — Lead takes O3 impulsively | Re-score in writing before any yes; the ≥ 0.2 weighted-score threshold is the discipline |
| Lead over-signals departure intent externally | Low | High — reads as disloyal in-org | Confidentiality posture in mod-111 ex-05 §2.5 holds |
| Lead under-signals internal ambition | Medium | Medium — O2 never materialises because sponsor assumes stasis | The next-1:1 signal is explicit; "development conversation" is the frame |
| The current org hits a material AI incident during the 9-15 month plan window | Medium | High — switching mid-incident is a career-defining attribution risk | Switching cost (D9) weighting increases while incident is open; departure window closes until resolution |

### 2.8 Step 7 — Reversal conditions (what would change the decision)

The Lead will revisit this decision immediately if any of:

- The exec sponsor departs, is re-orged, or signals in a quarterly 1:1 that the O2 path is not viable in the next 12 months.
- The current organisation's AI program is de-scoped, defunded, or politically re-cast (e.g., merged into IT without governance autonomy).
- A concrete O3 posting arrives whose specific-posting re-score clears O2 by ≥ 0.2 weighted and whose first-180-day risk is acceptable under the Lead's control-posture.
- A material incident (mod-109) at the current organisation changes D9 (switching cost) materially — either because the Lead is attribution-responsible for a rollback that is in-flight, or because the incident has resolved and a natural departure window opens.
- The Lead's Family A / Family B portfolio (mod-111 ex-05) moves materially enough that O4 or O6 becomes a serious option.
- A life-fit change (D8) that is the primary driver — relocation, family commitment, health.

In the absence of any of these, the Lead does not re-open the decision. Re-opening without a trigger is a sign the Lead is anxious, not deciding.

### 2.9 Step 8 — What this artifact does NOT do

- It does not predict which specific recruiter will call.
- It does not commit the Lead to leaving on a specific date.
- It does not commit the Lead to staying if conditions deteriorate.
- It does not read as a complaint against the current org or sponsor.
- It does not get shared with the current employer or any prospective employer.

The artifact is a private operating document. Its purpose is to make a surprise opportunity a decision, not an improvisation.

### 2.10 Decision rationale — why this shape, not another

- **Why enumerate options before scoring.** A rubric applied only to two pre-selected options is a tilted rubric; the Lead has already decided. Enumerating six real option-classes, including the null, is what makes the exercise honest.
- **Why include O0 (stay) with the same discipline as external options.** Mid-career Leads who skip scoring the null option are the ones who leave prematurely. The null option deserves the same scoring and the same risk-control treatment.
- **Why the scoring rubric is fixed before the options are re-read.** Dimensions drift toward the option the Lead wants; fixing them before the scoring step is a cheap discipline that catches most drift.
- **Why weights are declared and defended.** A rubric without weights hides the dimension actually driving the decision. Making weights visible lets a mentor or coach push back.
- **Why near-ties produce a decision, not a coin flip.** For O2 vs. O3 (425 vs. 420), the scoring doesn't decide; the risk-control posture does. The decision writes down what would reverse it, which converts a tie into an actionable plan.
- **Why the decision specifies a signal to the sponsor.** The Lead who waits for the sponsor to notice their ambition is the Lead whose promotion never comes. Signalling the ambition is part of the posture; it is bounded, dated, and framed as development, not ultimatum.
- **Why the reversal conditions are pre-written.** Decisions that do not name what would reverse them are not decisions. The pre-written list converts future ambiguity ("should I re-think this?") into pattern-match ("did any of X, Y, Z happen?").
- **Why the first-180-day risk on O3 is a named threshold.** Mid-career operators who take external vertical moves frequently fail in the first 180 days for reasons that could have been assessed before signing. Naming the check is the control.
- **Why the exercise is re-run quarterly.** Rubric weights drift (life circumstances shift, sponsor relationships shift, the field shifts); options shift (new organisations appear; current org re-orgs); the Lead's portfolio shifts. Quarterly re-run catches the drift early.
- **Why this artifact is private.** It contains current-employer specifics and private weight preferences. Sharing it with a prospective employer during interview reads as transactional; sharing it internally reads as an ultimatum. Private is correct.

## 3. Validation steps

1. **Six option classes enumerated** (stay, lateral+, vertical-in, vertical-out, governance-adjacent, L&D/productivity-adjacent, advisor/founder — at least five families with the null option named).
2. **Null option (stay) scored with the same discipline** as external options.
3. **Scoring rubric with ≥ 8 dimensions** named with explicit weights summing to 100.
4. **Weights declared before any option is scored.**
5. **Each dimension has a "what a 5 looks like" and "what a 1 looks like."**
6. **Every option scored 1-5 on every dimension** and weighted-total computed.
7. **Scoring read honestly** — the honest read of the near-ties, the floor, and the under-scored options is explicit.
8. **Decision posture named for this cycle** with a preferred option, an alternative, a floor, and a declined set.
9. **Risks table** names ≥ 4 risks with likelihood, impact, and named control per risk.
10. **Reversal conditions pre-written** with ≥ 4 triggers.
11. **Confidentiality posture** named — artifact is private; sponsor signal is bounded.
12. **Re-run cadence** named (quarterly + off-cycle triggers).
13. **`org-specific` and `author-to-confirm` tags** on all specifics (the Lead's actual scores, actual weights, actual dates).

## 4. Rubric / review checklist

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | Six option classes enumerated with null option included | 15 | Fewer options or null option omitted. |
| R2 | Null option scored with the same discipline as external options | 5 | Null option scored as filler or not scored at all. |
| R3 | ≥ 8 scoring dimensions with explicit weights summing to 100 | 15 | Fewer dimensions, missing weights, or weights not summing to 100. |
| R4 | Weights declared before options re-read, with rationale | 5 | Weights set after options are scored. |
| R5 | Every option scored on every dimension with weighted total | 10 | Partial scoring or no totals. |
| R6 | Scoring read honestly — near-ties, floor, under-scored named | 5 | Reading skipped or sanitised. |
| R7 | Decision posture names preferred / alternative / floor / declined | 10 | Decision ambiguous. |
| R8 | Risks table ≥ 4 risks with likelihood / impact / control per risk | 10 | Risks named without controls. |
| R9 | Reversal conditions pre-written with ≥ 4 triggers | 10 | Reversal absent. |
| R10 | Confidentiality posture — private artifact, bounded sponsor signal | 10 | Artifact shareable externally; no signal discipline. |
| R11 | Re-run cadence named (quarterly + off-cycle triggers) | 5 | Exercise treated as one-time. |
| R12 | `org-specific` / `author-to-confirm` tags on specifics | 2 | Unmarked specifics. |
| R13 | Decision rationale provided | 3 | Rationale thin or absent. |

**Pass threshold:** ≥ 85/100 and no R1 / R3 / R7 / R9 fail. R1 (full options), R3 (scoring rubric with weights), R7 (named decision), and R9 (reversal conditions) are the four discriminators between a worked example that holds up under hostile read and one that reads as a sanitised rationalisation.

## 5. Common mistakes

- **Shortlisting to two options before scoring.** If the rubric only runs against the two options the Lead already prefers, the rubric is a decoration. Six options minimum, one of which is the null.
- **Scoring the null option dismissively.** O0 (stay) often scores high on D3, D4, D8, D9, D10 and genuinely competes with external moves. Scoring it 2/5 on every dimension is dishonest.
- **Setting weights after reading the options.** Weights drift toward the option the Lead wants. Fix weights before; defend them to a mentor.
- **No weighted total.** Scoring without weighted total hides which dimension is driving. The weighted total is the discipline.
- **Treating a near-tie as "either is fine."** A tie resolves to a decision (one is preferred, the other is alternative) *and* a set of controls (what would flip the preference). A tie is not permission to drift.
- **No risk table.** A decision without risks named is a plan without controls.
- **No reversal conditions.** A decision without a named reversal is a preference, not a decision.
- **Sharing the artifact with any employer (current or prospective).** The artifact is private. The signal to the sponsor is bounded, framed as development, and does not reference the scoring.
- **Running the exercise once.** Rubric weights, options, and portfolio all drift. Quarterly re-run.
- **Running the exercise under duress** (bad week at work, hard sponsor meeting, hostile exec round). The rubric reads as pre-decision rationalisation if run under duress. Run it on a calm week.
- **Over-weighting D5 (compensation)** — compensation gains that trade off against D1/D2/D7 (scope / craft / portfolio leverage) are typically a bad mid-career trade. The 10-point weight on D5 is deliberate.
- **Under-weighting D9 (switching cost)** when the current org has a live incident or a mid-flight rollback the Lead is attribution-responsible for. D9 is a dial, not a constant.
- **Ignoring D10 (reversibility)** on O6 (advisor/founder). An off-ramp back to an AI Enablement Lead role from a founder attempt is possible but not automatic; D10's 5 points are honest about that.
- **Writing the decision as a rant about the current sponsor.** The decision is about the Lead's trajectory; the sponsor is one input. Framing the decision as sponsor-criticism is both inaccurate and a confidentiality breach if the artifact ever leaves the Lead's possession.

### 5.1 Stretch — mentor pressure-test

Before the Lead treats this cycle's decision as settled, they walk one mentor through the artifact — not to solicit the mentor's answer, but to force the Lead to defend the weights, the scores, and the control posture out loud. A mentor who agrees with every weight and every score is a mentor not pushing hard enough. Patterns of mentor pushback across two or three mentors (not one) are signals to update weights or scores before the cycle is closed.

The mentor conversation is also the one place where "what am I afraid of?" is worth asking directly. A rubric cannot capture fear; a mentor can. The Lead who declines O3 at a specific score threshold should know whether the decline is driven by D9 (named control) or by fear (not named, not controllable by the rubric). If it is fear, the rubric is not the problem; the Lead needs a different conversation.

## 6. References

- **Learning material (local):**
  - [mod-106 — Outcome Measurement and Executive Reporting](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-106-outcome-measurement-and-executive-reporting) — the attribution-honesty discipline this decision applies to the Lead's own capability claims.
  - [mod-107 — Budget, ROI, and Build-vs-Buy at Org Scope](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-107-budget-roi-and-build-vs-buy-at-org-scope) — the structured-choice posture (options enumerated, scored, bounded) generalises from the org-scope decision to the Lead's own.
  - [mod-108 — Industry and Regulatory Flavours of Enablement](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-108-industry-and-regulatory-flavours-of-enablement) — sector calibration that shapes D4 (mission / sector fit) across options.
  - [mod-109 — AI Incident Response and Enablement-Side Rollback](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-109-ai-incident-response-and-enablement-side-rollback) — the live-incident condition on D9 (switching cost).
  - [mod-110 — Commissioning Internal AI Tools and Custom Agents](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-110-commissioning-internal-ai-tools-and-custom-agents) — the commissioning portfolio that Family D (mod-111 ex-05) draws on; relevant to D7 (portfolio leverage).
  - [mod-111 — AI CoE Operations, Vendor Management, and Cross-Functional Leadership](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-111-ai-coe-operations-vendor-management-and-cross-functional-leadership) — Exercise 05 credentials portfolio that D7 (portfolio leverage) scores against and that this decision feeds back into.
  - [mod-112 — Career Positioning and the Next Step on the Ladder](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-112-career-positioning-and-the-next-step-on-the-ladder) — the dedicated module this exercise sits inside.
  - [Exercise 01 — Exec Communication Story Outline](../exercise-01-exec-communication-story-outline/SOLUTION.md) — the venue where the O2 development conversation gets framed (V1 skip-level) and the V5 promotion packet is prepared.
  - [Exercise 03 — Credentials Portfolio External Positioning](../exercise-03-credentials-portfolio-external-positioning/SOLUTION.md) — external positioning that shapes which options (O3, O4, O6) are even credible from the portfolio's current state.
  - [Exercise 04 — Public Artifact Set Plan](../exercise-04-public-artifact-set-plan/SOLUTION.md) — the public artifact schedule that compounds into D7 (portfolio leverage) over time.
- **Official standards and frameworks:**
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — the posture discipline (state the move, state the risks, state the controls) that this decision generalises from the org-scope to the personal.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — relevant when D2 (craft growth) includes AI security posture in O4 (governance-adjacent).
  - [MITRE ATLAS](https://atlas.mitre.org/) — relevant when D2 (craft growth) includes adversarial-technique context in O4 (governance-adjacent).
