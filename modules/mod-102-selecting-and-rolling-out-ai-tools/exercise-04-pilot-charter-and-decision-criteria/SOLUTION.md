# Exercise 04 — Pilot Charter and Decision Criteria — Solution

> Module: `mod-102-selecting-and-rolling-out-ai-tools`
> Exercise type: design / charter template + worked decision criteria
> Exercise brief: `lessons/mod-102-selecting-and-rolling-out-ai-tools/exercises/exercise-04-pilot-charter-and-decision-criteria.md` (in the learning repo)

## 1. Solution overview

A pilot without a written charter is a tool that will never be rolled back, because nobody agreed in advance on what "it didn't work" would look like. The exercise forces the AI Enablement Lead to **pre-commit** to decision criteria before the pilot starts.

This solution supplies:

1. A **pilot charter template** — a single document, short, with mandatory fields.
2. A **filled-in worked example** for an AI coding assistant pilot in one engineering practice area.
3. **Decision-criteria scaffolding** that distinguishes three gate types (hard gates, outcome gates, operational gates) and three outcomes (proceed, hold, roll back) — not a binary go/no-go, which is the classic failure mode.

The charter is the input to exercise-05 (rollout artifact set) and defines the outcome rows that exercise-03's weekly report will fill in each week.

## Implementation

Apply this solution by filling the charter template in section 2 against the specific pilot, pre-committing the gate thresholds and the hold-budget before start, and collecting co-signer signatures on the same version of the document. Validate the finished charter against section 3 and score against the rubric in section 4; section 5 lists the common failure modes the three-gate / three-outcome structure is designed to resist.

## 2. Worked answer

### Pilot charter template

> **Pilot Charter — `[Tool Name]` — v1.0**
>
> **Sponsor:** [exec, named]
> **Pilot owner:** [AI Enablement Lead or delegate, named]
> **Co-signers at pilot start:** Legal · Security · DPO · Engineering leadership · People/HR
> **Dates:** start [YYYY-MM-DD] → end [YYYY-MM-DD] (hard end; extension requires new charter version)
>
> **1. Problem and non-goals**
> Carry forward the problem statement and non-goals from exercise-01. Do not restate; link.
>
> **2. Scope**
> - Teams: [named teams, named counts].
> - Repositories / data / workflows in scope: [named].
> - Explicitly out of scope: [named].
>
> **3. Success definition (outcome, not usage)**
> - Primary outcome metric: [metric, baseline, target, source]. One metric, not three. Taken from exercise-06.
> - Secondary outcome metrics (≤ 2): [metric, baseline, target, source]. Each with the same shape.
> - Non-regressions (things that must *not* get worse): [metric, floor, source]. At least one. Typically a quality or safety metric.
>
> **4. Leading indicators (usage, watched not managed)**
> - Enrollment, activation, suggestions accepted rate, etc. Explicitly labeled "leading, not success."
>
> **5. Decision criteria**
> - **Hard gates (fail = roll back, not hold):** named governance/security/legal conditions.
> - **Outcome gates (fail = hold, then re-decide):** outcome metric thresholds.
> - **Operational gates (fail = hold, then re-decide):** support load, exception rate, incident count.
>
> **6. Decision outcomes at the end of the pilot**
> - **Proceed** to broader rollout if: all hard gates pass + ≥ one primary outcome gate passes + no non-regression floor is breached.
> - **Hold** if: any outcome or operational gate fails but no hard gate fails. A hold triggers a re-decision within [N weeks].
> - **Roll back** if: any hard gate fails. Roll back path is per `mod-109-ai-incident-response-and-enablement-side-rollback`. <!-- to-verify: confirm cross-module reference in the learner's version of the curriculum. -->
>
> **7. Governance cadence**
> - Weekly: executive rollout report (exercise-03).
> - At midpoint: health check with co-signers. Short charter revision allowed; new success thresholds are not.
> - At end: decision meeting. Attendees = co-signers. Decision recorded in writing.
>
> **8. Risks pre-registered**
> - [risk, likelihood/impact classification, mitigation, owner].
> - At least one should map to `owasp-ml-top-10` or `mitre-atlas`.
>
> **9. Rollback contract**
> - What "rolled back" means operationally: [licenses revoked by when, data retained how long, user comms, policy status].
> - Named operator of the rollback: [individual].
> - Rollback should be executable in ≤ [N] business days. <!-- to-verify: confirm this time budget against the vendor contract; do not invent a number. -->
>
> **10. Signatures**
> Sponsor · Pilot owner · Legal · Security · DPO · Engineering lead · People/HR — with dates. All on the same version of this charter.

### Worked example (filled)

> **Pilot Charter — [AI Coding Assistant] — v1.0**
>
> **Sponsor:** CTO. **Pilot owner:** AI Enablement Lead.
> **Dates:** 2026-11-01 → 2026-12-27 (8-week hard end).
>
> **Scope:** platform-infrastructure practice area, 18 engineers, repositories currently tagged `tier-standard` and `tier-internal` only. Out of scope: anything `tier-restricted` or `tier-regulated`; mobile client code; infrastructure-as-code with production credentials.
>
> **Success (outcome):**
> - *Primary:* median change-review cycle time on AI-assisted PRs, taken from SDLC telemetry; baseline from the four weeks before pilot start; target = meaningful improvement vs. baseline as pre-defined in exercise-06. <!-- to-verify: insert the concrete threshold the learner's charter commits to; do not invent one. -->
> - *Secondary:* reviewer-rated code quality on AI-assisted PRs; target ≥ baseline.
> - *Non-regression:* post-merge defect rate on AI-assisted PRs; floor = baseline.
>
> **Leading (usage, watched):** enrollment, activation, suggestions-accepted rate, policy acknowledgments.
>
> **Decision criteria:**
> - *Hard gates:* zero unresolved high-severity security findings at end of pilot; zero DPO-flagged personal-data-in-prompt incidents without a disclosed path to fix; contract clause that prohibits training-on-tenant remains in force.
> - *Outcome gates:* primary outcome metric improved vs. baseline; secondary not worse; non-regression floor not breached.
> - *Operational gates:* exception rate ≤ 3 steady-state at week 8; support load ≤ [threshold]; ≤ [N] onboarding escalations.
>
> **Outcomes:**
> - *Proceed* to extension in a second practice area if all three gate families pass.
> - *Hold* for a 2-week decision re-run if any outcome or operational gate fails.
> - *Roll back* if any hard gate fails.
>
> **Governance cadence:** weekly report → sponsor + co-signers (exercise-03 template). Midpoint check at Week 4. End decision at Week 8.
>
> **Risks (pre-registered, examples):**
> - Prompt injection via repository content triggering off-policy suggestions — maps to `owasp-ml-top-10` category and `mitre-atlas` techniques for LLM-integrated apps. Mitigation: no code suggestions accepted into auth/crypto/access-control paths without second-pair review (per policy §3); detection via logged prompts. Owner: AI Enablement Lead + CISO delegate.
> - Vendor outage during pilot: mitigation = pilot is not on a critical path; fallback = turn the extension off, continue existing workflow. Owner: Engineering lead.
> - User frustration with low-quality suggestions in a particular stack — mitigation = Week-2 coaching session; detection = support channel sentiment and open exception count. Owner: AI Enablement Lead.
>
> **Rollback contract:**
> - Rolled back = SSO entitlement revoked for pilot users within 1 business day; prompt/completion logs retained per contract; comms per the rollout kit; policy marked archived. Operator: AI Enablement Lead; delegate: IT ops lead.
>
> **Signatures:** CTO · AI Enablement Lead · General Counsel · CISO · DPO · VP Engineering · VP People — 2026-11-01.

### Decision-criteria notes (why it is scaffolded this way)

- **Three gate types, not one.** Collapsing everything into "is it successful" hides the difference between "we made a mistake selecting this" (hard gate) and "we may need more time" (outcome/operational gate). The first should roll back immediately; the second should hold.
- **Three outcomes, not two.** Binary go/no-go is a trap because every pilot that is "nearly there" becomes a quiet go. The explicit *hold* option forces a second honest decision.
- **"Hold" has a budget.** The charter pre-commits to a maximum hold duration; a hold that never ends is a drift pattern.
- **Hard gates are written to be inarguable.** "Zero unresolved high-severity findings" is checkable. "Security is comfortable" is not.
- **Non-regression floor.** Without one, the pilot optimizes the headline outcome at the expense of a thing nobody is watching. This is `nist-ai-rmf` Measure in spirit: measure the thing you don't want to lose, not only the thing you want to gain.

## 3. Validation steps

Reading only the learner's charter, a reviewer should answer **yes** to all of:

1. Are start and end dates both present, with a hard end?
2. Is scope stated with named teams, named repos/data/workflows, and named out-of-scope items?
3. Is there exactly one primary outcome metric with a baseline, target, and source?
4. Are usage indicators explicitly labeled "leading" and *not* used as the success definition?
5. Is there at least one non-regression floor?
6. Are hard gates separated from outcome gates separated from operational gates?
7. Are the three outcomes (proceed / hold / roll back) each defined with specific trigger conditions?
8. Is the hold duration bounded (not open-ended)?
9. Does the rollback contract name an operator by individual and describe operational steps?
10. Is at least one risk mapped to `owasp-ml-top-10` or `mitre-atlas`?
11. Are all co-signers named and signing the **same version** of the charter?

## 4. Rubric or review checklist

Scored out of 20. 14+ passes; below 10 is a rework.

| # | Criterion | Max |
|---|---|---|
| 1 | Hard end date present | 1 |
| 2 | Named scope + named out-of-scope | 2 |
| 3 | Single primary outcome metric with baseline/target/source | 2 |
| 4 | Non-regression floor exists | 2 |
| 5 | Usage indicators clearly labeled "leading" | 1 |
| 6 | Three gate types separated | 3 |
| 7 | Three outcomes each with trigger conditions | 3 |
| 8 | Bounded hold duration | 1 |
| 9 | Rollback contract with individual operator + operational steps | 2 |
| 10 | At least one risk mapped to `owasp-ml-top-10` or `mitre-atlas` | 1 |
| 11 | Co-signers named and on the same charter version | 1 |
| 12 | Clear forward link to exercise-03 (report) and exercise-06 (metrics) | 1 |

## 5. Common mistakes

- **No hard end date.** "We'll see how it goes" is not a pilot.
- **Multiple primary outcomes.** Picking "the top 3" is picking none; nobody will roll back when 2 of 3 pass.
- **Usage dressed up as outcome.** "80% weekly active" is not a success definition.
- **Missing non-regression floor.** The pilot "succeeds" and three months later leadership discovers a quality regression nobody was watching.
- **Hard gates that are not hard.** "Legal is happy" is a vibe. Hard gates must be objectively checkable.
- **No bounded hold.** A hold that "continues until further notice" is a default-ship. Bound it.
- **Rollback described as a sentence.** "We'd just turn it off" is not a rollback contract. Name the operator and the steps.
- **Signatures on different versions.** If any co-signer signed a draft, the charter is not signed.

## 6. References

- NIST AI Risk Management Framework (AI RMF 1.0): <https://www.nist.gov/itl/ai-risk-management-framework> — the Measure and Manage functions motivate the gate-structure and non-regression floor.
- OWASP Machine Learning Security Top 10: <https://owasp.org/www-project-machine-learning-security-top-10/> — source material for the hard gates and pre-registered risks.
- MITRE ATLAS: <https://atlas.mitre.org/> — technique framing for LLM-integrated-app risks that go into pre-registered risks.
- Local context: `exercise-01` for upstream shortlist + decision; `exercise-03` for the weekly report; `exercise-05` for the broader artifact set; `exercise-06` for the outcome metric. Cross-module: `mod-109-ai-incident-response-and-enablement-side-rollback` for the rollback mechanics.
