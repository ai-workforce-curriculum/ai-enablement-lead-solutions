# Exercise 04 — Governance Council Pre-Read Authoring — Reference Solution

> Learning file: [`exercise-04-governance-council-pre-read-authoring.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-103-policy-co-authoring-with-governance/exercises/exercise-04-governance-council-pre-read-authoring.md)

## 1. Solution overview

The pre-read is a **one-page, three-section, named-ask-per-section** artifact the enablement seat produces every council cycle. Its quality shapes how the council weights the enablement voice over time. The constraint is the exercise — one page, three sections, each section capped at six body-text lines.

The worked pre-read below continues the archetype from Exercises 01–03 (coding assistant at a 3,000-person US bank, with the Exercise 03 intake submission already in flight) and pairs it with a plausible second in-flight item and one champion-network trend that crosses the "at least three champions or at least two BUs" threshold.

Posture checks the solution encodes:

- **Status tags per intake item.** The council sees the pipeline in one glance; items without tags force the chair to ask.
- **No classification proposed in Section 2.** Inputs only. `senior-ai-governance-architect` + `head-of-ai-governance` produce the classification.
- **Section 3 is a trend, not an anecdote.** Minimum threshold enforced: three champions or two BUs.
- **Named ask per section** — `decision`, `discussion`, or `informational`. Three "informational" is not using the seat.
- **Role names throughout.** No people names.

## 2. Implementation — worked answer (`council-pre-read.md`)

---

### AI Governance Council — Enablement Pre-Read

**Council date:** Tuesday, 2026-11-17.
**Chair:** `head-of-ai-governance` (L60).
**Attendee roles:** Chair; `senior-ai-governance-architect` (L50); General Counsel (data-protection practice); CISO delegate; Data Protection Officer; `ai-risk-engineer` (L25); `ai-governance-analyst` (L15); AI Enablement Lead (author).
**Author:** AI Enablement Lead (this role).
**Distribution:** Monday 2026-11-16 09:00 to the council shared drive.

---

#### Section 1 — Intake pipeline update

- **INT-2026-091** — Copilot-class coding assistant, Phase 1 Consumer Lending engineering cohort. Status: **`awaiting-council-decision`**. Pre-review surfaced an AUP Section 3 touchpoint (test-fixture scrubbing) proposed for walking-redline before GA. **Ask: decision** — approve, approve-with-condition, decline, or defer.
- **INT-2026-096** — `<!-- org-specific: confirm second in-flight tool, e.g., meeting-summarization tool piloted by HR Business Partners -->`. Status: **`schema-complete`**. Three AUP touchpoints flagged (Sections 3, 4, 6); SOP touchpoint on egress jurisdictional claim open. **Ask: decision** — expected to be `council-deferred` pending privacy sign-off on egress.
- **INT-2026-087** — Vendor data-labeling pilot requested by Wealth advisory. Status: **`council-deferred-from-last-cycle`**. Deferral was pending counsel's read on third-party-confidential-input language; counsel's redline arrived 2026-11-10. **Ask: discussion** — intend to resubmit as `schema-complete` at the next cycle.
- **Named ask for this section: decision** on INT-2026-091; **discussion** on the two others.

#### Section 2 — Risk-classification input

**Named tool: Copilot-class coding assistant (INT-2026-091).** Field-level usage over the 60-day Phase 1 pre-launch orientation cohort (`<!-- org-specific: confirm orientation-cohort size, approximately 40 engineers -->`) differs from the submitted cohort description in ways the council may want as inputs.

- **Cohort actually using the tool:** Phase 1 orientation cohort of `<!-- org-specific: confirm ~40 -->` engineers, all in Consumer Lending platform-services team; role mix skewed senior (staff and principal engineers over-represented relative to the planned Phase 1 roster of ~180); geography US-only so far (`<!-- org-specific: confirm whether the Hyderabad-based contracted engineers are in orientation -->`).
- **Task mix observed (champion-network workflow interviews, three champions, 2026-10-20 → 2026-11-10):** boilerplate generation (~55% of observed uses); code explanation (~25%); unit test authoring (~15%); migration or refactor drafting (~5%). No observed use inside regulated-decision code paths.
- **Data classes observed in operator practice:** Public and Internal classes dominate; Confidential appeared twice via draft design docs pasted into prompts (both self-corrected before submit); Restricted and Regulated: zero observed uses, zero observed accident-path triggers across the 60-day window.
- **Named ask for this section: discussion.** Classification inputs only; classification is `senior-ai-governance-architect` + `head-of-ai-governance`.

#### Section 3 — Field signal from champions

**Pattern:** Champions in two business units are reporting that engineers are uncertain which approved use covers "generating configuration files from a specification I wrote" — an increasingly common task that does not clearly fit any of the current AUP Section 2 approved-use entries.

- **Evidence this is a trend, not an anecdote:** Four champions (two in platform-services, two in developer-experience) across two BUs (Consumer Lending engineering and `<!-- org-specific: confirm second BU — likely Cards engineering or Wealth advisory engineering -->`), reporting the same pattern in the 2026-10-05 → 2026-11-10 window. The pattern appeared in `<!-- org-specific: confirm count -->` logged `#ai-enablement-help` threads over the same window.
- **Recommended action framed as input:** Recommend the council consider whether AUP Section 2 should add an approved use covering configuration-file generation from an engineer-authored specification, or whether this case is better resolved via the if-in-doubt default (Section 5) and the walking-redline cycle rather than a new approved-use entry. *The directional call is the council's.*
- **Named ask for this section: discussion.**

---

### End of worked pre-read

## 3. Validation steps

1. **Page count.** Render Markdown. Confirm it fits on one page at normal body-text size. If it spills, cut — this is the exercise.
2. **Per-section line count.** No section exceeds six body-text lines. Bulleted lists count their bullets as lines; sub-bullets are allowed and counted.
3. **Header completeness.** Council date, chair, attendee roles, author. All four.
4. **Three sections, in order:** intake pipeline update → risk-classification input → field signal from champions. Reordering is a Chapter 02 fail.
5. **Section 1: at least two in-flight items, each with a status tag.** Permitted tags: `pre-intake`, `intake-in-progress`, `schema-complete`, `awaiting-council-decision`, `council-deferred-from-last-cycle`. Items `awaiting-council-decision` carry the specific ask (approve / decline / defer).
6. **Section 2: one named tool, three bullets of field evidence** (cohort, task mix, data classes observed), **no proposed classification**. Grep for classification vocabulary ("high risk," "tier 2," "limited risk") — any hit fails.
7. **Section 3: one trend, meeting the "at least three champions or at least two BUs" threshold explicitly stated.** The pattern must be one-sentence; the evidence must be one-sentence; the recommended action must be one-sentence and framed as input ("Recommend the council consider whether…"), not as a decision to ratify ("the AUP should add…").
8. **Named ask per section.** `decision`, `discussion`, or `informational`. Sanity check: if all three sections are `informational`, the pre-read is not using the seat.
9. **Role names, not people names.** Grep for first names. Any hit means a people name slipped in; rewrite as role.
10. **`<!-- org-specific: ... -->` on every unknown.** Second in-flight tool identity, orientation-cohort size, second BU for the champion-network pattern, specific help-thread counts. Each marker names the specific slot the partner would fill.
11. **Coherence with Exercise 03.** The intake submission from Exercise 03 appears explicitly in Section 1 by ID (`INT-2026-091`). If you did not do Exercise 03, the pre-read still works — but the coherence is the carried-forward quality signal.

Markdown lint the file.

## 4. Rubric / review checklist

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | Fits on one page at normal body-text size | 10 | Spills. |
| R2 | Header present with date, chair, attendee roles, author | 5 | Any missing. |
| R3 | Three sections in required order | 10 | Reordered or missing. |
| R4 | No section exceeds 6 body-text lines | 10 | Any section over 6. |
| R5 | Section 1: ≥ 2 in-flight items, each with a valid status tag | 10 | Fewer than 2 items, or any item missing a tag. |
| R6 | Section 1: items `awaiting-council-decision` carry the specific decision ask | 5 | Decision-ready items without the approve/decline/defer call-out. |
| R7 | Section 2: one named tool, exactly three bullets of field evidence | 10 | Wrong structure. |
| R8 | **Section 2: no proposed classification** | 10 | Any classification vocabulary present. |
| R9 | Section 3: one trend (not an anecdote), with the "3 champions or 2 BUs" threshold explicit | 10 | Threshold not stated, or evidence is single-user anecdote. |
| R10 | Section 3: recommended action framed as input, not a decision to ratify | 5 | Imperative framing ("the AUP should add…"). |
| R11 | Explicit named ask per section (`decision`, `discussion`, `informational`) | 5 | Any section without ask. |
| R12 | Role names throughout; no people names | 5 | Any first name used for a role. |
| R13 | `<!-- org-specific: ... -->` on every unknown, with specific slots | 3 | Invented facts, or vague markers. |
| R14 | Coherence with Exercise 03 (intake item appears by ID if Exercise 03 was done) | 2 | Drift. |

**Pass threshold:** ≥ 85/100 and no R1 / R4 / R8 / R9 fail. R1 and R4 are the hard-constraint fails; R8 is the schema-vs-runner discipline fail; R9 is the trend-vs-anecdote discipline fail.

## 5. Common mistakes

- **Letting Section 1 spill into a status report.** The council reads Section 1 for one-glance pipeline status. Three or four items, each with a status tag and a one-line note, is enough. If it is longer than six lines, cut items (the oldest / least-contested ones) and name them in the "watch next cycle" stretch footer instead.
- **Proposing a classification in Section 2.** The section's whole point is to feed the architect's schema the field-level inputs the architect does not otherwise have. The architect produces the classification. Rewrite any "we recommend medium-risk classification" as inputs.
- **Dressing up a single-user complaint as a champion-network trend.** Section 3 fails if the "pattern" is actually one champion forwarded three times. Threshold is at least three champions or at least two BUs — hold yourself to it.
- **Framing Section 3's recommended action as a decision to ratify.** "The council should add approved use X." Rewrite as "Recommend the council consider whether approved use X should be added, or whether the case is better resolved via the if-in-doubt default."
- **All three sections marked `informational`.** That is a pre-read not using the seat. If genuinely no section needs a decision or discussion, then consider whether the pre-read should be shorter still and whether the enablement seat should ask for time back from the council.
- **Using people names.** "Sarah from the CISO's office said…" fails the role-names discipline. Rewrite as "CISO delegate."
- **Omitting the status tag on an item.** Section 1 without tags is the chair's "what is this?" question — the exact meeting-time waste the pre-read exists to preempt.
- **Letting Section 1 and Section 2 drift apart.** If INT-2026-091 is in Section 1 as `awaiting-council-decision` and in Section 2 as "classification inputs for council review," the pre-read is coherent. If the two sections name different tools without a reason, the enablement voice looks disorganized.

## 6. Stretch — pre-read Slack note, champion report-back template, watch-next-cycle footer, bilateral agenda

**3-sentence Slack message to `head-of-ai-governance`** (sent Monday with the pre-read):

> Pre-read is in the shared drive for tomorrow. Two items I expect to be contested: INT-2026-091 (Consumer Lending Phase 1 approval — my Section 3 touchpoint may push the architect toward a higher classification than I am collecting inputs for) and the Section 3 field-signal pattern on configuration-file generation (I expect counsel will want to weigh in on whether a new approved-use entry is a material policy change). I am aligned on house position for both — would still like 15 minutes Monday afternoon if you can spare it.

**Report-back-to-champions template** (sent 2–3 business days after the council, assuming it acted on the Section 3 field signal):

> Council reviewed last Tuesday and discussed the configuration-file-generation pattern you (and three other champions) surfaced. The decision: `<!-- org-specific: confirm actual council outcome — one of (a) add an approved-use entry at the next walking-redline; (b) resolve via if-in-doubt default; (c) defer to next cycle -->`. What that means at the field level: for the next two weeks, continue routing uncertain cases via the if-in-doubt default. I will circulate the specific guidance by `<!-- org-specific: confirm date -->`. Thanks for the signal — this is exactly the kind of pattern the council needs from the field.

**Watch-next-cycle footer** (1–2 lines, not part of the one-page body but an optional appendix):

> **Watch next cycle:** A pattern may be emerging around engineers pasting unit-test output (not inputs) into prompts for explanation — insufficient champion coverage yet to call a trend; targeting next cycle.

**Bilateral agenda — 30 minutes with `head-of-ai-governance`** (day before council):

1. **House position on INT-2026-091** (approve-with-condition likely) — 10 min. Specifically: condition language on AUP Section 3 walking-redline before Consumer Lending GA, and whether the condition names a specific target date or leaves it open.
2. **Section 2 handoff to architect** — 5 min. The architect will produce the classification; align on how to brief them on the Consumer Lending partial-regulated-domain nuance without pre-empting their call.
3. **Section 3 configuration-file pattern** — 10 min. Whether the council should route this to an AUP walking-redline directly or treat it as an if-in-doubt default conversation first.
4. **Remaining 5 min** — any late-breaking items from counsel, CISO, or DPO pre-reads that would reshape the agenda.

## 7. References

- **Learning material (local):**
  - [Chapter 02 — The Governance Council Liaison Seat](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-103-policy-co-authoring-with-governance/02-the-governance-council-liaison-seat.md)
  - [Chapter 06 — The Intake Questionnaire](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-103-policy-co-authoring-with-governance/06-the-intake-questionnaire.md)
  - [Chapter 07 — What You Route Out](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-103-policy-co-authoring-with-governance/07-what-you-route-out-counsel-soc-architect.md)
  - [mod-105 — Champion Networks and Change Management](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-105-champion-networks-and-change-management) — context for the "three champions or two BUs" trend threshold.
  - Exercise 03 ([`SOLUTION.md`](../exercise-03-intake-questionnaire-co-author/SOLUTION.md)) — carried-forward intake submission and classification inputs.
- **Official standards and frameworks** (context on why the council exists; not cited inside the pre-read):
  - [NIST AI RMF](https://www.nist.gov/itl/ai-risk-management-framework) — GOVERN function; the governance council is a GOVERN-category operating body.
  - [NIST AI 600-1: Generative AI Profile](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf) — generative-AI-specific considerations relevant to Section 2 inputs.
