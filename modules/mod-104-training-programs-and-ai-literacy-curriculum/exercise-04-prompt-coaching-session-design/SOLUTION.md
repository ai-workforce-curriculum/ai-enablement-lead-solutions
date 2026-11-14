# Exercise 04 — Prompt Coaching Session Design — Reference Solution

> Module: `mod-104-training-programs-and-ai-literacy-curriculum`
> Exercise type: design artifact
> Learning file: [`exercise-04-prompt-coaching-session-design.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-104-training-programs-and-ai-literacy-curriculum/exercises/exercise-04-prompt-coaching-session-design.md)

## 1. Solution overview

Prompt coaching is the smallest-unit intervention in the module. Where the curriculum (`exercise-02`) is self-paced and the playbook (`exercise-03`) is reference, **coaching** is a live, 1:1 or small-group conversation with real prompts, real outputs, and a real workflow in front of both people. It is where fluency actually moves.

This solution designs the coaching session as a **repeatable 45-minute drop-in** for a non-engineer coachee, driven by the coachee's own live work. The design is grounded in the fluency target map (`exercise-01`) and the function playbook (`exercise-03`): the coach uses those artifacts as the checklist, not a slide deck.

Archetype: same ~3,000-person US bank. Primary coachee segment is **S4 Product/program/BA** because that segment holds the Level 2 prompt-craft target and is the biggest surface for drifted prompts outside engineering.

Posture checks:

- **Coach the coachee's work, not a prepared example.** Preparing a sample prompt is a tempting shortcut that collapses the session into a demo. The coachee brings two live prompts; those are the session.
- **Before / during / after structure.** Every coaching session produces three artifacts: an intake note (before), a session log (during), and a changed workflow (after). "After" is the only one that matters, so the other two are kept small.
- **Coach to the refusal, not past it.** If the coachee's live prompt should not have been run at all, the session is about recognizing that. "Great prompt, rewrite it differently next time" misses the point.
- **No new content.** Coaching teaches nothing the curriculum does not already contain. The coach's job is to make the coachee apply the Module 3 four-move pattern to their specific job, not to invent a new pattern.
- **Observable outcome.** The session ends with a changed draft of the coachee's prompt and a one-sentence commitment the coachee will act on in the next 7 days.

## Implementation

Apply this solution by running section 2 end-to-end — produce the intake note (before), run the 45-minute session structure in order (0–5, 5–15, 15–25, 25–35, 35–40, 40–45), log it, and capture the changed workflow artifact (after). Validate against section 3 and the session pass criteria, score with the rubric in section 4, and use section 5 to watch for the recurring coaching failures (becoming a demo, missing the refusal, inventing new content) before scaling via section 6's coach-training and plant-library stretch.

## 2. Worked answer — `coaching-session-design.md`

### Coaching session — v0.1 (S4 Product/program/BA; archetype: 3,000-person US bank)

**Format:** 45-minute 1:1 (preferred) or 2-person same-function (allowed).
**Mode:** Video with screen share by default; in-person acceptable.
**Cadence:** Offered as drop-in via `exercise-05` office hours; also bookable for any employee at Level 1 trying to reach Level 2 on prompt craft or output evaluation.
**Facilitator:** the AI Enablement Lead (this role) in the first 60 days post-GA; a trained function champion from +60 days onward.

---

### Session structure (45 minutes)

#### 0–5 min — Frame and set the goal

- Coach reads out the goal: "We are going to work on one or two of your real prompts from the last week, and by the end you will have a rewritten version plus one thing you will do differently next week."
- Confirm scope: this is prompt craft and output evaluation, not a general tool training. Policy questions go to `#ai-enablement-help`, not here.
- Confirm no sensitive data in the examples the coachee brought. If the coachee needs to scrub a prompt, coach them through the scrub (that is itself a Module 2 moment).

#### 5–15 min — Walk the coachee's first live prompt

- Coachee pastes the prompt they used this week and the output they got.
- Coach asks three questions, in order:
  1. "What were you trying to produce?"
  2. "Looking at the output, did it do that?"
  3. "Was there anything in the prompt that was not supposed to be there?"
- Coach does **not** suggest a rewrite yet. The first ten minutes are diagnostic.

#### 15–25 min — Apply the four-move pattern to the first prompt

- Coach pulls up the four-move pattern (**context / goal / constraints / format**) from Module 3 of the curriculum — on screen so the coachee reads it alongside the prompt.
- Coach and coachee rewrite the prompt together. The coachee types; the coach narrates. Two rules:
  1. **The rewrite names each of the four moves inline** the first time (so the coachee builds the pattern recognition), then collapses to clean prose the second time.
  2. **At least one new constraint comes from the playbook (`exercise-03`), not from the coach's head.** This threads the playbook into real use.
- The coachee runs the new prompt live; the output is captured in the session log.

#### 25–35 min — Walk the coachee's second prompt (or a refusal)

Two branches, decided by what the coachee brought:

- **Branch A — second drafting prompt.** Same structure as the first, 10 minutes, less coach narration. The coachee does more of the work.
- **Branch B — the "I almost ran this" prompt.** If the coachee brought a prompt they chose not to run (or that the coach recognizes they should not run), the next 10 minutes are a **refusal rehearsal**: the coachee practices saying out loud why the prompt did not run and what channel they used. This is the highest-leverage ten minutes of the session. Many coachees bring Branch B only on prompting.

#### 35–40 min — Output-evaluation drill

- Coach surfaces a prepared single plant: a prompt-output pair from the coachee's function that contains a hidden hallucination, fabricated citation, or stale fact. The pair is **not** about the coachee's own work — this is a pattern exercise.
- The coachee reviews for 3 minutes, flags what they see, and states one review step they would add to catch it in their own work.
- Coach reveals the plant and closes with the OWASP ML Top 10 and MITRE ATLAS reference for the specific failure pattern.

#### 40–45 min — Close with a commitment

- Coachee states one commitment aloud: "In the next 7 days I will …" Example commitments the coach should be looking for:
  - "Rewrite one of my recurring prompts with the four moves."
  - "Add the fact-containment constraint to any prompt that cites a regulation or policy."
  - "Use the refusal script from the playbook when asked to summarize a dispute."
- Coach types the commitment into the session log; coachee gets a copy.
- Coach offers one followable artifact: either the Module 3 four-move cheat card or the function playbook section relevant to the coachee's commitment.

---

### Materials used in session

- The coachee's **two live prompts** (brought by the coachee before the session).
- The function playbook (`exercise-03`) open to the relevant workflow.
- The four-move pattern from Module 3 (`exercise-02`) on a single slide or doc, visible on screen.
- **One** prepared plant per coaching session, kept in a coach-only library of 10–15 plants per segment. Plants rotate so the same two coachees do not see the same plant.

### Intake note (before) — 1 page

Coachee fills this in when booking:

1. Segment (from `exercise-01` map): S1 / S2 / S3 / S4 / S5 / S6.
2. One sentence about the kind of work the coaching should focus on (e.g., "weekly status drafts," "test-case generation," "policy-draft summaries").
3. Two prompts they used this week, pasted. Scrubbed of Restricted / Regulated data. If the coachee cannot find two, one is acceptable and the coach will draw the second from a prepared library of function-typical starting points.
4. One goal for the session, one sentence. Example: "I want my status drafts to stop sounding like a hallucinated meeting summary."

### Session log (during) — 1 page

Captured by the coach during the session. Not shared outside the coaching pair except as anonymized patterns in the aggregated monthly report (`exercise-06`).

- Coachee segment and function.
- Prompt 1: before text, after text, which of the four moves were added, which playbook constraint was added, whether the output changed.
- Branch A or B taken in the 25–35 min slot; brief notes.
- Plant used and whether the coachee caught it unaided.
- Commitment stated aloud by the coachee.

### Workflow change (after) — 1 artifact

The **changed prompt the coachee will actually reuse next week**, saved either in the coachee's prompt library or inside the tool's saved-prompt feature where available. This is the only artifact that matters for measuring the session's effect.

---

### Session pass criteria

The coach's job at the end of the session is to be able to answer **yes** to all of the following:

1. Did we work on at least one real prompt the coachee brought?
2. Did we apply the four-move pattern to that prompt live?
3. Did we add at least one constraint from the playbook, not from the coach's head?
4. Did the coachee practice either a rewrite or a refusal aloud?
5. Did the coachee catch the plant unaided, or get coached through the pattern?
6. Did the coachee leave with one named commitment they will act on in 7 days?

Five of six is a pass. Below five, the coach schedules a follow-up within two weeks.

### What the session does not do

- It does not teach the tool's features. If the coachee cannot operate the tool, the right intervention is the Module 1/2 refresh, not coaching.
- It does not debug the coachee's output as a standalone artifact. Output is examined only through the prompt that produced it; "fix this output" without "fix the prompt" is the fail state.
- It does not cover policy questions. Those route to `#ai-enablement-help`.
- It does not promise a result. Fluency is cumulative; a single session should produce one observable change, not a transformation.

---

### End of worked session design

## 3. Validation steps

1. **Session length is 45 minutes.** Shorter collapses to a demo; longer loses attention and becomes re-training.
2. **Each slot in the 0–45 min structure is present and sized as named.** The 25–35 min branch logic is the most often-skipped part.
3. **The session uses live coachee prompts, not prepared examples.** The intake note confirms this.
4. **The four-move pattern is named explicitly and cited back to Module 3.** If the coach is teaching a different pattern, the design has drifted.
5. **At least one constraint added to the rewrite comes from the function playbook (`exercise-03`).** Grep the session log; the playbook link should appear.
6. **A plant is used, from the coach-only library.** The coach does not improvise a plant in session.
7. **Commitment is stated aloud and captured in writing.** Silent commitments are not commitments.
8. **Pass criteria are 5-of-6 of the stated checks.** Perfection is not the gate.
9. **The after-artifact is a saved, reusable prompt.** Not a session summary.
10. **Design does not teach the tool's features.** If a section describes feature training, the coaching has drifted into onboarding.

Markdown lint before sharing.

## 4. Rubric or review checklist

Scored out of 100. ≥ 85 passes. R1, R3, R5, R6 fails are launch-gate equivalents.

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | 45-minute structure with named slot sizes | 10 | No sizing or structure. |
| R2 | 0–5 framing names scope and excludes policy/features | 5 | Framing is a general intro. |
| R3 | Diagnostic three-question walk before any rewrite | 10 | Coach jumps to a rewrite. |
| R4 | Rewrite uses four-move pattern, named inline | 10 | Rewrite is a demo. |
| R5 | Rewrite adds at least one playbook constraint | 10 | Constraint invented ad hoc. |
| R6 | 25–35 min branch covers refusal rehearsal when applicable | 10 | Refusal branch absent. |
| R7 | Output-evaluation drill uses a prepared plant | 10 | Plant improvised. |
| R8 | Commitment stated aloud and captured in writing | 10 | Commitment unspoken. |
| R9 | Before / during / after artifacts all defined | 5 | Only during-session log. |
| R10 | Session does not teach tool features | 5 | Feature training embedded. |
| R11 | Pass gate is 5-of-6, not 6-of-6 | 5 | Perfection required. |
| R12 | Plant drill grounded in OWASP ML Top 10 or MITRE ATLAS pattern | 5 | No threat-model grounding. |
| R13 | `<!-- to-verify: ... -->` on org specifics (plant library size, coach count) | 5 | Invented specifics. |

## 5. Common mistakes

- **Prepared slides.** The moment the session has slides, it is not coaching, it is training. Keep materials to live prompts + the four-move card + the playbook open on a second screen.
- **Rewriting before diagnosing.** The three-question diagnostic is where the coachee learns to see their own prompt. Skipping it is the single biggest coaching failure mode.
- **Fixing the output instead of the prompt.** The coachee leaves with a better output but no better prompt discipline; next week's prompt drifts again.
- **Running without a commitment.** A session without a named "in the next 7 days I will …" is a nice chat. Fluency does not move.
- **Coaching every coachee the same way.** S3 (RCLA) coaching emphasizes refusals; S4 (BA) coaching emphasizes fact containment; S1 (engineer) coaching emphasizes output evaluation on silently wrong suggestions. Same 45-minute structure, different weight in the 25–35 slot.
- **No plant.** The output-evaluation drill becomes a conversation about the coachee's output, which the coachee already wrote and cannot see with fresh eyes.
- **Letting the session run long.** Over 60 minutes and the coachee is cooked. Stop on time; book a follow-up.
- **Coaches writing the session log as a long narrative.** A 1-page template with checkboxes keeps the coach honest and aggregates for `exercise-06` measurement.

## 6. Stretch — coach-training and the plant library

**Coach training (for champion handoff at +60 days):**

- 90-minute workshop led by this role. Two candidates per function, drawn from the champion network (`mod-105`).
- Workshop content: watch a recorded coaching session, run a mock session with this role as the coachee playing a typical S4 case, run a mock with a Branch B refusal case.
- Certification criterion: trainee coach passes 5-of-6 of the session pass criteria when coaching this role playing a planted coachee.

**Plant library:**

- 10–15 plants per segment, each a prompt+output pair drawn from real anonymized field cases or deliberately constructed to carry one named failure mode.
- Each plant is tagged with:
  - Segment (S1–S6).
  - Failure mode (hallucinated fact, fabricated citation, stale regulation, silently wrong code, drifted refusal, missed MRM boundary, missed Restricted-class input, missed external-output rule).
  - OWASP ML Top 10 or MITRE ATLAS reference.
- Plants rotate so no coachee sees the same plant twice.
- Library owner: this role. Contributions reviewed and tagged weekly.

**Session-telemetry rollup (into `exercise-06`):**

- Monthly: number of coaching sessions per segment; percentage with Branch A vs Branch B; percentage of plants caught unaided; percentage of commitments reported as completed at 7-day follow-up.
- The 7-day follow-up is a one-question async note from the coach: "Did you do the thing you said you would do?" Response is self-reported but patterns across the month surface the signal.

## 7. References

- **Learning material (local):**
  - [Exercise brief — `exercise-04-prompt-coaching-session-design.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-104-training-programs-and-ai-literacy-curriculum/exercises/exercise-04-prompt-coaching-session-design.md)
  - This module: `exercise-01` (segment context), `exercise-02` (four-move pattern anchor), `exercise-03` (playbook constraints), `exercise-05` (office-hours cadence — delivery channel), `exercise-06` (measurement — reads commitment follow-up), `exercise-07` (L&D — co-owns coach training).
  - Cross-module: `mod-103 exercise-02` (SOP accident path — anchors the Branch B refusal rehearsal), `mod-105` (champion networks — source of coach cadre).
- **Official standards and frameworks:**
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — MEASURE function informs the pass criteria and plant-library structure.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — plants reference the output-trust, prompt-injection, and sensitive-data-leak categories.
  - [MITRE ATLAS](https://atlas.mitre.org/) — technique framing for the untrusted-content and output-manipulation plants.
