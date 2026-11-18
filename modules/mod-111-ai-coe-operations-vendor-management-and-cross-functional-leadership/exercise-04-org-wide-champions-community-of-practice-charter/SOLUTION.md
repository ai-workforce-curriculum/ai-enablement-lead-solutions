# Exercise 04 — Org-Wide Champions Community of Practice Charter — Reference Solution

> Module: `mod-111-ai-coe-operations-vendor-management-and-cross-functional-leadership`
> Exercise type: design / worked example
> Exercise brief: [`lessons/mod-111-ai-coe-operations-vendor-management-and-cross-functional-leadership/exercises/exercise-04-org-wide-champions-community-of-practice-charter.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-111-ai-coe-operations-vendor-management-and-cross-functional-leadership/exercises/exercise-04-org-wide-champions-community-of-practice-charter.md) (in the learning repo)

## 1. Solution overview

The deliverable is a **Community of Practice (CoP) charter** for the organisation-wide AI champions network. The charter is the written constitution that elevates a single business unit's champion network (the mod-105 pattern) into a durable, cross-BU community with explicit membership, explicit purpose, explicit decision rights, explicit rituals, explicit recognition, and explicit sunset conditions. It is the artifact that lets a champions network scale past the first BU without becoming either (a) an under-governed mailing list or (b) an over-governed ambassador program nobody wants to join.

The charter sits above the mod-105 single-BU champion-network design and below the mod-103 governance posture. It is the forum where field-level AI practice is surfaced, where cross-BU learning accumulates, and where early signals of policy or tool stress are heard before they become incidents.

Posture checks this solution encodes:

- **The CoP is a community, not an org unit.** Members have a day job; the CoP is a commitment on top. The charter respects this — membership is finite, the ask is bounded, and the time commitment is honest.
- **Membership is explicit and revocable.** A roster is maintained. Dormant members are rotated off. Joining is an application, not an assumption.
- **The purpose is bounded.** The CoP amplifies and surfaces; it does not own policy, tools, procurement, or incident response. Collapsing those back into the CoP destroys the CoP's trust with its members.
- **Decision rights are explicit but light.** The CoP has decision rights on recognition, rotation, curriculum topics, and field-report themes. It is Consult, not Driver, on policy and tool decisions.
- **Rituals are predictable and limited.** One monthly huddle; one quarterly in-person-or-virtual gathering; async working channels. More than this is a program masquerading as a community.
- **Recognition is explicit.** The ask on champions is real; the recognition must be real. Visible, non-financial recognition that the member's manager values is the dominant signal; small-stipend or training-budget recognition where the organisation permits it is secondary.
- **Psychological safety for field reports is explicit.** Field reports are the CoP's most valuable output; champions must be able to surface problems without retribution, including problems with sanctioned tools. The charter protects this.
- **Equity across BUs is explicit.** Representation across business units, geographies, and functions is tracked. A CoP dominated by one BU drifts away from org-wide signal.
- **Role-name addressing.** The charter survives personnel changes.
- **Sunset conditions are pre-committed.** A CoP can age out; the charter names when.

## 2. Implementation — worked answer (`ai-champions-cop-charter.md`)

```
AI Champions — Community of Practice Charter
Charter version:   <!-- org-specific: version and effective date -->
Owner (steward):   AI Enablement Lead (this role)
Ratifying body:    CoE exec sponsor + head-of-ai-governance (L60) + L&D partner
Next review:       Annual — end of fiscal year
```

### 2.1 Purpose

The AI Champions Community of Practice is the organisation-wide forum through which business-unit AI champions:

1. **Surface** field-level signal on AI tooling, policy, workflow friction, and user-reported incidents.
2. **Amplify** CoE-ratified policy, SOP, training content, and tool guidance into their BU.
3. **Exchange** cross-BU practice — what worked for one BU is offered, not imposed, to another.
4. **Co-author** curriculum and SOP updates that the champions themselves use in the field (per mod-104 and mod-103).

The CoP is **not**:

- The governing body for AI policy — that is the governance council (per mod-103).
- The decision body for tool procurement or vendor certification — those are the Vendor Vetting and Governance Intake Review services (per Exercise 01).
- The incident-response command structure — that is the mod-109 incident command.
- A talent-sourcing pipeline — champions are recognised for their field work, not recruited into the CoE or Applied AI Engineering by default.
- A mandatory training-delivery mechanism — L&D owns delivery infrastructure; champions co-author content and may deliver, but delivery is not an unfunded demand on champions.

### 2.2 Membership

#### 2.2.1 Who can be a champion

| Criterion | Requirement |
|---|---|
| Role | Any role where AI-assisted work is material to the operator's workflow, not limited to engineering. Examples: customer-support agent, marketing writer, financial analyst, legal paralegal, HR partner, engineer, data analyst. |
| Tenure | ≥ 6 months in the BU (gives the champion context to compare before-and-after) |
| Manager support | Named manager acknowledges and supports the time commitment (see 2.2.4) |
| Baseline literacy | Has completed the organisation's core AI literacy curriculum (per mod-104) |
| Commitment | Agrees to the time commitment in 2.2.4 and the field-report commitment in 2.4 |

#### 2.2.2 Representation

Representation is tracked and balanced annually. The CoP is not representative by accident.

- **Business-unit floor and ceiling.** Each in-scope BU has ≥ 1 champion and ≤ 20% of the total roster. A BU that cannot staff ≥ 1 champion after reasonable outreach is a signal; the CoE and the BU leader review.
- **Geography.** Where the org operates in multiple regions, representation across regions is maintained to keep field signal from skewing to HQ's experience.
- **Function.** Representation across engineering, operations, revenue-facing, and back-office functions is maintained.
- **Role level.** The CoP intentionally mixes individual contributors and people-managers; a CoP dominated by one or the other produces predictable blind spots.

#### 2.2.3 Size

The charter commits to a size band, not a target number. For the scenario here: **40-80 active champions** across ~2,500 employees — approximately 1.5-3% of the workforce. `<!-- org-specific: calibrate to the learner's org size -->` A roster below the floor indicates the CoP is under-staffed for signal volume; above the ceiling indicates diluted cadence and recognition.

#### 2.2.4 Time commitment

The honest ask on a champion, per month:

| Activity | Expected time |
|---|---|
| Monthly huddle attendance | 60 minutes |
| Field-report participation (one field report per month minimum) | 30-60 minutes to draft; 15-20 minutes in async discussion |
| Async working channel reading and contribution | ~30 minutes per week |
| Quarterly gathering (one half-day per quarter) | 4 hours per quarter (amortises to ~1 hour per month) |
| Occasional co-authoring on curriculum / SOP (opt-in) | Variable — in the catalog service's hours, not additive |

Total ≈ **4-6 hours per month** sustained; up to 8 hours in a quarterly gathering month.

The ask is written so a champion's manager can see it in advance. A champion whose job does not have a sustainable 4-6 hours per month for this is a champion who should not be recruited; sustained over-commitment destroys the program.

#### 2.2.5 Application and onboarding

| Step | Owner | Rhythm |
|---|---|---|
| Nomination (self or manager) | Prospective champion or their manager | Open rolling; quarterly review |
| Manager acknowledgement | Prospective champion's manager | 2 weeks |
| CoE conversation | AI Enablement Lead or Enablement Partner | 30-minute conversation within 2 weeks |
| Onboarding module | Prospective champion | 2 hours, self-paced |
| Onboarding buddy pairing | AI Enablement Lead | Within 1 week of ratification |
| Roster entry and announcement | Enablement Operations Analyst | At the next monthly huddle |

Onboarding buddies are existing champions who commit to a 90-day pairing with a new champion. The pairing commitment is itself in the champion's monthly time budget.

#### 2.2.6 Rotation and offboarding

Rotation is **expected**, not punitive.

| Trigger | Outcome |
|---|---|
| Two consecutive months of no field-report participation and no huddle attendance | Written check-in from the AI Enablement Lead; if the champion signals burnout or role change, offboard with thanks |
| Role change to a non-AI-touching role | Offboard at the role-change date |
| Manager withdraws support | Offboard with thanks |
| Champion requests rotation | Offboard with thanks; alumni status offered |
| Annual tenure ≥ 2 years with sustained engagement | Rotation conversation — stay with explicit renewal, rotate to alumni status, or elevate to Senior Champion (see 2.5) |

Offboarding is written, not implicit. A champion who is quietly dropped from a huddle invite silently becomes an ambassador against the program.

### 2.3 Rituals and operations

Rituals are predictable and limited. More than this is a program masquerading as a community.

#### 2.3.1 Monthly huddle

Governed by Exercise 03 Section 2.5.3. 60 minutes. Agenda: field-report themes, top wins, top blockers, policy/tool updates, Q&A. Live-with-recording for champions who cannot attend live.

#### 2.3.2 Quarterly gathering

| Field | Value |
|---|---|
| Rhythm | Once per fiscal quarter, 4 hours |
| Format | Virtual or in-person, rotating region if multi-region |
| Standing agenda | 1) Quarter's field-report themes and CoE response (60 min); 2) Cross-BU practice exchange — 2-3 champion-led lightning talks (45 min); 3) Policy / tool / curriculum roadmap preview (30 min); 4) Champion co-authoring working groups (60 min); 5) Recognition (45 min) |
| Decision scope | Co-authoring commitments for next quarter; recognition cohort for next quarter; elevation to Senior Champion |
| Downstream artifact | Gathering summary + roadmap preview deck shared org-wide |

#### 2.3.3 Async working channels

| Channel | Purpose | Moderator |
|---|---|---|
| `#ai-champions-general` | Community conversation; link-sharing; Q&A | AI Enablement Lead (rotating champion moderator weekly) |
| `#ai-champions-field-reports` | Structured field reports (per 2.4) | Enablement Operations Analyst |
| `#ai-champions-working-groups` | Sub-threads per working group | Working-group lead champion |
| `#ai-champions-alumni` | Alumni-only; lower-tempo | AI Enablement Lead |

Channels are moderated for norms, not for content — a critical field report about a sanctioned tool is not moderated away. Moderation enforces respectful tone, confidentiality (per 2.6), and relevance.

#### 2.3.4 Working groups

Working groups form on explicit demand, run for a quarter, and sunset. A working group is not a standing sub-committee. Examples: curriculum co-authoring for L2 support, SOP co-authoring for marketing creative, measurement-plan design for a specific commissioned tool.

Each working group has: a lead champion (Driver); a charter (one-page); a sunset date (end of the quarter); an output artifact. Working groups that overrun their quarter are explicitly re-chartered, not drifted.

### 2.4 Field reports — the CoP's most valuable output

#### 2.4.1 What a field report is

A field report is a champion's structured observation of how AI practice is actually landing in their BU. Field reports are the CoP's primary signal into the CoE's scorecard (per mod-106), vendor-stack review (per Exercise 02), policy refresh (per Exercise 03), and incident runbook library (per mod-109).

A field report includes:

- **What happened** — a specific incident, workflow change, user response, or observation. Dated; grounded in the BU; one or more data points.
- **What the champion thinks it signals** — a hypothesis about what the observation means. Marked as hypothesis.
- **What the champion would recommend** — optional; may be "I don't know, I am surfacing this" (this is a legitimate output).
- **Attribution and anonymisation posture** — see 2.6.

#### 2.4.2 How field reports are triaged

| Step | Owner | Rhythm |
|---|---|---|
| Field report posted in `#ai-champions-field-reports` | Champion | Rolling; ≥ 1 per month per champion |
| Triage into themes | Enablement Operations Analyst | Weekly |
| Themed into the monthly huddle agenda | AI Enablement Lead | Monthly |
| Routed into a CoE service (intake, policy refresh, vendor registry update, incident intake, scorecard row, training-content hotfix) | AI Enablement Lead | At monthly huddle or weekly triage |
| Closed-loop: the originating champion receives a written response within one monthly cycle | AI Enablement Lead | Monthly |

A field report that does not get a closed-loop response is the single most damaging thing the CoP can do. The closed-loop commitment is non-negotiable.

#### 2.4.3 The "escalation-without-retribution" rule

A field report that surfaces a problem — including a problem with a sanctioned tool, with a CoE-ratified SOP, or with a CoE-delivered training module — is received with thanks, not with defence. The CoP's trust with its members depends on this. The AI Enablement Lead is personally responsible for enforcing this norm.

Behaviours that violate the rule (including from other partner functions when they consume field reports): dismissing the report as "that's just one user"; publicly attributing the report to its originator without consent; retaliatory re-routing of work away from the originating champion; treating the field report as a performance-management signal.

The violation path: the AI Enablement Lead raises the behaviour with the responsible function's leader; a second violation routes to the exec sponsor of the CoE.

### 2.5 Recognition

The ask on champions is real; the recognition must be real.

#### 2.5.1 Recognition tiers

| Tier | Trigger | Form of recognition |
|---|---|---|
| Field recognition | Any field report that lands a direct policy / tool / curriculum / scorecard change | Named in the gathering summary; manager cc'd; CoE letter of recognition for the champion's HR record where the org supports this |
| Quarterly champion recognition | Nominated by peer champions; ratified at the quarterly gathering | Named in the gathering recognition segment; surfaced to the exec sponsor; small token / reward where the org supports this |
| Senior Champion | ≥ 2 years sustained; co-authored ≥ 1 major artifact (SOP, curriculum, measurement plan); led ≥ 1 working group | Named role; standing invite to the quarterly strategic review (Exercise 03); mentorship commitment to newer champions; exec visibility |
| Alumni | On offboarding | Alumni channel access; invite to annual champion event |

#### 2.5.2 What the recognition is NOT

- Not a performance-management input unless the champion explicitly asks for it in their performance cycle.
- Not a retention play that props up the role in lieu of the champion's day-job progression.
- Not a payroll substitute for the champion's manager's recognition.
- Not public attribution of sensitive field reports without consent.

#### 2.5.3 Manager visibility

The AI Enablement Lead sends a quarterly thank-you note to each champion's manager, naming the champion's specific contributions. This is the dominant signal that the champion's day-job manager sees; it is the piece of recognition that makes the ask sustainable.

### 2.6 Confidentiality and anonymisation

| Content type | Default posture |
|---|---|
| Field reports | Posted with originator attribution; originator may request pseudonymity at post time; CoE honours the request |
| Field reports about security-sensitive or personnel-sensitive incidents | Posted in a private sub-channel; escalates to mod-109 incident intake outside the CoP channels |
| Policy / SOP drafts shared in working groups | Pre-ratification; marked DRAFT; not for cross-BU circulation until ratified |
| Working-group outputs | Shared org-wide at ratification unless classified by the governance council |
| Cross-BU field observations | Attribution to BU allowed; attribution to specific teams or individuals requires consent |

A field report reporting unlawful or safety-critical behaviour routes to the organisation's standing ethics / whistleblower channel immediately, not through the CoP. The charter is explicit that the CoP is not the forum for those reports — the CoP amplifies and surfaces field signal; the standing ethics channel handles conduct reports.

### 2.7 Decision rights (DACI)

The CoP has light but explicit decision rights. The charter does not re-litigate the CoE's or governance council's decision rights; it names where the CoP sits in each.

| Decision | AI Enablement Lead (CoP steward) | Champions (as body) | CoE | Governance council | Business sponsor of affected BU |
|---|---|---|---|---|---|
| Recognition cohort for the quarter | A | D (nominate) | C | I | I |
| Elevation to Senior Champion | A | C | C | I | C |
| Working-group chartering | A | D | C | I | I |
| Monthly huddle agenda | D | C | C | I | I |
| Quarterly gathering agenda | A | D | C | I | I |
| Curriculum topic prioritisation | C | D | A | C | C |
| SOP amendments routed from field reports | C | C | D | A | C |
| Policy amendments routed from field reports | C | C | C | A | C |
| Tool decisions routed from field reports | C | C | C/D per catalog | A per catalog | A for BU-scoped |
| Charter amendments | D | C (consult, not vote) | A | C | C |
| CoP sunset or restructure | D | C | A | C | I |

Champions are a consult, not a vote, on charter amendments. The CoP is not a democracy that can amend its own constitution; the charter is held by the CoE steward with ratifying-body sign-off.

### 2.8 Metrics the CoP reports on

The CoP contributes to the mod-106 scorecard. The specific rows:

| Row | Family | Measured by |
|---|---|---|
| Champion-network reach — % of in-scope BUs with ≥ 1 active champion | Representation | Quarterly |
| Active-champion count and roster against size-band | Representation | Monthly |
| Field-report volume — total per month and distribution across BUs | Signal | Monthly |
| Field-report closed-loop rate — % of field reports with written response within one monthly cycle | Trust | Monthly |
| Routed outcomes — % of field reports that produced a policy / SOP / tool / curriculum / scorecard change | Effectiveness | Quarterly |
| Champion retention — % of champions still active at 6 months, 12 months | Sustainability | Quarterly |
| Recognition events — count per quarter; representation across BUs | Equity | Quarterly |
| Qualitative champion sentiment — annual pulse | Sustainability | Annual |

A field-report closed-loop rate below 90% for two consecutive months is a CoP amber signal. Below 80% is red and triggers an off-cycle review with the exec sponsor.

### 2.9 Sunset / restructure conditions

The CoP is a tool; tools age out. The charter pre-commits:

- **Restructure** on any of: field-report closed-loop rate < 80% for two consecutive quarters; champion retention < 50% at 6 months for two consecutive cohorts; roster below floor for two consecutive quarters; representation across in-scope BUs < 70% for two consecutive quarters.
- **Sunset** on: an annual re-grounding votes to sunset; a successor forum (e.g., an org-wide AI practitioners guild) has absorbed the CoP's purpose; the organisation's AI posture has shifted materially (e.g., AI practice has become a normal part of role L&D for every role) such that the CoP's signal role is no longer load-bearing.

A sunset is written, honoured with a recognition event, and documented with the final roster and final retrospective. A sunset is not a failure; it is a graduation.

### 2.10 Interlocks with the broader operating model

| Partner function | Interlock |
|---|---|
| CoE (Exercise 01 catalog) | CoP is the field-signal source for several services (Policy and SOP Co-Authoring, Training Program Design, Governance Intake Review, Measurement-Plan Co-Design) |
| Mod-105 BU-level champion networks | Charter extends the mod-105 single-BU pattern; BU-level network leads join the CoP as Senior Champions by default |
| Mod-103 governance council | Champions are not council members by default; field reports with policy implications route through the CoE into council pre-reads |
| Mod-106 scorecard | CoP contributes the rows named in Section 2.8 |
| Mod-109 incident response | Field reports surfacing Sev-2+ signal route to incident intake outside CoP channels |
| L&D | L&D is partner on curriculum co-authoring working groups; L&D is Driver on delivery |
| Internal Comms | Partner on CoP-facing comms; Driver on org-wide rollout comms that CoP amplifies |
| Procurement / Finance | Consult on tool-related field reports that route into Vendor Vetting or consolidation decisions |

### 2.11 Decision rationale — why this shape, not another

- **Why a charter and not just a mailing list.** Without a written charter, champions are recruited on an ambassador model and the ask drifts upward until manager support erodes. The charter is what makes the ask bounded, the time honest, and the sunset conditions pre-committed.
- **Why membership is an application, not an assumption.** Opt-in membership is the predictor of sustained participation. "Everyone is a champion" means nobody is. The application / nomination ritual is the forcing function for manager acknowledgement of the time commitment.
- **Why rotation is expected.** A CoP that never rotates ages into a clique. Explicit rotation with alumni status preserves institutional memory while refreshing the field-signal stream.
- **Why recognition specifically names managers.** The dominant failure mode in observed CoP programs is "the central team thanks the champion; the champion's manager does not see it; the champion's promotion cycle does not reflect the work; the champion burns out quietly". The quarterly manager thank-you is the piece that prevents this.
- **Why the escalation-without-retribution rule is explicit.** Champions self-censor on sanctioned-tool problems unless the charter *says*, in writing, that the problem-report is received with thanks. Unwritten norms do not survive the first partner-function pushback.
- **Why the field-report closed-loop is non-negotiable.** A single uncollected field report is a shrug; a pattern of them is the moment champions stop reporting. The 90% monthly closed-loop rate is the vital-sign of the CoP; below that, the program is dying slowly.
- **Why working groups sunset by quarter.** Standing sub-committees accumulate; the working group becomes an identity rather than a mechanism. The quarterly sunset forces re-chartering, which forces re-justification of the group's purpose.
- **Why psychological-safety posture is written, not implied.** This is the mod-105 psychological-safety pattern carried into the CoP. The charter protects it because not every partner function instinctively honours it.
- **Why representation is tracked and balanced.** A CoP dominated by one BU drifts to that BU's experience and the signal to the CoE narrows. Floor-and-ceiling per BU keeps signal diverse.
- **Why champions are consult, not vote, on charter amendments.** A community that can amend its own constitution drifts; successive amendments broaden the ask until the charter no longer resembles what the manager acknowledgement originally covered. The CoE steward owns the charter and consults.
- **Why `nist-ai-rmf` GOVERN is referenced.** The CoP is an instance of the GOVERN function in practice — written roles, ratifying body, metrics, review cadence, sunset conditions. Naming the framework is what lets the CoP be defended as governance, not performative community-building.

## 3. Validation steps

1. **Charter has a stated purpose with ≥ 4 purpose statements AND an explicit "not" section.** Both halves present.
2. **Membership has explicit criteria** — role, tenure, manager support, baseline literacy, commitment.
3. **Representation tracked across BU, geography, function, role level** with floor-and-ceiling per BU.
4. **Size band named** (not a target number) with floor and ceiling.
5. **Time commitment honestly quantified** at 4-6 hours per month sustained; manager-visible.
6. **Application, onboarding, rotation, offboarding** all documented with owner and rhythm per step.
7. **Rituals limited to monthly + quarterly + async channels** — no weekly huddle; no standing sub-committees.
8. **Working groups sunset by quarter** with explicit re-charter requirement.
9. **Field-report structure named** (what happened, hypothesis, recommendation, attribution).
10. **Field-report closed-loop rate committed to ≥ 90% monthly** as the vital-sign metric.
11. **Escalation-without-retribution rule written** with named behaviours that violate and named escalation path.
12. **Recognition tiers named** (field, quarterly, Senior Champion, alumni) with form per tier.
13. **Manager thank-you cadence** named at quarterly.
14. **Confidentiality posture named per content type** with explicit ethics-channel routing for conduct reports.
15. **DACI has CoP as Consult (not Driver) on policy / tool decisions**; Driver only on recognition, rotation, curriculum topics, working-group chartering.
16. **Metrics include ≥ 7 scorecard rows** across representation, signal, trust, effectiveness, sustainability, equity.
17. **Sunset / restructure conditions pre-committed** with ≥ 3 trigger criteria.
18. **Interlocks named** with ≥ 6 partner functions.
19. **Role-name addressing throughout.**
20. **`nist-ai-rmf` GOVERN referenced** as the framework anchor.

## 4. Rubric / review checklist

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | Purpose + explicit "not" section | 5 | Only purpose; no "not" boundary. |
| R2 | Membership criteria with role, tenure, manager support, baseline literacy, commitment | 10 | Any criterion missing. |
| R3 | Representation tracked with BU floor-and-ceiling | 5 | No representation posture. |
| R4 | Size band (floor + ceiling), not a target number | 3 | Single target headcount. |
| R5 | Honest time commitment at 4-6 hours/month; manager-visible | 5 | Ask understated or invisible to manager. |
| R6 | Application, onboarding, rotation, offboarding documented | 7 | Any missing. |
| R7 | Rituals limited (monthly + quarterly + async); no weekly huddle | 5 | Over-ritualised. |
| R8 | Working groups sunset by quarter | 3 | Standing sub-committees. |
| R9 | Field-report structure named | 7 | No structure; free-form only. |
| R10 | Closed-loop rate committed ≥ 90% monthly as the vital-sign | 10 | No closed-loop commitment. |
| R11 | Escalation-without-retribution rule explicit with escalation path | 10 | Unwritten or absent. |
| R12 | Recognition tiers named with form per tier; manager visibility explicit | 7 | Recognition vague or no manager visibility. |
| R13 | Confidentiality posture named per content type; ethics-channel routing explicit | 5 | Conflates CoP with ethics channel. |
| R14 | DACI has CoP as Consult on policy / tool, Driver only on light decisions | 8 | CoP as Driver on policy or tool. |
| R15 | ≥ 7 scorecard rows across named families | 5 | Fewer or no families. |
| R16 | Sunset / restructure conditions pre-committed | 5 | No sunset posture. |
| R17 | `nist-ai-rmf` GOVERN referenced | 3 | Framework not named. |
| R18 | Role-name addressing throughout | 2 | People names used. |

**Pass threshold:** ≥ 85/100 and no R10 / R11 / R14 fail. R10 (closed-loop commitment), R11 (escalation-without-retribution), and R14 (CoP is Consult not Driver on policy / tool) are the three discriminators between a CoP that champions will actually sustain and a CoP that becomes an unreliable ambassador program.

## 5. Common mistakes

- **CoP as a Driver on policy or tool decisions.** Collapses the governance council into a popularity contest and erodes the CoP's trust when decisions go against the community. The CoP is Consult, not Driver.
- **No closed-loop commitment on field reports.** Champions report once, hear nothing, and never report again. The 90% monthly closed-loop rate is non-negotiable.
- **Unwritten "please raise anything" culture without the retribution rule.** Champions self-censor on sanctioned-tool problems. Written rule + named escalation path is the control.
- **Ambassador program with no honest time ask.** Managers find out about the time commitment via the champion's calendar, resent the program, and withdraw support quietly. Manager acknowledgement at application is the control.
- **Standing sub-committees instead of quarterly-sunset working groups.** Working groups become identities and over-govern the CoP. Sunset-by-quarter is the control.
- **Weekly huddle as the default cadence.** Produces thin signal and a busy calendar. Monthly is the right tempo for field-report accumulation.
- **Recognition that the champion's manager does not see.** The quarterly manager thank-you is the piece that makes the ask sustainable; without it, central-team recognition is noise relative to the day-job progression signal.
- **Rotation as a punitive signal.** Rotation is expected and honoured with alumni status. A quiet drop-off is what sours the program; a named, thanked offboarding sustains it.
- **CoP as recruitment pipeline for CoE / Applied AI Engineering.** Champions become ambassadors for their own career move rather than their BU's field signal. The recognition tier structure keeps career advancement neutral to the CoP.
- **One BU dominating the roster.** Signal narrows; the CoP stops being org-wide. Floor-and-ceiling per BU is the control.
- **CoP as the ethics / whistleblower channel.** Confuses amplification with conduct reporting; the standing ethics channel handles conduct reports. The charter is explicit about this routing.
- **Charter amendments by champion vote.** A community that can amend its own constitution drifts. Steward-owned, consultation-based amendments preserve the ask.

### 5.1 Stretch — maturity curve

A new CoP should launch at the lower end of the size band (40 champions) with monthly huddle, async channel, and quarterly gathering — but *without* working groups in the first quarter. Working groups come in Q2 once a cohort of field reports has accumulated enough theme signal to warrant a chartered group. A CoP that launches with working groups before field reports is building process ahead of signal.

By year 2, the CoP operates the full charter with the quarterly cadence and Senior Champion elevation. By year 3, the CoP has produced a cohort of alumni who continue to participate lightly and whose cross-BU perspective is the most valuable signal in the monthly huddle.

## 6. References

- **Learning material (local):**
  - [mod-103 — Policy Co-authoring with Governance](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-103-policy-co-authoring-with-governance) — governance council posture; the CoP is a Consult into council pre-reads.
  - [mod-104 — Training Programs and AI Literacy Curriculum](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-104-training-programs-and-ai-literacy-curriculum) — baseline literacy requirement for champions; curriculum co-authoring working-group pattern.
  - [mod-105 — Champion Networks and Change Management](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-105-champion-networks-and-change-management) — the BU-level champion network the org-wide CoP extends; the psychological-safety pattern consumed by the escalation-without-retribution rule.
  - [mod-106 — Outcome Measurement and Executive Reporting](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-106-outcome-measurement-and-executive-reporting) — the scorecard rows the CoP contributes (Section 2.8).
  - [mod-108 — Industry and Regulatory Flavours of Enablement](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-108-industry-and-regulatory-flavours-of-enablement) — sector-specific posture that shapes representation and curriculum co-authoring.
  - [mod-109 — AI Incident Response and Enablement-Side Rollback](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-109-ai-incident-response-and-enablement-side-rollback) — Sev-2+ signals surfaced via field reports route into incident intake outside CoP channels.
  - [Exercise 01 — CoE Service Catalog and Intake Cadence](../exercise-01-coe-service-catalog-and-intake-cadence/SOLUTION.md) — the services (Policy and SOP Co-Authoring, Training Program Design, etc.) the CoP's field reports feed into.
  - [Exercise 02 — Vendor Vetting and Certification Rubric](../exercise-02-vendor-vetting-and-certification-rubric/SOLUTION.md) — vendor-related field reports route into Vendor Vetting and de-certification triggers.
  - [Exercise 03 — Quarterly Operating Ritual Plan](../exercise-03-quarterly-operating-ritual-plan/SOLUTION.md) — the monthly champion huddle and quarterly gathering are scheduled on the ritual plan.
  - [Exercise 05 — Credentials Portfolio and Signalling Plan](../exercise-05-credentials-portfolio-and-signalling-plan/SOLUTION.md) — Senior-Champion co-authoring artifacts and talks are inputs to the AI Enablement Lead's own credentials portfolio.
- **Official standards and frameworks:**
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — the GOVERN function anchors the charter: written roles, ratifying body, metrics, review cadence, sunset conditions.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — field reports that surface security-adjacent patterns are mapped against this list before routing into the governance council.
  - [MITRE ATLAS](https://atlas.mitre.org/) — adversarial-pattern context for field reports surfacing prompt-injection, model-drift, or evasion patterns.
