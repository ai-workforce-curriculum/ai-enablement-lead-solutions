# Exercise 04 — Opt-In vs. Mandate Decision Worked Example — Reference Solution

> Learning file: [`exercise-04-opt-in-vs-mandate-decision-worked-example.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-105-champion-networks-and-change-management/exercises/exercise-04-opt-in-vs-mandate-decision-worked-example.md)

## 1. Solution overview

Two artifacts: a **decision framework** (the axes and the thresholds that force the call) and a **worked recommendation memo** carrying the mod-103 archetype — a coding-assistant rollout at a ~3,000-person US bank — through the framework to a concrete recommendation (opt-in at pilot, opt-out at GA, mandate for a narrow slice at T+12mo).

Posture checks the solution encodes:

- **Three postures, not two.** The call is not a binary. The useful axis is **opt-in → opt-out → mandate**, and the decision for most AI rollouts is which of the three applies to which population at which phase. A binary opt-in-vs-mandate frame hides the opt-out path, which is where most enterprise rollouts actually live by month 6.
- **The decision is per cohort × phase, not organization-wide.** New-hire onboarding may be a mandate while the identical workflow is opt-out for tenured staff. A single posture across all cohorts is nearly always wrong.
- **The framework is six factors, not a vibes check.** Regulatory posture, change-management maturity, existing fluency distribution, fluency-floor risk, union/works-council exposure, and compensation-alignment effect are the six. Each produces a direction; the call is the vector sum, with any single veto-factor overriding.
- **Veto factors are explicit.** A union/works-council surface that requires consultation, a regulator surface that requires attestation of voluntary use, or a compensation-alignment effect that would convert tool-use into a performance metric — any of the three overrides the vector sum and pushes to opt-in.
- **The reversibility ladder is written down.** Posture changes in only one direction without a documented reset: opt-in → opt-out → mandate. Rolling a mandate back to opt-in after six months is possible but is a change-management event, not a quiet config flip. The memo pre-authors the trigger that would force a rollback.

## 2. Implementation — worked answer

### 2.1 Deliverable A — `opt-in-mandate-framework.md`

#### The three postures

| Posture | Default state | Operator action to use | Operator action to not use | Typical phase |
|---|---|---|---|---|
| **Opt-in** | Tool access requires an explicit request by the operator (or an explicit grant by their manager). | Request access and complete onboarding gates. | No action; the default is "not using." | Pilot; populations with veto-factor exposure. |
| **Opt-out** | Operators in scope have access by default; they may choose not to use the tool and face no consequence. | Open the tool. | Continue not opening it. | Post-pilot GA for most enterprise rollouts. |
| **Mandate** | Operators in scope are required to use the tool for a defined workflow set. Non-use is a documented exception. | Use for the named workflow set. | File a documented exception. | Narrow, high-value workflows with low fluency-floor risk; post-maturity. |

#### The six-factor framework

Each factor produces one of three signals — `→ opt-in`, `→ opt-out`, `→ mandate` — or a veto that overrides the vector sum.

| # | Factor | How to read it | Output |
|---|---|---|---|
| 1 | **Regulatory posture** | Is the organization operating under a regulatory regime that treats AI-tool use as subject to attestation, documented consent, or model-risk review? (`<!-- org-specific: for banking archetype, this is SR 11-7 MRM, OCC AI guidance, and the EU AI Act Article 4 literacy floor -->`) | High regulatory sensitivity on the affected workflows → opt-in or opt-out. Low regulatory sensitivity → opt-out or mandate. |
| 2 | **Change-management maturity** | Does the organization have a functioning champion network, a working version-note briefing surface, and a scorecard surface operating for ≥ 1 quarter? | Mature → opt-out or mandate. Early → opt-in. |
| 3 | **Existing fluency distribution** | What % of in-scope operators have ≥ basic AI fluency (per mod-104 role-tier definitions)? | High distribution (≥ 70%) → opt-out or mandate. Low distribution (≤ 40%) → opt-in. Middle → opt-out. |
| 4 | **Fluency-floor risk** | If a low-fluency operator uses the tool incorrectly, what is the cost of the worst likely error? | High cost (customer harm, regulatory finding, safety-of-life) → opt-in. Medium → opt-out. Low → mandate (within the workflow set). |
| 5 | **Union / works-council exposure** | Is any population represented by a union or works-council whose agreement requires consultation on new tooling? | Any yes → **veto to opt-in** pending consultation. `<!-- org-specific: works-council surface is standard in EU and often unionized US operations; confirm for the organization and jurisdiction -->` |
| 6 | **Compensation-alignment effect** | Would an opt-out or mandate posture create a de facto expectation that performance is measured in part by tool-use? | Likely yes → **veto to opt-in** until the compensation surface is explicitly decoupled by HR. |

Reading rule: compute the vector sum of factors 1–4. Any veto on 5 or 6 overrides.

#### The reversibility ladder

```
opt-in  →  opt-out  →  mandate       (documented posture-change; comms cadence applies)
mandate →  opt-out  →  opt-in        (requires rollback-event memo and council sign-off)
```

A rollback is not a quiet config flip. It is a scorecard-visible event. The rollback trigger is pre-authored (section 2.2 below).

### 2.2 Deliverable B — `opt-in-mandate-recommendation.md`

```
To:     head-of-engineering-enablement (L55)
Cc:     head-of-ai-governance (L60), sponsor exec
From:   AI Enablement Lead (this role)
Date:   <!-- org-specific: confirm memo date -->
Re:     Opt-in vs. opt-out vs. mandate posture for the coding assistant — phased recommendation
```

#### Recommendation

**Pilot phase (weeks T−12 → T+0): opt-in**, limited to a named 150-operator pilot cohort drawn across all four engineering BUs, with the champion network pre-seeded within the cohort. No non-pilot operators have access.

**Post-pilot GA (T+0 → T+9mo): opt-out** for all in-scope engineers and the four G&A functions in scope. All in-scope operators receive access on launch day; operators may choose not to use the tool and face no consequence. The "do not use" default from AUP Section 5 (if-in-doubt) remains the operator-facing posture when in doubt.

**Post-maturity (T+9mo → T+12mo review): mandate for a narrow workflow set.** The workflow set recommended for mandate is: **new-hire engineering onboarding — tool is used for the "unfamiliar code walk-through" exercise in week 2 of onboarding, per the engineering-onboarding playbook.** No other mandate at T+12mo; the opt-out posture persists for all other workflows.

#### How the framework reads for this organization

| # | Factor | Reading for this rollout | Output |
|---|---|---|---|
| 1 | Regulatory posture | SR 11-7-aligned MRM process applies to any code touching credit, lending, AML, or sanctions decision-paths. AUP Section 3 already prohibits tool use inside the MRM-managed decision path. `<!-- org-specific: confirm the bank's MRM process name -->` | Pilot and GA phases: **opt-out** for the broad population (MRM-managed workflows are already carved out of tool scope by the AUP). |
| 2 | Change-management maturity | At pilot kickoff: no mature cadence; champion network is being recruited in parallel. At T+9mo: champion network has been operating for ≥ 2 quarters; scorecard has published 9 monthly cycles; version-note briefing surface has fired ≥ 4 times. | Pilot: **opt-in**. GA and onward: **opt-out**. Mandate-eligibility unlocks only at T+9mo. |
| 3 | Existing fluency distribution | `<!-- org-specific: confirm the mod-104-defined fluency distribution for the engineering population at this organization; the archetype assumes ~60% basic-or-above fluency at pilot, ~85% at T+9mo -->` | Pilot: **opt-in**. GA: **opt-out**. T+9mo: **opt-out** general / **mandate** for narrow slices. |
| 4 | Fluency-floor risk | High-cost errors exist (code paths that reach production customer-facing output; code that touches regulated decision-paths). Those are already prohibited uses by AUP Section 3. For the remaining workflows, worst-likely error is a reviewed-and-rejected PR or an operator time-loss event. | **opt-out** or **mandate**, depending on workflow. The onboarding "unfamiliar code walk-through" workflow has essentially zero fluency-floor risk (it is a learning exercise with a human reviewer at the end). → mandate for that workflow at T+9mo. |
| 5 | Union / works-council exposure | `<!-- org-specific: confirm whether any US operations populations are represented by a union; confirm whether any non-US operations in scope have works-council obligations — likely to affect EU operations if any -->` For the US-only archetype as scoped by the AUP, no veto triggers. | No veto for US scope. **If EU operations are added to scope**, the mandate decision triggers works-council consultation and defaults to opt-in in those operations pending consultation. |
| 6 | Compensation-alignment effect | Current performance management framework does not include tool-use measures. `<!-- org-specific: confirm with HR that no performance plan references coding-assistant adoption as a metric -->` HR has committed in writing to not introduce such a measure for the first 12 months post-GA. | No veto. If HR changes posture before T+12mo, the mandate recommendation is pulled. |

**Vector sum:** pilot — opt-in. GA — opt-out. T+9mo — opt-out general, mandate for the narrow onboarding workflow. **No veto triggers under the US-only scope**; EU expansion forces re-scoping of factor 5.

#### What each posture looks like operationally

**Pilot (opt-in).** 150 operators across four BUs; access is granted through a managed-request flow, with manager sign-off. Operators complete mod-104 role-tier 1 onboarding before access is granted. Non-pilot operators have no access and no expectation to use.

**GA (opt-out).** All in-scope operators receive access on T+0. The launch announcement names the opt-out posture explicitly: "you have access; you do not have to use the tool." Line managers are briefed (managers digest T−2w) that opting out is a legitimate choice and must not be reflected in performance signalling. Operators who have not opened the tool by T+30 days receive an invitation to a consultation office-hours session — not a nudge to use, a listening check for whether the "do not use" is informed.

**Mandate for narrow workflow (T+9mo).** The engineering-onboarding playbook adds a mandated step: in week 2 of a new engineer's onboarding, they use the coding assistant to walk through an unfamiliar bank-repo codepath, under the guidance of their onboarding buddy. Exceptions are documented (medical, religious, legal) and tracked without naming the individual in aggregate. No other mandate.

#### Pre-authored rollback trigger

The T+9mo mandate rolls back to opt-out automatically if any of the following fire in the first 3 months after mandate activation:

- A documented complaint from a new-hire cohort — via the champion network or the ombuds surface — indicating the mandate is being used in performance evaluation despite the HR commitment.
- An accident-path event (per mod-103 Exercise 02 SOP) attributable to the mandated workflow.
- An audit finding (internal or external) that the mandate creates a documented-consent or documented-use-attestation surface that is not being met.

Rollback is a scorecard-visible event and is briefed to the governance council at the next pre-read cycle.

#### What the memo does *not* decide

- The scope of the mandate beyond the named onboarding workflow. That is a decision for T+12mo review, informed by the rollback-trigger surface and the scorecard outcome signal at that date.
- The EU-expansion posture. Deferred until legal entity scope is confirmed.
- The compensation-alignment surface. Owned by HR; this role carries the signal that any change there changes the posture recommendation.

#### Co-author surface

> Drafter: AI Enablement Lead (this role).
> Ratifier: `head-of-engineering-enablement` (L55).
> Governance signer: `head-of-ai-governance` (L60).
> HR signer: HR partner (compensation) — confirms the no-tool-use-metric commitment for the first 12 months.
> Labor-relations signer: `<!-- org-specific: confirm labor-relations partner role title; typically General Counsel or dedicated LR counsel -->` — confirms factor 5 reading and any works-council implications.
> Sponsor exec sign-off required before the posture change at T+9mo.

---

### End of worked memo

## 3. Validation steps

1. **The framework has three postures, not two.** If the framework is opt-in vs. mandate only, the opt-out middle — where most enterprise rollouts live — is missing and the framework is wrong.
2. **Decisions are per cohort × phase.** The recommendation should name pilot, GA, and post-maturity postures separately. A single organization-wide posture is a fail.
3. **Six factors named explicitly** (regulatory, change-maturity, fluency distribution, fluency-floor risk, union/works-council, compensation-alignment). Any fewer and the framework hides a factor that will surface under pressure.
4. **Veto factors are called out.** Union/works-council and compensation-alignment are the two most common vetoes in enterprise AI rollouts. Missing either produces a mandate recommendation that will be reversed under pressure.
5. **The reversibility ladder is written down.** A mandate without a pre-authored rollback trigger is a one-way ratchet that cannot be defended at the budget review.
6. **The memo names what it does *not* decide.** Scope creep in the posture memo is a signal the drafter did not understand the decision.
7. **"Opt-out" is defined operationally, not aspirationally.** Opt-out means (a) access by default, (b) no performance consequence for not using, (c) line managers briefed on the posture. If any of the three is missing, the posture is a de facto soft mandate.
8. **The mandate scope is narrow and workflow-specific.** "Mandate tool use for all engineers" fails on fluency-floor risk and on compensation-alignment. "Mandate for the onboarding week-2 unfamiliar-code walk-through" passes both.
9. **The compensation-alignment factor is checked with HR in writing.** A verbal commitment from HR is not sufficient; the memo should reference a written commitment.
10. **`<!-- org-specific: ... -->` on regulator names, MRM process name, labor-relations partner role, EU operations scope.** `<!-- org-specific: ... -->` on fluency-distribution numbers and on specific mod-105 chapter claims.

## 4. Rubric / review checklist

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | Framework has three postures (opt-in / opt-out / mandate), not two | 10 | Binary framework |
| R2 | Decisions are per cohort × phase (named pilot, GA, post-maturity) | 10 | Single org-wide posture |
| R3 | ≥ 6 factors named explicitly | 15 | Fewer than 6 or factors without directional output |
| R4 | Veto factors (union/works-council, compensation-alignment) explicit with override behavior | 15 | Missing veto surface |
| R5 | Reversibility ladder stated with rollback as a documented event | 10 | No rollback path, or rollback as quiet config flip |
| R6 | Pre-authored rollback trigger with ≥ 3 named conditions | 10 | No rollback trigger, or trigger without conditions |
| R7 | Opt-out defined operationally (access + no-consequence + manager brief) | 10 | Opt-out as a word only, no operational definition |
| R8 | Mandate scope is narrow (named workflow, not "all engineers") | 10 | Broad mandate without workflow boundary |
| R9 | Compensation-alignment factor backed by a written HR commitment reference | 5 | Verbal commitment or no reference |
| R10 | "What this memo does not decide" section exists with ≥ 2 items | 5 | Scope-creep; memo attempts to decide EU and HR surfaces |
| R11 | `<!-- org-specific: ... -->` on regulator, MRM, LR partner, EU scope; `<!-- org-specific: ... -->` on chapter-specific claims | 5 | Invented facts or unverified numbers |

**Pass threshold:** ≥ 85/100 and no R3/R4/R7/R8 fail.

## 5. Common mistakes

- **Framing as opt-in vs. mandate only.** The middle posture (opt-out with no performance consequence) is where most enterprise rollouts live. A binary frame forces the recommendation into one of two extremes.
- **Single posture for the whole organization.** The onboarding week-2 workflow and the trading-desk reconciliation workflow do not belong in the same posture. Per cohort × phase is the discipline.
- **Mandating adoption as a performance metric.** The fastest way to destroy field-signal credibility is to turn tool-use into a KPI. Operators will adopt the tool minimally, falsely report, and resist the governance surface for the duration of the rollout.
- **Missing the union / works-council veto.** EU works-councils have co-determination surfaces that require consultation on new tooling that affects operator work. A US-centric memo that silently covers EU operations will be reversed.
- **Opt-out that is a soft mandate.** If line managers are not briefed that opting out is legitimate, operators correctly infer that opting out will be used against them in performance reviews. The opt-out becomes a soft mandate and all the risks of mandate apply.
- **A mandate with no rollback trigger.** A mandate that cannot be rolled back is irreversible. The pre-authored trigger is what makes the mandate defensible at council.
- **"Mandate for all engineers."** Too broad. Fluency-floor risk and compensation-alignment effect both veto. The narrow onboarding workflow is the shape that passes.
- **Inventing a specific regulator or an MRM process name.** `<!-- org-specific: ... -->` slots.
- **Deciding the EU scope in this memo.** EU operations trigger a separate works-council consultation. This memo defers that decision explicitly.
- **Compensation-alignment "we would never do that" commitment without a written artifact.** HR's verbal commitment is not defensible; a written one is.

## 6. References

- **Learning material:**
  - [Exercise 04 learning file](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-105-champion-networks-and-change-management/exercises/exercise-04-opt-in-vs-mandate-decision-worked-example.md)
  - [mod-105 chapters (champion networks and change management)](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-105-champion-networks-and-change-management) `<!-- org-specific: confirm which mod-105 chapters cover the opt-in / opt-out / mandate ladder, veto surfaces, and reversibility; link the specific chapter files here -->`
  - [mod-103 Exercise 01 — Acceptable-Use Policy](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-103-policy-co-authoring-with-governance/exercises/exercise-01-one-page-acceptable-use-policy-drill.md) — the Section 3 prohibited-uses carve-outs that the regulatory factor reads against.
  - [mod-104 (training programs and AI literacy curriculum)](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-104-training-programs-and-ai-literacy-curriculum) — fluency-tier definitions used in factor 3.
  - [mod-108 (industry and regulatory flavours of enablement)](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-108-industry-and-regulatory-flavours-of-enablement) — regulated-industry constraints referenced in factor 1.
- **Official standards and frameworks:**
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — GOVERN function (accountability and workforce competence); MANAGE function (risk response, rollback).
  - [NIST AI 600-1: Generative AI Profile](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf) — generative-AI-specific risk considerations relevant to the mandate-scope recommendation.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — context for the fluency-floor-risk reading on prompt injection and output review.
  - [MITRE ATLAS](https://atlas.mitre.org/) — adversarial technique context for the rollback-trigger surface.
  - EU AI Act Article 4 (AI literacy obligation) — the literacy-floor surface the opt-in-at-pilot phase evidences. `<!-- org-specific: direct link to Article 4 on an authoritative EU source -->`
