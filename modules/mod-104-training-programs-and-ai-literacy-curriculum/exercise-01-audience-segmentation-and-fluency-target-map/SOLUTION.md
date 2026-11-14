# Exercise 01 — Audience Segmentation and Fluency Target Map — Reference Solution

> Module: `mod-104-training-programs-and-ai-literacy-curriculum`
> Exercise type: design artifact
> Learning file: [`exercise-01-audience-segmentation-and-fluency-target-map.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-104-training-programs-and-ai-literacy-curriculum/exercises/exercise-01-audience-segmentation-and-fluency-target-map.md)

## 1. Solution overview

This is the artifact that comes out of asking "who in the company is the training program for, and what does 'fluent' mean for each of them?" The deliverable is a **fluency target map**: one row per workforce segment, one column per fluency dimension, with a named target level and a short rationale for why that target is the right one for that segment.

The solution carries the same archetype used across mod-102/103 — a **~3,000-person US-regulated bank** rolling out a coding assistant (Copilot-class) as its first bank-wide AI tool, with knowledge of the AUP and SOP drafted in mod-103 — so the segmentation choices here feed directly into exercises 02–07 of this module.

Posture checks this solution encodes:

- **Segments are drawn by what an employee needs to decide, not by HR hierarchy.** The retail branch teller and the back-office operations analyst sit in different HR trees but decide the same kinds of AI questions; they belong in one segment for literacy purposes.
- **Fluency is multi-dimensional.** A single "level 1/2/3" scale collapses too much. The map below separates **risk literacy**, **tool operation**, **prompt craft**, **output evaluation**, and **escalation behavior**. Each has its own target per segment.
- **Targets anchor to behavior, not to course completion.** "Can recognize a Restricted-class input and not paste it" is the target. "Completed the 30-min e-learning" is not.
- **The map is a planning artifact.** It is not published to employees. It is used by this role, L&D, and segment champions to size and sequence the rest of the module's deliverables (curriculum, playbook, cadence).

The segment taxonomy, five fluency dimensions, and target-level rubric are the content of the artifact. Everything else in this solution is scaffolding around that artifact.

## Implementation

Apply this solution by working section 2 in order — segments (A), dimensions (B), rubric (C), target map (D), per-segment rationale (E), ramp (F), and scope-of-work exclusions (G). Validate against section 3, score with the rubric in section 4, and review section 5 for failure modes before sharing the v0.1 map with L&D and the governance partner via the stretch memo in section 6.

## 2. Worked answer — `fluency-target-map.md`

The artifact below is the planning document. It is paired with a short memo (Section 6 — Stretch) that frames it for the governance partner and L&D counterpart.

---

### Fluency Target Map — v0.1 (Coding-assistant rollout, 3,000-person US bank)

**Scope:** All employees and contractors covered by the AUP drafted in `mod-103 exercise-01`. Vendors without bank identity are out of scope and are covered by the vendor-management track, not this map.

**Timeframe:** 12-month fluency plan tied to the tool's GA ramp — pre-GA, +90d, +180d, +365d.

---

#### A. Segments (six, drawn by decision surface)

| # | Segment | Approx. headcount | Why this is one segment |
|---|---|---|---|
| S1 | Software engineers and SRE | ~350 | Primary daily users of the coding assistant; they make the most frequent output-quality judgments. |
| S2 | Data, analytics, and model-risk analysts | ~180 | Frequent prompt use against bank data; adjacent to the MRM boundary from `mod-103 exercise-01` Section 3.3. |
| S3 | Risk, compliance, legal, audit (RCLA) | ~220 | Consumers of model output; redliners of policy; need enough literacy to challenge engineering claims without having to code. |
| S4 | Product, program, business analysts | ~400 | Heaviest users of non-code assistant features (drafting, summarization) that the AUP still governs; biggest "unexpected prompt" surface. |
| S5 | Operations, retail, customer-facing staff | ~1,600 | Largest headcount; customer-data proximity makes the Restricted-class discipline the critical target. |
| S6 | Executive and senior leaders (L55+) | ~50 | Decide budget, reversal, and public positioning; literacy here is about reading reports and asking the right governance questions, not using the tool daily. |

Segment boundaries are **decision-based**, not HR-tree-based. A data engineer embedded in RCLA for a project is in S2 (decision surface = engineering output quality), not S3.

> Note: the headcount column is the planning estimate used to size the curriculum, not an official org-chart census. Confirm with People/HR before any budget ask. <!-- to-verify: confirm actual segment headcounts for a specific target org before publishing this map externally. -->

---

#### B. Fluency dimensions (five, each measured independently)

1. **Risk literacy** — recognizes data classes, prohibited uses, and the "if-in-doubt" default from the AUP (`mod-103 exercise-01`). Can explain to a peer why a given input is Restricted without being told.
2. **Tool operation** — can perform the tool's supported workflows (e.g., invoke in IDE, review suggestions, accept/reject), knows where the tenant-level controls are, knows where logs live.
3. **Prompt craft** — can decompose a task, set context, give constraints, iterate; recognizes when a prompt is too vague or too stuffed. Non-engineers get a prompt-craft target too; it is not an engineering-only skill.
4. **Output evaluation** — can spot hallucination, stale information, fabricated citations, and silently wrong code; knows what "review before commit" looks like in their own role.
5. **Escalation behavior** — knows the data-handling SOP accident path (`mod-103 exercise-02`), the governance-question path (`#ai-enablement-help`), and the security-incident path. The target is **demonstrated** behavior in drill, not stated knowledge.

The five dimensions are meant to be scored independently. A software engineer with high tool-operation but weak output-evaluation (treats suggestions as correct by default) is a known risk pattern; the map surfaces it.

---

#### C. Target-level rubric

Each dimension is scored on a 4-level rubric. Levels are behavioral, not credentialed.

| Level | Meaning |
|---|---|
| 0 — Not-yet | Has not been trained; no claim can be made. |
| 1 — Aware | Can state the policy or recognize the risk when prompted. Does not yet act on it reliably. |
| 2 — Applied | Acts correctly in normal cases; still needs a prompt or checklist for edge cases. |
| 3 — Fluent | Acts correctly in edge cases without a prompt; can coach a peer at Level 2. |

Level 3 is the ceiling for a general literacy program. Deeper expertise (threat modeling, secure development with AI, model-risk analysis) lives in role-specific training outside this module's scope and is the subject of `mod-110` and `mod-109`.

---

#### D. The target map

Cell values are **target level at +180 days from GA** (the midpoint of the 12-month plan). Pre-GA and +90d targets are the ramp; +365d is the sustained-state target (equal to or one level above +180d).

| Segment | Risk literacy | Tool operation | Prompt craft | Output evaluation | Escalation |
|---|---|---|---|---|---|
| S1 Engineers/SRE | 3 | 3 | 3 | 3 | 3 |
| S2 Data/analytics/MRM | 3 | 2 | 3 | 3 | 3 |
| S3 RCLA | 3 | 1 | 2 | 2 | 3 |
| S4 Product/program/BA | 2 | 2 | 2 | 2 | 2 |
| S5 Operations/retail/customer-facing | 3 | 1 | 1 | 1 | 3 |
| S6 Executives | 2 | 0 | 0 | 2 | 2 |

Reading the map:

- **S5 is Level 3 on risk and escalation, Level 1 on everything else.** The largest segment also has the largest customer-data proximity; the training investment goes where it changes the most behavior. Prompt craft for a retail teller is not what keeps the bank safe.
- **S3 (RCLA) is Level 1 on tool operation.** Risk/legal/compliance staff need to understand the tool exists and roughly what it does; they do not need to operate it. Pushing them to Level 2 is a known waste.
- **S6 (execs) is Level 0 on tool operation and prompt craft** by design. The failure mode here is leaders demanding course completion for tool skills they will not use, and then evaluating the program by their own fluency.
- **S1 and S2 are Level 3 across the board** — they are the operators the AUP's "review before commit" line depends on.

---

#### E. Rationale per segment (one paragraph each)

**S1 Engineers/SRE.** They are the audience the tool was procured for. If their output evaluation is below fluent, the "review before commit" line in the AUP (`mod-103 exercise-01` Section 2) is unenforceable. The target is uniform 3.

**S2 Data/analytics/MRM.** Analysts are frequent prompt users against bank data and sit next to the model-risk-managed decision boundary. Level 3 on risk, prompt, output, escalation. Tool operation sits at Level 2 because the specific IDE workflows are not their daily surface.

**S3 RCLA.** Their fluency target is the ability to challenge engineering and analytics claims about AI output: "show me how you verified that." Level 3 on risk and escalation; Level 2 on prompt and output so they can read someone else's prompt and tell whether it should have passed review. Tool operation stays at Level 1 because the role does not use the tool directly, and asking them to is a known productivity leak.

**S4 Product/program/BA.** The segment most likely to use non-code assistant features in day-to-day work (draft a status note, summarize a meeting, rewrite a ticket). The AUP still governs these uses. Level 2 across the board, with a stretch to 3 on risk after +180d. This is the segment that most often hits the "if-in-doubt" default and must act on it.

**S5 Operations/retail/customer-facing.** The largest segment and the one in closest proximity to customer data (S-class and R-class in the data map from `mod-103 exercise-01` Section 4). Risk and escalation at Level 3; the other dimensions stay at Level 1. The training investment for S5 is deliberately **narrow and deep** — teach the three things the segment will actually need, not a general AI literacy curriculum.

**S6 Executives.** Fluency here is governance behavior: can read the executive rollout report (`mod-102 exercise-03`), can tell the difference between an outcome metric and a usage metric, can ask the reversal question when the pre-committed exit condition fires. Tool operation and prompt craft are explicitly Level 0 so that the program's success is not measured by whether the CEO wrote a prompt that week.

---

#### F. Ramp — how each segment gets to its target

| Segment | Pre-GA | +90d | +180d | +365d |
|---|---|---|---|---|
| S1 Engineers/SRE | 2,2,2,2,2 | 3,3,3,3,3 | 3,3,3,3,3 | 3,3,3,3,3 |
| S2 Data/analytics/MRM | 2,1,2,2,2 | 3,2,3,2,3 | 3,2,3,3,3 | 3,2,3,3,3 |
| S3 RCLA | 2,0,1,1,2 | 3,1,2,2,3 | 3,1,2,2,3 | 3,1,2,2,3 |
| S4 Product/program/BA | 1,1,1,1,1 | 2,2,2,2,2 | 2,2,2,2,2 | 3,2,2,2,2 |
| S5 Operations/retail/CF | 1,0,0,0,1 | 2,1,1,1,2 | 3,1,1,1,3 | 3,1,1,1,3 |
| S6 Executives | 1,0,0,1,1 | 2,0,0,2,2 | 2,0,0,2,2 | 2,0,0,2,2 |

Each tuple is in dimension order: risk, tool, prompt, output, escalation.

---

#### G. What this map does not do

- It does not assign specific courses, instructors, or SKUs. Course mapping is `exercise-02` (foundational curriculum) and `exercise-03` (role-based playbook).
- It does not set measurement instruments. Measurement is `exercise-06`.
- It does not commit L&D to delivery. That commitment is `exercise-07`.

The map is the input to all four of those.

---

### End of worked artifact

## 3. Validation steps

Before sharing the map with L&D and the governance partner, run it through this checklist. Reviewers grading this exercise should do the same.

1. **Segment count.** 4–7 segments. Fewer than 4 under-resolves; more than 7 is usually decision-surface drift and should be collapsed.
2. **Segment boundary test.** For each segment, write the one-sentence "decision surface" that defines it. If two segments have the same decision-surface sentence, merge them.
3. **Dimension count.** Exactly 5 dimensions (risk, tool, prompt, output, escalation), each independently scored. Collapsing to a single "AI fluency level" is the fail state from the lesson's level-1/2/3 critique.
4. **Rubric is behavioral.** Each level is defined as an observable action. "Understands AI" is not a level.
5. **Target levels are not uniform across the row.** If any segment has the same level in all 5 dimensions, challenge it — real segments have shape (e.g., S5 risk=3, tool=1 is a shape).
6. **S5 (largest segment) has the shape you want to defend.** The common failure mode is pushing S5 to Level 2 across all dimensions "because it is most of the company"; that spends the training budget on the wrong fluency.
7. **S6 (executives) has at least one 0 by design.** If every dimension is ≥1, you have likely confused executive-reporting fluency with user fluency.
8. **Ramp exists.** +90d and +180d are explicit; the map is not a static year-end picture.
9. **Rationale per segment is one paragraph, naming the segment's decision surface.** Not a list of courses.
10. **`<!-- to-verify: ... -->` on headcounts.** Those are planning estimates until People/HR confirms.

Markdown lint the artifact before sharing.

## 4. Rubric or review checklist

Scored out of 100. ≥ 85 passes; R3/R4/R5/R7 fails are launch-gate equivalents.

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | 4–7 segments defined | 5 | <4 or >7. |
| R2 | Each segment has a one-sentence decision-surface definition | 10 | Segments described by HR tree only. |
| R3 | Five fluency dimensions present, independently scored | 15 | Collapsed to single score. |
| R4 | Rubric levels are behavioral, not credential-based | 10 | "Completed e-learning" used as a level. |
| R5 | Target-level matrix populated for every segment × dimension cell | 10 | Any cell blank. |
| R6 | At least one segment has a non-uniform row (shape) | 10 | All rows uniform. |
| R7 | S5-equivalent (largest segment) prioritizes risk + escalation over tool/prompt | 10 | S5 pushed to Level 2 across all dimensions. |
| R8 | S6-equivalent (executives) explicitly deprioritizes tool/prompt | 5 | Execs assigned Level 2+ on tool operation. |
| R9 | 90-day / 180-day / 365-day ramp present | 10 | Only a year-end target. |
| R10 | Per-segment rationale names the decision surface | 10 | Rationale lists courses instead. |
| R11 | Unknown headcounts marked with `<!-- to-verify: ... -->` | 3 | Invented or implied-authoritative numbers. |
| R12 | Map explicitly says what it does NOT commit (no courses, no cadence, no L&D sign-off) | 2 | Map treated as a delivery plan. |

## 5. Common mistakes

- **Drawing segments by HR hierarchy.** Produces 11 segments that duplicate the same decision surface. Collapse by what the segment has to decide about AI.
- **Collapsing to a single fluency level.** "Level 1/2/3 across the company" is the straw target the module explicitly rejects. Keep the five dimensions.
- **Making every segment Level 2+ everywhere.** Equal-opportunity literacy is the most expensive and least effective shape. Real maps have holes on purpose.
- **Treating executives as a "needs more training" segment.** Their fluency is governance-reading fluency, not tool-use fluency. Mis-scoping here poisons the whole program.
- **Course names in the rationale column.** The map is role-and-outcome. Course names belong in `exercise-02` and `exercise-03`.
- **Static year-end target with no ramp.** The 90-/180-day structure is what the champion network and cadence plan key off; without it, `exercise-05` has no anchor.
- **Inventing headcounts.** Every org has a real census. Flag with `<!-- to-verify: ... -->` until People/HR confirms; do not publish the map with placeholder numbers that look authoritative.
- **Shipping the map to employees.** It is a planning artifact. Published, it reads as "you are a Level 1" — which is demeaning and does not change behavior.

## 6. Stretch — framing memo to L&D and governance partner

**Audience:** `head-of-learning-and-development` and `head-of-ai-governance`. CC: segment champions.

**Length:** one page.

> **Subject:** Fluency target map v0.1 for the coding-assistant rollout
>
> Attached is v0.1 of the fluency target map for the 12-month rollout window. It is a planning artifact, not a published document. Three decisions I need from you in the next two weeks:
>
> 1. **Segment boundaries.** Do you agree with the six segments drawn by decision surface rather than HR tree? Specifically, I have combined operations and retail into one segment (S5) on the basis that both decide the same data-class questions. I expect pushback and want it before `exercise-02` keys off this segmentation.
> 2. **S5 shape.** I have deliberately held S5 at Level 1 on tool operation, prompt craft, and output evaluation while pushing risk and escalation to Level 3. This is the largest segment; the budget implication is real. If you want S5 at Level 2 across the board, I need the extra training budget committed before `exercise-05` publishes a cadence.
> 3. **S6 ceiling.** Executives are explicitly Level 0 on tool and prompt. If the CEO expects to be trained on the tool, this is the wrong map. Please confirm or push back.
>
> I expect the +90d ramp to be the most heavily redlined because it determines what has to be ready by GA minus two weeks. The map does **not** yet assign courses, instructors, or a cadence — those come in `exercise-02`, `exercise-03`, and `exercise-05`, each of which treats this map as input.

## 7. References

- **Learning material (local to module):**
  - [Exercise brief — `exercise-01-audience-segmentation-and-fluency-target-map.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-104-training-programs-and-ai-literacy-curriculum/exercises/exercise-01-audience-segmentation-and-fluency-target-map.md)
  - Companion exercises in this module (build on this artifact): `exercise-02-foundational-ai-literacy-curriculum-outline`, `exercise-03-role-based-playbook-for-one-function`, `exercise-05-workshop-and-office-hours-cadence-plan`, `exercise-06-fluency-growth-measurement-drill`, `exercise-07-l-and-d-partnership-contract`.
  - Cross-module: `mod-102 exercise-03` (executive rollout report — anchors S6 fluency), `mod-103 exercise-01` (AUP — anchors S1–S5 risk dimension), `mod-103 exercise-02` (data-handling SOP — anchors escalation dimension).
- **Official standards and frameworks:**
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — GOVERN function (roles and responsibilities) and MAP function (context, intended users) are the scaffolding for segmentation.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — the output-evaluation dimension draws on recognizing prompt-injection, data-leakage, and hallucination patterns.
  - [MITRE ATLAS](https://atlas.mitre.org/) — adversary technique context that informs what "Level 3 output evaluation" means for S1/S2.
