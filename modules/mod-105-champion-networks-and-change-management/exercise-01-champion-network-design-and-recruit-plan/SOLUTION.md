# Exercise 01 — Champion Network Design and Recruit Plan — Reference Solution

> Learning file: [`exercise-01-champion-network-design-and-recruit-plan.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-105-champion-networks-and-change-management/exercises/exercise-01-champion-network-design-and-recruit-plan.md)

## 1. Solution overview

Two artifacts: a **network design memo** (sizing, selection, responsibilities, lifecycle) and a **recruit plan** (identification, outreach, offer, onboarding). Together they are the one-page view `head-of-engineering-enablement` (L55) and the sponsor executive will ask for before authorizing the network as a standing operating-model surface.

The worked example carries the mod-103 archetype forward: a **coding-assistant rollout at a ~3,000-person US bank** (approximately 1,500 engineers across ~30 teams in 4 business units, plus ~1,500 G&A). Using the same archetype across modules keeps the champion roster, intake corpus, redline log, and executive scorecard describing the same organization.

Posture checks the solution encodes:

- **Champions are an awareness and signal surface, not a governance layer.** They do not approve use cases, sign SOPs, or hold enforcement authority. That line is explicit in the NIST AI RMF GOVERN surface — accountability lines belong to named owners, not to volunteer advocates.
- **Sizing is to span-of-influence, not to headcount.** The target ratio is one champion per ~50 operators in a tight-knit function, loosened or tightened by the function's existing community strength.
- **Selection criteria are operator-voice.** "Trusted by peers, hands-on practitioner, willing to spend 2–4 hours a week" beats "high performer" — the latter selects for people with no time to actually do the work.
- **Cross-BU threshold for pattern escalation is written down.** The design states explicitly that three champions from two business units reporting the same pattern constitutes a signal that escalates to the governance council, so that the escalation path is predictable and not political.
- **Exit path is designed before entry.** A champion rotates off at a fixed cadence (default: 12 months) with a defined handoff, so that network membership is not a career artifact and burnout does not compound.

## 2. Implementation — worked answer

### 2.1 Deliverable A — `champion-network-design.md`

```
Champion Network — Design Memo (v0.1)
Author:  AI Enablement Lead (this role)
Audience: head-of-engineering-enablement (L55), head-of-ai-governance (L60)
Scope:   Coding-assistant rollout, all US-regulated operations
Status:  Draft for sponsor review; not yet announced
```

#### Purpose

The champion network exists to carry **two-way signal** between the enablement seat and the operator population: field observations flow up, policy and guidance flow down. It is an awareness-and-communication surface — NIST AI RMF GOVERN Clause 7.3 / 7.4 territory — not a governance or approval layer.

#### Scope

In scope: all users of the Enterprise tenant of the coding assistant, both in the production IDE integration and the sandbox, across the bank's four engineering business units (`<!-- org-specific: confirm the four BU names — likely Retail Banking Tech, Commercial & Wholesale Tech, Risk & Compliance Tech, Shared Platform/Infra -->`) and the four non-engineering functions where the general-purpose LLM is also deployed (`<!-- org-specific: confirm the G&A functions in scope — typically HR, Finance, Legal/Compliance, Marketing -->`).

Not in scope: executive leadership (the sponsor cadence is separate), external contractors not holding bank identity, and personal-device usage (prohibited under the AUP).

#### Sizing and coverage

Target ratio: **one champion per 50 operators**, with floor and ceiling adjustments:

- **Floor: two champions per in-scope business unit** regardless of size. A single champion is a single point of failure and cannot carry both signal directions during PTO or departures.
- **Ceiling: four champions per ~250-operator function** before further coverage is added through a different surface (training rosters, office hours).
- For the archetype (3,000 operators across 8 functions in scope): **network size = ~32 champions**, allocated roughly: 4 Retail, 4 Commercial, 3 Risk & Compliance, 4 Platform, 3 HR, 3 Finance, 3 Legal/Compliance, 3 Marketing — with slack of 2 for rotation and onboarding at any given time. `<!-- org-specific: confirm whether mod-105 learning content specifies a different default ratio -->`

| BU / function | In-scope operators | Target champions | Notes |
|---|---|---|---|
| Retail Banking Tech | ~500 | 4 | Highest coding-assistant velocity expected |
| Commercial & Wholesale Tech | ~400 | 4 | Highest regulatory sensitivity on model-risk-managed code |
| Risk & Compliance Tech | ~200 | 3 | Coupled to the MRM review process |
| Shared Platform/Infra | ~400 | 4 | Platform migrations drive the heaviest refactor-plan usage |
| HR | ~150 | 3 | G&A LLM, not coding assistant |
| Finance | ~200 | 3 | G&A LLM, plus spreadsheet-adjacent workflows |
| Legal/Compliance | ~100 | 3 | Coupled to the redline log |
| Marketing | ~200 | 3 | Content workflows on the G&A LLM |
| **Total** | **~2,150 in scope** | **~27 named + 5 slack** | Rest are out-of-scope or bench |

The numbers are directional — the correct size is the smallest that still carries signal across every in-scope function with two-person redundancy.

#### Selection criteria

Champions are selected on four criteria, in priority order:

1. **Hands-on practitioner.** The champion uses the tool in their actual work. Not a line manager; not a tool-advocate from the vendor-management org. This is the single most important criterion and is non-negotiable.
2. **Trusted by peers.** When the champion raises a concern, their colleagues treat it as substantive. This is measurable crudely by asking "who would your team ask for help on this tool" in the nomination survey.
3. **Capacity.** The champion has approximately two to four hours a week to spend on the role, with sponsor sign-off from their line manager. Without this, the champion defaults into silence and the signal dies.
4. **Representative of the function.** The champion is not the one highest-fluency early adopter in the function. A champion who is three standard deviations ahead of the typical operator cannot see the typical operator's problems.

Anti-criteria (non-starters): line managers of in-scope operators; vendor-management or procurement roles; external contractors; anyone currently on a performance-improvement plan.

#### Responsibilities (what champions do)

1. Attend the **weekly champion sync** (45 minutes, standing agenda — see Exercise 02 for the drill).
2. Carry **two-way signal**: surface field observations (what is working, what is not, what operators are confused by) upward to the enablement seat; carry policy guidance (version-note briefings per redline log, new prohibited uses, SOP changes) downward to their function in operator voice.
3. Run or host **office hours** for their function at a cadence they choose (default: weekly or bi-weekly, 30 minutes).
4. Act as **first-line triager** for in-function policy questions ("is use X permitted?"). They do not answer governance questions themselves; they route to `#ai-enablement-help` or escalate to the `ai-governance-analyst` on-call.
5. Nominate **cases for the executive scorecard** (mod-106) where real productivity signal or real accident-path signal is seen in the field.

#### Responsibilities (what champions do not do)

- They do not approve use cases. All approvals route through the intake questionnaire and governance council.
- They do not sign the AUP, SOP, or any policy artifact. The co-author surface for those is fixed and documented in mod-103.
- They do not hold incident-response authority. Security incidents route to the SOC through the standard IR channel; data-handling accidents follow the SOP.
- They do not conduct training. Training rosters and curriculum are mod-104 territory.
- They are not expected to resolve resistance alone. The resistance playbook (Exercise 05) is a shared resource; the enablement seat owns the response to systemic resistance.

#### Two-way signal — escalation thresholds

The enablement seat routes signal by volume and spread:

- **Single champion report:** logged, not escalated. Watched for repeat across subsequent syncs.
- **Three reports from champions in two or more business units** inside a 30-day window: escalates to the governance council pre-read as a named pattern. `<!-- org-specific: confirm the exact threshold the mod-105 learning content specifies; if different, adjust -->`
- **Any report that implicates the AUP prohibited-use list, SOP accident path, or kill-switch surface:** escalates immediately to the on-call analyst and does not wait for the weekly sync.

Escalation thresholds are published to the network at onboarding. Predictable thresholds prevent the network from becoming a political-signal channel.

#### Lifecycle

- **Term:** 12 months, renewable once with manager sign-off.
- **Rotation cap:** no champion carries the role for more than 24 consecutive months. Two years out, they rotate off and may return after a 12-month gap.
- **Onboarding:** 2-hour synchronous session covering the role charter, the signal thresholds, the office-hours template, and the escalation paths. First four weekly syncs are mandatory attendance.
- **Offboarding:** 30-minute exit interview with the enablement seat (what was carried, what did not work, what the successor should know) and handoff to the replacement champion within two sync cycles. Office-hours cadence is owned by the function, not the individual, so continuity is preserved.
- **Removal:** a champion is removed from the network (not from the tool) for sustained non-attendance, for acting outside the charter (signing policies, approving use cases), or at the request of their line manager.

#### Measurement

The network is itself a change-management-health signal surface (Exercise 06). The enablement seat tracks:

- **Coverage:** % of in-scope operators with an active champion in their reporting chain. Target: ≥ 95%.
- **Signal rate:** reports per champion per month. Expected range: 1–4; below 1 indicates a silent champion, above 4 may indicate a resistance hotspot.
- **Pattern-escalation count:** number of patterns meeting the 3-in-2-BU threshold per quarter. Reported to the governance council.
- **Office-hours attendance:** aggregate across the network. Floor: 10% of in-scope operators per month.
- **Rotation health:** number of champions in month 10–12 of their term without an identified successor. Floor: zero.

#### Co-author surface on this memo

> Drafter: AI Enablement Lead (this role).
> Ratifier: `head-of-engineering-enablement` (L55) — primary sponsor for sizing and lifecycle.
> Governance signer: `head-of-ai-governance` (L60) — confirms the "not a governance layer" line.
> Function sponsor sign-off required from each in-scope BU head before any nomination is opened in that BU.

---

### 2.2 Deliverable B — `champion-recruit-plan.md`

```
Champion Network — Recruit Plan (v0.1)
Timeline: T−6 weeks to T+2 weeks relative to tool GA
```

#### Week −6: sponsor alignment

- Present the design memo to `head-of-engineering-enablement` (L55) and `head-of-ai-governance` (L60). Confirm sizing, criteria, and the escalation-threshold language.
- Get written sign-off on the **per-BU slot allocation** from each BU head. Without BU sponsor sign-off, nominations will not land.

#### Week −5: nomination opens

- Send a one-page announcement (≤ 300 words) to each in-scope function's distribution list, co-signed by the BU head and this role. The announcement names the role, the time commitment, the criteria, the term, and what the champion gets in exchange (see "offer" below).
- Open a nomination form (self-nomination + peer nomination both allowed). The form captures: name, role, function, approximate tool usage to date, manager name, and a two-sentence "why I want to do this."
- Target: 3× over-subscription against slot count. For 27 named slots: ~80 nominations.

#### Week −4: nomination screen

- Screen nominations against the four selection criteria and the anti-criteria list. Produce a long list of ~50.
- Share the long list with the respective BU head for a plus-one/minus-one pass. BU heads see candidates from their own function only.
- Short-list to approximately 1.5× slot count: ~40 names.

#### Week −3: 20-minute candidate conversations

- Hold a 20-minute conversation with each short-listed candidate. Questions are fixed across conversations to keep the bar consistent:
  1. "Describe the last three times you used the tool in your actual work."
  2. "A colleague says the tool got something wrong and they don't trust it. Walk me through what you would do."
  3. "Policy says you cannot paste customer PII into a prompt. You see a colleague do it. What is your next step?"
  4. "What is one thing you want to see this network do that is not in the design memo?"
- Note-take against the four criteria. Score 0–2 per criterion; 6+ to be recommended to BU head.

#### Week −2: final selection

- Ratify the final roster with BU heads. Each champion's manager receives a one-page sponsor brief noting the time commitment, the term, and the manager's role (protect the time, do not use the role for performance signalling).
- Publish the roster internally to the governance council and the engineering-enablement org. The roster is public to the in-scope population.

#### Week −1: onboarding

- 2-hour synchronous onboarding session (recorded for future cohorts). Agenda:
  - Role charter (10 min)
  - Signal thresholds and escalation paths (15 min)
  - Weekly sync format + first-cycle agenda (10 min)
  - Office-hours template and co-host pairing (20 min)
  - Policy walk-through — AUP, SOP, intake, escalation surface (45 min)
  - Live Q&A (20 min)

#### Week 0 / GA week

- First weekly champion sync, 48 hours after GA. Standing agenda from Exercise 02.
- First office hours launched by week 1 in every in-scope function.

#### Week +2: nomination close-out

- Replace any candidate who declined between offer and week 0 from the ranked short-list.
- Publish the version 1.0 roster and begin the measurement cadence.

#### The offer (what the champion gets)

- **Named recognition** in the role's internal profile and in any enablement-team artifact that cites field signal they carried.
- **Direct line to the enablement seat** — a standing 1:1 cadence available monthly.
- **Early access** to new tooling, pilot charters, and training material one cycle ahead of general release.
- **A professional-development story to tell** — champion rotation is a résumé-visible leadership experience with concrete artifacts (field-signal briefings, pattern-escalation records) they own and can cite at promotion time.

Anti-pattern: do not offer a stipend or spot-bonus tied to the champion role. Pay-for-advocacy corrupts the signal.

#### Recruit-plan risks and mitigations

| Risk | Mitigation |
|---|---|
| BU head nominates a line manager or "star" instead of a hands-on practitioner. | Written anti-criteria list in the nomination announcement; BU head's selections are passed through the enablement-seat screen with veto on the four criteria. |
| Under-subscription in a specific function (common in Legal / Compliance where capacity is tight). | Named manager sponsorship — the BU head commits the ~2–4 hour weekly capacity in writing before nomination opens. |
| Over-representation of the earliest-adopter cohort. | Selection criterion #4 (representative, not extreme-adopter). Mix term starts so a second cohort recruits 6 months in and rebalances. |
| Champions self-select into a social group and lose cross-BU signal. | Weekly sync format rotates facilitation across BUs; pattern-escalation threshold is explicitly cross-BU. |

---

### End of worked artifacts

## 3. Validation steps

Before sharing the design memo and recruit plan for sponsor sign-off, run the following checks. A reviewer grading the exercise should do the same.

1. **The memo answers five questions in this order:** purpose, scope, sizing, selection, responsibilities, two-way signal thresholds, lifecycle, measurement. If any section is missing, the memo is not yet ready for sponsor review.
2. **Sizing is justified.** The ratio, the per-BU floor and ceiling, and the total are stated with the underlying operator count visible. Pulling a number without a denominator is a fail.
3. **Selection criteria are operator-voice.** Grep for "high performer," "top talent," "A-player" — if present, rewrite. The criterion is hands-on practice and peer trust, not career status.
4. **Anti-criteria are explicit.** At minimum: no line managers of in-scope operators, no vendor-management roles, no external contractors. If the anti-criteria list is missing, sponsors will fill it with the wrong defaults.
5. **"What champions do not do" is written down.** Approval, signing, incident response, training, and resistance-resolution should all appear in the not-do list.
6. **Escalation threshold is numerically specific.** "Three reports from two BUs in 30 days" beats "when a pattern emerges." Vague thresholds become political thresholds. Mark with `<!-- org-specific: ... -->` if the mod-105 learning content specifies a different default.
7. **Lifecycle covers term, rotation cap, onboarding, offboarding, and removal.** Missing any of the five is a reviewer stop.
8. **Offer does not include money.** Stipends, spot bonuses, or compensation-adjacent recognition fail the pay-for-advocacy check.
9. **Recruit-plan weeks are concrete.** Each week has a named deliverable. "Nominations open for a few weeks" is not a plan.
10. **`<!-- org-specific: ... -->` markers on BU names, function names, and any fact tied to the organization.** Each marker names the specific slot the partner will fill.

Markdown lint both files (`markdownlint champion-network-design.md champion-recruit-plan.md`) before sharing.

## 4. Rubric / review checklist

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | Design memo has all eight sections, in required order | 10 | Any section missing or reordered |
| R2 | Sizing stated as ratio + per-BU floor/ceiling, with operator counts visible | 10 | Number without denominator, or no per-BU breakdown |
| R3 | Selection criteria in priority order; hands-on-practitioner criterion is #1 | 10 | Selection by career status (performance level, title) |
| R4 | Anti-criteria explicit (≥ 3 named) | 5 | Missing or implicit |
| R5 | "What champions do" and "what champions do not do" both present | 10 | Only do-list present, or do-not list empty |
| R6 | Escalation threshold is numerically specific and cross-BU | 10 | "When a pattern emerges"–style vagueness |
| R7 | Lifecycle covers term, rotation cap, onboarding, offboarding, removal | 10 | Any of the five missing |
| R8 | Measurement surface named (≥ 4 metrics, each with floor/target) | 5 | No metrics, or metrics without floors |
| R9 | Recruit plan is week-by-week with named deliverables | 10 | Narrative only, no week markers |
| R10 | Nomination screen includes 20-minute candidate conversation with fixed questions | 5 | Freeform or no candidate conversation |
| R11 | Offer does not include money or compensation-adjacent recognition | 10 | Stipend, bonus, or pay-adjacent reward named |
| R12 | `<!-- org-specific: ... -->` on BU names, function names, and org facts; `<!-- org-specific: ... -->` on learning-content-specific claims | 5 | Invented org facts, or unverified numbers passed as fact |

**Pass threshold:** ≥ 85/100 and no R1/R3/R6/R11 fail (those four are launch-gate equivalents in the real role).

## 5. Common mistakes

- **Sizing to headcount instead of span-of-influence.** "One champion per 100 operators" across a 3,000-person org produces 30 champions, but if those 30 are all clustered in the two highest-fluency BUs, three BUs are uncovered. Floor-per-BU fixes this.
- **Selecting line managers as champions.** Line managers hear what their reports want them to hear. The first time a champion is also the reports' manager, the signal goes to zero. The anti-criteria list exists to prevent this.
- **Vague escalation thresholds.** "Escalates when it becomes a pattern" invites political judgment. Fixed thresholds (3 in 2 BUs in 30 days) are predictable and audit-defensible.
- **No exit path.** A champion is never asked to leave, rotates themselves off through burnout, and the network loses institutional memory. The 12-month term with handoff mechanics is the correction.
- **Offering money.** A stipend attached to the champion role makes the role attract the wrong people and corrupts the signal. Named recognition and professional-development framing are the right incentives.
- **Writing the responsibilities list with no not-do list.** Champions default into approval authority, policy signing, and incident response if the not-do list is not explicit. The governance council will escalate this as a finding.
- **Letting BU heads nominate without a cross-screen.** BU heads over-weight visible performers. The enablement-seat screen on the four criteria is non-negotiable.
- **No measurement surface.** A network without measurement cannot be defended at the budget review. Four metrics with floors is the minimum.
- **Inventing a vendor-DPA or a specific regulator fact.** Those are `<!-- org-specific: ... -->` slots. Invention breaks the co-author posture carried over from mod-103.

## 6. References

- **Learning material:**
  - [Exercise 01 learning file](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-105-champion-networks-and-change-management/exercises/exercise-01-champion-network-design-and-recruit-plan.md)
  - [mod-105 chapters (champion networks and change management)](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-105-champion-networks-and-change-management) `<!-- org-specific: confirm which chapter numbers in mod-105 cover network design, two-way signal, and lifecycle; link them directly once confirmed -->`
  - [mod-103 Exercise 01 — Acceptable-Use Policy Drill](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-103-policy-co-authoring-with-governance/exercises/exercise-01-one-page-acceptable-use-policy-drill.md) — the policy surface the champion network briefs operators on
  - [mod-102 Chapter 03 — The Rollout Artifact Set](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-102-selecting-and-rolling-out-ai-tools/03-the-rollout-artifact-set.md) — where the champion network sits in the rollout artifact set
- **Official standards and frameworks** (for the hooks this network exposes to governance):
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — GOVERN function (accountability structures, workforce awareness and competence).
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — context for the field signal champions carry upward on prompt-injection, output-review, and data-leak patterns.
  - [MITRE ATLAS](https://atlas.mitre.org/) — adversarial technique context for the "report immediately" escalation surface.
