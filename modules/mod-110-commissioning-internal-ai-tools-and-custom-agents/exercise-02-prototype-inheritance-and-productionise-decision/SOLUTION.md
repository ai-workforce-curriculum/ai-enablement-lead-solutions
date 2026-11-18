# Exercise 02 — Prototype Inheritance and Productionise Decision — Reference Solution

> Module: `mod-110-commissioning-internal-ai-tools-and-custom-agents`
> Exercise type: design / worked example
> Exercise brief: [`lessons/mod-110-commissioning-internal-ai-tools-and-custom-agents/exercises/exercise-02-prototype-inheritance-and-productionise-decision.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-110-commissioning-internal-ai-tools-and-custom-agents/exercises/exercise-02-prototype-inheritance-and-productionise-decision.md) (in the learning repo)

## 1. Solution overview

The deliverable is a **decision artifact**: a short written review of a bottom-up prototype (a notebook, a user-authored agent, a vibe-coded script, a self-hosted GPT) that reaches one of four verdicts — **Inherit as-is**, **Productionise**, **Rebuild**, or **Sunset** — and names the posture under which that verdict was reached. The decision is a judgement call; the artifact is what makes the call reviewable, repeatable, and reversible.

This exercise matters because the single highest-volume commissioning path is not a top-down brief — it is a bottom-up artifact that already has users. Someone in Finance built a reconciliation helper. Someone in Marketing wired an agent into a shared drive. Someone in Engineering shipped an internal copilot inside a Slack bot. These are not hypotheticals to be stopped; they are the *existence proof* that the capability has user demand. The Enablement Lead's job is to decide which to inherit, which to rebuild, which to sunset, and to do so without either (a) shutting down grassroots innovation, or (b) adopting a trail of obligations the Enablement function cannot uphold.

Posture checks this solution encodes:

- **Every prototype is reviewed against a fixed dimensions set.** Case-by-case judgement is fine; case-by-case *criteria* is how inconsistency becomes policy.
- **The four verdicts are exclusive and exhaustive.** A verdict of "let's revisit" is not a verdict — it is a scheduling decision.
- **Each verdict carries pre-committed obligations.** "Inherit as-is" is not a free action; it adds a row to the Enablement function's inventory.
- **Author willingness and skill are first-class dimensions.** Inheriting a prototype away from its author rarely works; productionising a prototype with its author rarely works at the same cost as the original author assumed.
- **Data-handling posture and risk sources are named.** `owasp-ml-top-10`, `mitre-atlas`, and `nist-ai-rmf` frame the risk read, so the verdict is reviewable by Security and the governance council.
- **The decision is reversible.** A verdict is not a signing ceremony; a trigger list names when the decision is revisited.

## 2. Implementation — worked answer

### 2.1 Decision dimensions

The ten dimensions below are the fixed set. A review that skips a dimension declares it explicitly ("not applicable because …"); it does not quietly drop it.

| # | Dimension | Signal (low) | Signal (high) | Why this dimension |
|---|---|---|---|---|
| D1 | **User demand — number of active users** | 1 (just the author) | 10+ across multiple teams | Demand validates the problem; demand without an author (D9) is a maintenance bomb. |
| D2 | **User demand — frequency and criticality** | Occasional, reversible decisions | Daily, revenue- or safety-impacting | The downside of mis-adoption scales with frequency × blast radius. |
| D3 | **Data-sensitivity exposure** | Public / internal only | Confidential, PII, or regulated | Confidential data in a vibe-coded prototype is a governance debt, not a feature. |
| D4 | **Reversibility of outputs** | Advisory; human-in-the-loop | Autonomous action against production systems | Autonomous prototypes carry rollback risk per mod-109. |
| D5 | **Dependency on production systems** | None (one-way read) | Write-back to production of record | Write-back dependencies turn a prototype into a system of record. |
| D6 | **Author skill — engineering / ML engineering** | Spreadsheet-driven | Production-grade engineering background | Determines feasibility of productionising *with* the author vs. rebuilding. |
| D7 | **Author willingness to maintain** | None stated | Explicit, time-boxed, written | A prototype without a committed author is a prototype the Enablement function is about to own. |
| D8 | **Security posture gap** | No gap identified | Secrets in source; no authn/z; no audit log | Each specific gap has a specific remediation cost. |
| D9 | **Observability gap** | Structured logging present | No logging, no eval harness, no drift monitor | Every gap is a line in the handoff contract or a kill criterion. |
| D10 | **Scale projection** | Flat or declining usage | Explosive growth; cross-BU pull | Scale projection drives the Buy / Build / Buy-plus-glue arm of the mod-107 Exercise 03 matrix. |

### 2.2 The four verdicts and their obligations

Each verdict is named along with the obligations it adds to the Enablement function's inventory. Every verdict is a commitment.

- **Inherit as-is.** The prototype joins the Enablement-sanctioned inventory under a lightweight *steward-of-record* arrangement — the author remains the technical steward, Enablement adds a row to the inventory, a lightweight SOP note is co-authored (per mod-103), and the measurement plan from Exercise 04 is instantiated at a minimum viable grain (presence of logs, presence of a quarterly review cadence). *Obligation added:* inventory row, SOP note, quarterly review. *Pre-conditions:* D3 ≤ Internal, D4 = advisory, D5 = none or read-only, D7 = written and time-boxed, D8 = no identified gaps, D9 = basic logging present.
- **Productionise.** The prototype is taken into the commissioning track as the starting artifact for an engagement with Applied AI Engineering. The brief (Exercise 01) is written against the prototype, the handoff contract (Exercise 03) governs the transfer, and the measurement plan (Exercise 04) is scoped at full grain. The prototype author is explicitly engaged as a consulted collaborator (C on the DACI, per Exercise 01 Section 5) but is not the Driver on implementation. *Obligation added:* a full commissioning engagement budget and headcount allocation. *Pre-conditions:* D1 ≥ 3 active users, D2 shows real stakes, D10 shows sustained demand, and either D3 or D4 or D5 is high enough to warrant the governance uplift.
- **Rebuild.** The prototype's *idea* is the input to the commissioning engagement, but the artifact itself is discarded. This verdict applies when D6 (author skill) or D8 (security posture gap) make the prototype uneconomic to productionise — the cost to remediate exceeds the cost to rebuild on a sanctioned platform. The prototype is explicitly deprecated at the same moment the rebuild starts; if the two overlap uncontrolled, users split and neither artifact wins. *Obligation added:* a full commissioning engagement **plus** a sunset plan for the original prototype on a named date. *Pre-conditions:* same as Productionise, plus D6 or D8 argues against carrying the original artifact forward.
- **Sunset.** The prototype is retired. This verdict applies when D1 and D2 are low (few users, low stakes) and D3 or D8 are high enough that the governance cost is not worth the user value, OR when D10 shows the demand is narrower than the governance uplift can justify. The author is informed in writing with a named effective date and a named alternative (either an existing sanctioned tool that covers the use case, or none — and that fact is said out loud). *Obligation added:* a one-line inventory note recording the retirement so the next bottom-up prototype addressing the same problem is seen in context. *Pre-conditions:* the user-value delta is below the governance uplift required to retain the prototype in any form.

### 2.3 Worked example — three prototypes, three verdicts

Three prototypes arrive in the same month. The decision artifact below walks through each.

#### Prototype P-01 — "Finance reconciliation helper"

A Finance analyst built a notebook that drafts the first-pass reconciliation narrative between two internal reports. Shared informally with four peers in Finance.

| Dimension | Reading | Notes |
|---|---|---|
| D1 Users | 5 | Author + 4 peers in Finance. |
| D2 Frequency × criticality | Weekly, low stakes | Draft only; the human reviews before sign-off. |
| D3 Data sensitivity | Internal | Report extracts are already Internal-classified. <!-- org-specific: verify classification --> |
| D4 Reversibility | Advisory | Author pastes the draft into the review memo; no autonomous action. |
| D5 Production dependency | Read-only | Reads report CSVs from a shared drive. |
| D6 Author skill | Spreadsheet-driven | Analyst, not engineer. |
| D7 Author willingness | Written, open-ended | Author states willingness to maintain for ≥ 12 months. |
| D8 Security posture gap | One gap | API key in a `.env` file checked into a local repo. |
| D9 Observability gap | Moderate | No eval harness; manual spot-check only. |
| D10 Scale projection | Flat | Finance team of ~12; low cross-BU pull. |

**Verdict: Inherit as-is, after D8 remediation.** The prototype is low-stakes, advisory, read-only, and has a committed author. The one identified gap (D8) is remediated in a week by rotating the credential and moving it into the sanctioned secret store. After remediation, P-01 joins the inventory as a steward-of-record entry. SOP note is co-authored with Finance per mod-103. Quarterly review tied to the mod-106 scorecard.

#### Prototype P-02 — "Customer-support reply drafter"

A support manager built an in-console helper that drafts first-reply emails for billing disputes. Used by ~30 agents daily.

| Dimension | Reading | Notes |
|---|---|---|
| D1 Users | ~30 | Across one BU. |
| D2 Frequency × criticality | Daily, customer-facing stakes | Replies reach customers — do-no-harm matters. |
| D3 Data sensitivity | Confidential | Account PII and billing details. |
| D4 Reversibility | Mostly advisory but some agents send verbatim | De-facto autonomous for the verbatim-send cases. |
| D5 Production dependency | Read + write | Reads CRM, writes draft into CRM ticket. |
| D6 Author skill | Moderate | The manager is engineering-adjacent; not an Applied AI Engineer. |
| D7 Author willingness | Partial | Author is willing to maintain but is also doing the day job. |
| D8 Security posture gap | Several | Shared service account; no per-user audit; no retention control on prompts/completions. |
| D9 Observability gap | High | No eval harness; no drift monitor; no incident route. |
| D10 Scale projection | Growing | Interest from a second BU. |

**Verdict: Productionise.** This is the Exercise 01 worked scenario in a different wrapper. The idea is validated (D1, D2, D10); the stakes are high (D3, D4, D5); the gaps (D8, D9) are addressable through a commissioning engagement; the author (D6, D7) joins the engagement as Consulted. A brief is written per Exercise 01, handoff contract per Exercise 03, measurement plan per Exercise 04. The existing prototype is sanctioned to continue running during the commissioning window with a named end-of-life date at the general-availability gate or at the kill-criteria trigger — whichever comes first.

#### Prototype P-03 — "Policy chat bot"

A tech-adjacent individual contributor wrapped the company HR policy PDF in a chat agent and shared the URL internally. Used by ~12 people over a two-week burst.

| Dimension | Reading | Notes |
|---|---|---|
| D1 Users | ~12 | Burst usage; tail off quickly. |
| D2 Frequency × criticality | Occasional, HR-adjacent stakes | Policy questions — risk of confidently-wrong answers on compliance-adjacent topics. |
| D3 Data sensitivity | Confidential | HR policy includes handling of restricted conduct topics. |
| D4 Reversibility | Advisory | But confidently-wrong outputs have real downside in this domain. |
| D5 Production dependency | None | Standalone. |
| D6 Author skill | High | Senior engineer. |
| D7 Author willingness | None stated | Author described it as a weekend experiment. |
| D8 Security posture gap | Several | Public-cloud inference provider not on the AUP-approved list; no authn/z; no audit log. |
| D9 Observability gap | High | No eval harness; no hallucination detection; no incident route. |
| D10 Scale projection | Flat or declining | Burst-driven; interest already fading. |

**Verdict: Sunset.** D1 × D2 × D10 argue against the user-value side; D3 + D8 argue the governance uplift is high; D7 (no maintainer) is the kill. The author is informed with a named effective date (two weeks out, to give the current users a soft landing). The alternative pointed to is the sanctioned HR help-desk workflow <!-- org-specific: confirm there is a sanctioned HR help-desk workflow to point users to; if not, this fact is said out loud in the sunset note -->. A one-line inventory note records the retirement so a future prototype in the same space arrives in context.

### 2.4 The written artifact (`prototype-decision.md`)

```
Prototype Decision — <P-ID> (<prototype short name>)
Author of prototype:     <!-- role / person; "person" is allowed here because this is a review artifact, not a durable org contract -->
Reviewer:                AI Enablement Lead (this role)
Date:                    <!-- date -->
```

1. **Prototype context** — one paragraph: what it does, who built it, how users encountered it, how long it has been in use.
2. **Dimension readings** — the D1–D10 table filled in for this prototype, with `<!-- org-specific: ... -->` tags on numbers that are not instrumented.
3. **Verdict** — one of {Inherit as-is, Productionise, Rebuild, Sunset}. One sentence.
4. **Rationale** — three to five sentences tying the verdict to the dimension readings. Avoid vendor-speak; use the dimension names.
5. **Obligations** — the obligations table for the verdict, filled in (inventory row ID, SOP note cross-reference, measurement-plan grain, named effective date for sunset, etc.).
6. **Author engagement** — how the prototype author is engaged going forward (steward-of-record, consulted on productionising engagement, informed of sunset). Written politely; the prototype demonstrated demand, and the author receives credit for that irrespective of verdict.
7. **Risk read** — a short list of the `owasp-ml-top-10`, `mitre-atlas`, and `nist-ai-rmf` items that drove the risk side of the verdict.
8. **Review trigger** — when the decision is revisited (user-count delta > 50%, new data class added, policy change, etc.).

### 2.5 Decision rationale — why this shape, not another

- **Why four verdicts, not two.** A "productionise or sunset" binary is too coarse and routes all the lightweight, low-stakes grassroots work either into a full commissioning engagement (expensive, kills innovation) or into the sunset pile (loses the user-value signal). Adding *Inherit as-is* and *Rebuild* is what matches the shape of the real distribution.
- **Why fixed dimensions, not open-ended review.** The same prototype reviewed on different weeks by the same Enablement Lead will reach different verdicts under open-ended review; under fixed dimensions it reaches the same one. The fixed dimensions are what make the artifact reviewable by Security and governance without re-litigating the criteria.
- **Why author willingness is a first-class dimension.** The two failure modes of Inherit-as-is — the author quietly stops maintaining, or the author goes on parental leave and nobody remembers — are both prevented by writing willingness down at decision time and committing to a quarterly review.
- **Why Rebuild is a distinct verdict, not a sub-case of Productionise.** The two have different obligations: Productionise carries the prototype forward during the engagement; Rebuild explicitly deprecates it at the same moment the rebuild starts. Collapsing them into one causes the two artifacts to coexist uncontrolled and user traffic to split.
- **Why the risk read cites `owasp-ml-top-10`, `mitre-atlas`, and `nist-ai-rmf` by ID.** Those are the sources Security and governance already use. Naming them is what lets the verdict be reviewed without re-negotiating the threat model.
- **Why review triggers, not just annual review.** A prototype at user-count 5 is different from the same prototype at user-count 50. Annual-only review misses the moment demand crosses the threshold where the earlier verdict should flip.

## 3. Validation steps

1. **The decision artifact is one page** (Sections 1–8 render on a single printable page).
2. **The dimension table is populated for all 10 dimensions.** A skipped dimension is declared explicitly ("D5 n/a — standalone prototype with no production dependency"); it is not quietly omitted.
3. **The verdict is one of the four named verdicts.** "Let's revisit" is not a verdict.
4. **Obligations are specific.** An "Inherit as-is" verdict with no inventory row ID and no quarterly-review commitment is not a verdict; it is a wish.
5. **Author engagement is addressed.** Silence on author engagement loses the user-value signal and demoralises the grassroots innovator.
6. **Risk read cites OWASP ML Top 10, MITRE ATLAS, and NIST AI RMF** by name — not generically.
7. **Review trigger is concrete.** A user-count delta threshold, a data-class change, or a policy change is concrete; "as needed" is not.
8. **`org-specific` tags** on any numbers that are not instrumented in the learner's org (e.g., the "5 active users" number for P-01 is marked if not from instrumentation).
9. **Consistency across prototypes.** The same Enablement Lead reviewing three prototypes on the same day uses the same dimensions in the same order and reaches verdicts whose rationales cite the same signals in the same direction.

## 4. Rubric / review checklist

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | Ten-dimension table populated or dimensions explicitly declared n/a | 20 | Any dimension silently skipped. |
| R2 | Verdict is one of {Inherit as-is, Productionise, Rebuild, Sunset} | 10 | "Revisit" or hedged verdict. |
| R3 | Obligations for the verdict are specific and actionable | 15 | Vague obligations ("add to inventory") or no obligations stated. |
| R4 | Author willingness and skill are called out as first-class dimensions | 10 | Dimensions D6/D7 blank or missing. |
| R5 | Risk read cites `owasp-ml-top-10`, `mitre-atlas`, and `nist-ai-rmf` by name | 10 | Generic risk list, or official sources not named. |
| R6 | Decision is reversible: review trigger named and concrete | 10 | "As needed" or no trigger. |
| R7 | Rationale ties verdict to dimension readings, not to vendor preference | 10 | Vendor-speak rationale. |
| R8 | Author engagement addressed (even for Sunset) | 5 | Silence on author. |
| R9 | `org-specific` tags on uninstrumented signals | 5 | Unmarked quoted numbers. |
| R10 | Consistency across multiple prototypes reviewed in the same cycle | 5 | Same signals produce inconsistent verdicts. |

**Pass threshold:** ≥ 85/100 and no R1 / R3 / R5 fail. R1 (the ten dimensions), R3 (specific obligations), and R5 (named risk sources) are the three discriminators between a decision artifact that holds up under governance review and a decision artifact that reads as personal opinion.

## 5. Common mistakes

- **Treating "Inherit as-is" as a free action.** It adds an inventory row, an SOP note, and a quarterly review cadence. A verdict without obligations is not a decision; it is a shrug.
- **Sunsetting without a named alternative.** Users will route around the sunset if there is no alternative — the prototype will come back under a different name, run by a different author, with the same gaps. If no sanctioned alternative exists, say so, and start the commissioning path for one.
- **Productionising without engaging the author.** The author knows the quirks of the data and the user cohort; discarding that context at productionisation time is one of the classic ways rebuilds end up with different quirks on top of the same problems.
- **Collapsing Rebuild into Productionise.** The two coexisting uncontrolled is the predictable outcome of a Rebuild verdict that forgets to name the sunset date for the original.
- **Open-ended review criteria.** Without fixed dimensions, the same prototype reviewed on different weeks reaches different verdicts, and the artifact stops being reviewable.
- **Skipping the risk read because the prototype "feels low risk."** The risk read is cheap when the risk is genuinely low (a one-line "D3 Internal, D4 advisory, D5 read-only — no `owasp-ml-top-10` items material to this prototype"). Skipping it is what loses the governance partnership next quarter.
- **Confusing D6 (skill) with D7 (willingness).** A skilled author who does not want to maintain is a prototype about to be an Enablement obligation; an unskilled author who is willing to maintain is a prototype about to be a security incident. The two dimensions are not substitutes.
- **Reviewing at too fine a grain.** The artifact is one page, not a design document. If the review requires five pages, the verdict is "Productionise" and the real design work happens under Exercise 01 downstream.
- **Reviewing at too coarse a grain.** A three-line verdict with no dimension readings is not reviewable by governance; it is a personal note.
- **Vendor-speak in the rationale.** "This is a great candidate for our transformation agenda" is a sentence without decision content. Use the dimension names.

### 5.1 Stretch — inventory and dashboarding

Over a quarter, the Enablement function accumulates a stream of these decision artifacts. For a mature program, the stream is rolled into a **prototype inventory dashboard** with four columns — one per verdict — and one row per decision. The dashboard is reviewed at the mod-106 scorecard cadence:

- The **Inherit as-is** column shows the lightweight-steward inventory; each entry has an author, a steward-of-record, and a last-reviewed date.
- The **Productionise** column shows the active commissioning engagements; each entry has a brief ID (per Exercise 01), a gate status, and a next-gate date.
- The **Rebuild** column shows active rebuilds with their original-prototype sunset date.
- The **Sunset** column shows retired prototypes with their effective date and, where applicable, the sanctioned alternative pointed to.

The dashboard's existence is what makes the fifth, sixth, seventh prototype review consistent with the first: patterns emerge from the stream that a single-artifact review cannot see.

## 6. References

- **Learning material (local):**
  - [Exercise 01 — Commissioning Brief Drill](../exercise-01-commissioning-brief-drill/SOLUTION.md) — the brief shape that is produced when the verdict is Productionise or Rebuild.
  - [Exercise 03 — Handoff Contract with Applied AI Engineer](../exercise-03-handoff-contract-with-applied-ai-engineer/SOLUTION.md) — the contract that governs the engineering engagement for Productionise and Rebuild verdicts.
  - [Exercise 04 — Commissioned Tool Measurement Plan](../exercise-04-commissioned-tool-measurement-plan/SOLUTION.md) — the measurement plan instantiated at minimum viable grain for Inherit-as-is and full grain for Productionise / Rebuild.
  - [mod-102 — Selecting and Rolling Out AI Tools](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-102-selecting-and-rolling-out-ai-tools) — the intake disciplines that make the inventory row legible to Procurement and Security.
  - [mod-103 — Policy Co-authoring with Governance](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-103-policy-co-authoring-with-governance) — the SOP co-authoring pattern that attaches to an Inherit-as-is verdict.
  - [mod-106 — Outcome Measurement and Executive Reporting](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-106-outcome-measurement-and-executive-reporting) — the scorecard cadence under which the prototype inventory dashboard is reviewed.
  - [mod-107 — Budget, ROI, and Build-vs-Buy at Org Scope](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-107-budget-roi-and-build-vs-buy-at-org-scope) — Exercise 03's build-vs-buy matrix is the next decision layer once a Productionise verdict is reached.
  - [mod-109 — AI Incident Response and Enablement-Side Rollback](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-109-ai-incident-response-and-enablement-side-rollback) — the incident-severity scale and rollback discipline informing D4 (reversibility) and D8 (security posture).
- **Official standards and frameworks:**
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — threat posture lens for the Section 7 risk read.
  - [MITRE ATLAS](https://atlas.mitre.org/) — adversarial-technique lens alongside OWASP for the risk read.
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — GOVERN and MEASURE functions behind the fixed-dimensions discipline and the review-trigger pattern.
