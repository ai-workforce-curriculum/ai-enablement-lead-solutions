# Exercise 02 — Foundational AI Literacy Curriculum Outline — Reference Solution

> Module: `mod-104-training-programs-and-ai-literacy-curriculum`
> Exercise type: design artifact
> Learning file: [`exercise-02-foundational-ai-literacy-curriculum-outline.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-104-training-programs-and-ai-literacy-curriculum/exercises/exercise-02-foundational-ai-literacy-curriculum-outline.md)

## 1. Solution overview

This is the **baseline curriculum** that every in-scope employee gets. It is the "everyone takes this" tier that sits beneath role-based playbooks (`exercise-03`) and specialty tracks. The deliverable is a module-by-module outline with learning objectives, assessment, time budget, and segment-targeting notes keyed to the fluency target map from `exercise-01`.

Archetype threaded from `exercise-01`: a **~3,000-person US-regulated bank** rolling out a coding assistant, with the AUP and SOP drafted in `mod-103`. The curriculum is sized for that scale and mix of segments.

Posture checks:

- **Shortest curriculum that hits the fluency targets, not longest.** The time budget is a constraint, not a boast. If the outline grows past the budget, something is being carried for completeness rather than effect.
- **Each module ends in an assessment whose pass criterion is a behavior.** "Can recognize a Restricted input and refuse to paste it" is a pass. "Scored 80% on the quiz" is not.
- **Modules are versioned to the AUP they teach.** When `mod-103 exercise-01` is redlined, the dependent modules re-ship. The outline makes the dependency visible.
- **Segments route through the curriculum differently.** The outline is linear in presentation but segmented in delivery — S5 (customer-facing) gets a 25-minute subset, S1 (engineers) gets the full set plus deep dives.

The curriculum has two tiers: **Core** (every in-scope employee) and **Core+** (engineers, data/analytics, and anyone with prompt-authoring responsibility). Role-specific content lives in `exercise-03`.

## Implementation

Apply this solution by walking section 2 top-to-bottom — scope and framing first, then Tier 1 Core modules (1–6) in order, then the Tier 2 Core+ add-ons (modules 7–10) for the segments that require them. Use the segment routing table to confirm each module's audience, validate the outline against section 3, score with the rubric in section 4, and use section 5 to pressure-test for the common curriculum-design failures before shipping v0.1 for L&D co-review.

## 2. Worked answer — `foundational-curriculum-outline.md`

### Scope and framing

- **Audience:** all employees and contractors covered by the AUP (`mod-103 exercise-01`, Section 1).
- **Time budget:**
  - Core: 55 minutes total, split across modules. Completion target within 30 days of hire or policy re-ship.
  - Core+: an additional 45 minutes layered on top for S1/S2 and prompt-author S4.
- **Delivery mode:** self-paced e-learning as the default; manager-led team debrief required for Modules 1, 3, and 6; live cohort delivery used only for the +180d refresher described in `exercise-05`.
- **Governance:** Owned by this role (AI Enablement Lead) jointly with L&D (`exercise-07`). Co-signed by `head-of-ai-governance`.

### Tier 1 — Core (55 minutes, all segments)

#### Module 1 — What this tool is and why we bought it (8 min)

- **Learning objectives**
  1. Name the tool, its vendor, and the tenant it runs in (versus personal accounts).
  2. State the problem the bank bought the tool to solve.
  3. Identify where to go for policy questions, accident reporting, and security incidents.
- **Content**
  - 90-second video from the executive sponsor (not this role). Executive voice matters here.
  - One-slide architecture: user → IDE/plug-in → bank tenant → vendor → response. Named vendor region.
  - A named map of the three escalation channels (policy, accident, security).
- **Assessment**
  - Three-question check. Example: "You suspect a prompt included customer PII — which channel do you use?" Correct answer references `mod-103 exercise-02` SOP, not a generic "tell your manager."
- **Segment notes**
  - S6 (executives) gets this module and stops here. The rest is below their decision surface.

#### Module 2 — Data classes and what you can and cannot put in a prompt (12 min)

- **Learning objectives**
  1. Name the bank's data classification tiers from `mod-103 exercise-01` Section 4.
  2. Identify a Restricted or Regulated input in a real workflow example.
  3. Apply the "if-in-doubt — do not use" default from the AUP.
- **Content**
  - The classification table from the AUP, reproduced verbatim (versioned).
  - Four worked examples: a code snippet with a customer account number embedded, a PII-free architecture question, a rate sheet, a ticket description referencing a case number.
  - The "if-in-doubt" default read aloud by `head-of-ai-governance` on camera.
- **Assessment**
  - A 6-item recognition exercise: the learner tags each example as allowed / review-required / forbidden. Pass = 6/6, not 5/6. The failure mode this module exists to prevent is "the learner knew the rule but mis-applied it in a realistic example."
- **Segment notes**
  - S5 (customer-facing) spends the most time here. This is the module that keeps the bank safe at scale.

#### Module 3 — Prompt craft — the four-move pattern (10 min)

- **Learning objectives**
  1. Decompose a task into context, goal, constraints, and format.
  2. Recognize two common failure modes: under-specified prompts and stuffed prompts.
  3. Draft a prompt that another employee could run and get a similar result.
- **Content**
  - The four-move pattern (context / goal / constraints / format). A single named pattern. Multiple competing patterns are a known failure mode — pick one and teach it.
  - Two paired examples: a weak prompt and the rewritten version, with the rewrite labeled by which of the four moves it added.
  - One explicit anti-pattern: "write me a report about X" with no context, goal, constraints, or format — show the output, show why it is not useful.
- **Assessment**
  - Rewrite exercise. Learner submits a before/after prompt for a task from their own job. A champion or facilitator reviews. Pass = the rewrite added at least two of the four moves and did not add a Restricted-class input.
- **Segment notes**
  - S3 (RCLA) completes this module at Level 2 behavior but is not required to generate original prompts; the goal is recognition.

#### Module 4 — Reading AI output (10 min)

- **Learning objectives**
  1. Recognize hallucinated facts, fabricated citations, and silently wrong code or text.
  2. State the "review before commit" rule from the AUP Section 2 in the learner's own role terms.
  3. Name one review step the learner will take before acting on an output in their own workflow.
- **Content**
  - Three paired examples with hidden errors: a fabricated API name, a plausible-but-fictional regulation citation, a code snippet that returns wrong results for an edge case.
  - A short checklist: "Did I verify this fact from a source I trust?" "Could this output be wrong in a way that looks right?" "If this were wrong, who would notice first?"
  - A named OWASP ML Top 10 reference for hallucination and LLM output-trust risk.
- **Assessment**
  - 3-of-3 recognition drill. The learner must flag all three example errors. 2-of-3 is a retake.
- **Segment notes**
  - S4 (product/BA) receives an extra 3 minutes on citation-fabrication because their drafting workflows produce the most unreviewed text.

#### Module 5 — Escalation drill (8 min)

- **Learning objectives**
  1. Walk the accident path from `mod-103 exercise-02` SOP without consulting the SOP document.
  2. Name the channel for a suspected security incident (not the same as an accident).
  3. State one thing the learner will **not** do if an accident happens (e.g., will not delete the prompt).
- **Content**
  - A tabletop scenario: "You pasted a ticket description that included a customer name. You realized it two minutes later. What now?" Read the SOP. Then a second scenario with a different failure mode.
  - A one-slide diagram of the three channels: policy, accident, security.
- **Assessment**
  - Scenario walk-through. The learner describes the first three actions they would take. Pass = no mention of deleting the prompt, correct first channel, correct SLA expectation.
- **Segment notes**
  - S5 gets this module twice at +90d and +180d in the cadence (`exercise-05`). The repetition is intentional.

#### Module 6 — What you cannot do and why (7 min)

- **Learning objectives**
  1. Name the six prohibited uses from the AUP Section 3.
  2. Explain in one sentence why one of the six is prohibited (not just that it is).
  3. State the review cadence and when the next review is.
- **Content**
  - The six prohibited uses, each with a one-sentence "why" from the AUP co-author's rationale.
  - The review cadence and a pointer to how to propose a change (via the `#ai-enablement-help` channel, not by ignoring the AUP).
- **Assessment**
  - Short free-response: "Pick one prohibited use. In one sentence, say why." A champion reviews; the answer is passed on sincerity and plausibility, not polish.
- **Segment notes**
  - S3 (RCLA) owns the review path for one of the six prohibitions and uses this module as the basis for `exercise-03` role-play.

### Tier 2 — Core+ (additional 45 minutes, S1 / S2 / prompt-author S4)

#### Module 7 — Threat-aware prompting (15 min)

- **Learning objectives**
  1. Recognize prompt-injection patterns in content the user paste into the tool (links, repos, ticket text with attacker-controlled content).
  2. Name two MITRE ATLAS techniques that map to the workflows the learner performs.
  3. Apply one mitigation: strip or quote untrusted content.
- **Assessment**
  - Learner is given a ticket description containing an injected instruction and a suspicious code snippet. They identify both and describe how they would handle it. Pass = both flagged.

#### Module 8 — Model-risk-managed boundary (10 min, S1 and S2 only)

- **Learning objectives**
  1. Name the boundary from the AUP Section 3.3: code that runs against credit / lending / AML / sanctions decisions.
  2. Identify a workflow that is on each side of that line.
  3. State the MRM review requirement before crossing the boundary.
- **Assessment**
  - Two-example boundary drill, pass = correct call on both.

#### Module 9 — Output evaluation deep dive (10 min, S1 only)

- **Learning objectives**
  1. Review a suggested code change for a hidden edge-case failure.
  2. Write a one-line verification step to run before accepting the suggestion.
- **Assessment**
  - Code-review exercise with a plant: a suggestion that compiles and passes a naive test but fails on the documented edge case.

#### Module 10 — Writing prompts others can reuse (10 min, prompt-author subset)

- **Learning objectives**
  1. Package a prompt with context, constraints, and acceptance criteria that another employee can reproduce.
  2. Avoid embedding bank data in the shared prompt.
- **Assessment**
  - Learner submits a shared prompt and a second employee reproduces it. Pass = reproducibility, not output quality.

### Segment routing table

| Segment | Core modules | Core+ modules | Total time |
|---|---|---|---|
| S1 Engineers/SRE | 1–6 | 7, 8, 9, 10 | 100 min |
| S2 Data/analytics/MRM | 1–6 | 7, 8, 10 | 90 min |
| S3 RCLA | 1, 2, 4, 5, 6 (Module 3 at recognition level only) | — | ~45 min |
| S4 Product/program/BA | 1–6 | 7, 10 (prompt-author subset) | 55–80 min |
| S5 Operations/retail/CF | 1, 2, 4, 5, 6 (Module 3 compressed to 4 min) | — | 25 min |
| S6 Executives | 1 only | — | 8 min |

The S5 25-minute budget is where most of the headcount is. The outline optimizes for that.

### Versioning and refresh

- The curriculum is **version-tagged to the AUP version it teaches**. Current: Core v0.1 against AUP v0.1 from `mod-103 exercise-01`.
- Any change to the AUP that touches Section 2, 3, or 4 triggers a refresh of Modules 2, 3, 4, 6.
- Refresh cadence: scheduled at +180d, mid-cycle triggered by AUP revision, regulator guidance update, or the champion network surfacing a Module 5 gap (`exercise-05`).

### Anti-goals

- Does not teach "what is a large language model" at the Core tier. That is interesting background, not behavioral content. If leadership wants it, it is a 5-minute pre-reading, not a module.
- Does not teach prompt craft to S5 at Level 2. Returns too little for the training spend on the biggest headcount.
- Does not use a graded quiz as the primary pass criterion. Quiz scores and behavioral fluency are measurably different.

## 3. Validation steps

1. **Total time at each segment ≤ fluency-target map budget.** S5 ≤ 25 min, S1 ≤ 100 min. If a module pushes a segment over, cut content, do not add time.
2. **Each module has 1–3 learning objectives, each phrased as an observable behavior.** "Understand X" is not a behavior; "Identify X in a given example" is.
3. **Each module has an assessment with a stated pass criterion.** No module should say "quiz TBD."
4. **Pass criteria are behavioral or at the minimum 100%-recognition.** The Module 2 pass is 6/6; lowering it is the fail state.
5. **Segment routing table is complete and matches `exercise-01` target map.** S6 is Module 1 only. S5 is risk/escalation heavy. S3 skips Module 3 at authoring level.
6. **Modules dependent on the AUP reference AUP version.** Grep the outline for AUP references; each should carry the version.
7. **Module 5 (escalation) appears twice in the S5 ramp** (via `exercise-05`). The repetition is intentional and must be visible in the outline.
8. **Core+ modules reference OWASP ML Top 10 and MITRE ATLAS by named technique or risk.** Generic references fail.
9. **No module teaches "what is an LLM" as Core content.** That is a frequent reviewer regression.
10. **Anti-goals present.** The outline names what it does not teach. Omission is the common failure.

Markdown lint before sharing.

## 4. Rubric or review checklist

Scored out of 100. ≥ 85 passes. R2, R4, R5, R10 fails are launch-gate equivalents.

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | Core total time ≤ 60 min, S5 total ≤ 30 min | 10 | Budget blown by any segment. |
| R2 | Each module states 1–3 observable learning objectives | 10 | "Understand" or "be aware" objectives. |
| R3 | Each module has a stated assessment with pass criterion | 10 | "Quiz TBD." |
| R4 | Pass criteria are behavioral or 100%-recognition | 10 | ≥80% quiz pass accepted. |
| R5 | Segment routing table matches the `exercise-01` fluency target map | 10 | Executives assigned Core+, S5 assigned Module 3 full. |
| R6 | Curriculum is version-tagged to AUP version | 5 | No version pointer. |
| R7 | AUP dependency is explicit per module | 5 | AUP mentioned without version or section. |
| R8 | Core+ references OWASP ML Top 10 and MITRE ATLAS by named technique | 10 | Generic references. |
| R9 | Module 5 (escalation) scheduled twice in S5 ramp | 5 | Once only. |
| R10 | Anti-goals listed | 10 | No anti-goals; curriculum reads as "everything AI." |
| R11 | Delivery mode stated per module (self-paced / team debrief / live) | 5 | Blanket "e-learning." |
| R12 | Refresh triggers named (AUP change, regulator update, champion signal) | 5 | Refresh cadence stated without triggers. |
| R13 | Unknown facts carry `<!-- to-verify: ... -->` | 5 | Invented headcounts, vendor numbers, regulator names. |

## 5. Common mistakes

- **Teaching "what is an LLM" at Core.** It is an interesting topic, not a behavior change. Moves the time budget away from Modules 2, 4, 5.
- **Letting Core grow past 60 minutes.** Completion rates drop sharply. The curriculum is a floor, not a comprehensive text.
- **Using a graded quiz as the primary pass gate.** Quiz pass and behavioral fluency correlate weakly. Prefer scenario or recognition drills.
- **Sending S6 (executives) through the full Core.** They stop at Module 1. Pushing further burns executive goodwill and does not change their decision-surface behavior.
- **Sending S5 through the full prompt-craft module.** The training spend returns little on segment behavior; S5 benefits more from double-dose Module 5.
- **Failing to version-tag the curriculum to the AUP.** The curriculum drifts from policy and the champion network catches the gap in the field.
- **Writing "learning objective: understand AI risks."** Not a behavior. Replace with recognize / state / apply / refuse / escalate.
- **No anti-goals.** The outline becomes a wish list and fails under budget pressure.

## 6. Stretch — segment pass-rate plan (post-GA) and the 90-day review

**Pass-rate plan (for reporting in the executive rollout report, `mod-102 exercise-03`):**

- Reported metric = **percentage of in-scope employees in each segment who have passed the behavioral assessment** for every module they are routed through. Not completions, not quiz averages.
- Reported cadence = weekly during the GA ramp (0–90 days), monthly after.
- Reported threshold = Core pass rate ≥ 90% per segment at +30 days. Below 85% in any segment triggers a champion-network root-cause pass (`mod-105` territory). <!-- to-verify: confirm the specific threshold with the executive sponsor; 90% is a reasonable default but may differ by regulatory expectation. -->

**90-day review inputs:**

- Pass-rate telemetry per segment × module.
- Channel signal from `#ai-enablement-help`: which Module numbers are generating repeat questions?
- Accident log from the data-handling SOP: did any accident path trace back to a Core module's gap?
- Champion-network field notes on what employees are actually doing versus what the modules teach.

## 7. References

- **Learning material (local):**
  - [Exercise brief — `exercise-02-foundational-ai-literacy-curriculum-outline.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-104-training-programs-and-ai-literacy-curriculum/exercises/exercise-02-foundational-ai-literacy-curriculum-outline.md)
  - This module: `exercise-01` (fluency target map — inputs segmentation), `exercise-03` (role-based playbook — inputs Core+), `exercise-05` (cadence — inputs refresh), `exercise-06` (measurement — inputs assessment pass criteria), `exercise-07` (L&D partnership — inputs ownership).
  - Cross-module: `mod-103 exercise-01` (AUP — anchors Modules 2, 3, 6), `mod-103 exercise-02` (SOP — anchors Module 5), `mod-102 exercise-03` (exec rollout report — inputs Stretch).
- **Official standards and frameworks:**
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — the Core curriculum maps to GOVERN (Module 1, 6), MAP (Module 2), MEASURE (Module 4), MANAGE (Module 5).
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — anchors Module 4 (output trust) and Module 7 (threat-aware prompting).
  - [MITRE ATLAS](https://atlas.mitre.org/) — technique references in Module 7.
