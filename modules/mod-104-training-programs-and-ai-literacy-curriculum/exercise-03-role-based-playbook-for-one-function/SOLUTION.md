# Exercise 03 — Role-Based Playbook for One Function — Reference Solution

> Module: `mod-104-training-programs-and-ai-literacy-curriculum`
> Exercise type: design artifact
> Learning file: [`exercise-03-role-based-playbook-for-one-function.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-104-training-programs-and-ai-literacy-curriculum/exercises/exercise-03-role-based-playbook-for-one-function.md)

## 1. Solution overview

A **role-based playbook** sits one layer below the foundational curriculum (`exercise-02`) and one layer above individual coaching (`exercise-04`). Its job is to take the generic AUP rules and the generic prompt-craft moves and turn them into **the specific prompts, examples, and refusal patterns a single function will use daily**. It is written for one function at a time because what makes a playbook useful — the named workflows, the named repos, the named system of record — is function-specific.

The worked example below builds the playbook for **Risk, Compliance, Legal, and Audit (RCLA)** in the ~3,000-person US bank archetype from `exercise-01`. RCLA is picked because it is the most demanding case: the segment that most frequently reads AI output produced by other segments, and the segment whose Level 1 tool operation + Level 2 output evaluation (from the fluency target map) has to translate into usable guidance.

Posture checks:

- **Function first, tool second.** The playbook is organized by the RCLA workflow — redline a policy, summarize a deposition, cross-check a control mapping — not by the tool's feature list. A playbook organized by "how to use feature X" fails because it reads as a product manual.
- **Approved prompts are paired with their anti-pattern.** Every "do this" has a "not this" twin, labeled. The playbook's job is to prevent the drifted version of the correct prompt.
- **Refusal patterns are named.** The hardest part of a playbook is teaching someone to not use the tool when they otherwise would. Named refusals do that work.
- **The playbook pairs with the AUP but never restates it.** It references AUP sections by number. Restating the AUP in the playbook is the fail state because the two artifacts drift apart.
- **Shipped as a living document.** Version tag; owner; `#ai-enablement-help` channel pointer; cadence for review tied to the AUP cadence.

## Implementation

Apply this solution by walking section 2 in order — sections A through F of the playbook, with the four approved workflows (B) and four named refusals (C) as the load-bearing content. Validate against section 3, score with the rubric in section 4, and use section 5 to catch the recurring playbook failures (organizing by feature, restating the AUP, missing refusals) before co-review with RCLA SMEs and the pilot plan in section 6.

## 2. Worked answer — `rcla-ai-playbook.md`

### Playbook — RCLA function (Risk / Compliance / Legal / Audit), v0.1

**Audience:** RCLA staff at the bank. Approximately `<!-- org-specific: confirm RCLA headcount from People; ~220 is the planning estimate from exercise-01 segment S3 -->` employees.
**Tool in scope:** Copilot-class coding assistant (Enterprise tenant), **and** any text-generation surface the same tenant exposes (chat UI, document assistant).
**Policy anchor:** AUP v0.1 (`mod-103 exercise-01`). Prohibited uses from AUP Section 3 are binding and are **not** reproduced here — they are referenced by number.
**Owner (operational):** this role (AI Enablement Lead) jointly with the `head-of-ai-governance`.
**Field contact:** `#ai-enablement-help` Slack; `ai-governance-analyst` on-call.
**Version cadence:** co-reviewed with every AUP revision.

---

### Section A — What this playbook is for

RCLA staff read AI output that other segments produce (engineers' code suggestions, analysts' summaries, product managers' drafts) and occasionally use the tool directly to redline, summarize, or cross-check. This playbook tells you (a) which of those uses are approved; (b) how to do them in a way that is defensible; (c) when to refuse.

It does **not** tell you how to do your job. It assumes you already know what a credible control mapping looks like, what a privileged document is, what a false-positive sanctions hit is. The tool does not change those judgments; it changes the speed at which you reach them.

---

### Section B — Four approved workflows (with prompts and refusals)

#### Workflow 1 — Summarize an internal policy draft for redline review

**When to use.** You received a policy draft from the business and need to produce a 1-page internal summary for your own redline session.

**Approved prompt skeleton**

```
Context: I am a [compliance analyst] at a US-regulated bank reviewing an internal draft policy.
The draft is below. It is marked INTERNAL and contains no customer data.
Goal: Produce a 1-page summary that lists (1) the draft's purpose in one sentence,
(2) the five obligations it imposes on employees, (3) the three gaps I should
challenge in redline.
Constraints: Do not propose policy language. Do not cite external regulations by name.
Flag anything that reads as a legal conclusion rather than a draft hook.
Format: Numbered list under three headings.

[paste draft text here, with any names or client references scrubbed]
```

- **Why this works.** The "do not propose policy language" constraint keeps the tool in the summary role, not the drafter role. The "do not cite external regulations by name" constraint stops the known failure mode of fabricated citations (OWASP ML Top 10 — output trust). The draft-vs-conclusion ask aligns the summary with RCLA's redline posture.
- **Anti-pattern (do not do this).** "Summarize this draft policy and tell me if it meets GLBA." That is asking the tool to issue a legal conclusion — the exact drift AUP Section 3 is written against, and the drift Chapter 07 of mod-103 (`what-you-route-out`) names explicitly.

#### Workflow 2 — Explain an unfamiliar code suggestion from engineering

**When to use.** An engineering team has flagged a Copilot-generated change for compliance review. You need to understand what the change does to decide whether it crosses an MRM, AML, or sanctions boundary.

**Approved prompt skeleton**

```
Context: I am a [model-risk analyst] reviewing a proposed code change in a non-production repo.
The change is below. The code processes [describe business function in generic terms, no client data].
Goal: Explain in plain language (1) what the change does, (2) which data classes it reads
from and writes to, (3) whether any part of it looks like a decision rule that would
require MRM review before production.
Constraints: Do not propose fixes. Do not speculate about intent. If a portion is
unclear, say "unclear" rather than guess.
Format: Three short paragraphs.

[paste the diff]
```

- **Why this works.** The "do not propose fixes" line keeps you in reviewer stance. "Say unclear rather than guess" is the single most important instruction against hallucination for RCLA use; it maps to OWASP ML Top 10 trust-boundary concerns.
- **Anti-pattern.** "Does this change need MRM review?" You are asking the tool for the governance decision. The tool produces a plausible-sounding yes/no and you now have an artifact that will look authoritative in discovery. Do not do this.

#### Workflow 3 — Draft a control-test narrative from your own evidence

**When to use.** You have the test evidence and need to draft a narrative paragraph for the audit workpaper. The facts are yours; only the prose is being accelerated.

**Approved prompt skeleton**

```
Context: I am an [internal auditor] drafting a control-test narrative.
The test evidence is below. It is drawn from internal control-testing records.
No customer data. No employee names.
Goal: Produce a 2-paragraph narrative that states (1) the control, (2) the test performed,
(3) the result, (4) any exceptions. Use passive voice. Do not conclude on control
effectiveness — I will add that line after review.
Constraints: Every fact in the narrative must appear in the evidence I pasted.
If a fact is not there, do not add it.
Format: Two paragraphs, no headings.

[paste evidence summary]
```

- **Why this works.** "Every fact in the narrative must appear in the evidence I pasted" is the single-line defense against the audit-fabrication failure mode. The "do not conclude" line preserves the auditor's professional judgment as the signing statement.
- **Anti-pattern.** Pasting the evidence and saying "write the workpaper narrative" without the fact-containment constraint. The tool will embellish and the embellishment will look authoritative. Discovery exposure.

#### Workflow 4 — Cross-check a control-to-regulation mapping

**When to use.** Someone has produced a mapping ("this control satisfies this regulatory requirement") and you need to sanity-check it.

**Approved prompt skeleton**

```
Context: I am a [compliance analyst] sanity-checking a control-to-regulation mapping.
The mapping is below.
Goal: For each row, tell me (1) whether the control, as described, could plausibly
satisfy the requirement as described, (2) what a reviewer would ask to see as evidence,
and (3) the three most common ways a mapping like this fails in real audits.
Constraints: Do not restate the regulation. Do not add rows. If you cannot make a
plausibility call from the text, say so.
Format: Table, one row per input row, three columns.

[paste mapping, with internal control IDs if needed]
```

- **Why this works.** The output is review ammunition, not an opinion on compliance. "If you cannot make a plausibility call, say so" is the explicit refusal path for the tool.
- **Anti-pattern.** "Does this mapping meet the requirement?" This is the same legal-conclusion drift as Workflow 1.

---

### Section C — Four named refusals

These are the uses most likely to be requested of RCLA and most likely to be done with the tool. Each is a **refusal** — you decline to use the tool and you say why. The refusal language is drafted so it is reusable across RCLA staff.

1. **"Write me a legal opinion on whether X complies with Y."** Refuse. The tool does not produce legal opinions; counsel does. See AUP Section 3 and `mod-103 Chapter 07` (`what-you-route-out`). Script: "I can summarize the draft and flag issues for redline, but a compliance call stays with us."
2. **"Draft a response to a regulator inquiry."** Refuse. Regulator-facing deliverables are external output and governed by AUP Section 3.4. Script: "Regulator responses are not drafted with the tool. Let me get the internal template and we can work from there."
3. **"Pull the customer file and summarize the dispute."** Refuse. Customer PII is Restricted (AUP Section 4) and the tool is not a document-retrieval system. Script: "The case system is the source of record for customer disputes. I'll pull it there."
4. **"Does this employee's chat log suggest they violated policy?"** Refuse. Employment decisions are prohibited per AUP Section 3.5. Script: "Employment judgments do not route through the tool. Please pick that up with HR Investigations and counsel."

---

### Section D — When to escalate instead of ask

- **The prompt you wanted to run would include customer PII or non-public financial data.** Do not strip and try again — route via `#ai-enablement-help` so the pattern gets captured. (The `<!-- to-verify: confirm the Slack channel name for the target org -->` is the governance signal we need.)
- **The output you got contains a plausible-sounding citation and you cannot verify it.** Treat as a hallucination (OWASP ML Top 10 — output trust). Do not use the output. Report to `#ai-enablement-help` with the prompt and output so the pattern is logged.
- **The tool's response contradicts a known control, regulation, or internal policy.** Escalate to the policy owner. Do not paper over it.
- **You suspect customer data was in a prompt that was already sent.** Follow the accident path from `mod-103 exercise-02` SOP. Do not delete the prompt.

---

### Section E — What success looks like for this playbook

By +90 days post-GA:

- Every RCLA staff member has run at least one Workflow 1 or Workflow 2 prompt and submitted the before/after for champion review.
- At least three refusals from Section C have been logged in `#ai-enablement-help` — evidence that the refusal behavior is being used, not that nothing is being asked.
- Zero audit findings trace back to AI-produced text used without the fact-containment constraint.
- Measured pass rate on the `exercise-02` Module 5 escalation drill ≥ 90% for RCLA segment.

---

### Section F — Versioning and ownership

- **Version:** v0.1 (first draft, pre-GA).
- **Owner:** this role, with RCLA section owner `<!-- org-specific: confirm the senior-most RCLA stakeholder who will co-sign the playbook (likely Chief Compliance Officer or General Counsel delegate) -->`.
- **Co-review:** on every AUP revision (minimum biannual).
- **Mid-cycle triggers:** any regulator guidance update on AI in regulated financial services, any Section C refusal that fires 3+ times in a month (indicates a gap in the foundational curriculum), any audit finding naming AI output.

---

### End of worked playbook

## 3. Validation steps

1. **Function scope is one function.** Playbook names its function in the title and does not drift into other functions. "RCLA and engineering combined" is the fail state.
2. **4–6 approved workflows.** Fewer is not useful; more becomes a reference text nobody reads.
3. **Every workflow has (a) when-to-use, (b) approved prompt skeleton, (c) why-this-works, (d) labeled anti-pattern.** All four. An anti-pattern-less workflow is the common gap.
4. **At least 3 named refusals.** Each with a reusable script line. Script lines matter; "escalate" without wording is not a refusal pattern.
5. **Refusals cite AUP sections by number, do not restate them.** Grep for prohibited-use text inside the playbook; it should not be there.
6. **Escalation section names channels, not people.** Role names and channel handles, not individuals.
7. **At least one workflow explicitly cites OWASP ML Top 10 or MITRE ATLAS** as the reason a constraint is in the prompt. If none do, the playbook has drifted from threat-grounded design.
8. **Success criteria are measurable and tied to `exercise-06`.** Not "RCLA uses the tool more"; instead pass rates, refusal counts, accident traces.
9. **Version tag and co-owner named.** Co-owner is a role, not this role alone.
10. **`<!-- org-specific: ... -->` on org facts** (headcount, senior stakeholder name, Slack channel). `<!-- to-verify: ... -->` on any factual claim that would need verification (e.g., regulator thresholds).

Markdown lint the file before sharing.

## 4. Rubric or review checklist

Scored out of 100. ≥ 85 passes. R2, R3, R4, R5 fails are launch-gate equivalents.

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | One function named and scoped; no drift | 5 | Multiple functions. |
| R2 | 4–6 approved workflows | 10 | <4 or >8. |
| R3 | Each workflow has when / prompt / why / anti-pattern | 15 | Any workflow missing one. |
| R4 | Prompt skeletons include fact-containment or refusal-permission language | 15 | Pure "summarize X" prompts. |
| R5 | ≥ 3 named refusals, each with a reusable script line | 15 | Refusals listed without wording. |
| R6 | Refusals cite AUP by section, not restated | 5 | AUP prohibited uses reprinted. |
| R7 | Escalation names channels, not individuals | 5 | Named people. |
| R8 | ≥ 1 workflow grounded in OWASP ML Top 10 or MITRE ATLAS | 10 | No threat-model grounding. |
| R9 | Success criteria tied to `exercise-06` instruments | 10 | "Adoption" as success. |
| R10 | Version tag + co-owner (role) | 5 | Single-owner, un-versioned. |
| R11 | `<!-- org-specific: ... -->` on org facts, `<!-- to-verify: ... -->` on factual claims | 5 | Invented specifics. |

## 5. Common mistakes

- **Organizing by tool feature rather than by function workflow.** Produces a product manual, not a playbook.
- **Omitting the anti-pattern twin.** The anti-pattern is the thing the playbook exists to prevent. Without it, the examples drift in deployment.
- **Weak refusals.** "Escalate to governance" with no scripted line is not a refusal pattern — RCLA staff will not improvise the wording under pressure.
- **Restating the AUP.** The playbook and the AUP drift; the AUP wins; the playbook now contradicts policy.
- **Measuring success by adoption.** "RCLA used the tool 40 times this week" says nothing about whether the right things were done. Pass rate, refusal count, and accident traceback are the measurable success signals.
- **Choosing engineering as the first playbook.** Tempting because it is the largest tool user. But engineering has its own established review discipline; RCLA or operations is usually the higher-leverage first playbook. Pick deliberately; document the choice in Section A.
- **Over-prompting.** A prompt skeleton with 15 constraints becomes unusable. 3–5 constraints is the working sweet spot.
- **Inventing a specific regulator policy, MRM threshold, or audit standard.** Those are `<!-- to-verify: ... -->` markers. Invention poisons the playbook's credibility with counsel.

## 6. Stretch — RCLA pilot plan and the champion handoff

**Pilot (first 30 days post-playbook publish):**

- 10 volunteer RCLA staff, mixed across Risk / Compliance / Legal / Audit. Each runs at least two Workflow 1 and two Workflow 2 prompts.
- Each pilot user submits before/after prompts for champion review; the champion is an RCLA-embedded person named by the RCLA section owner, not an engineer.
- At day 15 and day 30, this role holds a 30-minute cohort debrief. Goal: identify the one workflow most frequently drifted and the one refusal most frequently avoided.

**Champion handoff:**

- At +60 days, the playbook is handed to the RCLA champion as the operational owner for day-to-day field questions. This role stays the owner of record; the champion owns the inbox.
- The handoff artifact is a 1-page `champion-brief.md` listing the four workflows, the four refusals, the escalation table, and the current review-cycle date.
- Champion success metric at +90 days: at least one playbook update proposed by the champion based on field signal. If no update, the playbook is either perfect (unlikely) or the champion is not yet operating (more likely) — this role re-engages.

**Cross-module hooks:**

- Champion network design: `mod-105-champion-networks-and-change-management`.
- Pilot measurement: `exercise-06-fluency-growth-measurement-drill`.
- L&D co-ownership: `exercise-07-l-and-d-partnership-contract`.

## 7. References

- **Learning material (local):**
  - [Exercise brief — `exercise-03-role-based-playbook-for-one-function.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-104-training-programs-and-ai-literacy-curriculum/exercises/exercise-03-role-based-playbook-for-one-function.md)
  - This module: `exercise-01` (segmentation — selects RCLA segment), `exercise-02` (Core+ builds on this), `exercise-04` (coaching — operationalizes the anti-patterns), `exercise-06` (measurement — reads success criteria), `exercise-07` (L&D — owns delivery).
  - Cross-module: `mod-103 exercise-01` (AUP), `mod-103 exercise-02` (SOP), `mod-103 Chapter 07` (`what-you-route-out`), `mod-105` (champion networks).
- **Official standards and frameworks:**
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — MAP function (intended use and task-specific risks) is the backbone of the per-workflow design.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — anchors the fact-containment and output-trust prompt constraints in Workflows 2 and 3.
  - [MITRE ATLAS](https://atlas.mitre.org/) — technique context for the untrusted-content warnings in Workflow 2.
