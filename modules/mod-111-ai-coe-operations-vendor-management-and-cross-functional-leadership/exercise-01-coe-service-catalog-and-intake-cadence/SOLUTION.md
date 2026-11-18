# Exercise 01 — CoE Service Catalog and Intake Cadence — Reference Solution

> Module: `mod-111-ai-coe-operations-vendor-management-and-cross-functional-leadership`
> Exercise type: design / worked example
> Exercise brief: [`lessons/mod-111-ai-coe-operations-vendor-management-and-cross-functional-leadership/exercises/exercise-01-coe-service-catalog-and-intake-cadence.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-111-ai-coe-operations-vendor-management-and-cross-functional-leadership/exercises/exercise-01-coe-service-catalog-and-intake-cadence.md) (in the learning repo)

## 1. Solution overview

The deliverable is a two-artifact pack the AI Center of Excellence (CoE) publishes and maintains:

1. A **service catalog** — the written list of services the AI CoE offers to the rest of the organisation, with service name, owner (role), inputs required, outputs produced, SLA, and the DACI interlock with the requesting function.
2. An **intake cadence** — the written rhythm by which incoming requests are received, triaged, prioritised, routed, and reported back on.

The catalog answers *"what can I ask the CoE for?"*. The intake cadence answers *"what happens when I ask?"*. Without either, the CoE becomes an ad-hoc concierge whose queue silently fills with inbound requests that no downstream function can plan around.

Posture checks this solution encodes:

- **Every service is addressed to a named consumer role, not "the business".** A service that is for everyone is for no one; intake volume explodes and the CoE cannot staff any one service to competence.
- **Every service names what it is NOT.** Without a stated out-of-scope boundary, scope drift is inevitable and the service becomes synonymous with "whatever people asked for last".
- **The catalog differentiates services from products.** A service is bounded, repeatable work the CoE performs on request (e.g., *governance intake review*, *vendor vetting*, *measurement-plan co-design*). A product is a long-lived asset the CoE maintains (e.g., *the AI policy*, *the enablement scorecard*). Confusing the two over-commits the CoE roster.
- **Intake is tiered by complexity, not by requester seniority.** A 30-minute tooling question and a six-week commissioning engagement are different services; both have intake paths; neither is routed by who is asking.
- **Every service names a kill / de-scope criterion.** Services the CoE *stops* offering are a feature of the catalog, not a bug.
- **The intake cadence is three-tempo** — continuous intake, weekly triage, quarterly portfolio — and the portfolio tempo is the one that governs capacity.
- **Decision rights are named per service.** The CoE is Driver on some services (e.g., policy co-authoring); Consult on others (e.g., technical architecture); Informed on others (e.g., platform engineering sprint planning). Being honest about which is which is what lets other functions co-operate rather than route around.
- **Role-name addressing throughout.** The catalog survives a re-org; the specific individuals in each role rotate without the artifact being rewritten.

## 2. Implementation — worked answer

The pack consists of two documents. Both are published on the CoE's internal landing page and are referenced by the mod-103 AI Policy, the mod-106 scorecard, and the mod-102 tool-intake questionnaire.

### 2.1 Worked scenario

- CoE scope: an AI Center of Excellence with a staffed roster of ~6 people (AI Enablement Lead, two Enablement Partners, an Applied AI Engineer embed, a Governance Partner embed from Legal/privacy, an Enablement Operations Analyst). `<!-- org-specific: calibrate roster to the learner's actual staffing -->`
- Organisational scope: ~2,500 employees across four business units. `<!-- org-specific: calibrate to the learner's org size -->`
- Fiscal tempo: quarterly OKRs; monthly executive review; weekly operational stand-up.
- Downstream partner functions: Applied AI Engineering, Procurement, Security, Legal/privacy, Finance, L&D, Internal Comms.
- Current pain point before the catalog: inbound requests arrive via DMs, hallway conversations, and three separate ticket systems; the CoE has no shared view of what it has committed to; partner functions have no way to predict CoE capacity.

### 2.2 Document 1 — `ai-coe-service-catalog.md`

```
AI CoE Service Catalog
Owner:            AI Enablement Lead (this role)
Catalog version:  <!-- org-specific: version and effective date -->
Next review:      Quarterly, per the intake-cadence companion document
Audience:         All employees; routed from the CoE landing page
```

#### Section 1 — Catalog scope

The catalog lists the services the AI Center of Excellence offers. It does **not** list:

- Platform engineering, infrastructure operations, or model-hosting services — these are owned by Applied AI Engineering and their platform owners.
- Procurement execution (contracting, PO issuance) — owned by Procurement; the CoE provides inputs via the Vendor Vetting service (Section 2.4).
- Legal review, privacy impact assessments, or security assurance as sign-offs — owned by Legal/privacy and Security; the CoE provides inputs via Governance Intake Review (Section 2.3).
- Data engineering, ETL, data-quality remediation — owned by the data platform function.

A request that routes to any of these functions directly is not a CoE request. The CoE will *route* such requests but will not *perform* them.

#### Section 2 — Services

Each service row includes: service name, consumer (role names), description, inputs required, outputs produced, SLA (clock-time from intake acceptance), CoE decision role, downstream interlock, kill / de-scope criterion.

##### 2.1 Tooling Advisory Consultation

| Field | Value |
|---|---|
| Consumer | Any people-manager or individual contributor considering a new AI-assisted tool |
| Description | A ≤ 30-minute consultation that returns: "is this tool in scope for the organisation's current AUP?", "has it been vetted?", "if not, what is the intake path?", and "what is the alternative in-scope tool?" |
| Inputs required | Tool name, vendor, intended use, requester's business unit and role |
| Outputs produced | A written advisory (one paragraph) with verdict (in-scope / needs intake / out-of-scope), referenced policy clause, and next step |
| SLA | 2 business days from intake acceptance |
| CoE decision role (DACI) | D on the advisory; C on any downstream Security / Legal review |
| Downstream interlock | Routes to Vendor Vetting (Section 2.4) if the tool is not yet in-scope |
| Kill / de-scope | Rolled into Vendor Vetting when inbound volume consistently requires > 5 same-tool consultations per quarter — at that volume, the tool has a procurement decision pending and is not an advisory question |

##### 2.2 Policy and SOP Co-Authoring

| Field | Value |
|---|---|
| Consumer | Business-unit leader or functional owner with a workflow that requires AI-specific policy or SOP updates |
| Description | The co-authoring engagement scoped in mod-103: joint drafting of AUP amendments, SOP addenda, or role-specific guidance; governance-council pre-read management |
| Inputs required | Workflow description, current SOP (if any), mod-103 pre-read template completed, governance-council slot requested |
| Outputs produced | Ratified policy or SOP addendum, change-log entry, communications pack for the affected population |
| SLA | 30 calendar days to ratified draft; governance-council slot cadence governs ratification |
| CoE decision role (DACI) | D on the drafting; C on governance-council ratification; D on the comms rollout |
| Downstream interlock | Governance council (A on ratification); Internal Comms (C on comms pack); L&D (I for curriculum updates per mod-104) |
| Kill / de-scope | De-scoped if the workflow is better served by a tool-specific SOP produced by the tool's vendor — the CoE does not maintain per-tool SOPs that a vendor will keep current |

##### 2.3 Governance Intake Review

| Field | Value |
|---|---|
| Consumer | Any project sponsor proposing a new AI-touching workflow, tool, or dataset |
| Description | The pre-governance-council review that lands a complete, routable intake packet in front of the governance council; produces a go / needs-work / needs-redirect verdict before formal council time is consumed |
| Inputs required | Mod-102 intake questionnaire completed, data classification per mod-103, risk posture mapped against `owasp-ml-top-10`, `mitre-atlas`, and `nist-ai-rmf`, sponsor named |
| Outputs produced | Review memo (2 pages max) with verdict, outstanding items, and routing recommendation |
| SLA | 5 business days from a *complete* intake packet; incomplete packets are returned same-day |
| CoE decision role (DACI) | D on the review memo; C on the governance-council decision |
| Downstream interlock | Governance council (A on go/no-go); Security intake, Legal/privacy review (C in parallel) |
| Kill / de-scope | Not de-scoped — this service is a product, not a service, once intake volume exceeds 20 reviews per quarter (see Section 3 on products below) |

##### 2.4 Vendor Vetting

| Field | Value |
|---|---|
| Consumer | Procurement AI-sourcing lead, or any sponsor proposing an external AI vendor |
| Description | The vetting engagement scoped in Exercise 02 of this module: evidence-gathered review against the certification rubric, scored verdict, and a renewal-due date |
| Inputs required | Vendor name, product scope, sponsor, mod-102 intake questionnaire, Security intake packet, Legal/privacy packet, Finance envelope per mod-107 Exercise 01 |
| Outputs produced | Signed vendor certification record (tier, scope, expiry, review-cadence), stored in the vendor registry |
| SLA | 15 business days from a complete packet; re-certification lead time starts 60 days before expiry |
| CoE decision role (DACI) | D on the certification record; A on tier; C on contracting (Procurement is A) |
| Downstream interlock | Procurement (A on contracting); Security (A on security tier); Legal/privacy (A on DPA/sub-processor posture); Finance (A on envelope per mod-107) |
| Kill / de-scope | De-scoped for a vendor when consolidation under mod-107 Exercise 05 retires the vendor; retired vendors remain in the registry with a `retired` status for audit |

##### 2.5 Measurement-Plan Co-Design

| Field | Value |
|---|---|
| Consumer | Sponsor of a tool or workflow about to enter limited-GA or GA |
| Description | Joint design of the measurement plan (per mod-106 and mod-110 Exercise 04): indicator families, review cadence, kill-or-grow thresholds, instrumentation ownership |
| Inputs required | Commissioning brief or vendor certification record, business-sponsor commitments on target metrics, Applied AI Engineering commitments on instrumentation feasibility |
| Outputs produced | Ratified measurement plan, three-tempo review cadence (weekly eval, monthly operational, quarterly strategic), scorecard rows for the mod-106 executive view |
| SLA | 10 business days from intake; condition of entry to limited-GA, not an output of it |
| CoE decision role (DACI) | D on the plan; C on engineering instrumentation feasibility; A on the scorecard rows |
| Downstream interlock | Business sponsor (A on business targets); Applied AI Engineering (A on instrumentation); Finance (C on the cost-family rows per mod-107) |
| Kill / de-scope | De-scoped when the tool is sunset per mod-110 Exercise 04 kill thresholds; the measurement-plan row leaves the scorecard within one review cycle of sunset |

##### 2.6 Training Program Design and Rollout Support

| Field | Value |
|---|---|
| Consumer | L&D partner or BU leader responsible for a specific role population |
| Description | Co-design of role-specific AI literacy curriculum (per mod-104); training-reach and learner-outcome instrumentation; champion-network support (per mod-105) |
| Inputs required | Role population description, current literacy baseline, in-scope tools per tool catalog, ratified SOP (per 2.2) |
| Outputs produced | Curriculum design doc, instructor-led slot plan, asynchronous module manifest, assessment approach, training-reach instrumentation plan |
| SLA | 45 calendar days to piloted curriculum; 90 calendar days to broad rollout |
| CoE decision role (DACI) | C on content accuracy; D on AI-specific pedagogical shape; L&D is D on delivery infrastructure |
| Downstream interlock | L&D (A on delivery); Internal Comms (C on rollout comms); Business sponsor (A on cohort selection) |
| Kill / de-scope | Retired when the curriculum is embedded in L&D's standing catalog and no longer requires AI-specific co-authoring |

##### 2.7 Incident Response — Enablement-Side

| Field | Value |
|---|---|
| Consumer | Incident commander (per mod-109) or sponsor of a tool experiencing an AI-specific incident |
| Description | The enablement-side incident-response commitments per mod-109: user-facing comms, SOP rollback, training-content hotfix, champion-network field-reporting coordination |
| Inputs required | Incident ticket, severity classification, affected tool / workflow, affected user population |
| Outputs produced | User-facing comms, SOP addendum or rollback note, training-content hotfix, post-incident review input |
| SLA | Response within 1 business day for Sev-2+; same-day for Sev-1 |
| CoE decision role (DACI) | D on enablement-side comms and SOP; C on engineering rollback (Applied AI Engineering is D); C on the post-incident review (per mod-109) |
| Downstream interlock | Applied AI Engineering (D on technical rollback); Internal Comms (C on comms channels); Governance council (I on severity escalation) |
| Kill / de-scope | Not de-scoped — this service is on 24/7 standby posture |

##### 2.8 Executive Reporting Partnership

| Field | Value |
|---|---|
| Consumer | Executive sponsor of the CoE (CIO / COO / chief-of-staff) and the executive consumers of the mod-106 scorecard |
| Description | Weekly scorecard, monthly narrative, quarterly board-ready review outline (per mod-106 exercises); ad-hoc exec-request response |
| Inputs required | Access to indicator instrumentation, governance-council minutes, vendor registry, incident ledger |
| Outputs produced | Weekly scorecard; monthly narrative memo; quarterly board-ready review (per mod-106 Exercise 03); ad-hoc briefings |
| SLA | Weekly scorecard by Monday 09:00 for the prior week; monthly narrative within 5 business days of month-end; ad-hoc within 2 business days |
| CoE decision role (DACI) | D on the scorecard and narrative; C on the exec sponsor's decisions |
| Downstream interlock | Exec sponsor (A on scorecard thresholds); Finance (C on cost rows per mod-107); Governance council (I on risk-indicator rows) |
| Kill / de-scope | Not de-scoped — this is a product (see Section 3) once stable; the service is the ongoing operation of the product |

#### Section 3 — Products (not services)

Products are long-lived CoE-owned assets. They are **not** on-request work; they are the artifacts that *enable* on-request work.

| Product | Steward (role) | Reviewed |
|---|---|---|
| AI Acceptable Use Policy and allied SOPs (per mod-103) | AI Enablement Lead + Governance Partner embed | Quarterly |
| In-scope tool catalog (per mod-102) | AI Enablement Lead | Monthly (adds); quarterly (full review) |
| Vendor registry (per Exercise 02) | AI Enablement Lead + Governance Partner embed | At each certification / re-certification |
| Executive scorecard (per mod-106) | AI Enablement Lead | Weekly |
| AI Literacy curriculum library (per mod-104) | AI Enablement Lead + L&D partner | Quarterly |
| Champion-network charter and roster (per mod-105 and Exercise 04 of this module) | AI Enablement Lead | Quarterly |
| Incident-response runbook library (per mod-109) | AI Enablement Lead + Applied AI Engineering lead | After each Sev-2+ incident; quarterly otherwise |
| Measurement-plan template library (per mod-106 and mod-110 Exercise 04) | AI Enablement Lead | Quarterly |

#### Section 4 — What the CoE does not do

Explicit out-of-scope for the CoE as a whole:

- Build, host, or operate inference infrastructure — this is Applied AI Engineering and the data-platform function.
- Make procurement decisions or sign contracts — this is Procurement.
- Make security or privacy sign-off decisions — this is Security / Legal; the CoE provides the intake-review memo that *supports* their decision.
- Operate as help-desk for individual tool support tickets — tool-specific support routes to the tool's vendor or to IT service desk.
- Deliver instructor-led training on general software topics — L&D owns this; the CoE co-authors only the AI-specific shape.
- Own the departmental OKRs of other functions — the CoE lands scorecard rows on the executive scorecard; it does not run other functions' OKRs.

#### Section 5 — Catalog governance

- The catalog is re-reviewed quarterly at the strategic review (Exercise 03).
- Each service row is reviewed at least annually with its named downstream interlocks.
- A new service enters the catalog only after one quarter of pilot operation with an explicit pilot-end date.
- A service leaves the catalog when it meets its stated kill / de-scope criterion or when the quarterly review votes to retire it.

### 2.3 Document 2 — `ai-coe-intake-cadence.md`

```
AI CoE Intake Cadence
Owner:            AI Enablement Lead (this role)
Cadence version:  <!-- org-specific: version and effective date -->
Operates in:      <!-- org-specific: ticketing system name -->
Audience:         CoE roster; partner-function interlocks; any catalog consumer
```

#### Section 1 — Intake channel

A single intake channel; one place; one form. The channel is the *only* way a request enters the CoE's work queue. Hallway conversations, DMs, and email requests are politely redirected to the channel. This is the single most important control.

- Channel: `<!-- org-specific: ticket queue / portal URL -->`.
- Form fields: requester (role + name), consumer business unit, requested service (dropdown drawn from the catalog), business context (one paragraph), urgency (routine / this-quarter / blocking-decision-this-week), sponsor named, attachments (intake questionnaire, SOP, etc.).
- The form validates: requested service exists in the current catalog; sponsor is named at a role level; urgency is self-selected with a one-line justification.
- Triage of an incomplete form returns it same-day with a "please complete the following" note; it does not enter the queue.

#### Section 2 — Three tempos

| Tempo | Rhythm | Participants (role names) | Purpose |
|---|---|---|---|
| **Continuous intake** | Business hours | On-duty Enablement Partner (rotates weekly) | Form intake, first-touch acknowledgement within 1 business day, de-duplication against existing tickets, incomplete-form returns |
| **Weekly triage** | 45 minutes, same slot each week | AI Enablement Lead, both Enablement Partners, Enablement Operations Analyst; Applied AI Engineering embed as C | Review inbound of the week; scope-sizing (T-shirt: S / M / L); route to service owner; set SLA start; identify cross-service dependencies; flag items for the monthly operational review |
| **Quarterly portfolio** | Half-day, aligned to the fiscal quarter | Weekly attendees + exec sponsor + Procurement AI-sourcing lead + Governance Partner embed + L&D partner + Internal Comms partner | Review the quarter's intake volume by service, by business unit, by urgency; review completions vs SLA; review the kill / de-scope criteria for each service; set the next quarter's capacity commitment; identify services for retirement or promotion-to-product |

#### Section 3 — Triage decisions

Weekly triage produces exactly one of these verdicts per inbound request:

| Verdict | Meaning | Clock starts for which SLA |
|---|---|---|
| **Accept** | The request matches a catalog service, the inputs are complete, capacity is available this week | The catalog SLA for that service |
| **Accept with scheduled start** | Catalog match, inputs complete, but current-week capacity is full; a start date is committed inside the quarter | The catalog SLA from the committed start date |
| **Return — inputs incomplete** | Needs completion of the intake questionnaire, data classification, or sponsor confirmation | No clock; re-enters triage when complete |
| **Route to partner function** | The request is better served by Procurement / Security / L&D / Applied AI Engineering directly; the CoE provides the routing note | No CoE clock; the routing note itself is a 1-business-day output |
| **Out-of-scope — decline with alternatives** | The request matches no catalog service and no partner function cleanly owns it; the CoE declines in writing with ≥ 1 alternative path | 1 business day for the written decline |
| **Promote to portfolio** | The request is larger than a single service invocation (multi-quarter engagement, cross-BU program) and escalates to the quarterly portfolio review for sizing | 1 business day for the escalation note; portfolio review sets capacity |

A triage that produces more than one verdict per request is a triage error; the request is returned to the queue and re-triaged.

#### Section 4 — Routing and ownership

Every accepted request has exactly one service owner — a single Enablement Partner (or the Lead, for Policy / SOP Co-Authoring and Governance Intake Review). Ownership is recorded in the ticket; re-assignment goes through triage, not DMs.

The service-owner responsibilities are:

- Execute the service per the catalog row.
- Record progress at the weekly triage checkpoint.
- Escalate at the monthly operational review if the SLA is at risk.
- Close the ticket with the named outputs attached.

#### Section 5 — Capacity accounting

Capacity is expressed in role-weeks of Enablement Partner time, not in headcount or in $-value. Current capacity for this scenario:

| Role | Role-weeks per quarter | Notes |
|---|---|---|
| AI Enablement Lead | 2.5 per quarter directly applied to catalog services; balance is leadership, exec partnership, product stewardship | Out-of-scope for standard service rotation |
| Enablement Partner (×2) | 9.0 each per quarter; two-person rotation | On-duty Enablement Partner carries continuous-intake duty for their week |
| Applied AI Engineer embed | 2.0 per quarter embedded in catalog services (primarily Governance Intake Review and Measurement-Plan Co-Design) | 0.5 FTE partnership, not full-time embed |
| Governance Partner embed | 3.0 per quarter embedded primarily in Policy / SOP Co-Authoring, Vendor Vetting, and Governance Intake Review | Legal/privacy partnership time |
| Enablement Operations Analyst | 10.0 per quarter — intake operations, reporting, documentation steward | Not a service-owner role; supports every service |

Capacity is *not* fungible across services — the Enablement Partners hold different sub-specialisations (training design, policy drafting, measurement design). Portfolio review balances allocation; it does not blindly aggregate.

#### Section 6 — Reporting and visibility

| Report | Rhythm | Audience |
|---|---|---|
| Intake-queue heartbeat | Daily auto-posted to the CoE Slack / channel | CoE roster + partner-function interlocks |
| Weekly intake digest | Monday 09:00 | Exec sponsor + partner-function leads |
| Monthly intake narrative | Within 5 business days of month-end | Exec sponsor (feeds mod-106 scorecard) |
| Quarterly portfolio review deck | At quarterly review | Exec sponsor, quarterly-review attendees |
| Annual service-catalog audit | End of fiscal year | Exec sponsor + governance council |

The daily heartbeat is a no-signal report when nothing is in motion; a heartbeat with zero inbound for two consecutive business days flags *either* a channel-discovery problem (people can't find the form) *or* a communications problem (the CoE isn't known). Either way, silence is a signal.

### 2.4 Decision rationale — why this shape, not another

- **Why services and products are separated.** The catalog answers *"what can I ask for?"*; the product list answers *"what does the CoE own that supports those asks?"*. Collapsing them produces a request queue where "the AI policy" and "a tooling advisory" sit side-by-side as inbound items, and the CoE spends weekly triage sorting the two. Separating them makes the request queue linear and the product list durable.
- **Why the catalog names a kill / de-scope criterion per service.** Services accumulate by default and never retire by default. A pre-committed kill criterion is the only way the catalog shrinks when conditions change (e.g., a per-tool consultation volume signalling consolidation, a curriculum embedded in L&D's standing catalog). Without it, the CoE's workload compounds.
- **Why decision rights are named per service, not once at the top.** The CoE is Driver on some services (policy co-authoring) and Consult on others (vendor contracting). Naming the role per row is what prevents a partner function from reading "the CoE owns AI" and assuming the CoE owns *their* decision. Per-row naming is what makes co-operation reliable.
- **Why the intake cadence is three-tempo.** Continuous intake is necessary to not block small requests (tooling advisory, Governance Intake Review on an urgent council slot). Weekly triage is necessary to prevent the queue becoming a first-come-first-served tyranny — the weekly rhythm is where competing urgency is reconciled. Quarterly portfolio is necessary to keep the catalog alive — services are added, retired, and rebalanced here, not between quarters.
- **Why capacity is expressed in role-weeks.** Headcount hides specialisation (the Enablement Partners are not fungible); $-value hides that AI Enablement's constraint is attention, not money. Role-weeks makes the capacity trade-off legible at portfolio time.
- **Why the single-channel discipline is non-negotiable.** Multi-channel intake is the dominant failure mode in observed CoEs — the CoE accumulates shadow commitments it does not know it has made. The single channel, even when politely redirected from DMs, is what makes the queue observable to anyone other than the person who took the request.
- **Why `nist-ai-rmf`, `owasp-ml-top-10`, and `mitre-atlas` are referenced on Governance Intake Review and Vendor Vetting.** Those are the official frameworks the governance council and Security partner already use. Naming them by ID on the intake-service rows is what lets downstream functions converge on a shared threat model without re-negotiating it per request.

## 3. Validation steps

1. **Catalog has ≥ 6 service rows.** A catalog with fewer services is either under-scoped (the CoE does more than it admits) or the services are too coarse (one row absorbing many sub-services that have different SLAs).
2. **Every service row has all nine fields populated** (consumer, description, inputs, outputs, SLA, CoE decision role, downstream interlock, kill / de-scope criterion, and consumer role names).
3. **Consumer roles are named at role level, not person level.** Grep the catalog for personal names.
4. **Every service row has a kill / de-scope criterion.** "Not de-scoped" is an acceptable value *only* with a stated reason (e.g., "24/7 standby posture").
5. **Services are separated from products.** The product section (Section 3 of the catalog) names ≥ 5 products and does not duplicate services.
6. **Section 4 (out-of-scope) is explicit.** "The CoE does not do X" lines are present and address at least Procurement, Security/Legal sign-off, data engineering, and help-desk support.
7. **Intake cadence has three named tempos** with rhythm, participants, and purpose per tempo.
8. **Triage produces one of six named verdicts.** No "it depends" catch-all.
9. **Every accepted request has a single service owner.** Ownership language is "one Enablement Partner (or the Lead)"; co-ownership is explicitly prohibited.
10. **Capacity is expressed in role-weeks** with role-level sub-specialisation acknowledged (Enablement Partners are not fungible).
11. **Single intake channel is named.** Multi-channel intake is explicitly redirected to the single channel.
12. **Reports have five rhythms** (daily, weekly, monthly, quarterly, annual) with named audiences.
13. **`org-specific` tags on all unverifiable specifics** (roster size, ticketing system, catalog version, population numbers).
14. **References to adjacent modules** (`mod-102`, `mod-103`, `mod-104`, `mod-105`, `mod-106`, `mod-107`, `mod-109`, `mod-110`) are specific — e.g., the Governance Intake Review row cites `owasp-ml-top-10`, `mitre-atlas`, `nist-ai-rmf` by ID.

## 4. Rubric / review checklist

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | Two-artifact pack (catalog + intake cadence) present | 5 | Only one artifact. |
| R2 | ≥ 6 catalog service rows with all nine fields populated per row | 15 | Fewer services, or missing fields. |
| R3 | Services separated from products; ≥ 5 products listed with stewards | 10 | Services and products collapsed into one list. |
| R4 | Explicit out-of-scope section naming Procurement, Security/Legal sign-off, data eng, help-desk | 5 | Missing or vague out-of-scope. |
| R5 | Every service has a kill / de-scope criterion (with stated reason if "not de-scoped") | 10 | Any service without a kill criterion. |
| R6 | Intake cadence has three tempos with rhythm, participants, purpose | 10 | Fewer tempos, or capacity accounting absent. |
| R7 | Triage produces one of six named verdicts | 10 | "It depends" or verdicts not enumerated. |
| R8 | Single-channel discipline named; multi-channel redirect called out | 5 | Multi-channel intake treated as normal. |
| R9 | Capacity in role-weeks with acknowledged non-fungibility across Enablement Partners | 5 | Capacity in $ or headcount only. |
| R10 | Decision rights named per service (DACI), with Driver / Approver distinct per row | 10 | One DACI at the top of the doc, or RACI-blurring. |
| R11 | Reports at five rhythms with named audiences | 5 | Fewer rhythms or no named audiences. |
| R12 | Role-name addressing throughout | 5 | People names used. |
| R13 | `org-specific` tags on unverifiable specifics | 5 | Unmarked quoted numbers / tools. |

**Pass threshold:** ≥ 85/100 and no R2 / R5 / R6 / R7 / R10 fail. R2 (catalog shape), R5 (kill criteria), R6 (intake cadence), R7 (triage verdicts), and R10 (per-service decision rights) are the five discriminators between a catalog the organisation uses and a catalog that becomes a dead link.

## 5. Common mistakes

- **Collapsing services and products into one list.** The catalog becomes a request queue that includes "the AI policy" as if someone could ask for it next Tuesday. Products are stewarded; services are requested. Keep them separate.
- **"Everything AI-related" as the CoE scope.** This is how the CoE becomes a help desk and never ships policy or training. The out-of-scope section is the most important section in the catalog.
- **Omitting the kill / de-scope criterion per service.** Services accumulate by default; they never retire by default. Without a pre-committed criterion, the CoE's queue grows monotonically and burns out.
- **Multi-channel intake treated as normal.** DMs, email, hallway, three ticket systems — this is the dominant failure mode. The single-channel discipline is not polite; it is operational.
- **Capacity expressed in $ or headcount.** Attention is the constraint. Role-weeks with named sub-specialisation is the honest unit. Headcount reads as "six people, six services, parity"; the honest picture is "two Enablement Partners with non-fungible sub-specialisations".
- **No weekly triage, "we triage as needed".** This is a queue that silently reorders by who talked to the Lead last. Weekly triage is the forcing function that reconciles urgency.
- **Service rows that don't name the consumer at role level.** A service for "the business" has no owner, no SLA, and no evaluability. Name the role.
- **DACI at the top of the document and nowhere else.** Per-service DACI rows are what make partner-function co-operation reliable. One top-level DACI collapses into "the CoE owns AI", which is false and resented.
- **Promising SLAs without capacity accounting.** An SLA table without role-week accounting is aspirational. Pair them.
- **Omitting the quarterly portfolio review.** Without it, the catalog never shrinks. Services are added between quarters and never retired.

### 5.1 Stretch — intake maturity curve

For a CoE operating in year 1, expect to run Section 2 (services) with ≤ 4 rows and the intake cadence with only two tempos (continuous + weekly). The quarterly portfolio review is run at month 6, not month 3 — there is not enough signal before that. Over year 2 the catalog grows to the full ≥ 6 rows, the quarterly portfolio becomes a standing cadence, and the annual service-catalog audit is introduced at the end of fiscal year 2. Attempting the full shape in quarter 1 of a new CoE produces heavy process over thin signal.

## 6. References

- **Learning material (local):**
  - [mod-102 — Selecting and Rolling Out AI Tools](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-102-selecting-and-rolling-out-ai-tools) — the tooling intake questionnaire referenced by Tooling Advisory Consultation and Governance Intake Review.
  - [mod-103 — Policy Co-authoring with Governance](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-103-policy-co-authoring-with-governance) — the AUP / SOP co-authoring pattern underlying the Policy and SOP Co-Authoring service.
  - [mod-104 — Training Programs and AI Literacy Curriculum](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-104-training-programs-and-ai-literacy-curriculum) — the curriculum pattern underlying the Training Program Design and Rollout Support service.
  - [mod-105 — Champion Networks and Change Management](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-105-champion-networks-and-change-management) — the champion-network pattern consumed by the CoP charter (Exercise 04).
  - [mod-106 — Outcome Measurement and Executive Reporting](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-106-outcome-measurement-and-executive-reporting) — the scorecard discipline underlying the Executive Reporting Partnership service.
  - [mod-107 — Budget, ROI, and Build-vs-Buy at Org Scope](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-107-budget-roi-and-build-vs-buy-at-org-scope) — Finance envelope and consolidation decisions referenced by Vendor Vetting and Measurement-Plan Co-Design.
  - [mod-109 — AI Incident Response and Enablement-Side Rollback](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-109-ai-incident-response-and-enablement-side-rollback) — the incident-response commitments underlying the Incident Response — Enablement-Side service.
  - [mod-110 — Commissioning Internal AI Tools and Custom Agents](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-110-commissioning-internal-ai-tools-and-custom-agents) — the commissioning brief and measurement plan consumed by Governance Intake Review and Measurement-Plan Co-Design.
  - [Exercise 02 — Vendor Vetting and Certification Rubric](../exercise-02-vendor-vetting-and-certification-rubric/SOLUTION.md) — the rubric executed inside the Vendor Vetting service.
  - [Exercise 03 — Quarterly Operating Ritual Plan](../exercise-03-quarterly-operating-ritual-plan/SOLUTION.md) — the quarterly portfolio review fits inside the broader quarterly ritual.
  - [Exercise 04 — Org-Wide Champions Community of Practice Charter](../exercise-04-org-wide-champions-community-of-practice-charter/SOLUTION.md) — the CoP consumes the Training Program Design and the Champion-network products.
- **Official standards and frameworks:**
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — referenced by the Governance Intake Review and Vendor Vetting services as the official source of the threat posture.
  - [MITRE ATLAS](https://atlas.mitre.org/) — adversarial technique context referenced by Governance Intake Review and Vendor Vetting.
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — the GOVERN function underpins the per-service DACI structure; the MEASURE function underpins the Measurement-Plan Co-Design service.
