# Exercise 04 — Procurement and Finance Partnership Contract — Reference Solution

> Module: `mod-107-budget-roi-and-build-vs-buy-at-org-scope`
> Exercise type: design / worked example
> Exercise brief: [`lessons/mod-107-budget-roi-and-build-vs-buy-at-org-scope/exercises/exercise-04-procurement-and-finance-partnership-contract.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-107-budget-roi-and-build-vs-buy-at-org-scope/exercises/exercise-04-procurement-and-finance-partnership-contract.md) (in the learning repo)

## 1. Solution overview

The deliverable is a **partnership contract** between the AI Enablement function and the two internal functions it depends on most for budget-and-buy decisions: **Procurement** and **Finance**. The contract is a one-page written agreement that names decision rights, information flows, cadences, and escalation. It is signed by the three function leads and republished whenever any one of the three changes. Without this artifact, every AI tool purchase re-negotiates the same working relationship from scratch; with it, the purchases move at the speed the business requires.

Posture checks this solution encodes:

- **Decision rights are explicit and asymmetric.** Enablement does not own procurement; Procurement does not own enablement outcomes. The contract names who decides what.
- **Information flows go both directions.** Enablement commits to a cadence of inputs for Procurement (demand plan, consolidation signals) and for Finance (variance commentary, cost-model updates). Procurement and Finance commit to inputs back (contract-pipeline visibility, actuals reconciliation).
- **The three cadences are named** — monthly operational, quarterly tactical, annual strategic — with explicit attendees and outputs per cadence.
- **Escalation path is named** and is role-name-addressed (not people-name-addressed) so the contract survives org changes.
- **SLAs are two-way.** Enablement commits to lead-time and intake-quality SLAs; Procurement and Finance commit to review-turnaround and reconciliation SLAs.
- **The contract names the artifacts it governs**: the Exercise 01 cost model, the Exercise 02 ROI projection, the Exercise 03 build-vs-buy matrix, and the mod-102 intake questionnaire. These are the documents that cross the function boundaries.
- **Reversibility is designed in.** The contract names when it is revisited and what signals trigger an off-cycle revisit.

## 2. Implementation — worked answer (`enablement-procurement-finance-partnership-contract.md`)

```
AI Enablement ↔ Procurement ↔ Finance — Partnership Contract
Effective:        <!-- org-specific: effective date -->
Signatories:      AI Enablement Lead (this role), Head of Procurement, Head of Finance for <enablement cost center>
Next review:      Annual (next revisit: <!-- org-specific: effective-date + 12 months -->), or off-cycle on a trigger listed in Section 6
Scope:            All AI-tool and AI-enablement spend in the enablement cost center,
                  including seat-priced vendor tools, consumption-priced API usage,
                  content and training engagements, and third-party audit / assurance engagements.
```

---

### Section 1 — Purpose

This contract names how the AI Enablement function works with Procurement and with Finance so that AI-tool and AI-enablement decisions move at the speed the business requires without compromising the sourcing, cost-governance, and fiduciary posture each function is accountable for. It is a working-arrangement artifact; it does not supersede the organization's corporate procurement policy, financial-controls policy, or governance council charter. Where this contract and a corporate policy differ, the corporate policy wins and this contract is amended within 30 days.

### Section 2 — Decision rights (DACI)

The three functions carry asymmetric decision rights. The convention used is: **D**river, **A**pprover, **C**onsulted, **I**nformed.

| Decision | Enablement | Procurement | Finance | Other |
|---|---|---|---|---|
| **Which capability to invest in** (program-level) | A | C | C | I: council (`head-of-ai-governance` L60) |
| **Which path for a capability** (Build / Buy / Buy-plus-glue, per Exercise 03 matrix) | D | C | C | A: council |
| **Which vendor to sign on a Buy path** (shortlist → selection) | D | A (commercial terms) | C | C: Security, Legal |
| **Contract value within annual envelope** | D | A | C | — |
| **Contract value > 25% of annual envelope** | D | C | A | A: CFO office `<!-- org-specific: confirm threshold and approver -->` |
| **Renewal, non-renewal, or re-negotiation** | D | A | C | — |
| **Consumption-pricing commitment uplift (e.g., committed-use agreement)** | D | A | A | — |
| **Mid-year reforecast** | C | C | D | A: CFO office |
| **Tool deprecation / consolidation decision (Exercise 05)** | D | A | C | C: council, affected BU sponsors |
| **Incident-driven emergency procurement (per mod-109)** | D | A | I | A: CISO or delegate |

### Section 3 — Information flows and artifacts

This contract names four artifacts that cross the function boundaries, with the owner and the cadence per artifact:

| Artifact | Owner (Driver) | Reviewers / Approvers | Cadence |
|---|---|---|---|
| **Enablement cost model** (Exercise 01 shape) | Enablement | Finance (A), Procurement (C) | Annual; mid-cycle refresh on trigger |
| **ROI projection with confidence bands** (Exercise 02 shape) | Enablement | Finance (A) | Annual; quarterly P50 update |
| **Build-vs-buy matrix** (Exercise 03 shape) | Enablement | Procurement (C), Finance (C), council (A) | Per capability |
| **Vendor intake and shortlist** (mod-102 intake questionnaire + shortlist criteria) | Enablement | Procurement (A on commercial), Security (A on threat posture), Legal (A on contract posture) | Per candidate |

Procurement in turn commits to publishing a **contract pipeline dashboard** (status of all AI-related RFPs, redlines, renewals, and expiration dates) that Enablement consumes weekly. Finance in turn commits to publishing **actuals vs. plan** for the enablement cost center monthly, broken out by the Exercise 01 categories. These two inputs are what let Enablement operate the monthly scorecard without asking.

### Section 4 — Cadences

Three recurring cadences; one-off off-cycle meetings on trigger.

| Cadence | Attendees (role names) | Standing agenda | Outputs |
|---|---|---|---|
| **Monthly operational** (45 min) | AI Enablement Lead, Procurement AI-sourcing lead, Finance AI-cost-center partner | Actuals vs. plan review; contract pipeline review; any new intakes; escalations from the field | Variance commentary filed within 5 business days; action-item log |
| **Quarterly tactical** (90 min) | Monthly attendees + Security intake partner + a rotating BU sponsor | Quarterly ROI update (Exercise 02 P50 refresh); committed-use agreement review; vendor-performance review; consolidation signals (feeds Exercise 05) | Updated quarterly ROI snapshot; vendor-performance scorecard; consolidation shortlist, if any |
| **Annual strategic** (half-day) | Quarterly attendees + `head-of-ai-governance` (L60) + `senior-ai-governance-architect` (L50) + CFO office delegate + CISO delegate | Full cost-model refresh (Exercise 01); full three-year ROI view; next year's capability roadmap and build-vs-buy decisions for roadmap items; contract-pipeline next 12 months | Signed cost model, ROI projection, and build-vs-buy decisions for the planning cycle |
| **Off-cycle on trigger** | Variable; convened by whichever function names the trigger | Trigger-specific | Written note to Section 2 decision-rights table or Section 3 artifact set |

### Section 5 — Service-level commitments (two-way)

The contract carries SLAs so that neither function is the silent bottleneck.

**Enablement commits to:**

| SLA | Target | Source / assumption |
|---|---|---|
| Deliver a filled intake questionnaire (mod-102 shape) with each vendor shortlist | ≥ 48 hours before the first commercial conversation | Per mod-102 Chapter 03 shortlist pattern |
| Provide a draft build-vs-buy matrix (Exercise 03 shape) | ≥ 2 weeks before any capability-level decision | Per Exercise 03 reversal-condition discipline |
| Publish a monthly variance commentary | 5 business days after Finance's monthly close | — |
| Pre-brief Procurement and Finance before taking any AI-spend item to the council | ≥ 5 business days | Per mod-103 governance council pre-read discipline |

**Procurement commits to:**

| SLA | Target | Source / assumption |
|---|---|---|
| Initial commercial review of a vetted vendor shortlist | ≤ 10 business days from receipt of the intake pack | `<!-- org-specific: confirm against the Procurement function's published SLAs -->` |
| Redline cycle on standard-tier contracts | ≤ 15 business days per round, max 3 rounds | `<!-- org-specific -->` |
| Publish the contract-pipeline dashboard | Weekly, every Monday 9:00 local | — |
| Flag renewals and auto-renewal windows | ≥ 60 days before the auto-renewal date | `<!-- org-specific -->` |

**Finance commits to:**

| SLA | Target | Source / assumption |
|---|---|---|
| Publish actuals vs. plan for the enablement cost center | ≤ 5 business days after monthly close | — |
| Reconcile vendor invoices against the cost model | Monthly, within the same 5-day window | — |
| Approve within-envelope spend requests | ≤ 5 business days | — |
| Approve above-threshold spend requests (> 25% of annual envelope) | ≤ 10 business days (with CFO office sign-off) | `<!-- org-specific -->` |

**All three functions commit to:**

- Honor the quiet-hours windows (end-of-quarter close for Finance; vendor-negotiation windows for Procurement) and route non-urgent work around them.
- Use role-name addressing in all written communications (per mod-103 Chapter 02 posture).
- Share information that would materially change the other functions' plans within 2 business days of learning it.

### Section 6 — Escalation and reversibility

Escalation path (in order):

1. The three signatories convene an off-cycle 30-minute meeting within 3 business days of a flagged escalation.
2. If unresolved, the item is routed to the governance council (`head-of-ai-governance` L60) as a written pre-read — not as a live debate at council. Council session itself is for ratifying the resolution.
3. If unresolved at council, CFO office and CISO office are briefed jointly within 5 business days.

**Contract-revisit triggers (off-cycle):**

- Any signatory's role changes (title, scope, cost-center ownership).
- Annual envelope changes by > 25% from one planning cycle to the next.
- A corporate procurement or finance policy changes materially (new signing thresholds, new commercial standards, new audit regime).
- An AI-related incident of severity Sev-2 or higher requires emergency procurement routing (per mod-109).
- A regulatory posture change (e.g., new EU AI Act operator obligations) requires a new category of audit or assurance spend.
- Two consecutive quarterly reviews show > 20% variance between actuals and plan without a reconciling explanation.

The contract is **short on purpose** — one page ratifying a working relationship — and is **ratified by a short signature block**, not by live debate at every refresh.

### Section 7 — Signatures

| Role | Signatory `<!-- org-specific: name -->` | Date | Version |
|---|---|---|---|
| AI Enablement Lead | <!-- org-specific --> | <!-- org-specific --> | 1.0 |
| Head of Procurement (AI-sourcing delegate) | <!-- org-specific --> | <!-- org-specific --> | 1.0 |
| Head of Finance (enablement cost-center partner) | <!-- org-specific --> | <!-- org-specific --> | 1.0 |

### End of contract

---

### 2.1 Decision rationale — why this shape, not another

- **Why a written contract rather than a shared workflow.** A shared workflow drifts the moment any of the three functions re-organizes. A written contract survives the drift because it names role-based decision rights and republishes on trigger. Mod-103's role-name-addressing discipline is the same discipline applied here.
- **Why DACI and not RACI.** For the specific set of decisions in Section 2, "Responsible" and "Accountable" get blurred because Enablement is often both. DACI — Driver, Approver, Consulted, Informed — makes the asymmetric roles clearer: the Driver proposes, the Approver signs, and the two never collapse into one.
- **Why three cadences, not one.** A single cadence either runs at the wrong pace (monthly operational is too frequent for annual strategic review; annual is too slow for operational) or becomes two de facto cadences on top of a single calendar entry. The three-cadence split is explicit.
- **Why two-way SLAs.** One-way SLAs (Enablement commits to Procurement only) breed asymmetry; the function that over-indexes on upstream inputs becomes the bottleneck when the downstream function has no reciprocal commitment.
- **Why revisit triggers and not just an annual cadence.** The partnership breaks most often on an off-cycle event (a re-org, a policy change, an incident). Naming the triggers up-front lets the three functions revisit without debating whether to revisit.
- **Why role-name addressing.** The contract must survive personnel changes. Any contract signed with people names is a contract that expires with the next org change; this one does not.

## 3. Validation steps

1. **One page.** Render markdown; the full contract (Sections 1–7) should fit on a single printable page. Remove narrative that belongs in the solution rationale rather than in the contract itself.
2. **Seven numbered sections** in the order shown (Purpose, Decision rights, Information flows, Cadences, SLAs, Escalation, Signatures).
3. **DACI table** in Section 2, with at least the ten decisions shown. Every row has a Driver and an Approver (not the same role).
4. **Information-flows table** in Section 3 names the four artifacts (cost model, ROI projection, build-vs-buy matrix, vendor intake). Owner and reviewers are named per artifact.
5. **Three cadences + off-cycle** named in Section 4 with attendees, agenda, and outputs per cadence.
6. **SLAs are two-way.** Enablement SLAs, Procurement SLAs, Finance SLAs, and joint commitments all present. A one-way contract fails.
7. **Escalation path** is written as a numbered sequence; it names the governance council and routes through the council as a pre-read (not live debate).
8. **Contract-revisit triggers** named in Section 6 — at least five.
9. **Role-name addressing throughout.** Grep for personal pronouns or people names.
10. **`org-specific` tags** on specific SLA numbers, threshold percentages, and signatory names.
11. **References mod-102 (intake), mod-103 (governance posture and role-name discipline), mod-106 (scorecard cadence), mod-109 (emergency procurement path), and Exercises 01 / 02 / 03** by name.
12. **No vendor product names.** No specific commercial terms. The contract is a working-relationship artifact, not a vendor agreement.

## 4. Rubric / review checklist

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | One printable page in total | 5 | Spills beyond one page. |
| R2 | Seven numbered sections in the order shown | 5 | Missing section or out of order. |
| R3 | Decision-rights table (DACI) with ≥ 10 decisions; every row has Driver + Approver, not collapsed | 15 | Collapsed rows, missing decisions, or RACI-blurring. |
| R4 | Information flows name the four cross-boundary artifacts and the owner per artifact | 10 | Missing an artifact or no owner named. |
| R5 | Three cadences + off-cycle, with attendees / agenda / outputs per cadence | 10 | Fewer than three cadences, or any cadence missing attendees/outputs. |
| R6 | Two-way SLAs (Enablement + Procurement + Finance + joint) | 15 | One-way SLAs only. |
| R7 | Escalation path routes through governance council as a pre-read, not live debate | 5 | Escalation path missing or routes council as live debate. |
| R8 | ≥ 5 contract-revisit triggers named operationally | 10 | Fewer than five, or vague ("as needed"). |
| R9 | Role-name addressing throughout | 10 | People names used. |
| R10 | `org-specific` tags on SLA specifics, thresholds, signatory names | 5 | Unmarked quoted numbers. |
| R11 | Explicit cross-references to mod-102 / mod-103 / mod-106 / mod-109 and Exercises 01 / 02 / 03 | 5 | No cross-references. |
| R12 | No vendor product names or specific commercial terms | 5 | Vendor names or commercial terms embedded. |

**Pass threshold:** ≥ 85/100 and no R3 / R6 / R9 fail. R3 (decision rights), R6 (two-way SLAs), and R9 (role-name addressing) are the discriminators between a contract that survives an org change and a contract that expires with the next quarterly re-org.

## 5. Common mistakes

- **Writing the contract as a one-way SLA for Enablement.** Enablement commits lead-times and intake quality; Procurement and Finance commit nothing back. The contract fails on first contact with a slow redline cycle.
- **Collapsing DACI into RACI.** Enablement ends up listed as both Responsible and Accountable for every row; no decision rights are actually clarified. Keep Driver and Approver distinct.
- **Addressing the contract to people names.** The contract expires with the next re-org. Address to roles.
- **Omitting the off-cycle triggers.** Without triggers, the contract stays in force past the event that should have revisited it (a policy change, an incident, a re-org).
- **Routing escalations as live council debate.** The council is not the escalation venue; it is the ratification venue. Escalations arrive at council as a pre-read with a proposed resolution.
- **Over-specifying commercial terms inside the contract.** The contract names working relationships, not vendor economics. Commercial terms belong in the individual vendor contracts, not here.
- **Omitting cross-references to the enabling artifacts.** The contract's load-bearing claims (Enablement's cost model, ROI projection, build-vs-buy matrix) must be named by artifact, so Procurement and Finance know what they are receiving.
- **Scheduling the annual strategic cadence without council and CFO/CISO delegates.** The annual cadence is the moment the full posture is reviewed; if the annual meeting is only the three function heads, it is a monthly meeting with extra chairs.
- **Writing the signature block as free text.** A table signature block makes the republication-on-trigger pattern work; free text drifts.
- **Quoting specific procurement-policy thresholds without tagging.** Threshold percentages (25%, 60 days, etc.) are org-specific; they must be tagged `<!-- org-specific -->` so the real artifact carries the learner's org's policy, not this solution's placeholder.

### 5.1 Stretch — appendix of standing templates

For a mature program, the contract is extended with a short appendix listing the templates each cadence consumes. The appendix is kept in the Enablement function's working folder, not on the printed contract page, so the contract itself stays one page:

- Template: **monthly variance commentary** (Enablement → Finance).
- Template: **weekly contract-pipeline dashboard** (Procurement → Enablement).
- Template: **quarterly ROI refresh snapshot** (Enablement → Finance, quarterly tactical cadence).
- Template: **annual planning pack** (Enablement → council, annual strategic cadence) — bundles Exercise 01 cost model, Exercise 02 ROI projection, Exercise 03 build-vs-buy decisions for roadmap items.
- Template: **emergency procurement routing** (Enablement + Procurement + CISO, Sev-2+ incident path, per mod-109).

Each template is one page, with a stable structure, so the cadence is not "produce a new deck each time" but "fill a known template."

## 6. References

- **Learning material (local):**
  - [Exercise 01 — Enablement Cost Model Drill](../exercise-01-enablement-cost-model-drill/SOLUTION.md) — the cost-model artifact the contract governs.
  - [Exercise 02 — ROI Projection with Confidence Bands](../exercise-02-roi-projection-with-confidence-bands/SOLUTION.md) — the ROI artifact the contract governs.
  - [Exercise 03 — Org-Scope Build-vs-Buy Matrix](../exercise-03-org-scope-build-vs-buy-matrix/SOLUTION.md) — the build-vs-buy artifact the contract governs.
  - [mod-102 — Selecting and Rolling Out AI Tools](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-102-selecting-and-rolling-out-ai-tools) — the intake questionnaire and shortlist pattern.
  - [mod-103 — Policy Co-authoring with Governance](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-103-policy-co-authoring-with-governance) — role-name addressing and governance-council pre-read posture.
  - [mod-106 — Outcome Measurement and Executive Reporting](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-106-outcome-measurement-and-executive-reporting) — the scorecard-cadence shape informing the monthly operational agenda.
  - [mod-109 — AI Incident Response and Enablement-Side Rollback](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-109-ai-incident-response-and-enablement-side-rollback) — the emergency-procurement routing in Section 2.
- **Official standards and frameworks:**
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — the GOVERN function underpins the asymmetric decision rights for third-party AI risk.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — threat posture context behind the Security-consulted rows in Section 2.
  - [MITRE ATLAS](https://atlas.mitre.org/) — adversarial-technique context for the Sev-2+ emergency-procurement path.
