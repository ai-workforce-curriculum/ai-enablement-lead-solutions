# Exercise 07 — L&D Partnership Contract — Reference Solution

> Module: `mod-104-training-programs-and-ai-literacy-curriculum`
> Exercise type: design artifact (partnership agreement)
> Learning file: [`exercise-07-l-and-d-partnership-contract.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-104-training-programs-and-ai-literacy-curriculum/exercises/exercise-07-l-and-d-partnership-contract.md)

## 1. Solution overview

Everything else in this module assumes the Learning & Development function is co-delivering. That assumption is where programs most often fail. L&D has its own calendar, budget, instructional-design standards, LMS, and relationships with managers — none of which this role controls. The **partnership contract** is the written artifact that declares who owns what, when, and how disagreements are resolved, so the program does not hinge on a handshake with one L&D counterpart who may be reorganized next quarter.

The deliverable is a one- to two-page contract, signed by this role and the L&D counterpart, with a RACI, a commitment table, an escalation path, and an explicit list of what is **not** in scope. The worked artifact below carries the ~3,000-person US-regulated bank archetype threaded through this module.

Posture checks:

- **A partnership contract is not an MOU with the vendor and not an OKR doc.** It is a working agreement between two in-house functions that normally do not share work.
- **RACI is single-A per row.** A row with two Accountables is a row without an owner; the contract fails the first time someone needs to decide.
- **Scope-out is as important as scope-in.** The most productive clauses in this document are the ones that say "L&D is not responsible for AI policy content accuracy" and "this role is not responsible for LMS uptime."
- **Cadence of the partnership is itself part of the contract.** A monthly standing meeting with named inputs prevents the drift that sinks most co-delivery.
- **Written in draft-for-redline voice, not managerial voice.** The counterpart will redline before signing; the right drafting posture is Chapter 01 of mod-103 (`the-co-author-posture-and-the-redline-log`).

## Implementation

Apply this solution by walking section 2 in order: Section 1 (what each party brings), Section 2 (RACI), Section 3 (commitments and hard dates), Section 4 (out of scope), Section 5 (escalation path), Section 6 (partnership cadence), and Section 7 (drafter note). Validate against section 3 of this solution, score with the rubric in section 4, review section 5 for RACI-dilution and scope-creep failures, and use section 6 as the amendment-flow and T+365 renewal stretch when the counterpart is ready to co-sign v1.0.

## 2. Worked answer — `l-and-d-partnership-contract.md`

### Partnership Contract — AI Enablement × Learning & Development, v0.1-draft

**Status:** Pre-redline. For reaction, not signature.
**Parties:**
- **AI Enablement Lead** (this role), representing the AI Enablement program across the bank.
- **Head of Learning & Development** (or named delegate), representing the L&D function.
- **Co-signers:** `head-of-ai-governance` (for policy anchoring), `<!-- org-specific: confirm the HR/People signer for cross-function working agreements — likely Head of People Operations or VP HR Business Partners -->`.

**Scope of this contract:**
Covers all learning experiences launched under the AI Enablement program for the 12-month rollout window from `exercise-05`. Includes the foundational curriculum, function playbooks, coaching program, workshop and office-hours cadence, and fluency-growth measurement.

**Review and renewal:**
Reviewed at T+180 days and T+365 days. May be reopened within a cycle by either party on written notice.

---

### Section 1 — What each party brings

**AI Enablement Lead (this role) brings:**

1. **Policy and governance anchoring.** The AUP, SOP, and playbooks (`mod-103 exercise-01/02/03`, `mod-104 exercise-03`) are owned by this role jointly with `head-of-ai-governance`. L&D does not write or alter policy content.
2. **Fluency target map** (`exercise-01`). Segmentation, dimensions, and target levels are set by this role. L&D does not reclassify segments.
3. **Curriculum design authority** (`exercise-02`). Learning objectives, pass criteria, assessments, and segment routing are owned by this role.
4. **Plant library** (`exercise-04`, `exercise-06`). The coaching plants and measurement plants are maintained by this role; new plants are proposed by L&D and approved by this role.
5. **Executive and governance reporting.** The executive rollout report (`mod-102 exercise-03`) and the measurement reports (`exercise-06`) are authored by this role. L&D contributes delivery data, not interpretation.
6. **Content review on every revision.** Any L&D edit to curriculum content that touches policy wording is routed back to this role.

**L&D brings:**

1. **Delivery expertise.** Instructional-design consultation, LMS configuration, SCORM packaging, captioning, accessibility review, localization where required.
2. **Facilitation capacity.** Named facilitators for workshops, office hours after T+90, and measurement-drill facilitation. Facilitator training and QA are an L&D responsibility.
3. **LMS and content infrastructure.** The LMS tenant, authoring tool, video hosting, captioning pipeline, and reporting infrastructure.
4. **Learner communications.** Manager comms, learner reminders, enrollment nudges, completion reporting to HR systems.
5. **Scheduling and logistics.** Room booking, calendar invites, recording distribution, attendance tracking.
6. **Content-standard compliance.** Instructional-design standards, accessibility standards (WCAG `<!-- to-verify: confirm the WCAG version the org commits to (likely WCAG 2.2 AA) -->`), and the L&D style guide. L&D does not override policy content to meet those standards without co-review.

---

### Section 2 — RACI

Single-A per row. Multi-R allowed. C/I generous where they help the work.

| # | Activity | R (do) | A (accountable, 1) | C (consulted) | I (informed) |
|---|---|---|---|---|---|
| 1 | Set fluency target levels per segment | This role | This role | L&D, segment champions | Head of AI Governance, L&D Head |
| 2 | Write policy content in modules | This role | This role | Head of AI Governance | L&D |
| 3 | Instructional-design review of modules | L&D | L&D | This role | Head of AI Governance |
| 4 | LMS packaging, captioning, accessibility | L&D | L&D | This role on accuracy only | — |
| 5 | Deliver office hours (T+0 to T+90) | This role, champion cohort | This role | L&D | Head of AI Governance |
| 6 | Deliver office hours (T+90 onward) | Champion cohort, L&D facilitators | L&D | This role | Head of AI Governance |
| 7 | Deliver workshops | This role + Head of AI Governance (as content), L&D (as delivery) | This role | L&D | Head of AI Governance |
| 8 | Run coaching (T+0 to T+60) | This role | This role | L&D | — |
| 9 | Run coaching (T+60 onward) | Trained champions | This role for program; L&D for facilitator quality | L&D | — |
| 10 | Train facilitators and champion coaches | This role (content), L&D (adult-learning craft) | Joint; see escalation | L&D Head | Head of AI Governance |
| 11 | Facilitate measurement drills | L&D facilitators | L&D | This role on scoring | Head of AI Governance |
| 12 | Score measurement drills | L&D facilitators | This role (scoring rubric) | L&D Head | Head of AI Governance |
| 13 | Author measurement report | This role | This role | L&D | Head of AI Governance, Exec Sponsor |
| 14 | Author exec rollout report | This role | This role | L&D for delivery data, Head of AI Governance for policy | Exec Sponsor |
| 15 | Manager communications and enrollment | L&D | L&D | This role for content | HRBPs |
| 16 | Trigger refresher content on AUP revision | This role | This role | L&D, Head of AI Governance | All in-scope managers |
| 17 | Decide to pause the program (reversal) | Exec Sponsor + Head of AI Governance | Exec Sponsor | This role, L&D Head | Board or risk committee as policy requires |

Row 10 has a **joint Accountable** which is explicitly flagged as the row most likely to deadlock. See Section 5 escalation path.

---

### Section 3 — Commitments (the hard dates)

**Pre-GA (T-30 to T-0).**

- This role delivers the Core curriculum content to L&D by T-30.
- L&D completes instructional-design review by T-21.
- L&D completes LMS packaging and accessibility review by T-14.
- Joint dry-run with segment champions by T-7.
- Go/no-go signal from L&D to this role by T-3; from this role to Exec Sponsor by T-3.

**T+0 to T+90.**

- L&D runs manager comms per segment on a fixed Monday schedule starting T+7.
- This role delivers the first +90d measurement drill content to L&D by T+60.
- L&D facilitates the +90d drill against sampled S4 cohort in T+85 to T+90 window.

**T+90 to T+180.**

- Facilitator-training cohort completes in T+90 to T+120 window; this role and L&D co-certify facilitators.
- Champion coach cadre certified by T+150.
- +180d measurement drill facilitated T+170 to T+180.

**T+180 to T+365.**

- Steady-state cadence per `exercise-05`.
- Partnership contract review at T+180 (minor revision window) and T+365 (renewal).

**On trigger (any time).**

- AUP revision touching Sections 2/3/4 of `mod-103 exercise-01` → this role ships refresher content within 10 business days; L&D distributes within 5 business days of receipt.
- Accident-path event per `mod-103 exercise-02` → this role drafts a 10-minute refresher within 72 hours; L&D distributes within 72 hours of receipt.

---

### Section 4 — Out of scope

Explicitly **not** covered by this contract:

- **Compliance training.** The bank's existing mandatory compliance curriculum is not merged into the AI literacy program. The two coexist; employees may complete both.
- **Vendor-procurement training.** Tool selection and procurement training is `mod-102` territory, delivered to a smaller leadership audience.
- **Role-based playbooks for every function.** This contract covers the foundational curriculum plus one function playbook at a time, per `exercise-03`. Expansion to additional functions reopens the contract.
- **Executive briefings.** The executive rollout report (`mod-102 exercise-03`) is authored by this role and is not an L&D deliverable.
- **Incident response coordination.** Belongs to the Security and Incident Response functions; L&D supports with training content on request, not with response operations.
- **Content for AI tools other than the one coding assistant.** Each additional tool reopens this contract and triggers a scope amendment.

---

### Section 5 — Escalation path

- **First level:** named L&D delegate and this role. Monthly standing meeting (Section 6).
- **Second level:** L&D Head and this role. Triggered on any RACI Row 10 dispute, any +90d/+180d delivery slip, or any dispute on scoring rubric authority.
- **Third level:** `head-of-ai-governance` + L&D Head + this role. Triggered on policy-content conflicts or on decisions to pause / reverse the program.
- **Final:** Exec Sponsor + `head-of-ai-governance`. Program-reversal decisions per Row 17.

Escalation time budget: first level resolves in ≤ 5 business days; second in ≤ 10; third in ≤ 15. If the time budget is exceeded, the matter escalates automatically.

---

### Section 6 — Partnership cadence (meta-meetings)

- **Monthly standing meeting** between this role, L&D delegate, and `head-of-ai-governance`. Thirty minutes. Inputs: field-channel signal, measurement deltas (`exercise-06`), cadence calendar for the next month (`exercise-05`), any RACI deadlocks. Outputs: next-month cadence sign-off and any contract amendments.
- **Quarterly review** (added to the monthly in that month). Review `exercise-06` rollup, the contract itself, and the executive rollout report.
- **Annual renewal** at T+365. Either party may propose a redraft; the default is renewal with the minor revisions logged during the year.

---

### Section 7 — Appended drafter note

I expect the L&D Head to redline **Row 2 (policy content ownership)** and **Row 12 (scoring)** most heavily. Row 2 is the line that prevents L&D from editing the AUP content inside modules to fit their content standard; Row 12 is where L&D will want scoring authority to sit with facilitators rather than with a scoring rubric authored by this role. I propose we keep Row 2 as drafted and are willing to move Row 12 to a joint-A model if the facilitator-training commitment in Row 10 is tightened in exchange.

---

### End of worked contract

## 3. Validation steps

1. **Single-A per row** across the RACI, with the one named exception (Row 10) flagged.
2. **Each party's "what they bring" list has at least five items,** not one or two.
3. **Commitments carry dates relative to GA,** not aspirational phrasing. Grep for "by T-" or "by T+".
4. **Out-of-scope section lists at least four exclusions.** Scope-in without scope-out is where this role gets volunteered into work L&D cannot own.
5. **Escalation path has four levels with time budgets.** Three or fewer is under-specified.
6. **Monthly meeting, quarterly review, annual renewal** named explicitly with inputs.
7. **References the module exercises by number.** The contract does not stand alone; it anchors into `exercise-01` through `exercise-06`.
8. **Appended note names the two rows expected to be redlined.** Signals the drafter has thought about which parts will move.
9. **`<!-- org-specific: ... -->` on org-specific signers** (HR delegate, WCAG version). `<!-- to-verify: ... -->` on anything that would be a factual claim.
10. **No managerial voice.** The contract reads as a draft-for-redline, not a signed-and-sealed MOU.

Markdown lint before sharing.

## 4. Rubric or review checklist

Scored out of 100. ≥ 85 passes. R2, R4, R5, R7 fails are launch-gate equivalents.

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | Two parties named with delegates + co-signers | 5 | Single-signer. |
| R2 | RACI has single Accountable per row (or flagged joint-A) | 15 | Multiple As throughout. |
| R3 | At least 15 RACI rows covering all module activities | 10 | <10 rows; misses activities. |
| R4 | "What each party brings" lists 5+ items per party | 10 | One-line descriptions. |
| R5 | Commitments carry dates relative to GA | 15 | Aspirational phrasing only. |
| R6 | Out-of-scope section with ≥ 4 exclusions | 10 | No scope-out. |
| R7 | Escalation path has 4 levels with time budgets | 10 | No time budgets. |
| R8 | Partnership cadence named (monthly / quarterly / annual) | 5 | No cadence. |
| R9 | References module exercises by number | 5 | Standalone doc. |
| R10 | Appended drafter note names ≥ 2 rows expected to be redlined | 5 | No note. |
| R11 | `<!-- org-specific: ... -->` / `<!-- to-verify: ... -->` on unknowns | 5 | Invented specifics. |
| R12 | Draft-for-redline voice, not finalized voice | 5 | Signed-tone draft. |

## 5. Common mistakes

- **Multiple Accountables per RACI row.** The row that is "owned" by both parties will not be owned at all. If joint-A is really required (Row 10 here), flag it and name the escalation.
- **Scope-only, no scope-out.** Without exclusions, the AI Enablement Lead becomes the de facto owner of every learning gap tangentially touching AI. Burnout and L&D's resentment follow.
- **Aspirational commitments without dates.** "We will collaborate on measurement" is not a commitment. "L&D facilitates the +90d drill in T+85 to T+90 window" is.
- **Escalation without time budgets.** Disputes drift. Budgets force a decision.
- **No partnership cadence.** The contract that lives in a shared drive until the next reorg is dead paper. Monthly meetings keep it alive.
- **Writing in finished-document voice.** The L&D counterpart will push back on half the rows; drafting as if signed makes redlining feel like contestation rather than co-authoring.
- **Omitting the exec-sponsor signer for program reversal (Row 17).** The contract that does not say who can pause the program is the contract that cannot pause it.
- **Silence on content ownership.** The row that says "this role writes policy content, L&D does not" is the row that keeps the AUP intact inside the modules. Without it, LMS content standards will slowly erode policy language.
- **Letting L&D own measurement interpretation.** L&D runs facilitation and captures data; this role interprets and reports. Blurring that line produces reports that describe delivery rather than fluency.

## 6. Stretch — contract amendment flow and the T+365 renewal

**Amendment flow during the cycle:**

- Either party proposes an amendment in writing via the monthly standing meeting.
- The amendment is tabled for one cycle (one month) to give both parties time to redline.
- The next monthly meeting is the decision point.
- Amendments that touch policy-content rows (Rows 2, 16) require `head-of-ai-governance` co-sign.
- Amendments that touch program-pause (Row 17) require Exec Sponsor co-sign.

**T+365 renewal:**

- The quarter leading up to T+365 adds a renewal item to each monthly meeting. Agenda:
  - Which RACI rows actually produced friction? Reassign if so.
  - Which commitments were missed? Were they missed because the date was wrong or because the capacity was wrong?
  - Which exclusions should be reopened? (E.g., "we should probably bring the second function playbook in-scope.")
  - Is the escalation path right? Did disputes reach the correct level in the time budget?
- Renewal is **not automatic**. If either party declines to renew, the escalation is to the Exec Sponsor and `head-of-ai-governance` to decide whether the program continues as structured, restructures the partnership, or pauses.

**Signaling to the broader org:**

- The contract itself is not published to employees. A one-paragraph summary ("AI Enablement and L&D co-deliver the AI literacy program. Policy content is owned by AI Enablement; facilitation and LMS are owned by L&D.") is the public-facing artifact.
- Managers ask "who do I go to for X?" The one-paragraph summary plus the `#ai-enablement-help` channel answers 95% of such questions.

## 7. References

- **Learning material (local):**
  - [Exercise brief — `exercise-07-l-and-d-partnership-contract.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-104-training-programs-and-ai-literacy-curriculum/exercises/exercise-07-l-and-d-partnership-contract.md)
  - This module: all six companion exercises (`exercise-01` through `exercise-06`) feed into the RACI and the commitments table.
  - Cross-module: `mod-102 exercise-03` (executive rollout report — authorship row), `mod-103 exercise-01/02` (AUP / SOP — anchors policy-content rows), `mod-105` (champion networks — anchors facilitator cadre), `mod-111` (cross-functional AI CoE operations — long-run owner of partnership patterns).
- **Official standards and frameworks:**
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — GOVERN function (roles, responsibilities, accountability chains) is the backbone of the RACI structure.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — context for the policy-content ownership rows that protect threat-grounded curriculum content from LMS-standard rewrites.
  - [MITRE ATLAS](https://atlas.mitre.org/) — context for the content rows covering S1/S2 deep-dive modules.
