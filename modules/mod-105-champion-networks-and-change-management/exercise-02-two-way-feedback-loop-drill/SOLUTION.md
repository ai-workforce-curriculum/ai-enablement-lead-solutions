# Exercise 02 — Two-Way Feedback Loop Drill — Reference Solution

> Learning file: [`exercise-02-two-way-feedback-loop-drill.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-105-champion-networks-and-change-management/exercises/exercise-02-two-way-feedback-loop-drill.md)

## 1. Solution overview

Three artifacts: a **weekly champion sync agenda template** (45 minutes, standing agenda), a **worked drill transcript** of one cycle showing signal in both directions, and a **triage-and-routing rubric** for what the enablement seat does with each class of signal between syncs. The drill is run against the mod-103 archetype (coding-assistant rollout at a ~3,000-person US bank; champion network defined in Exercise 01).

Posture checks the solution encodes:

- **The sync is a signal cadence, not a status meeting.** No slide decks; no roll-call of individual projects. The standing agenda has four blocks; "any other business" is capped at five minutes and is a signal of agenda failure if it runs long.
- **Upward and downward signal are separated.** The agenda carries two blocks for field-signal-up and one block for policy-and-guidance-down, so neither direction crowds the other out.
- **Routing is written down, not improvised.** Each class of signal (policy question, accident path, pattern, resistance, feature ask) has a pre-decided route. Improvised routing is how political routing happens.
- **The drill is a run-through, not a theatrical exercise.** It uses realistic signal items, surfaces an uncomfortable pattern, and ends with a decision — not a round of appreciation.
- **The field signal becomes a durable record.** Each cycle produces a 1-page `field-signal-log` entry that the enablement seat files and that becomes input to the executive scorecard (mod-106) and the governance council pre-read (mod-103 Exercise 04).

## 2. Implementation — worked answer

### 2.1 Deliverable A — `weekly-champion-sync-agenda.md`

```
Weekly Champion Sync — Standing Agenda
Duration:  45 minutes
Cadence:   Weekly, same day/time, held on video with recording
Facilitator: Rotating champion (BU rotation per quarter)
Timekeeper + note-taker: AI Enablement Lead (this role)
Attendees: All active champions (standing)
Observers: head-of-engineering-enablement (L55) once per month; ai-governance-analyst as needed
Outputs:    `field-signal-log` entry (this role), routing commitments (facilitator)
```

| Block | Minutes | Owner | Purpose |
|---|---|---|---|
| 1. Opening + previous-cycle commitments check | 5 | Facilitator | Review commitments from last cycle. Each is closed, re-opened, or re-scoped. No new discussion. |
| 2. Upward signal — field observations | 15 | Each champion, 60–90 sec round-robin | What did operators do with the tool this week. What worked. What did not. Any policy-gray-area moments. |
| 3. Upward signal — resistance and silence patterns | 10 | Facilitator-led | What is *not* being said. Which function has gone quiet. Which population is still not using the tool despite access. |
| 4. Downward signal — policy and guidance from governance | 10 | AI Enablement Lead (this role) | Version-note briefings (redline log). AUP/SOP changes. New prohibited uses. Scorecard cases being used. |
| 5. Decisions and commitments | 5 | Facilitator | What gets escalated this cycle. Who carries which message back. Named commitments only; no "we should think about this." |

Agenda discipline rules:

- **No slides.** Each champion speaks to their round-robin slot in operator voice. Decks are a signal-killer and crowd out short observations.
- **No status reports from individual projects.** Signal is operator-pattern-centric, not initiative-centric.
- **The note-taker produces the `field-signal-log` entry in-meeting**, not after. Anything that would need a post-sync write-up is already lost.
- **Escalations happen in the sync**, not in a separate decision. The rubric (section 2.3) is the pre-committed routing.

### 2.2 Deliverable B — `drill-transcript.md` (one worked cycle)

This is a realistic transcript of one weekly sync. Names below are role-only; they map to the archetype champion roster from Exercise 01. Comments in italics are what the enablement seat was doing between spoken turns.

```
Sync — Week 7 of GA
Attendees: 24 of 27 named champions present; 3 absent (noted)
Facilitator (this cycle): Retail Banking Tech champion A
```

**Block 1 — Opening + commitments check (5 minutes).**

Facilitator: "Three commitments carried over from last week — (1) version-note briefing on the AUP 1.1 revision to Section 3.3, (2) the office-hours-time conflict in Risk & Compliance, (3) the sandbox-timeout escalation to the tenant admin. Round them."

*This role (note-taker): marks (1) closed — briefing delivered to 2,047 of 2,150 in-scope operators, acknowledgement rate 94%. (2) re-scoped — Risk & Compliance office hours moves to Thursdays 2pm from Tuesdays 4pm. (3) still open — tenant admin ticket is in queue; carries to this cycle.*

**Block 2 — Upward signal — field observations (15 minutes, round-robin).**

Platform/Infra champion A: "Four of our ten engineers started using the tool to generate migration plans off a legacy Oracle schema this week. The plans look good. None have been applied yet; my concern is whether they will be reviewed thoroughly enough when the pressure is on."

Retail Banking Tech champion B: "Two cases of operators pasting JIRA ticket text into the tool. The tickets had customer account numbers in them. Neither was caught by the DLP before the paste. Both reported themselves to me within an hour of realizing. I filed accident-path per SOP."

*This role: this is an AUP Section 3.1 hit. Flag for Block 5 escalation.*

Commercial & Wholesale Tech champion A: "The tool refused to generate code for a trading-desk reconciliation workflow — output said 'this workflow may be subject to model-risk-management review.' Operators are not sure whether this is the tool being correct and useful or the tool being over-cautious."

HR champion A: "Pay-equity analysis request came in — operator wanted to run compensation data through the G&A LLM to look for patterns. Operator did not run the data; they asked first. I told them the AUP prohibits employment-decision use and routed them to the HRIS analytics team."

Legal/Compliance champion A: "Nothing substantive from Legal this week. Volume is still very low."

*This role: Legal/Compliance silence is the third consecutive week of zero reports. Flag for Block 3 resistance/silence pattern discussion.*

Finance champion A: "Two accountants are now using the G&A LLM to draft commentary on monthly variance reports. They say the output is useful. They are not pasting actuals into the prompt — they are describing the shape of the variance in plain language."

Marketing champion B: "One case of an operator trying to generate claims copy for a Retail product. The output asserted a specific APR range. The operator did not publish. This is the first time I have seen the tool make a numeric claim; worth watching."

Platform/Infra champion B: "Three engineers are now using the tool as a first-pass code-review partner before requesting human review. The practice is informal and is not covered by any explicit guidance."

Retail Banking Tech champion A: "Shadow cohort — two team leads in Mobile are running their own internal tips thread independent of the enablement surface. Content is OK; concern is drift from the AUP as it evolves."

*(Round-robin continues; 14 more champions speak. Trimmed for the worked example.)*

**Block 3 — Upward signal — resistance and silence patterns (10 minutes).**

Facilitator: "Legal/Compliance is three weeks silent. Risk & Compliance has only one report per week on average. Both are below the signal floor from the design memo. What is happening?"

Legal/Compliance champion A: "Operators are not using the tool. They opened the AUP, saw the regulated-environment framing, and defaulted to 'do not use.' I think the if-in-doubt default is working — maybe too well."

Risk & Compliance Tech champion A: "Similar. The MRM-scope line is unclear to our operators. They are defaulting to not using the tool even on workflows where the AUP would permit it."

*This role: this is the second "if-in-doubt default is over-weighting" signal this month. Flag for Block 5 as a pattern that meets the cross-BU threshold (3 reports from 2 BUs in 30 days).*

**Block 4 — Downward signal — policy and guidance (10 minutes).**

This role: "Three items. First, AUP v1.2 ratified yesterday. The change is in Section 4 — the Confidential tier now requires explicit routing through a champion before prompt use rather than inline review. One-page version-note briefing goes out this afternoon; you will carry it to your function within five business days with acknowledgement tracking. Second, the kill-switch tabletop is scheduled for week 10 — champions are invited observers, not participants. Third, the executive scorecard for this month uses two cases champions surfaced — Platform/Infra's migration-plan pattern and Finance's variance-commentary pattern. Named attribution to the champion is in the scorecard."

**Block 5 — Decisions and commitments (5 minutes).**

Facilitator: "Five items from today."

| # | Signal | Routing (per rubric) | Owner | Due |
|---|---|---|---|---|
| 1 | Retail — two accident-path events with customer account numbers in JIRA ticket text; DLP did not catch. | SOP accident-path logged (done). Escalate the DLP gap to `ai-risk-engineer` (L25) and the identity team. | This role | Next cycle |
| 2 | Commercial — trading-desk reconciliation refused by the tool; operators unsure whether behavior is correct. | Route to `head-of-ai-governance` for a clarification note in the version-note surface. | This role | Next cycle |
| 3 | Legal/Compliance + Risk & Compliance — if-in-doubt default appears to be over-weighted. 3 reports / 2 BUs / 30 days — meets cross-BU threshold. | **Escalate to the governance council pre-read.** | This role | 10 business days |
| 4 | Marketing — first numeric-claim case by the tool; informal practice is forming. | Add to the resistance/opportunity playbook (Exercise 05) and brief at the next sync. | Marketing champion B | Next cycle |
| 5 | Retail — shadow cohort in Mobile running an independent tips thread. | Not a resistance signal; it is a champion-coverage gap. Confirm whether Mobile has active coverage; if not, add an interim champion. | Retail champion A | 2 cycles |

End of sync. `field-signal-log` entry filed before the meeting disbands. Field-signal-log rollup delivered to `head-of-engineering-enablement` on Friday as part of the standing weekly digest.

### 2.3 Deliverable C — `signal-routing-rubric.md`

What the enablement seat does with each class of signal:

| Signal class | Example from the drill | Pre-committed route | SLA |
|---|---|---|---|
| **Policy question** ("is use X permitted?") | HR — pay-equity analysis ask. | Champion routes to the AUP; if ambiguous, logs to `#ai-enablement-help` for the `ai-governance-analyst` on-call. | One business day for routine; four hours for ambiguous. |
| **Data-handling accident path** (per SOP) | Retail — JIRA tickets with account numbers. | SOP accident-path procedure. Do not delete the prompt. Contact first-line triager via `#ai-incident-first-line`. | Immediate; log to `field-signal-log` same-sync. |
| **Cross-BU pattern** (3 reports / 2 BUs / 30 days) | Legal/Compliance + Risk & Compliance — over-weighted if-in-doubt default. | Escalates to the governance council pre-read as a named pattern. | 10 business days to the next council cycle. |
| **Silence / resistance pattern** | Legal/Compliance three-week silence. | Flagged in Block 3 of the next sync. If silence persists for 6 weeks, enablement seat initiates a listening pass with the function. | 6 weeks before active listening pass. |
| **Feature or tenant-configuration ask** | Platform — sandbox timeout. | Enablement seat files with the tenant admin; status tracked on the next cycle's commitments check. | Next cycle; escalation to CISO delegate if blocked > 3 cycles. |
| **Security incident** | Credential exposure, tenant misconfiguration, prompt-injection evidence. | SOC via standard IR channel immediately; parallel route to `ai-risk-engineer` (L25). | Out-of-band; do not wait for sync. |
| **Shadow practice / coverage gap** | Mobile tips-thread cohort. | Not a resistance signal. Enablement-coverage investigation; interim champion if the gap is confirmed. | 2 cycles. |
| **Opportunity / new case** | Marketing — tool making numeric claims. | Added to the resistance/opportunity playbook; briefed at next sync. | Next cycle. |

Rubric publication: this table is posted in the champion-onboarding deck and is reviewed at every onboarding. Any new signal class discovered in practice is added by the enablement seat and notified on the next cycle.

---

### End of worked artifacts

## 3. Validation steps

1. **Agenda has four signal blocks in required order:** upward-field, upward-resistance/silence, downward-policy, decisions/commitments. Opening and commitments check are bookends; "any other business" is not a block.
2. **Timing adds up to exactly 45 minutes** with the five-minute discipline on commitments check. 60-minute syncs slide into status-meeting territory.
3. **No slides in the agenda.** Explicit rule. If the agenda allows slides, decks will replace signal.
4. **Round-robin structure for upward field signal** — every champion speaks, at a fixed cap (60–90 seconds). An unstructured discussion lets the loudest two voices carry the cycle.
5. **Routing is pre-committed, not improvised.** The rubric names routes for ≥ 6 distinct signal classes. If routing is "we'll decide at the time," escalations become political.
6. **Cross-BU pattern threshold is numerically specific** (3 reports / 2 BUs / 30 days or whatever the design memo specifies) and matches the Exercise 01 design.
7. **The `field-signal-log` entry is produced in-meeting**, not after. The drill transcript should show the log being filed before the meeting disbands.
8. **The drill surfaces at least one uncomfortable pattern** — resistance, silence, or an escalation to the governance council. A drill transcript with only positive signal is not a realistic drill.
9. **Decisions block ends with named owners and dues.** "We should think about this" is a failure of the decisions block.
10. **`<!-- org-specific: ... -->` on tenant names, DLP vendor, SOC channel, MRM process name, regulator name.** `<!-- org-specific: ... -->` on any specific mod-105 chapter claim.

## 4. Rubric / review checklist

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | Agenda has 4 signal blocks in required order + 2 bookends | 10 | Any block missing or reordered |
| R2 | Timing adds up to 45 minutes with per-block caps | 5 | Longer than 60 or no per-block caps |
| R3 | "No slides" rule is explicit | 5 | Agenda silently permits decks |
| R4 | Upward field signal uses round-robin with fixed per-speaker cap | 10 | Unstructured discussion |
| R5 | Downward signal block exists and carries version-note briefings | 10 | No downward block, or no version-note surface |
| R6 | Routing rubric covers ≥ 6 signal classes with pre-committed routes and SLAs | 15 | < 6 classes, or routes without SLAs |
| R7 | Cross-BU pattern threshold is numerically specific and matches design memo | 10 | Vague ("when it emerges") or inconsistent with Exercise 01 |
| R8 | `field-signal-log` entry is produced in-meeting | 5 | Post-sync write-up required |
| R9 | Drill transcript surfaces ≥ 1 uncomfortable pattern | 10 | All-positive drill |
| R10 | Decisions block has named owners + dues (≥ 3 decisions) | 10 | Decisions without owners/dues |
| R11 | Resistance / silence block exists and acts on ≥ 6 consecutive weeks of silence | 5 | No silence surface |
| R12 | `<!-- org-specific: ... -->` on tenant/DLP/SOC/MRM/regulator; `<!-- org-specific: ... -->` on chapter-specific claims | 5 | Invented facts or unverified numbers |

**Pass threshold:** ≥ 85/100 and no R1/R6/R9/R10 fail.

## 5. Common mistakes

- **Running the sync as a status meeting.** Once the agenda allows initiative-centric status, the sync stops producing field signal and starts producing anxiety. The round-robin on operator-pattern is the discipline.
- **Allowing slides.** A 15-minute round-robin becomes a 45-minute slide carousel the first time one champion brings a deck. Rule it out at onboarding.
- **Letting "any other business" run long.** If AOB consistently runs 10+ minutes, the agenda is wrong and should be revised.
- **Improvised routing.** The first time a cross-BU pattern is escalated without a pre-committed threshold, the escalation becomes political. Publish the rubric at onboarding.
- **No silence surface.** Weeks of quiet from a function is not good news; it usually means the function has opted out. The resistance/silence block catches it.
- **Writing up the sync after the meeting.** Anything that needs a post-sync write-up is lost. The log entry is produced in-meeting.
- **Drill transcripts with no uncomfortable signal.** Reviewers can tell. A realistic drill surfaces at least one resistance pattern, one accident-path hit, or one escalation to governance.
- **Decisions without owners.** "We should look into that" is how the next cycle starts with the same signal unaddressed.
- **Inventing a DLP product name or a specific SOC channel.** Those are `<!-- org-specific: ... -->` slots.
- **Changing the cross-BU threshold mid-year without a governance-council consult.** The threshold is the predictability guarantee; moving it unilaterally is how the network loses trust with sponsors.

## 6. References

- **Learning material:**
  - [Exercise 02 learning file](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-105-champion-networks-and-change-management/exercises/exercise-02-two-way-feedback-loop-drill.md)
  - [mod-105 chapters (champion networks and change management)](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-105-champion-networks-and-change-management) `<!-- org-specific: confirm which mod-105 chapters cover sync cadence, upward signal mechanics, and routing rubric; link the specific chapter files here -->`
  - [mod-103 Exercise 04 — Governance Council Pre-Read Authoring](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-103-policy-co-authoring-with-governance/exercises/exercise-04-governance-council-pre-read-authoring.md) — the destination for cross-BU pattern escalations.
  - [mod-106 chapters (outcome measurement and executive reporting)](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-106-outcome-measurement-and-executive-reporting) — where the `field-signal-log` feeds the executive scorecard.
- **Official standards and frameworks:**
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — GOVERN function (transparency, communication, accountability) and MANAGE (incident response and corrective action) surfaces that the routing rubric exposes.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — context for the security-incident and prompt-injection routing lines.
  - [MITRE ATLAS](https://atlas.mitre.org/) — adversarial technique context for the "out-of-band — do not wait for sync" security-incident route.
