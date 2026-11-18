# Exercise 03 — Quarterly Operating Ritual Plan — Reference Solution

> Module: `mod-111-ai-coe-operations-vendor-management-and-cross-functional-leadership`
> Exercise type: design / worked example
> Exercise brief: [`lessons/mod-111-ai-coe-operations-vendor-management-and-cross-functional-leadership/exercises/exercise-03-quarterly-operating-ritual-plan.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-111-ai-coe-operations-vendor-management-and-cross-functional-leadership/exercises/exercise-03-quarterly-operating-ritual-plan.md) (in the learning repo)

## 1. Solution overview

The deliverable is a **quarterly operating ritual plan**: the written calendar, agendas, and decision-rights map for the recurring rituals the AI CoE runs each quarter. A ritual is a pre-committed meeting (or asynchronous review) with a stated purpose, named attendees, a standing agenda, and a decision scope. The plan is the artifact that converts "we should meet about this stuff" into an operating system other functions can plan around.

The plan sits above the weekly triage tempo in Exercise 01 (which handles intake) and feeds the mod-106 scorecard discipline (which handles reporting). Where Exercise 01's intake cadence governs *inbound* requests, this ritual plan governs *recurring operations*: scorecard review, portfolio review, vendor-renewal review, policy refresh, champion-network governance, incident retrospective, planning for the next quarter.

Posture checks this solution encodes:

- **Every ritual has one owner (Driver).** A ritual with co-ownership silently drifts to no ownership; the next quarter's planning never happens.
- **Every ritual has a stated decision scope.** "Discussion-only" rituals accumulate; after six months the calendar is full and no decisions have been made.
- **Every ritual has a kill / de-scope criterion.** Rituals persist by default; without a pre-committed criterion, the calendar grows monotonically.
- **The plan has four cadences** — daily operational, weekly tactical, monthly operational, quarterly strategic — with an incident-triggered off-cycle path.
- **Each ritual feeds a specific downstream artifact** — the scorecard, the portfolio decision, the budget planning cycle, the quarterly board-ready review (per mod-106 Exercise 03).
- **Role-name addressing throughout.** The plan survives personnel changes.
- **The plan is published, not implicit.** Partner functions should be able to read it and know, in advance, when they will be consulted on which decisions.
- **Decision rights tie to the DACI in Exercise 01 service catalog** — the ritual plan does not re-litigate decision rights; it schedules the forum where they are exercised.

## 2. Implementation — worked answer (`ai-coe-quarterly-ritual-plan.md`)

### 2.1 Scope and context

This plan governs the recurring CoE operating rituals that hang off the quarterly fiscal rhythm. It assumes:

- Quarterly OKR cycle; monthly executive reviews; weekly operational stand-ups.
- The CoE roster and services defined in Exercise 01.
- The vendor registry and tier-dependent re-certification cadence from Exercise 02.
- The mod-106 scorecard discipline.
- The mod-109 incident-response posture for off-cycle rituals.

The plan is **not** a project-management document. It does not list in-flight engagements, open tickets, or sprint content. Those are governed by Exercise 01's weekly triage and the service-owner tracking per catalog service.

### 2.2 Cadence overview

| Cadence | Rhythm | Primary purpose | Primary downstream artifact |
|---|---|---|---|
| **Daily** | Business days | Operational heartbeat and signal detection | CoE intake-queue heartbeat (per Exercise 01 Section 6) |
| **Weekly** | 1-2 slots per week | Intake triage; eval-signal review on in-flight tools | Weekly intake digest; eval signals for commissioned tools |
| **Monthly** | 2 slots per month | Operational reviews; scorecard synthesis; stakeholder touchpoints | Executive scorecard narrative (per mod-106); monthly operational-review minutes |
| **Quarterly** | 4-6 slots in the final two weeks of the fiscal quarter | Strategic reviews; portfolio decisions; planning for the next quarter | Quarterly board-ready review (per mod-106 Exercise 03); next-quarter plan |
| **Off-cycle** | On incident-trigger | Sev-2+ post-incident review; policy or vendor-posture emergency review | Mod-109 post-incident review record; policy / vendor update memo |

### 2.3 Daily ritual

#### 2.3.1 Daily operational heartbeat

| Field | Value |
|---|---|
| Owner (D) | Enablement Operations Analyst |
| Attendees (A, C, I) | Auto-posted to the CoE channel; no live attendance required |
| Form | Asynchronous post in the CoE channel at 09:00 local |
| Duration | Read in ≤ 3 minutes |
| Standing content | Open intake tickets by service; SLA at-risk tickets; yesterday's eval-harness exceptions; vendor-registry alerts (upcoming re-cert within 60 days; sub-processor changes); open incidents from mod-109; comms needed today |
| Decision scope | None directly; surfaces signals for weekly rituals |
| Kill / de-scope | Not de-scoped; the heartbeat is the lowest-cost signal we have |

Silence for two consecutive business days is a signal — either the auto-generation pipeline is broken or there genuinely is nothing moving. Both warrant a check-in.

### 2.4 Weekly rituals

#### 2.4.1 Weekly intake triage

See Exercise 01 Section 2.3 cadence Section 2 — this ritual is governed there and is referenced here as a weekly fixture. Owner: AI Enablement Lead. Attendees: full Enablement Partners roster + Enablement Ops Analyst; Applied AI Engineering embed as C. Produces: triage verdicts per inbound ticket.

#### 2.4.2 Weekly eval and safety signal review

| Field | Value |
|---|---|
| Owner (D) | AI Enablement Lead (co-chaired with Applied AI Engineering lead for specific weeks) |
| Attendees | AI Enablement Lead, Applied AI Engineer embed, Enablement Operations Analyst; Security intake partner as C on any Sev-2+ signal; Governance Partner embed as C on any policy-touching signal |
| Form | Live 30-minute meeting; async written readout afterwards |
| Standing agenda | Eval-harness readouts for all in-flight commissioned tools (per mod-110 Exercise 04 Section 2.4 weekly tempo); drift-monitor alarms; prompt-injection probe-set status; user-reported-incident queue (per mod-109) |
| Decision scope | Hold / investigate / pause-and-triage on any in-flight tool; escalate to monthly operational review; convene incident-path review if Sev-2+ signal |
| Kill / de-scope | Not de-scoped; the weekly tempo is a condition of entry to limited-GA per mod-110 Exercise 04 Section 2.5 |

#### 2.4.3 Weekly cross-function working slot (optional, demand-driven)

| Field | Value |
|---|---|
| Owner (D) | Rotating Enablement Partner (per ticket) |
| Attendees | Variable by ticket; typically CoE + one partner function |
| Form | 60-minute working slot; agenda is the specific ticket under discussion |
| Standing agenda | None — this is a block held open for cross-function working sessions on active tickets (Vendor Vetting, Measurement-Plan Co-Design, Policy Co-Authoring) |
| Decision scope | Within the ticket's catalog service decision scope |
| Kill / de-scope | De-scoped when the ticket's working session can be absorbed into the owning service's standard rhythm |

### 2.5 Monthly rituals

#### 2.5.1 Monthly operational review

| Field | Value |
|---|---|
| Owner (D) | AI Enablement Lead |
| Attendees | CoE roster + business sponsors of in-flight engagements + L&D partner + Security intake partner + Finance partner for cost rows |
| Form | 90-minute live meeting; agenda circulated 2 business days in advance |
| Standing agenda | Full indicator pack from the mod-106 scorecard; adoption cohort progress; cost reconciliation (mod-107 Exercise 01); CSAT / FCR trends on commissioned tools; vendor-registry status; champion-network field reports; outstanding governance-council items |
| Decision scope | Scope changes within existing engagements; rollout cohort widening; kill-criterion check; scorecard threshold updates; convene off-cycle incident review if needed |
| Downstream artifact | Monthly scorecard narrative (per mod-106); updates to the vendor registry and measurement plans |
| Kill / de-scope | Not de-scoped; the monthly review is the standing forum where cross-service threads are reconciled |

#### 2.5.2 Monthly executive touchpoint

| Field | Value |
|---|---|
| Owner (D) | AI Enablement Lead |
| Attendees | Executive sponsor of the CoE (CIO / COO / chief-of-staff per org); AI Enablement Lead |
| Form | 30-minute 1:1 |
| Standing agenda | Scorecard narrative (one page); top-3 items needing exec attention; one risk, one bet, one block |
| Decision scope | Resource unblocks; exec-level visibility on items escalated from the monthly operational review |
| Downstream artifact | Exec-sponsor minutes (private); any resource / exec decisions captured in the intake queue |
| Kill / de-scope | Not de-scoped; the exec touchpoint is a two-way visibility ritual |

#### 2.5.3 Monthly champion-network huddle

| Field | Value |
|---|---|
| Owner (D) | AI Enablement Lead (with rotating champion co-chair per Exercise 04) |
| Attendees | Champions + CoE roster; L&D partner as C; Internal Comms as C |
| Form | 60-minute live; recorded and summarised asynchronously for champions who cannot attend live |
| Standing agenda | Field-report themes; top-3 wins; top-3 blockers; policy / tool updates for the field; Q&A |
| Decision scope | Champion-specific unblocks; policy or SOP amendment candidates routed into the Policy Co-Authoring service (per Exercise 01); curriculum updates routed into Training Program Design |
| Downstream artifact | Field-report digest (feeds the mod-106 qualitative-signal row and the mod-109 user-reported-incident intake) |
| Kill / de-scope | De-scoped per champion-network segment if the segment drops below the activity threshold named in Exercise 04 Section 6 |

### 2.6 Quarterly rituals

The quarterly rituals are the plan's load-bearing elements. They are scheduled in the **final two weeks of the fiscal quarter**, in a specific sequence — each ritual's output is an input to the next.

#### 2.6.1 Quarter-end sequence (2-week window)

| Day (relative to Q-end) | Ritual | Owner | Produces |
|---|---|---|---|
| Q-end minus 14 | Quarterly scorecard freeze and narrative draft | AI Enablement Lead | Scorecard narrative draft (per mod-106 Exercise 03) |
| Q-end minus 12 | Quarterly portfolio review | AI Enablement Lead | Catalog amendments; capacity commitments for next quarter |
| Q-end minus 10 | Quarterly vendor-stack review | AI Enablement Lead | Consolidation / expansion recommendations; approaching re-cert queue (per Exercise 02) |
| Q-end minus 8 | Quarterly policy and governance refresh | AI Enablement Lead + head-of-ai-governance | AUP amendments list; governance-council agenda for next quarter |
| Q-end minus 6 | Quarterly champion-network review | AI Enablement Lead | Champion-network charter check (per Exercise 04); recognition and rotation decisions |
| Q-end minus 3 | Quarterly incident retrospective | AI Enablement Lead + Applied AI Engineering lead | Incident retrospective summary (per mod-109); rollback-playbook updates |
| Q-end minus 1 | Quarterly board-ready review (per mod-106 Exercise 03) | AI Enablement Lead | Board-ready slide pack; next-quarter OKR commitments; budget decisions (per mod-107) |
| Q-end plus 3 | Quarterly all-hands CoE retrospective | AI Enablement Lead | Internal team retrospective; next-quarter staffing and ritual-plan amendments |

The spacing is deliberate: each ritual lands its output into the next ritual's attendee pre-read. The portfolio review (Q-end minus 12) feeds the vendor-stack review and the policy refresh. The vendor-stack review feeds the budget decision at the board-ready review (Q-end minus 1). The incident retrospective feeds the rollback-playbook updates that feed the next quarter's measurement plans.

#### 2.6.2 Quarterly portfolio review — full ritual card

| Field | Value |
|---|---|
| Owner (D) | AI Enablement Lead |
| Attendees | CoE roster + business sponsors of all in-flight engagements + L&D + Internal Comms + Procurement AI-sourcing lead + Governance Partner embed + Security intake partner + Finance partner |
| Form | Half-day (3-4 hour) in-person-or-video; pre-read circulated 3 business days in advance |
| Pre-read contents | Current catalog with service-level load; quarter's intake volume by service, by BU; completion rate vs SLA; kill / de-scope candidate list; services proposed for promotion to product; capacity ask for next quarter |
| Standing agenda | 1) Previous quarter's ritual commitments — delivered / slipped (15 min); 2) Catalog review: additions / retirements / promotions (45 min); 3) Capacity commitments for next quarter (30 min); 4) Scorecard rows: which services are on the exec scorecard next quarter (30 min); 5) Partner-function dependency map (30 min); 6) Decisions and action owners (30 min) |
| Decision scope | Catalog amendments; capacity commitments; service-level SLA changes; service-kill decisions; promote-to-product decisions; scorecard additions / removals |
| Downstream artifact | Updated service catalog; capacity-plan memo for next quarter; scorecard-row change list |
| Attendee discipline | Attendees are expected to arrive having read the pre-read; a quarterly review that spends the first hour re-reading the pre-read is a failed quarterly review. The pre-read is circulated 3 business days in advance precisely so attendees have time to read it. |

#### 2.6.3 Quarterly vendor-stack review — full ritual card

| Field | Value |
|---|---|
| Owner (D) | AI Enablement Lead (co-chaired with Procurement AI-sourcing lead) |
| Attendees | AI Enablement Lead, Procurement AI-sourcing lead, Finance partner, Security intake partner, Legal/privacy partner, head-of-ai-governance (L60), business-unit sponsors of vendor stacks |
| Form | Half-day |
| Pre-read contents | Current vendor registry (tiers, scope, expiry); approaching-re-cert queue (next 180 days); consolidation candidates per mod-107 Exercise 05; de-certification candidates; new intake pipeline (vendors in Vendor Vetting service queue) |
| Standing agenda | 1) Registry audit — currency, scope drift, grace-period items (30 min); 2) Re-certification queue and lead-time check (30 min); 3) Consolidation review (60 min — per mod-107 Exercise 05); 4) De-certification review (30 min); 5) New-vendor pipeline (30 min); 6) Budget alignment for next quarter (30 min) |
| Decision scope | Vendor consolidation / sunset decisions; tier changes; conditional-certification extensions or terminations; next-quarter vendor-spend commitments |
| Downstream artifact | Updated vendor registry; consolidation-decision memos; budget commitments for Finance (per mod-107 Exercise 01) |
| Kill / de-scope | Not de-scoped; the vendor-stack review is standing |

#### 2.6.4 Quarterly policy and governance refresh — full ritual card

| Field | Value |
|---|---|
| Owner (D) | AI Enablement Lead (co-chaired with head-of-ai-governance) |
| Attendees | AI Enablement Lead, head-of-ai-governance (L60), Governance Partner embed, Security intake partner, Legal/privacy partner; business-unit sponsors for sector-specific sections (per mod-108) |
| Form | 2-hour live |
| Pre-read contents | Current AUP; amendments proposed since last quarter (from champion-huddle routing, incident retrospectives, vendor-stack review); regulatory-horizon scan (per mod-108); governance-council minutes since last quarter |
| Standing agenda | 1) AUP amendment review (45 min); 2) SOP addendum review by sector (30 min); 3) Regulatory-horizon items (30 min); 4) Governance-council slot planning for next quarter (15 min) |
| Decision scope | AUP amendments to propose to governance council; sector-specific SOP changes; governance-council agenda commitment for next quarter |
| Downstream artifact | Governance-council pre-read pack (per mod-103); updated AUP; sector-specific SOP addenda |
| Kill / de-scope | Not de-scoped; the refresh is a GOVERN-function requirement per `nist-ai-rmf` |

#### 2.6.5 Quarterly incident retrospective — full ritual card

| Field | Value |
|---|---|
| Owner (D) | AI Enablement Lead (co-chaired with Applied AI Engineering lead) |
| Attendees | AI Enablement Lead, Applied AI Engineering lead, Security intake partner, Governance Partner embed, incident commanders from the quarter's Sev-2+ incidents (per mod-109) |
| Form | 2-hour live |
| Pre-read contents | All Sev-2+ incidents from the quarter with post-incident review records; themes from Sev-3 patterns; rollback-playbook invocations |
| Standing agenda | 1) Themes from Sev-2+ (45 min); 2) Rollback-playbook invocation review — what worked, what didn't (30 min); 3) Policy / tool-posture updates to propose to the policy refresh (30 min); 4) Cross-function training-content hotfix candidates (15 min) |
| Decision scope | Rollback-playbook updates; policy amendments to route into the policy refresh; training-content hotfix commitments for the next quarter |
| Downstream artifact | Updated incident runbook library (Exercise 01 product list); routed amendments into the policy refresh |
| Kill / de-scope | Not de-scoped; the retrospective is a MANAGE-function requirement per `nist-ai-rmf` |

#### 2.6.6 Quarterly board-ready review

Governed by mod-106 Exercise 03. Referenced here as a scheduled fixture; owner: AI Enablement Lead. Produces: the board-ready slide pack; next-quarter OKR commitments; budget decisions (per mod-107).

### 2.7 Off-cycle ritual — Sev-2+ post-incident review

| Field | Value |
|---|---|
| Owner (D) | Incident commander (per mod-109) convening; AI Enablement Lead co-chair |
| Attendees | Incident commander, AI Enablement Lead, Applied AI Engineering lead, Security intake partner, Governance Partner embed, business sponsor of the affected tool |
| Form | Live convening within 1 business day of incident closure; 60-90 minutes |
| Standing agenda | Per mod-109 post-incident-review template |
| Decision scope | Immediate rollback or policy posture changes; routing of any longer-lived items into the next quarterly incident retrospective |
| Downstream artifact | Post-incident-review record; any hot amendments to the AUP, SOP, measurement plan, or rollback playbook |
| Kill / de-scope | Not de-scoped; the off-cycle ritual is a mod-109 commitment |

### 2.8 Quarter-start commitments

The first week of a new quarter has three standing commitments that the quarterly rituals produce:

| Commitment | Owner | Due |
|---|---|---|
| Updated service catalog published (Exercise 01) | AI Enablement Lead | Day 3 of new quarter |
| Capacity-plan memo circulated to partner functions | AI Enablement Lead | Day 5 of new quarter |
| Next-quarter OKR commitments logged with the exec sponsor | AI Enablement Lead | Day 5 of new quarter |

Partner functions should be able to read the new catalog, see where capacity is committed, and know where their intake slots will land.

### 2.9 Annual rituals (reference)

Two annual rituals hang off the quarterly plan and are mentioned for completeness; they are not elaborated here:

- **Annual service-catalog audit** (per Exercise 01 Section 2.5) — end of fiscal year with governance council.
- **Annual ritual-plan re-grounding** — end of fiscal year, with CoE roster and partner-function interlocks, to re-evaluate which rituals are meeting their purpose and which should be amended or retired.

### 2.10 Ritual retirement criteria

A ritual is retired (not simply paused) on any of:

- Three consecutive instances with no decisions recorded (the ritual is a status-share, not a decision forum).
- The decision scope has been absorbed into another ritual with no loss of visibility.
- The downstream artifact is no longer referenced by any partner function for two consecutive quarters.
- An annual ritual-plan re-grounding votes to retire the ritual.

A ritual retirement produces a written memo citing the criterion; the memo is circulated to all former attendees.

### 2.11 Decision rationale — why this shape, not another

- **Why four cadences + off-cycle.** Daily is cheap signal that other cadences consume. Weekly handles tactical decisions (intake triage, eval review) that cannot wait a month. Monthly handles operational decisions (scorecard, cost, cohort) that cannot wait a quarter. Quarterly handles strategic decisions (catalog, vendor stack, policy, portfolio) that cannot be re-litigated monthly. Off-cycle handles Sev-2+ incident commitments. Collapsing any one of these produces a predictable failure — e.g., quarterly-only misses mid-quarter scope slide.
- **Why every ritual names a decision scope.** "Discussion-only" rituals accumulate. After six months the calendar is full and no decisions have been made. The decision scope is the test: if a ritual has no decision scope, it is either a status-share (should it be an async digest?) or a disguised decision ritual (whose scope should be written down).
- **Why every ritual has one owner.** Co-ownership silently drifts to no ownership. The next quarter's planning never happens. One Driver per ritual is non-negotiable.
- **Why quarterly rituals are sequenced in the final two weeks.** Each ritual feeds the next. Portfolio → vendor stack → policy → champion → incident → board-ready → retrospective. Running them in a scrambled order produces board-ready decks that reference catalogs that have not yet been amended; it is incoherent downstream.
- **Why pre-reads are circulated 3 business days in advance of quarterly rituals.** A quarterly review that spends the first hour re-reading the pre-read is a failed quarterly review. The 3-day window makes the pre-read actually readable.
- **Why the champion-network huddle is monthly, not weekly.** Field reports take time to accumulate. A weekly cadence produces thin reports and a busy calendar; a monthly cadence produces substantive field signal.
- **Why the vendor-stack review is quarterly, not annual.** Vendor posture (model changes, sub-processor changes, pricing shifts) evolves materially within 12 months; annual misses the shifts. Quarterly aligns with the fiscal-planning rhythm and feeds budget decisions.
- **Why the incident retrospective is quarterly in addition to the per-incident Sev-2+ off-cycle ritual.** The per-incident review captures the incident; the quarterly retrospective captures the *theme* across incidents. Themes are what drive policy and rollback-playbook amendments.
- **Why ritual retirement criteria are pre-committed.** Rituals persist by default. Without a pre-committed criterion, the calendar grows monotonically and the CoE eventually spends more time in rituals than on ritual outputs.
- **Why role-name addressing.** The plan survives personnel changes. A ritual whose attendee list names specific individuals breaks at the first attendee departure.

## 3. Validation steps

1. **Five cadences named** (daily, weekly, monthly, quarterly, off-cycle) with rhythm and primary purpose per cadence.
2. **Every ritual card has: owner (Driver), attendees (role names), form, standing agenda, decision scope, downstream artifact, kill / de-scope criterion.**
3. **Every ritual has exactly one Driver.** Grep for "co-chaired" — co-chairing is allowed only when the co-chair role is explicit AND the ritual's decision scope names which decisions each co-chair drives.
4. **Every ritual has a stated decision scope.** "Discussion-only" / "status share" rituals must be converted to async digests or absorbed into another ritual.
5. **Quarterly rituals are sequenced in a stated order** within the final two weeks of the fiscal quarter, and the sequence is motivated (each ritual feeds the next).
6. **Pre-read discipline is named** for quarterly rituals (≥ 3 business days in advance) with an attendee-expectation statement.
7. **Ritual retirement criteria pre-committed** with ≥ 4 criteria including ≥ 1 outside ritual-owner control (annual re-grounding vote).
8. **Decision rights tie to Exercise 01 catalog DACI.** The plan does not re-litigate decision rights; it names the ritual where the catalog's decision rights are exercised.
9. **Downstream artifacts are named per ritual** (updated catalog, updated registry, scorecard narrative, board-ready pack, etc.). A ritual that produces no artifact is a ritual that should be retired.
10. **Incident off-cycle path is named** with a 1-business-day convening SLA and mod-109 coupling.
11. **Quarter-start commitments are named** (service catalog update, capacity-plan memo, next-quarter OKR commitments) with owner and due day.
12. **Role-name addressing throughout.** No personal names.
13. **`org-specific` tags on all unverifiable specifics** (fiscal-quarter dates, exec sponsor role at this specific org, ticket system).
14. **References to `nist-ai-rmf` GOVERN / MANAGE functions** anchor the policy refresh and incident retrospective rituals.

## 4. Rubric / review checklist

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | Five cadences named with rhythm and primary purpose | 10 | Fewer cadences; e.g., no incident off-cycle path. |
| R2 | Every ritual card has all seven fields (owner, attendees, form, agenda, decision scope, downstream artifact, kill / de-scope) | 15 | Any field missing on any ritual. |
| R3 | One Driver per ritual; co-chairing only with named decision split | 10 | Co-chair without split, or no Driver. |
| R4 | Every ritual has a stated decision scope | 10 | "Discussion-only" rituals permitted. |
| R5 | Quarterly rituals sequenced with motivated order; each ritual feeds the next | 10 | Scrambled order, or sequencing not motivated. |
| R6 | Pre-read discipline (≥ 3 business days in advance) stated for quarterly rituals | 5 | Missing pre-read posture. |
| R7 | Ritual retirement criteria pre-committed with ≥ 4 criteria including ≥ 1 outside owner control | 5 | Fewer criteria or all owner-controlled. |
| R8 | Downstream artifacts named per ritual | 10 | Any ritual without a named artifact. |
| R9 | Incident off-cycle path named with ≤ 1 business day convening SLA and mod-109 coupling | 5 | No off-cycle path, or weak coupling. |
| R10 | Quarter-start commitments named with owner and due day | 5 | Missing commitments. |
| R11 | Decision rights tie to Exercise 01 catalog; plan does not re-litigate DACI | 5 | Ritual plan re-derives DACI, creating drift. |
| R12 | Role-name addressing throughout | 5 | People names used. |
| R13 | `nist-ai-rmf` GOVERN / MANAGE anchor the policy and incident rituals | 5 | Framework not named. |

**Pass threshold:** ≥ 85/100 and no R2 / R3 / R4 / R5 / R8 fail. R2 (ritual-card shape), R3 (single Driver), R4 (stated decision scope), R5 (quarterly sequencing), and R8 (named artifacts) are the five discriminators between a ritual plan the organisation operates and a ritual plan that becomes an overloaded calendar.

## 5. Common mistakes

- **Rituals without decision scope.** "Weekly working group" accumulates. After six months the calendar is full and no decisions have been made. If a ritual has no decision scope, it should be an async digest or absorbed.
- **Co-chaired rituals without a named decision split.** "Both of us run it" silently becomes neither running it. Co-chair only when the decision split is written down.
- **Quarterly rituals run in a scrambled order.** Board-ready decks reference catalogs that have not yet been amended; vendor-stack decisions depend on portfolio decisions not yet made. Sequence matters.
- **Pre-reads circulated on the morning of.** Attendees spend the first hour reading. Circulate 3 business days in advance.
- **Monthly operational review treated as a status-share.** It is a *decision* ritual: scope changes, cohort widening, kill-criterion checks, scorecard threshold updates. Status-share content belongs in the daily heartbeat or weekly digest.
- **No ritual retirement criteria.** Rituals persist by default; the calendar grows; the CoE eventually spends more time in rituals than on their outputs. Pre-commit the retirement criteria.
- **Attendee lists with personal names.** The plan breaks at the first attendee departure. Role-name addressing survives re-orgs.
- **Treating the champion-network huddle as weekly.** Field reports take time to accumulate. Weekly produces thin reports; monthly produces substantive signal.
- **No quarterly incident retrospective because "we review each incident at closure".** Per-incident review captures the incident; themes across incidents are what drive policy and playbook amendments.
- **Running quarterly rituals outside the final two weeks of the quarter.** Rituals in week 1 of the quarter are planning for a quarter nobody has yet executed; rituals in the middle of the quarter produce inputs with no window to act on.
- **Re-litigating DACI inside the ritual plan.** The decision rights live in the Exercise 01 service catalog. The ritual plan schedules the forum; it does not override the catalog.

### 5.1 Stretch — ritual-plan maturity curve

A year-1 CoE should not run the full quarterly sequence described here. The realistic year-1 quarterly ritual set is: scorecard narrative, portfolio review (lightweight), policy refresh (with the governance council), and board-ready review. Vendor-stack review, incident retrospective, and the full quarterly sequence come in year 2. Attempting the full plan in year 1 over-indexes on ritual overhead relative to signal volume.

## 6. References

- **Learning material (local):**
  - [mod-103 — Policy Co-authoring with Governance](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-103-policy-co-authoring-with-governance) — the governance-council pre-read posture the quarterly policy refresh feeds.
  - [mod-105 — Champion Networks and Change Management](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-105-champion-networks-and-change-management) — the field-report pattern consumed by the monthly champion-network huddle.
  - [mod-106 — Outcome Measurement and Executive Reporting](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-106-outcome-measurement-and-executive-reporting) — the scorecard discipline underlying the weekly, monthly, and quarterly reviews; Exercise 03 of that module is the quarterly board-ready review.
  - [mod-107 — Budget, ROI, and Build-vs-Buy at Org Scope](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-107-budget-roi-and-build-vs-buy-at-org-scope) — the budget and consolidation decisions the vendor-stack and portfolio reviews feed.
  - [mod-108 — Industry and Regulatory Flavours of Enablement](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-108-industry-and-regulatory-flavours-of-enablement) — the regulatory-horizon scan the quarterly policy refresh consumes.
  - [mod-109 — AI Incident Response and Enablement-Side Rollback](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-109-ai-incident-response-and-enablement-side-rollback) — the Sev-2+ definition and post-incident review template underlying the off-cycle ritual and the quarterly incident retrospective.
  - [mod-110 — Commissioning Internal AI Tools and Custom Agents](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-110-commissioning-internal-ai-tools-and-custom-agents) — Exercise 04 of that module defines the eval and measurement cadence the weekly eval review consumes.
  - [Exercise 01 — CoE Service Catalog and Intake Cadence](../exercise-01-coe-service-catalog-and-intake-cadence/SOLUTION.md) — the service catalog and intake tempo the ritual plan sits above.
  - [Exercise 02 — Vendor Vetting and Certification Rubric](../exercise-02-vendor-vetting-and-certification-rubric/SOLUTION.md) — the vendor registry the quarterly vendor-stack review audits.
  - [Exercise 04 — Org-Wide Champions Community of Practice Charter](../exercise-04-org-wide-champions-community-of-practice-charter/SOLUTION.md) — the CoP charter whose monthly huddle is on the ritual plan.
- **Official standards and frameworks:**
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — the GOVERN function anchors the quarterly policy refresh; the MANAGE function anchors the incident retrospective and the ritual-retirement discipline.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — referenced by the weekly eval and safety signal review via the mod-110 Exercise 04 indicator pack.
  - [MITRE ATLAS](https://atlas.mitre.org/) — adversarial-technique context consumed by the weekly eval review's prompt-injection probe-set status row.
