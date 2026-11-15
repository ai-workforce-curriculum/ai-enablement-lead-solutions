# Exercise 06 — Fluency Growth Measurement Drill — Reference Solution

> Module: `mod-104-training-programs-and-ai-literacy-curriculum`
> Exercise type: measurement design + walkthrough
> Learning file: [`exercise-06-fluency-growth-measurement-drill.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-104-training-programs-and-ai-literacy-curriculum/exercises/exercise-06-fluency-growth-measurement-drill.md)

## 1. Solution overview

Fluency growth is measurable, but not with the first-instinct instruments. Course completions, tool licenses, prompts-per-user, and self-rated confidence surveys all correlate weakly with the behaviors the program is trying to move (recognize Restricted-class input, write a reusable prompt, catch a plausible hallucination, apply a refusal script). This exercise designs **the measurement set that actually moves with fluency** and walks one segment's drill end-to-end.

The deliverable is a short measurement plan plus a worked **one-segment drill** for S4 (Product/program/BA), which is the archetype's biggest Level-2-prompt-craft lift and the segment most likely to produce drifted prompts without the measurement surfacing it.

Posture checks:

- **Measure behavior, not activity.** License counts and prompt counts are leading indicators at best and misleading at worst. The core instrument is a **scenario drill with a plant** — exactly like the coaching plant (`exercise-04`) — scored on behavior.
- **Instruments pair to dimensions, not to a single aggregate score.** The five fluency dimensions from `exercise-01` get five instruments. Rolling them into one number loses the shape.
- **Report change over a baseline, not absolute score.** The baseline is captured pre-GA; reports describe deltas with named instruments.
- **Self-report is an input, not a measurement.** Confidence surveys are useful for triage and signal but are reported as such; they do not substitute for drill scoring.
- **Costs and consent are explicit.** A measurement that cannot be sustained on the available budget, or that reads as surveillance to employees, is not a measurement — it is a one-off audit that will corrode trust.

## Implementation

Apply this solution by walking section 2 in order: the five instruments (A), their delivery mechanics (B), the five secondary signals (C), the reporting shape (D), the worked S4 drill at +90 days (E), and the anti-measurements list (F). Validate against section 3, score with the rubric in section 4, review section 5 for the "measure activity, not behavior" failures, and use section 6 as the cross-cycle comparison and corrective-cadence stretch.

## 2. Worked answer — `fluency-measurement-plan.md`

### Measurement plan — v0.1 (coding-assistant rollout, 3,000-person US bank)

**Scope:** fluency growth for segments S1–S6 across the 12-month window from `exercise-01`.
**Owner:** this role (AI Enablement Lead), co-owned with L&D (`exercise-07`).
**Reporting cadence:** monthly to L&D; quarterly to executive via `mod-102 exercise-03`.
**Consent:** instruments are communicated in advance, scoring is per-segment aggregate, no individual rankings are published.

---

### A. Five instruments, one per fluency dimension

| Dimension (from `exercise-01`) | Instrument | How it is scored | Cadence |
|---|---|---|---|
| Risk literacy | **Recognition drill** — 6 example prompts, learner tags each as allowed / review-required / forbidden | 6-of-6 = fluent (Level 3); 5/6 = applied (Level 2); 4/6 = aware; ≤ 3 = not-yet | Baseline pre-GA; retake at +90d and +180d |
| Tool operation | **Observed task drill** — 2 scenarios in the actual tool UI (e.g., configure a save, read the audit log) | 2-of-2 unassisted = fluent; 2-of-2 with coach prompt = applied; 1-of-2 = aware | +90d and +180d for S1/S2; +180d only for S3/S4 (S3/S4 are not expected to reach fluent on this dimension) |
| Prompt craft | **Rewrite drill** — learner receives a weak prompt and rewrites using the four-move pattern | Scored by named-rubric (context / goal / constraints / format each 0–1). 3–4 = fluent; 2 = applied; 1 = aware | +90d and +180d; +365d for Level-3 segments |
| Output evaluation | **Plant drill** — learner reviews a prompt+output pair with a hidden hallucination, fabricated citation, or silently wrong output | Plant caught unaided = fluent; caught with coach hint = applied; missed = aware/not-yet | Pre-GA baseline (optional), +90d, +180d |
| Escalation behavior | **Scenario walk-through** — oral/written walk of the SOP accident path for a scripted scenario | All three channels correctly identified, no "delete the prompt" action, correct SLA named = fluent; one error = applied | +30d, +180d; retriggered within 72h of any real accident-path event |

Each instrument is a 5–15 minute interaction. Plant and rewrite drills are already in the coaching library (`exercise-04`); measurement reuses the same library with a different protocol (not during a coaching session).

---

### B. Delivery of the instruments

- **Who runs it.** Instruments are facilitated by L&D, not by this role. Facilitators are trained in a 60-minute session that includes scoring consistency on the rubric.
- **Where it sits.** Baseline and +90d instruments are inside a brief 20-minute measurement block delivered via Teams. +180d instruments are inside the mid-cycle refresher workshop (`exercise-05`). +365d is a refresh-to-baseline comparison.
- **Sampling, not census, for S5.** S5 has ~1,600 headcount; running the full instrument set against all of S5 is not sustainable. Instead:
  - Risk and escalation instruments **are** run against all of S5 (they are the Level-3 targets).
  - Prompt and output instruments are run on a stratified random sample (by region and shift) sized to detect a 10-percentage-point move per segment with 90% confidence. <!-- to-verify: confirm statistical-sampling assumptions (expected variance, inter-rater agreement on the rubric) with People Analytics or the measurement team before publishing thresholds. -->
- **For executives (S6).** No instruments. S6 fluency is measured by the quality of the questions asked at the quarterly rollout-report review (`mod-102 exercise-03`), captured as a short reviewer note, not a score.

---

### C. The five secondary signals (not primary measurements)

These are real signals but are reported as context, not as fluency measurement:

1. **Field-channel volume** (`#ai-enablement-help`). Weekly count, repeat-question rate, pattern-tagging.
2. **Accident-path events** from `mod-103 exercise-02` SOP. Count per segment, root-cause tag.
3. **Refusal-script usage** in RCLA and S4 playbook work (`exercise-03`). Count per week, context.
4. **Coaching commitment follow-through**, self-reported in `exercise-04` 7-day check-in. Count and percentage.
5. **Confidence survey** — a 4-question Likert survey per segment, pre-GA and at +90d. Reported separately as "how employees feel," never collapsed into fluency score.

A rising confidence score with a flat recognition-drill score is a known **mis-fluency signal** — employees feel capable while behavior has not changed. That pattern triggers the champion-network review (`mod-105`).

---

### D. Reporting shape

Reports to leadership use three view types:

1. **Segment × dimension matrix** showing current level and delta from baseline. Same shape as the fluency target map from `exercise-01`.
2. **Trend line per segment** showing recognition-drill and plant-drill pass rates over time.
3. **Behavior-change narrative** — three paragraphs per segment on what actually changed. Not generated by the tool; written by this role from the facilitator logs and the field-channel signal.

The segment × dimension matrix has four columns: baseline, +90d, +180d, +365d target. Target cells are the `exercise-01` target cells. The report is one page per segment.

---

### E. Worked drill — S4 (Product/program/BA) at +90 days

**Context.** S4 target per `exercise-01` is 2 across the board at +90d. Fluency target map carried 1 across the board pre-GA (baseline). This drill measures whether +90d reached Level 2 on risk, prompt, and output.

**Participants.** 30 S4 staff selected by stratified sample across the 400-person segment. Participation communicated two weeks ahead, framed as "the thing that tells us if the training was useful."

**Drill contents (20 minutes).**

- **Risk recognition (3 min).** 6 example prompts; learner tags. Three of the six reference non-public financial data; one references customer PII; two are clean. Pass threshold: 5/6 at Level 2.
- **Prompt rewrite (7 min).** Starting prompt: "Summarize the attached Q2 results and send to the team." Target rewrite adds context (role, audience), goal (one-paragraph internal note), constraints (no numbers reproduced that are not in the source; mark anything inferred as inferred), format (one paragraph, no headings). Scored by the named rubric.
- **Output plant (5 min).** Prompt+output pair from a product manager summarizing a legal draft, with a fabricated regulation citation and one silently wrong number. Learner flags.
- **Escalation walk (5 min).** Scenario: "You pasted a draft email that referenced a customer by name. You noticed 2 minutes later." Learner writes the first three actions.

**Scoring and expected result.**

| Instrument | Pass threshold at +90d | Expected result at Level 2 |
|---|---|---|
| Risk recognition | 5/6 | 70–85% of participants |
| Prompt rewrite | 2 of 4 moves added | 60–80% of participants |
| Output plant | Caught at least one of the two plants | 50–70% of participants |
| Escalation walk | All three channels named, no delete | 80%+ of participants |

<!-- to-verify: the expected-result ranges above are planning estimates for a segment going through a well-sequenced curriculum; validate against the first real cohort before using them as thresholds in later cycles. -->

**Facilitator debrief (10 min, same session).**

- Facilitator calls out the plant unaided-catch percentage and names the common missed pattern (fabricated citation vs silently wrong number). This becomes the content hook for the next office hour (`exercise-05`).
- Participants self-rate confidence on the four Likert items.
- No individual results are shared or stored under an individual's name after the session; only facilitator-coded aggregate scores persist.

**Rollup reporting (next business day).**

- Segment × dimension row for S4 updates.
- Narrative paragraph authored by this role, naming one specific gap (likely: fabricated-citation detection) and the office-hour topic queued for the next two weeks.
- Trend line updates against baseline.

**If S4 at +90d is below Level 2 on ≥ 2 dimensions.**

- The cadence plan triggers a +90d-to-+120d corrective subcadence: one extra workshop and two extra office hours, scoped to the failing dimensions.
- Champion for S4 reviews the playbook's workflow 1 and 3 and proposes a prompt update.
- This role notes the shortfall in the executive rollout report without softening the signal.

---

### F. Anti-measurements

Explicitly **not** reported as fluency measurement:

- Seats in training. Already tracked in L&D; not fluency.
- Course completions. Correlate weakly with behavioral fluency.
- Number of prompts per user. High volume is not high quality; may indicate tool over-use.
- Confidence survey score alone. Triage input only.
- Vendor-reported productivity numbers. Vendor artifact, not independent evidence. Flagged as vendor-reported anywhere they appear (per `mod-102 exercise-01`).
- NPS-style satisfaction scores on the training program. Measures delivery feeling, not fluency growth.

---

### End of worked measurement plan

## 3. Validation steps

1. **Five instruments map to the five fluency dimensions.** No single-aggregate fluency score.
2. **Instruments are behavioral.** Recognition, rewrite, plant, scenario walk. "Self-rated understanding" is not an instrument.
3. **Each instrument states a pass threshold tied to a fluency level.** No "scored well" framing.
4. **Baselines are captured.** Reports compare to baseline, not just current.
5. **Sampling plan for the largest segment.** Full-segment instruments are the exception, not the default.
6. **S6 (executives) is not instrumented.** Governance-question quality is the reported signal.
7. **Secondary signals are labeled as context,** not as measurement.
8. **The mis-fluency pattern is named.** Rising confidence + flat recognition is a watched signal.
9. **At least one worked drill is present end-to-end** with expected ranges, plant content, and facilitator debrief.
10. **Anti-measurements are explicitly listed** and named as not-fluency.
11. **`<!-- to-verify: ... -->` on planning ranges.** Expected-result ranges and sampling assumptions are flagged until validated against real cohort data.

Markdown lint before sharing.

## 4. Rubric or review checklist

Scored out of 100. ≥ 85 passes. R1, R2, R6, R10 fails are launch-gate equivalents.

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | Five instruments, one per fluency dimension | 10 | One instrument for all. |
| R2 | Instruments are behavioral (recognition / rewrite / plant / scenario) | 15 | Primarily self-report. |
| R3 | Pass thresholds tied to fluency levels from `exercise-01` | 10 | Unanchored thresholds. |
| R4 | Baseline captured, deltas reported | 10 | Current score only. |
| R5 | Sampling plan for large segments | 5 | Blanket census. |
| R6 | S6 measurement is governance-question quality, not drills | 10 | Execs scored on drills. |
| R7 | Secondary signals labeled as context, not fluency | 5 | Signals used as scores. |
| R8 | Mis-fluency pattern (rising confidence + flat behavior) named | 5 | Pattern not acknowledged. |
| R9 | One worked drill end-to-end, with expected ranges | 10 | Only generic drill design. |
| R10 | Anti-measurement list present | 10 | Vendor or completion metrics treated as fluency. |
| R11 | Reporting shape named (matrix + trend + narrative) | 5 | Report is a slide. |
| R12 | Monthly / quarterly cadence named with recipients | 5 | Reporting cadence absent. |
| R13 | `<!-- to-verify: ... -->` on planning ranges | 5 | Invented thresholds treated as validated. |

## 5. Common mistakes

- **One aggregate fluency score.** Loses the shape; makes the segments look similar when they are not; invites over-rotation to the metric. Keep the dimension matrix.
- **Self-reported confidence as the headline metric.** Confidence rises with exposure independent of behavior. Report it separately, labeled.
- **Vendor productivity numbers.** Vendor-reported; not independent. If they appear, label as vendor-reported and do not substitute for behavioral drills.
- **Course completions.** A completion-based program looks like progress; the actual Level-2 recognition drill shows it is not. Report completions only where completion is the instrument (which it never is here).
- **Blanket census.** Running the full instrument set against 1,600 S5 staff burns facilitator budget and does not add signal versus a stratified sample.
- **Measuring execs with drills.** Sends the wrong signal, wastes exec time, and misses the real fluency question (are they asking the right governance questions in the rollout review).
- **No baseline.** Deltas are the signal. Absolute scores at a single moment are not interpretable.
- **Scoring individuals under their names.** Converts measurement into surveillance. Aggregate by segment; narrative tags no individual.
- **Prompt-count per user as a leading indicator.** Spurious correlation; drives behavior toward volume, not quality.
- **No anti-measurement list.** The list is what keeps leadership from asking for completion rates as the primary KPI.

## 6. Stretch — cross-cycle comparison and the corrective-cadence trigger

**Cross-cycle comparison (year-over-year):**

- The `exercise-01` target cells are the comparator for year-end. Segments that reach their +180d target and hold at +365d are reported as **held**; segments that improve beyond target are reported as **grown**; segments that slip from +180d to +365d are reported as **slipped** and get a Q1 intervention.
- Year-over-year reporting goes into the executive-level `mod-106-outcome-measurement-and-executive-reporting` work.

**Corrective-cadence trigger:**

- Below Level 2 on ≥ 2 dimensions in any segment at +90d or +180d → trigger a corrective subcadence (one workshop + two office hours over the next 30 days, scoped to the failing dimensions).
- Rising confidence + flat recognition for two consecutive measurement windows → trigger a champion-network re-briefing (`mod-105`) and a rewrite of the Module 2 and Module 4 examples in `exercise-02` (because the content is being read without being learned).

**Executive-report line item:**

- One paragraph per segment per quarter, naming the matrix cell that moved and the matrix cell that did not. Not a graph alone — graphs without the named gap read as progress. See `mod-102 exercise-03`.

## 7. References

- **Learning material (local):**
  - [Exercise brief — `exercise-06-fluency-growth-measurement-drill.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-104-training-programs-and-ai-literacy-curriculum/exercises/exercise-06-fluency-growth-measurement-drill.md)
  - This module: `exercise-01` (dimensions and target map — anchors the instruments), `exercise-02` (assessments — reused as instruments), `exercise-03` (playbook — anchors refusal counts), `exercise-04` (coaching — shares the plant library), `exercise-05` (cadence — delivers the measurement blocks), `exercise-07` (L&D co-ownership — runs the facilitation).
  - Cross-module: `mod-102 exercise-03` (executive rollout report — receives the reporting), `mod-103 exercise-02` (SOP — provides accident-event signal), `mod-105` (champion review on mis-fluency), `mod-106` (year-over-year measurement work).
- **Official standards and frameworks:**
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — MEASURE function (test, evaluate, verify) is the backbone of the instrument set.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — plants reference output-trust and prompt-injection categories and the drill reports back to these risks.
  - [MITRE ATLAS](https://atlas.mitre.org/) — technique framing for the S1/S2 plant designs.
