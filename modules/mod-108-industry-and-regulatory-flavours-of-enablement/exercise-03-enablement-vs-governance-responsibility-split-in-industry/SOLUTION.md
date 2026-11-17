## Exercise 03 — Enablement vs. Governance Responsibility Split in Industry — Reference Solution

> Module: `mod-108-industry-and-regulatory-flavours-of-enablement`
> Exercise type: design / worked example (DACI / responsibility split)
> Exercise brief: [`lessons/mod-108-industry-and-regulatory-flavours-of-enablement/exercises/exercise-03-enablement-vs-governance-responsibility-split-in-industry.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-108-industry-and-regulatory-flavours-of-enablement/exercises/exercise-03-enablement-vs-governance-responsibility-split-in-industry.md) (in the learning repo)

## 1. Solution overview

The deliverable is a **responsibility-split artifact** that draws the line between **AI enablement** and **AI governance** in a specific regulated-industry context. The artifact is a one-page DACI matrix plus a short rationale section the AI Enablement Lead walks their governance partners through so both sides sign off on where the line sits before the first live decision tests it. The exercise's point is not "enablement is X and governance is Y"; it is to teach that the line *moves* with industry and regulatory context — the same decision is enablement's in a lightly regulated SaaS company, co-signed in a bank, and governance-owned in a clinical decision-support deployment at a hospital.

The archetype carried through this solution is a **US investment-bank-affiliated depository institution, ~15,000 FTE and contractors, three business units (Commercial Banking, Capital Markets, Wealth Management)**, that is rolling out general-purpose AI assistants across staff and a code assistant for Engineering, with scoped exploration of AI in trading-adjacent workflows. The archetype is explicit because the enablement-vs-governance line in a bank is stricter than in most other regulated industries — it sits closer to governance because of SR 11-7 model-risk-management expectations, OCC heightened-standards exposure for large institutions, SEC / FINRA conduct obligations, and the bank-specific CCAR / stress-testing posture. <!-- org-specific: adjust the stringency of the split for the learner's actual industry and the specific supervisory posture of the organization's primary regulator(s). -->

Posture checks this solution encodes:

- **The enablement function is operational; the governance function is custodial.** Enablement *runs* the program (training, champions, intake-authoring, scorecards). Governance *authorizes* the program (approves the policy, signs the intake, rules on edge cases). Each DACI row makes the distinction explicit.
- **The line is drawn per decision, not per function.** A blanket "enablement does adoption, governance does policy" is wrong at the row level — enablement co-authors policy, governance co-sponsors adoption KPIs. The split is decision-by-decision.
- **Regulatory gravity shifts the line.** For in-scope use-cases that touch model-risk-managed decisions, lending credit, trading, or AML/sanctions, governance owns more than it would otherwise, and the enablement function's role compresses to communication, training, and change discipline. The artifact names which decision classes carry that shift.
- **Edge cases are enumerated, not left implicit.** A new high-risk use-case request, a mid-cycle regulation change, an AI-touching incident, an executive-pushed exception: each is a named row with a named owner. "We'll figure it out in the moment" is the failure mode.
- **Escalation paths are role-name-addressed** so the artifact survives org changes and leadership turnover. Specific people's names appear only in the Appendix.
- **No specific regulator-enforcement claims that cannot be verified.** The artifact references regulatory frameworks by name but flags specific supervisory expectations with `<!-- verify-with-sme: ... -->` where the drafter has not confirmed with Compliance / Legal.

## 2. Implementation — worked answer — the responsibility-split artifact

### 2.1 Framing (`enablement-vs-governance-split.md`)

```
AI Enablement ↔ AI Governance — Responsibility Split
Organization:        <!-- org-specific: legal entity name; name the regulated subsidiary explicitly -->
Primary regulators:  OCC (bank), SEC + FINRA (broker-dealer within group), Federal Reserve (BHC)
                      <!-- org-specific: confirm regulator constellation, especially state-level supervisors
                      and foreign regulators if the group operates cross-border. -->
Scope:               AI tools and AI-enablement spend, program decisions, and rollout operations
                      across the Enablement cost center and in the three business units.
Definitions:         Enablement — the function that operationalizes safe, measurable adoption.
                     Governance — the function(s) that authorize, review, and attest.
                     "Governance" is NOT one organization; it is Model Risk Management,
                     Compliance, Legal, Privacy, CISO, and the AI Governance Council
                     acting under their respective mandates. This artifact names the
                     governance signer per decision row.
Effective:           <!-- org-specific: effective date -->
Owners:              AI Enablement Lead (this role) + head-of-ai-governance (L60).
                     Co-signed at the start of the planning cycle and re-signed annually
                     or on trigger (Section 2.6).
```

### 2.2 The split — DACI matrix

Each row carries, for enablement and the named governance counterparts, who is **D**river, **A**pprover, **C**onsulted, or **I**nformed. The "governance" column is split into the governance counterpart(s) actually involved in that decision — that is a core teaching point: governance is a constellation, not a monolith.

#### A. Program-level and policy decisions

| Decision | Enablement | Model Risk Mgmt | Compliance | Legal / Privacy | CISO | AI Governance Council | Business-Unit Sponsor |
|---|---|---|---|---|---|---|---|
| **Program charter** (why the program exists, in-scope capabilities, risk appetite) | D | C | C | C | C | A | C |
| **AUP (acceptable-use policy)** — baseline | D (co-author) | C (any model-risk-adjacent sections) | A | A | C | A | I |
| **AUP — industry-adjusted overlays** (`mod-108 exercise-04`) | D (co-author) | A (model-risk sections) | A | A | C | A | I |
| **Data-handling SOP** | D (co-author) | C | A | A | A (control-surface sections) | I | I |
| **Intake questionnaire** | D (authors / maintains) | C (adds model-risk fields) | C | C | A (adds control-surface fields) | I | I |
| **Baseline training curriculum** (`mod-104`) | D | I | C | C | I | I | C |
| **Role-based training playbook** (per BU) | D | C (if BU touches MRM scope) | C | C | I | I | A (that BU) |
| **Champion-network charter** (`mod-105`) | D | I | I | I | I | I | C |
| **Executive scorecard content** (`mod-106`) | D | C (defines model-risk KPIs) | C (defines compliance KPIs) | I | I | A | C |
| **Risk-appetite statement for AI tool adoption** | C | A | A | A | A | A | I |

#### B. Per-tool / per-intake decisions

| Decision | Enablement | MRM | Compliance | Legal / Privacy | CISO | Council | BU Sponsor |
|---|---|---|---|---|---|---|---|
| **Tool intake triage** (is this in scope; what tier) | A | C | C | C | C | I | I |
| **Tool classification — is it a "model" under SR 11-7?** | C | A | C | C | I | I | I |
| **Tool classification — does it touch the model-risk-managed decision path?** | C | A | A | C | C | A | C |
| **Tool classification — does it touch customer-facing surface?** | C | I | A | A | I | I | A (that BU) |
| **Tool approval for pilot** (data-scoped, population-scoped) | D | C | A (if customer-adjacent) | A (DPIA / privacy review) | A (security review) | C | A (that BU) |
| **Tool approval for GA rollout** | D | A (if MRM-scoped) | A | A | A | A | A (that BU) |
| **Tool deprecation / consolidation** (`mod-107 exercise-05`) | D | A (if MRM-scoped tool) | C | C | C | A | A (that BU) |
| **Vendor contract redlining** | C | C (MRM clauses if applicable) | A (regulatory-reporting clauses) | A | A (security clauses, BAA / DPA equivalents) | I | I |
| **Pilot exit decision** (GA vs retire vs extend) | D | A (if MRM-scoped) | A | C | A | A | A (that BU) |

#### C. Operational and run-the-program decisions

| Decision | Enablement | MRM | Compliance | Legal / Privacy | CISO | Council | BU Sponsor |
|---|---|---|---|---|---|---|---|
| **Monthly adoption scorecard publication** | D | I | I | I | I | I | I |
| **Adoption-signal source selection** (what counts as "use") | D | C | C | C | C | I | C |
| **Champion recruitment and recognition** | D | I | I (incentive-design review) | C | I | I | C |
| **Communications publication** (`mod-105 exercise-03`) | D | I | C (regulatory-claims review) | A (brand / public-statement review) | I | I | I |
| **Training-content refresh** (periodic or triggered) | D | C (if MRM scope) | A (regulatory-content review) | A | I | I | I |
| **Office-hours / workshop operations** | D | I | I | I | I | I | I |
| **L&D delivery partnership** (`mod-104 exercise-07`) | D | I | C | I | I | I | I |
| **Vendor-management check-in cadence** (per `mod-111` / `mod-107`) | C | C (if MRM scope) | C | C | C | I | I |

#### D. Incident / exception / change-request decisions

| Decision | Enablement | MRM | Compliance | Legal / Privacy | CISO | Council | BU Sponsor |
|---|---|---|---|---|---|---|---|
| **AI-touching incident declared** (`mod-109`) | C | C (if MRM scope) | C (if regulatory scope) | C (if privacy scope) | A (declaring authority) | I | I |
| **Incident response — enablement-side actions** (communications, policy refresh, training refresh) | D | I | C | C | C | I | I |
| **Incident response — regulator notification decision** | I | C | A | A | C | I | I |
| **Policy exception request** (business asks to use a prohibited data class or workflow) | C | A (if MRM scope) | A | A | A | A | I |
| **Executive-sponsored exception** (an L60+ pushes for a shortcut) | C | A | A | A | A | A | I |
| **Mid-cycle regulation change** (new rule, new guidance) | C | C | A (ownership) | A | C | A | I |
| **New high-risk use-case request** (BU proposes a novel AI use that may touch MRM scope) | C | A | A | A | C | A | A (that BU) |
| **De-scope / shutdown decision** for a tool (significant policy-driven) | C | A (if MRM scope) | A | A | A | A | A (that BU) |

#### E. Reporting and attestation decisions

| Decision | Enablement | MRM | Compliance | Legal / Privacy | CISO | Council | BU Sponsor |
|---|---|---|---|---|---|---|---|
| **Internal council pre-read authoring** (`mod-103 exercise-04`) | D | C | C | C | C | A | C |
| **Board-visible AI update** (risk-committee or audit-committee material) | C | C | A | A | C | A | I |
| **Regulator-facing attestation (where applicable)** | I | A (model-risk sections) | A (overall) | A | A (security sections) | A | I |
| **External audit / assurance engagement** (ISO/IEC 42001 prep, third-party assurance) | C | C | A | A | A | A | I |
| **Workforce-training attestation** (that staff have been trained — the HIPAA-and-EU-AI-Act-adjacent evidence duty) | D | I | A | A | I | I | I |

### 2.3 How the line moves by industry — a short crosswalk

The archetype carries a **US investment-bank-affiliated depository institution**. Several of the rows above shift position in other regulated industries. This section is deliberately short because the deep walk-throughs are in Exercises 04 (policy) and 05 (training); the point here is only to show that the artifact shape is portable.

| Row | In this archetype (US bank) | In a US health system | In an EU multinational (deployer) | In a US federal contractor |
|---|---|---|---|---|
| Tool classification — SR 11-7 "model"? | MRM is A | N/A (replace with "SaMD?" question, Regulatory Affairs is A) | N/A (replace with Article 6 / Annex III question, Legal is A) | N/A (CUI touch? Security + contracting office is A) |
| Tool approval for GA rollout | MRM is A, Compliance is A, CISO is A | Compliance (CCO) is A, Privacy Officer is A, CMIO is A, CISO is A | DPO is A, Legal is A, works-council consulted | Contracting Office is A, CISO is A, FedRAMP posture gate |
| Risk-appetite statement | MRM is A | Quality & Patient Safety is A alongside CCO | Legal / DPO are A, with works-council consultation | Contracting Office + CISO are A |
| Regulator notification decision | Compliance is A, legal counsel involved | Compliance (CCO) is A for HIPAA breach; separate decisions for state law | Legal / DPO are A for GDPR; Market-surveillance authority notification for AI Act Article 73 serious-incident, Compliance is A | Contracting Office is A for incident reports to the contracting activity |
| Workforce-training attestation | HR / L&D and MRM | HR / L&D and Compliance (HIPAA workforce training) | HR / L&D and DPO (AI Act Article 4 evidence) | HR / L&D and contracting office (CMMC/awareness attestation) |

Pattern: the governance constellation changes, but the *shape* of the artifact — DACI, decision-class ordering, named counterparts — does not.

### 2.4 Rationale — why this split, not another

Three design choices account for the shape of the matrix above:

1. **Enablement is Driver on most operational rows, Co-author on most policy rows, Consulted on most authoritative rows.** This is deliberate. The failure mode on the left (enablement as Approver on policy) centralizes authority the role is not accountable to carry; the failure mode on the right (enablement as Consulted on champion-network operations) centralizes authority governance is not operationally equipped to carry. The matrix respects both.
2. **MRM is Approver on every row that touches a "model" or the model-risk-managed decision path.** In a bank, SR 11-7 expectations attach to any model used in decision-making. AI tools that output recommendations consumed by human decision-makers in credit, lending, AML, sanctions, or trading-adjacent workflows are MRM-scoped by default; the classification *question* is on the Enablement Lead to route, the *answer* is MRM's to issue. <!-- verify-with-sme: SR 11-7 is 2011 OCC / FRB joint guidance; confirm the organization's Internal MRM policy for how it maps AI tools to the "model" definition. -->
3. **The AI Governance Council is Approver on program-level and tool-level GA decisions, and on exception requests.** Operational decisions do not route through the council; this preserves council capacity for the decisions that actually need it. A council that approves training-content refreshes is a council that has stopped mattering.

### 2.5 Edge cases — explicit enumeration

The matrix is tested at the edges. Six named edge cases follow with the decision owner and the specific trigger that routes it.

1. **An executive sponsor at L60+ pushes for an AI tool to be approved for a prohibited data class.** → Row D, "Executive-sponsored exception." The Enablement Lead is **Consulted**; MRM, Compliance, Legal / Privacy, CISO, and the Council are all **Approvers**. The Enablement Lead's job is to document the ask, surface the risks in writing, and route to the Council — not to absorb the exception into operational practice. The failure mode is for the Enablement Lead to accept the exception verbally and shield the sponsor from governance; this failure, repeated, is what ends an Enablement Lead's career in a regulated industry.
2. **An AI-touching incident is declared during a weekend.** → Row D, incident response. CISO holds **A** (declaring authority), with the enablement-side actions (communications, refresh, triage) owned by the Enablement Lead the Monday after. The Enablement Lead does not have declaring authority. If the incident involves a model-risk-managed decision, MRM joins the response. If it involves PHI or GDPR personal data, Privacy joins.
3. **A new regulation or supervisory letter is published mid-cycle.** → Row D, mid-cycle regulation change. Compliance is **A**; the Enablement Lead is **Consulted** and is responsible for translating the Compliance determination into policy / SOP / training updates within a committed turnaround (per the partnership contract from `mod-107 exercise-04`).
4. **A business unit proposes a novel AI use that may touch MRM scope.** → Row D, new high-risk use-case request. The Enablement Lead's role is intake and routing; MRM and Compliance decide whether the use is in scope and whether it can proceed. Enablement reclaims **D** once the decision is made and the use enters the standard rollout path.
5. **The organization is asked by a regulator to attest to AI workforce training.** → Row E, regulator-facing attestation. The Enablement Lead is **Informed** (the attestation is signed by Compliance / MRM / an officer with authority); Enablement produces the evidence package per `mod-108 exercise-01`.
6. **A tool is being deprecated against a BU sponsor's objection.** → Row B, tool deprecation. If the tool is MRM-scoped, MRM is **A** on the deprecation; otherwise, the Council is **A**. The Enablement Lead is **D** on the decision proposal and on the communications / migration plan; the BU sponsor is **A** on the migration schedule but not on the deprecation itself.

### 2.6 Review cadence and triggers

The artifact is signed at the start of the planning cycle and re-signed:

- **Annually** at the full-year planning cadence (per `mod-107 exercise-04` annual strategic).
- **Off-cycle** on any of: organizational restructure that changes governance reporting lines, new regulatory guidance that changes an Approver, an incident whose post-mortem recommends a DACI change, a new in-scope business unit, a new in-scope regulator (e.g., a new cross-border subsidiary).
- **Expiry on silence.** If the artifact is not re-signed within 14 months, it lapses; operations continue under the lapsed artifact, but the Enablement Lead must raise the lapse to the Council at the next meeting. This prevents the artifact from drifting into "signed once and forgotten" status.

### 2.7 Appendix — current signers (people-named, versioned separately)

<!-- org-specific: maintain the current-signer list in a separate appendix file so people's names changing does not re-version the artifact body. -->

## 3. Validation steps

1. **Every row carries explicit A for exactly one party.** DACI discipline says one Approver per decision. Multiple A's on a row (common failure mode) means the decision has no owner and will stall in a tie.
2. **Enablement is never Approver on a policy row, intake-sign row, or exception row.** Enablement is Driver on operational rows and Co-author / Consulted on policy rows. An artifact that gives Enablement A on an AUP sign-off row is role-confused.
3. **MRM is Approver on every row in Section B flagged "if MRM-scoped" and on every exception row in Section D.** If MRM is missing from a model-risk-adjacent row, the artifact under-weights SR 11-7 posture.
4. **Compliance is Approver on regulator-facing, policy, and training-content-refresh rows.** A Compliance-light artifact is not fit for regulated-industry use.
5. **The council is Approver only on program-level, exception, and incident-escalation rows — not on operational rows.** If the council is Approver on monthly scorecard publication, the matrix has centralized operations where it should not.
6. **BU sponsors are Approver on their BU's tool approval, training playbook, and migration schedule — not on program-wide rows.** BU sponsors should not be in the A column on AUP or on the champion-network charter.
7. **Industry crosswalk (Section 2.3) is present with at least three non-archetype industries.** The teaching point is that the line moves; a single-industry artifact misses the point.
8. **Edge cases (Section 2.5) are enumerated with at least six entries** covering: executive-sponsored exception, weekend incident, mid-cycle regulation, novel use-case, regulator attestation, contested deprecation. Fewer than six, or missing the executive-exception row, is a fail — the executive-exception row is the single most important edge case for an Enablement Lead in a regulated industry.
9. **Cadence (Section 2.6) includes both periodic and triggered re-signing** and defines an expiry behavior. A sign-and-forget artifact fails.
10. **`org-specific` and `verify-with-sme` markers** are present on the regulator constellation line, on specific SR 11-7 interpretation, and on any specific supervisory expectation. Unmarked regulator-specific claims are a hard fail.

## 4. Rubric / review checklist

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | DACI discipline — one A per row, consistent role notation | 10 | Multi-A rows, missing A, or inconsistent notation. |
| R2 | Enablement is Driver on operational rows, Co-author / Consulted on policy rows, not Approver on policy / intake / exception | 15 | Enablement is Approver on an authoritative row, or Driver on an authoritative row. |
| R3 | MRM is Approver on every model-risk-adjacent row, with the SR 11-7 question explicit in the classification rows | 15 | MRM missing from model-risk-adjacent rows, or SR 11-7 question absent. |
| R4 | Compliance is Approver on regulator-facing, policy, and training-content-refresh rows | 10 | Compliance absent from regulator-facing or training-attestation rows. |
| R5 | AI Governance Council is Approver only on program-level / exception / incident rows — not on operational rows | 10 | Council centralized on operational rows, or absent from exception rows. |
| R6 | BU sponsor involvement scoped to their BU's decisions only | 5 | BU sponsor in A on a program-wide or cross-BU row. |
| R7 | Industry crosswalk (Section 2.3) covers at least three non-archetype industries | 10 | Only the archetype industry presented; no demonstration that the line moves. |
| R8 | Edge cases enumerated — at least six, including executive-sponsored exception, weekend incident, mid-cycle regulation change, novel use-case, regulator attestation, contested deprecation | 15 | Fewer than six edge cases, or missing the executive-exception row. |
| R9 | Review cadence covers annual + triggered re-signing + expiry behavior | 5 | Artifact lacks triggered re-signing or expiry. |
| R10 | `org-specific` and `verify-with-sme` markers on regulator-specific claims; no fabricated supervisory-expectation statements | 5 | Unmarked quoted supervisory specifics. |

**Pass threshold:** ≥ 80 / 100 and no R2 / R3 / R8 fail. R2 (enablement role discipline) and R3 (MRM scope) are the discriminators between an artifact that holds under regulatory scrutiny and one that collapses.

## 5. Common mistakes

- **Enablement as Approver on the AUP.** The most common failure. In regulated industries, the AUP is co-authored by enablement and approved by Compliance / Legal. An Enablement Lead who signs the AUP alone has absorbed authority the role does not carry and will bear accountability the role cannot support in an audit.
- **Treating "governance" as a monolith.** Governance in a regulated industry is a constellation — MRM, Compliance, Legal, Privacy, CISO, the Council — each with distinct mandates. An artifact that puts a single "Governance" column in the DACI collapses the structure that actually makes decisions.
- **Omitting MRM for AI tools that "aren't really models."** In a bank, if the tool's output is consumed by a human decision-maker in a model-risk-managed path, the tool is likely in-scope regardless of how the Enablement Lead would like to classify it. The classification decision is MRM's, and the Enablement Lead's job is to route the question, not to answer it. Misclassifying a tool as out-of-scope and then having an MRM review retroactively re-classify it is a well-known failure pattern and is often what leads to a public supervisory finding.
- **Collapsing to "enablement does adoption, governance does policy."** The line moves per decision. Enablement co-authors policy; governance co-sponsors adoption KPIs. A function-level collapse loses the decision-level discipline and produces an artifact that is simultaneously too narrow and too broad.
- **No executive-exception row.** The single most important edge case. An Enablement Lead who has not thought through "what happens when an L60+ asks for a shortcut" will handle their first live exception badly. The matrix names the route explicitly.
- **Missing cadence and expiry.** Signed-once-and-forgotten is the long-run failure mode. The artifact lapses on silence precisely to force re-signing at least annually.
- **Centralizing operational rows on the council.** If the council is Approver on the monthly scorecard, the council's capacity is spent on operations and is unavailable for the decisions that genuinely need it. The matrix reserves council capacity for program-level, exception, and incident rows.
- **Regulator-specific claims without `verify-with-sme`.** SR 11-7 interpretation is organization-specific; a learner's assertion that "any LLM is in scope" or "LLMs are out of scope" is unverifiable in the abstract. The artifact carries the claim as a question the organization's MRM policy answers.
- **Role-confusing the BU sponsor.** BU sponsors are Approver on their BU's tool-approval and migration decisions. They are not Approver on program-wide artifacts. A BU sponsor on the AUP sign-off row is role-confused.
- **Writing the artifact in people-names rather than role-names.** People leave. The DACI uses role-names ("head-of-ai-governance (L60)"); the current signer list lives in Appendix 2.7, versioned separately.

### 5.1 Stretch — re-running the split in a non-regulated industry

For a non-regulated industry (a commercial SaaS vendor, a consumer-internet company, a late-stage startup), the same artifact shape applies but the line shifts markedly left — enablement is Driver on more rows, Approver on a handful of tool-tier decisions, and the governance constellation collapses to a smaller set (Legal, Security, maybe Privacy). Running the same artifact in both contexts is the fastest way to internalize the "regulatory gravity moves the line" lesson.

The absence of regulatory gravity does not remove the need for the artifact; it changes which rows collapse. In particular, the executive-exception row remains load-bearing in every industry; executive-exception discipline is not regulatory, it is organizational.

## 6. References

- **Learning material (local):**
  - [mod-101 — Role and the Org-wide Enablement Operating Model](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-101-role-and-the-org-wide-enablement-operating-model) — the baseline operating model the split sits inside.
  - [mod-103 — Policy Co-authoring with Governance](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-103-policy-co-authoring-with-governance) — the AUP, SOP, intake, and council pre-read artifacts this matrix governs.
  - [mod-107 — Budget, ROI, Build-vs-Buy at Org Scope](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-107-budget-roi-and-build-vs-buy-at-org-scope), exercise 04 — the partnership-contract pattern this artifact extends to the governance constellation.
  - [mod-109 — AI Incident Response and Enablement-Side Rollback](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-109-ai-incident-response-and-enablement-side-rollback) — the incident path referenced in Section D rows.
  - [mod-111 — AI CoE Operations, Vendor Management, and Cross-functional Leadership](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-111-ai-coe-operations-vendor-management-and-cross-functional-leadership) — the vendor-management cadence referenced in Section C.
- **Official standards and frameworks:**
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — the GOVERN function is the authority frame; MAP / MEASURE / MANAGE are the operational frames split across the matrix.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — threat taxonomy referenced in CISO-column rows (Section B tool approvals).
  - [MITRE ATLAS](https://atlas.mitre.org/) — adversarial-technique vocabulary for Security-side approvals.
- **Regulatory references (verify exact citation and current applicability before relying on):** SR 11-7 / OCC 2011-12 model-risk-management guidance; OCC Heightened Standards; FFIEC IT examination handbooks; SEC / FINRA conduct rules where a broker-dealer is in the group structure; EU AI Act for cross-border; HIPAA / 42 CFR Part 2 for US health systems; NIST SP 800-171 / CMMC for US federal contractors. <!-- verify-with-sme: re-confirm specific supervisory expectations with the organization's Compliance / MRM / Legal partners before relying on this artifact in a live decision. -->
