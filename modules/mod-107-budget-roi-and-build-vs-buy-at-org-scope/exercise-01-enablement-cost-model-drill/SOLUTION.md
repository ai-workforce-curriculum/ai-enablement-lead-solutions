# Exercise 01 — Enablement Cost Model Drill — Reference Solution

> Module: `mod-107-budget-roi-and-build-vs-buy-at-org-scope`
> Exercise type: design / worked example
> Exercise brief: [`lessons/mod-107-budget-roi-and-build-vs-buy-at-org-scope/exercises/exercise-01-enablement-cost-model-drill.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-107-budget-roi-and-build-vs-buy-at-org-scope/exercises/exercise-01-enablement-cost-model-drill.md) (in the learning repo)

## 1. Solution overview

The deliverable is an **org-scope enablement cost model**: a per-period roll-up of the full cost of running the AI Enablement function for one fiscal year, broken out at the line-item grain Finance can reconcile against general-ledger (GL) codes. The model is what the AI Enablement Lead walks into the budget-planning conversation with — not a slideware number, but a spreadsheet-shaped artifact where every cell traces to an assumption and every assumption is either tied to an organizational signal or marked as `org-specific`.

Posture checks this solution encodes:

- **Every line item carries a unit, a unit cost, a quantity, and a source.** Finance will reject any number that is not reducible to those four columns.
- **Cost categories are exhaustive at the family level** (direct software, direct infrastructure/consumption, labor, change-management, governance/compliance, and risk reserve) even when individual IDs are `<!-- org-specific: ... -->` for the learner's own org.
- **Labor is modeled at fully-loaded cost**, not base salary. Benefit load, employer taxes, facilities, and tooling allocation are included. The default fully-loaded multiplier used in the worked example is `1.35x base`; the learner must confirm their org's actual multiplier. <!-- org-specific: confirm the fully-loaded labor multiplier used by the learner's Finance function; 1.3x–1.4x is a common public-sector range but is not a universal constant. -->
- **Indirect labor (champion-network time, L&D partnership time, Security intake review) is modeled explicitly.** Omitting this is the single most common failure mode — it is what makes enablement look "free" on paper and under-funded in practice.
- **A risk reserve line exists.** Incident response, rollback, and policy-driven mid-cycle refresh have a non-zero expected cost; the model carries them.
- **No vendor names, no quoted vendor rate cards.** The worked example uses generic categories; quoting a specific vendor's dollars-per-seat without a verified rate card is a hard fail.

## 2. Implementation — worked answer

### 2.1 Scenario envelope used for the worked example

- Organization size: ~2,000 knowledge workers across three business units.
- Addressable population for AI enablement: ~1,400 (the 70% of staff who have been intake-questionnaire-reviewed and are in-scope per the acceptable-use policy).
- Fiscal year: one full year (12 months).
- Currency and VAT treatment: USD, ex-tax. <!-- org-specific: confirm whether the learner's Finance function wants ex-tax or tax-inclusive line items; the model below is ex-tax. -->
- Stage of program: mature pilot exiting into general availability for two tools; one tool still in evaluation.

### 2.2 The model — `enablement-cost-model.md`

```
Enablement cost model — FY<YYYY>
Author:        AI Enablement Lead
Finance owner: <!-- org-specific: name the Finance partner on the GL side -->
Snapshot date: <!-- org-specific: confirm as-of date for assumptions -->
```

#### Category A — Direct software licensing

| Line item | Unit | Unit cost (USD) | Quantity | Annualized total (USD) | Source / assumption |
|---|---|---|---|---|---|
| General-availability AI assistant, Tier-1 users (daily operators) | per seat / year | 240 | 900 | 216,000 | Procurement-cleared rate card, FY<YYYY> `<!-- org-specific: confirm actual seat price from the signed order form -->` |
| General-availability AI assistant, Tier-2 users (occasional operators) | per seat / year | 120 | 500 | 60,000 | Same rate card, Tier-2 SKU `<!-- org-specific -->` |
| Specialist tool — code assistant for Engineering | per seat / year | 300 | 180 | 54,000 | Engineering BU-owned contract `<!-- org-specific -->` |
| Specialist tool — meeting-notes assistant pilot | per seat / month | 15 | 60 seats × 6 months | 5,400 | Pilot contract, charter-scoped to 6 months |
| **Category A subtotal** |  |  |  | **335,400** |  |

#### Category B — Direct infrastructure and consumption

| Line item | Unit | Unit cost (USD) | Quantity | Annualized total (USD) | Source / assumption |
|---|---|---|---|---|---|
| LLM API consumption — shared prompt-engineering platform | per million tokens, blended | 2.50 | 48M tokens | 120,000 | Historical six-month telemetry extrapolated to 12 months; blended rate reflects mix of input/output and model tiers `<!-- org-specific: validate blended per-million-token rate against the vendor's billing report -->` |
| Vector / retrieval index hosting | per month | 1,800 | 12 | 21,600 | Managed-service tier currently sized for ≤ 25M vectors `<!-- org-specific -->` |
| SSO and identity platform allocation (incremental for AI tools) | per month | 400 | 12 | 4,800 | IT chargeback to Enablement cost center `<!-- org-specific -->` |
| Observability / logging allocation | per month | 350 | 12 | 4,200 | Shared platform chargeback |
| **Category B subtotal** |  |  |  | **150,600** |  |

#### Category C — Labor (fully loaded at 1.35x base)

| Line item | Unit | Fully-loaded unit cost (USD) | Quantity (FTE-years) | Annualized total (USD) | Source / assumption |
|---|---|---|---|---|---|
| AI Enablement Lead (this role) | 1 FTE-year | 243,000 | 1.00 | 243,000 | Base 180,000 × 1.35 `<!-- org-specific: confirm actual base and multiplier -->` |
| AI Enablement Program Manager | 1 FTE-year | 189,000 | 1.00 | 189,000 | Base 140,000 × 1.35 `<!-- org-specific -->` |
| Enablement-side training designer (shared with L&D) | 1 FTE-year | 162,000 | 0.50 | 81,000 | Allocated — half-time to AI enablement `<!-- org-specific -->` |
| Enablement operations analyst (data, scorecard, telemetry) | 1 FTE-year | 148,500 | 0.75 | 111,375 | Base 110,000 × 1.35, three-quarters-time |
| **Category C subtotal** |  |  |  | **624,375** |  |

#### Category D — Indirect labor (business-unit time allocated to enablement work)

This is the category that is most often omitted. Including it is what lets Finance see the full cost; it is also what lets the business-unit owners see that the "ask" they fund in cash is a fraction of the total.

| Line item | Unit | Fully-loaded unit cost (USD) | Quantity | Annualized total (USD) | Source / assumption |
|---|---|---|---|---|---|
| Champion-network time | hour | 95 | 1,800 hours (30 champions × 60 hours/year) | 171,000 | Blended fully-loaded hourly rate for mid-level ICs across the three BUs `<!-- org-specific: the champion network is sized per mod-105 Chapter 02 pattern (3 champions per BU minimum), and the hours-per-champion assumption needs to be calibrated to the learner's actual champion charter -->` |
| L&D partnership time (training design, facilitation, roster ops) | hour | 110 | 500 hours | 55,000 | L&D cost center allocation `<!-- org-specific -->` |
| Security intake review time | hour | 160 | 120 hours (≈ 2.5 hours/week of a Security engineer) | 19,200 | Security chargeback or allocation `<!-- org-specific -->` |
| Legal/privacy review time | hour | 220 | 80 hours | 17,600 | Counsel allocation `<!-- org-specific -->` |
| Procurement sourcing time | hour | 130 | 60 hours | 7,800 | Procurement allocation `<!-- org-specific -->` |
| Executive-sponsor time (council meetings, pre-reads, escalations) | hour | 450 | 40 hours | 18,000 | Blended L60+ rate |
| **Category D subtotal** |  |  |  | **288,600** |  |

#### Category E — Change-management and content

| Line item | Unit | Unit cost (USD) | Quantity | Annualized total (USD) | Source / assumption |
|---|---|---|---|---|---|
| Training content development (external vendor top-up) | engagement | 25,000 | 1 | 25,000 | Scoped per mod-104 outsourcing exercise `<!-- org-specific -->` |
| LMS seat / course-hosting cost (allocated share) | per year | 8,000 | 1 | 8,000 | LMS allocation |
| Champion-network meeting and recognition budget | per year | 15,000 | 1 | 15,000 | Internal recognition cost center |
| Internal communications production (video, briefings) | per year | 12,000 | 1 | 12,000 | Comms cost center |
| **Category E subtotal** |  |  |  | **60,000** |  |

#### Category F — Governance and compliance

| Line item | Unit | Unit cost (USD) | Quantity | Annualized total (USD) | Source / assumption |
|---|---|---|---|---|---|
| External legal review (AUP, DPA redlines, EU AI Act Article 4 posture) | engagement | 40,000 | 1 | 40,000 | Outside-counsel retainer allocation `<!-- org-specific -->` |
| External standards / audit engagement (ISO/IEC 42001 preparation) | engagement | 60,000 | 1 | 60,000 | Pre-certification engagement `<!-- org-specific: confirm whether the org has booked a specific pre-certification audit -->` |
| Third-party pen test / red-team adjacent to AI tooling | engagement | 35,000 | 1 | 35,000 | Scoped to tools in general availability; contexts from `owasp-ml-top-10` and `mitre-atlas` drive scope |
| **Category F subtotal** |  |  |  | **135,000** |  |

#### Category G — Risk reserve

| Line item | Unit | Unit cost (USD) | Quantity | Annualized total (USD) | Source / assumption |
|---|---|---|---|---|---|
| Incident-response reserve (enablement-side rollback, re-training, communications) | per year | 50,000 | 1 | 50,000 | Scoped per mod-109 rollback playbook; set at ~3% of direct software + consumption spend as a planning heuristic `<!-- org-specific -->` |
| Policy-driven mid-cycle refresh reserve (AUP / SOP walking-redline cycles outside annual) | per year | 20,000 | 1 | 20,000 | Scoped to 2 mid-cycle refreshes per year |
| **Category G subtotal** |  |  |  | **70,000** |  |

#### Grand total

| Category | Annualized total (USD) | % of total |
|---|---|---|
| A — Direct software licensing | 335,400 | 20.4% |
| B — Direct infrastructure and consumption | 150,600 | 9.2% |
| C — Labor (fully loaded) | 624,375 | 38.1% |
| D — Indirect labor | 288,600 | 17.6% |
| E — Change-management and content | 60,000 | 3.7% |
| F — Governance and compliance | 135,000 | 8.2% |
| G — Risk reserve | 70,000 | 4.3% |
| **Total (annualized, FY<YYYY>)** | **1,663,975** | **100%** |

#### Cost-per-reached-operator view (derived)

- Addressable population (in-scope operators): 1,400.
- Reached operators FY<YYYY> target: 1,250 (per mod-104 fluency-growth cadence and the executive scorecard reach target in mod-106).
- Cost per reached operator (annualized): **~1,331 USD/operator-year**.
- Cost per reached operator if indirect labor excluded: **~1,100 USD/operator-year**. (This is the number that is *tempting* to quote. It is the wrong number for budget planning, because it hides the ~288k of indirect labor the business units are already paying for.)

### 2.3 Decision rationale — why this shape, not another

- **Why seven categories, not three.** Collapsing to "software + labor + other" loses the governance and risk-reserve lines Finance needs to see distinctly, and it hides indirect labor inside "other." The seven-category split maps cleanly to the GL account families Finance already carries (software, infrastructure, people, external services, contingency) and makes the enablement-vs-tool distinction legible — a Finance partner can see at a glance that ~60% of the spend is the enablement operation itself, not the tools.
- **Why fully-loaded labor, not base.** Any cost model Finance will accept for budget planning uses fully-loaded rates; quoting base salary inflates the apparent ROI by ~25–40% because it is subsidizing itself with un-costed benefit load. The multiplier is org-specific — the solution uses 1.35x and marks it as `org-specific`.
- **Why a risk reserve.** Incidents and policy refreshes are a near-certain cost when amortized over 12 months; carrying them as a reserve prevents mid-year surprise asks. The ~3% heuristic on direct software + consumption is a planning placeholder, not a load-bearing claim; the reserve should be re-baselined after the first year's actuals.
- **Why no vendor-specific numbers.** Quoting a vendor's public rate card without a signed order form is an accuracy risk (negotiated discounts are the norm) and a disclosure risk (public rate-card quotes can appear in artifacts that leak). The model uses generic unit costs and tags the rate-card source for each line.

## 3. Validation steps

1. **Unit discipline.** Every line in Categories A–G has a `unit`, `unit cost`, `quantity`, and `annualized total`. Grep for any row missing one of the four.
2. **Arithmetic check.** `unit cost × quantity = annualized total` to the dollar for every row. Category subtotals = sum of rows. Grand total = sum of category subtotals.
3. **Fully-loaded labor check.** Every row in Categories C and D uses a fully-loaded rate, not base. If the multiplier is not explicitly carried in the row's "Source / assumption" column, the row fails.
4. **Indirect-labor presence check.** Category D is populated. The failure mode is an empty or token Category D ("1 champion-hour: $500"); the champion-network, L&D, Security, Legal, Procurement, and executive-sponsor lines should all be present. If the learner's org does not use one of these functions (e.g., an in-house-only Legal function), the row still appears with a zero and a `<!-- org-specific: ... -->` note explaining why.
5. **`org-specific` markers are present where claims are not verifiable from local exercise context.** Unmarked quoted numbers (specific vendor rate-card dollars, specific employer-tax rates, specific regulatory engagement costs) are a hard fail.
6. **Cost-per-reached-operator carries two values.** The with-indirect and without-indirect numbers are both quoted, and the model is explicit that the with-indirect number is the correct one for budget planning.
7. **Risk reserve is non-zero.** A zero-reserve model fails on this criterion regardless of how the rest of the model looks.
8. **No vendor names.** Grep for vendor product names, trademark marks, or `.com` strings. The model is generic by design.
9. **Alignment with the official sources.** Category F references `owasp-ml-top-10` and `mitre-atlas` by name when scoping red-team / pen-test work; Categories A and D reference the mod-102 selection-and-rollout and mod-104 training materials by module ID.
10. **Markdown lint.** Table columns align; no broken row rendering.

## 4. Rubric / review checklist

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | Seven categories present and populated (A–G), covering direct software, direct infrastructure/consumption, direct labor, indirect labor, change-management, governance/compliance, risk reserve | 15 | Any category missing or empty. |
| R2 | Every line item has unit, unit cost, quantity, source | 15 | Any row missing one of the four. |
| R3 | Labor at fully-loaded rates with multiplier disclosed | 10 | Base-salary rates used, or multiplier missing. |
| R4 | Indirect labor (Category D) populated with champion, L&D, Security, Legal, Procurement, executive-sponsor lines | 15 | Category D omitted or materially incomplete. |
| R5 | Risk reserve present and non-zero | 5 | Reserve omitted or set to 0. |
| R6 | Arithmetic ties (row totals, category subtotals, grand total) | 10 | Any broken total. |
| R7 | Cost-per-reached-operator computed both with and without indirect labor, with explicit note that with-indirect is the planning number | 5 | Only one computed, or the wrong one named as planning number. |
| R8 | Vendor-specific numbers absent or clearly marked as rate-card references | 5 | Public rate-card dollars quoted without tag. |
| R9 | `org-specific` markers on specific sub-costs, tax rates, benefit multipliers, and audit engagement costs | 10 | Unmarked quoted numbers. |
| R10 | GL / Finance-partner mapping named (owner, snapshot date, ex-tax/tax-inclusive treatment) | 5 | Model not addressed to a Finance partner or missing date/tax basis. |
| R11 | References the official sources where applicable (mod-109 for incident reserve scoping, `owasp-ml-top-10` and `mitre-atlas` for red-team scoping) | 5 | No cross-reference to governance/security standards. |

**Pass threshold:** ≥ 85/100 and no R2 / R3 / R4 fail. R4 (indirect labor) is the single most common failure mode and the discriminator between a cost model Finance will sign and one Finance will send back.

## 5. Common mistakes

- **Omitting indirect labor (Category D).** The cost of champion time, L&D partnership, Security intake, Legal/privacy review, and executive-sponsor time is the single largest line-item surprise for first-year enablement cost models. Omitting it makes enablement look free on paper and under-funded in practice; it also undermines the ROI projection in Exercise 02, because the denominator is wrong.
- **Quoting base salary instead of fully-loaded labor.** The 25–40% error this introduces compounds in the ROI projection and in the build-vs-buy comparison. Finance will ask for fully-loaded rates on first review; starting there saves a cycle.
- **Quoting vendor rate cards as fact without a signed order form.** Public list prices are a sales artifact, not a contract. The negotiated rate is almost always different. The cost model uses the rate card as a planning placeholder tagged `org-specific`, not a decision input.
- **Zero risk reserve.** Over any 12-month horizon, incidents, mid-cycle refreshes, and policy-driven re-scoping are near-certain. A zero-reserve model is a budget that will come back to Finance mid-year for a supplementary ask.
- **Mixing one-time and recurring costs without flagging them.** The pilot contract line in Category A is explicitly scoped to 6 months and labeled as such. A model that annualizes a one-time number (e.g., pretending a 25,000 USD training-content engagement recurs every year without saying so) will over-state recurring spend.
- **Collapsing to three categories to "simplify."** Finance will not sign a three-line cost model for a function this size. The failure mode is to simplify away the categories that make the enablement operation legible and leave only the software license line, which reinforces the "free enablement" misconception.
- **Not naming the Finance partner.** The model header should name the Finance partner on the GL side. Without a named counterparty, the model is not a budget artifact — it is an opinion piece.
- **Quoting specific vendor product names.** Omitted by design. Replace with "Tier-1 AI assistant, general-availability SKU" style naming.

### 5.1 Stretch — monthly amortization and three-year horizon

For the budget conversation that follows FY<YYYY>, the same model is extended two ways, both added as additional tabs (or additional top-level tables) rather than rewritten inline:

- **Monthly amortization.** Software license subscriptions amortize evenly; the pilot contract amortizes across its explicit 6-month window and then drops to 0; training-content and audit engagements are modeled in the month invoiced, not amortized, so the monthly view carries a realistic lumpy shape rather than a smoothed one.
- **Three-year horizon.** Year-over-year assumptions: Tier-1 seat growth of 10%/year as adoption spreads; Tier-2 seat growth of 5%/year; API consumption growth of 25%/year (adoption curve + model-tier upgrade mix); labor flat (no new FTE assumed, with a `<!-- org-specific: confirm headcount plan -->` note); governance/compliance declining in Year 2 (post-certification) and rising again in Year 3 (recertification cycle). The three-year view is the one the build-vs-buy exercise (Exercise 03) and the consolidation exercise (Exercise 05) lean on.

## 6. References

- **Learning material (local):**
  - [mod-102 — Selecting and Rolling Out AI Tools](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-102-selecting-and-rolling-out-ai-tools) — the pilot-charter and procurement-intake pattern that feeds the Category A and B rows.
  - [mod-104 — Training Programs and AI Literacy Curriculum](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-104-training-programs-and-ai-literacy-curriculum) — the training-design and L&D-partnership pattern feeding Category E.
  - [mod-105 — Champion Networks and Change Management](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-105-champion-networks-and-change-management) — the champion-charter pattern feeding Category D.
  - [mod-106 — Outcome Measurement and Executive Reporting](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-106-outcome-measurement-and-executive-reporting) — the executive-scorecard reach target feeding the cost-per-reached-operator derivation.
  - [mod-109 — AI Incident Response and Enablement-Side Rollback](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-109-ai-incident-response-and-enablement-side-rollback) — the incident-reserve scoping for Category G.
- **Official standards and frameworks:**
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — the GOVERN function is the frame for scoping the Category F governance engagements.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — the threat context used to scope the red-team / pen-test line in Category F.
  - [MITRE ATLAS](https://atlas.mitre.org/) — the adversarial-technique context used alongside OWASP for scoping the pen-test line.
