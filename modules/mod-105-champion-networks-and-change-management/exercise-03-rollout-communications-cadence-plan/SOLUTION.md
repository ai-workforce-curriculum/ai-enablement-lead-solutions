# Exercise 03 — Rollout Communications Cadence Plan — Reference Solution

> Learning file: [`exercise-03-rollout-communications-cadence-plan.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-105-champion-networks-and-change-management/exercises/exercise-03-rollout-communications-cadence-plan.md)

## 1. Solution overview

One artifact: a **communications cadence plan** that spans T−6 weeks (pre-launch) through T+12 months (year-one). The plan is expressed as a dated matrix: rows are communications moments; columns are audience, channel, owner, voice, and purpose. The worked plan is for the mod-103 archetype — a coding-assistant GA at a ~3,000-person US bank with the champion network from Exercise 01 — so it lands with the same roles, BUs, and signal thresholds as the rest of the mod-105 solution set.

Posture checks the solution encodes:

- **Communications are instrumented, not intuitive.** Every moment has a measurable outcome: acknowledgement rate, attendance, question-volume, or scorecard-case count. Moments that cannot be instrumented are suspect — usually they are pageantry.
- **Each audience has a voice.** Executives read scorecard-voice; operators read operator-voice; champions read internal-sync voice. Mixing voices ("we at the bank believe artificial intelligence is a journey") is a credibility killer and is the AUP-voice drift from mod-103.
- **The cadence is paced to the AUP / SOP / scorecard rhythm.** A version-note briefing fires within 5 business days of every ratified policy increment; a scorecard touch fires monthly; a council-escalation touch fires per pre-read cycle. Communications ride the artifact set rather than inventing their own cadence.
- **Downside moments are planned, not improvised.** The plan carries scripted communications for the first data-handling accident, the first AUP revision that tightens an approved use, and the first scorecard month where outcome signal is flat. Each is written in advance because improvised messaging under pressure is where drift shows up.
- **The plan has an end state.** At T+12 months the "rollout" ends and the tool is folded into a BAU operating surface. Rollout-mode communications end; the champion-network cadence persists.

## 2. Implementation — worked answer

### 2.1 Deliverable — `rollout-comms-cadence.md`

```
Rollout Communications Cadence (v0.1)
Scope:   Coding assistant (Enterprise tenant); all US-regulated operations
Owner:   AI Enablement Lead (this role)
Window:  T−6 weeks → T+12 months
Status:  Draft for sponsor sign-off
```

#### Audience map (who reads what, in what voice)

| Audience | Voice | Primary channels | What they are reading for |
|---|---|---|---|
| **Executives** (`head-of-engineering-enablement`, sponsor exec, `head-of-ai-governance`, CIO staff) | Scorecard-voice; metrics-forward; ≤ 1 page. | Monthly scorecard; quarterly council pre-read. | Outcome signal, risk signal, decision asks. |
| **Line managers of in-scope operators** | Manager-voice; written as "here is what to tell your team tomorrow." ≤ 2 paragraphs. | Managers digest (bi-weekly); version-note briefings cc'd. | What to tell their team; what to protect their team's time for. |
| **Champions** | Internal-sync voice; signal-and-routing centric. | Weekly sync; `#ai-champions`; `field-signal-log`. | Signal thresholds, routing updates, drill content. |
| **Operators (in-scope)** | Operator-voice; team-meeting-aloud test. ≤ 300 words per moment. | Launch announcement; version-note briefings; office hours; tool-in-IDE banner. | What they can do; what they cannot; where to ask. |
| **Operators (out-of-scope)** | Short-form, neutral. | One-off announcement at GA; quarterly FAQ update. | Why they are not in scope and when they might be. |
| **Governance council** | Pre-read voice; decision-ask forward. | Quarterly pre-read (mod-103 Exercise 04). | Pattern escalations, policy-revision asks, risk signal. |
| **External** (regulators, auditors, vendor) | Formal, counsel-reviewed. `<!-- org-specific: confirm whether regulator notification is required for this tool class — likely OCC / Federal Reserve / FDIC guidance applies -->` | Counsel-owned; this role drafts and routes. | Posture statement; evidence pointers. |

#### Pre-launch window — T−6 weeks to T−1 week

| Date | Moment | Audience | Channel | Owner | Measurable outcome |
|---|---|---|---|---|---|
| T−6w | **Exec readout — rollout plan confirmed** | Executives | 30-minute standing slot | This role | Sign-off on the comms plan (this artifact) |
| T−5w | **Champion nomination announcement** | Operators + line managers | Function-wide email, co-signed by BU head | This role + BU heads | ~3× over-subscription against slots |
| T−4w | **AUP v1.0 ratification note** | All operators in scope | Intranet post + managers digest | This role + `head-of-ai-governance` | ≥ 90% acknowledgement by T−2w |
| T−3w | **Office-hours calendar published** | Operators, champions | Calendar invites + `#ai-enablement-help` | This role | Published; no measurable attendance yet |
| T−2w | **Line-manager brief — "what you need to protect"** | Line managers | Managers digest | This role + `head-of-engineering-enablement` | ≥ 80% open rate; ≥ 50% confirmed read via one-click ack |
| T−1w | **Pre-GA FAQ** | All in-scope operators | Intranet + Slack post | This role | Question volume in `#ai-enablement-help` tracked as input to launch-week FAQ |
| T−1w | **Champion onboarding wrap-up + roster publication** | Champions, governance council | `#ai-champions` + council pre-read | This role | Roster live; first weekly sync scheduled |

#### Launch window — Week 0 to Week 4

| Date | Moment | Audience | Channel | Owner | Measurable outcome |
|---|---|---|---|---|---|
| T+0 (launch day) | **GA announcement** | All operators | All-hands email, co-signed by sponsor exec + `head-of-ai-governance` + this role | Sponsor exec | Access-rate signal + initial question volume |
| T+0 | **Tool-in-IDE welcome banner** | In-scope operators | Tool banner surface | This role (via tenant admin) | Click-through rate |
| T+0 to T+4 days | **Daily office hours** | Operators | Zoom / Teams, drop-in, 30 min | Champions + this role | ≥ 10% of in-scope attend at least once in week 1 |
| T+3 days | **First manager digest after launch** | Line managers | Managers digest | This role | ≥ 50% ack; question-volume included |
| T+1w | **First weekly champion sync** | Champions | Standing sync (Exercise 02 agenda) | Facilitator + this role | `field-signal-log` entry filed |
| T+1w | **First "what we are seeing" operator note** | In-scope operators | Intranet + `#ai-enablement-help` | This role | Operator-voice synthesis of champion signal from week 1; ≤ 300 words |
| T+2w | **Managers digest #2 — early patterns** | Line managers | Managers digest | This role | Includes two "what to tell your team" items |
| T+3w | **First version-note briefing drill** | Operators | Intranet + manager digest | This role | Dry run even if no AUP change has landed yet; verifies the 5-business-day briefing surface works |
| T+4w | **Week-4 scorecard moment** | Executives | Monthly scorecard (mod-106) | This role | First outcome signal: access rate, usage breadth, incident count |

#### Steady-state rollout window — Month 2 through Month 6

- **Monthly scorecard** (executives). First business day of the month. Owner: this role. Instrumentation: distribution list + one-click ack.
- **Weekly champion sync** (champions). Standing from Exercise 02. Owner: facilitator. Instrumentation: `field-signal-log` entry + decisions-and-commitments register.
- **Bi-weekly managers digest** (line managers). Alternate Thursdays. Owner: this role. Instrumentation: open and ack rates + question-volume cross-reference.
- **Quarterly council pre-read** (governance council). Owner: this role + `head-of-ai-governance`. Instrumentation: council decision log.
- **Office hours** (operators). Weekly in high-volume BUs, bi-weekly elsewhere. Owner: champions. Instrumentation: attendance and question count.
- **Version-note briefings** (operators). Within 5 business days of every ratified policy increment. Owner: this role. Instrumentation: acknowledgement rate — floor 90%.
- **"What we are seeing" operator note** (operators). Monthly, synthesized from the `field-signal-log`. Owner: this role. Instrumentation: open rate.
- **Quarterly all-hands moment** (all operators + leadership). 10-minute slot in the existing all-hands; scorecard-voice outcome + two operator-voice cases. Owner: sponsor exec + this role.

#### Scripted downside moments (planned in advance)

These are the three communications the plan pre-authors so the response under pressure is not improvised.

1. **First data-handling accident after GA.** Operator-voice note (≤ 200 words) posted within 24 hours of the accident-path event closing. Content: what happened (no operator names), what the SOP did, what operators should take from it. Reviewed by counsel before posting. Pre-authored template lives in `comms-templates/accident-note-template.md`.
2. **First AUP revision that tightens an approved use.** Version-note briefing (≤ 1 page). Content: what changed, why, what operators do differently as a result. Co-signed by `head-of-ai-governance`. Pre-authored template lives in `comms-templates/version-note-tightening-template.md`.
3. **First scorecard month where outcome signal is flat or negative.** Scorecard-voice note (≤ 1 page) to executives in the monthly scorecard. Content: what the signal shows, what the enablement seat is doing about it, decision asks for the next council cycle. Pre-authored template lives in `comms-templates/flat-scorecard-template.md`.

#### End-of-rollout window — Month 9 through Month 12

| Date | Moment | Audience | Channel | Owner | Measurable outcome |
|---|---|---|---|---|---|
| T+9mo | **Rollout retrospective — governance council** | Council | Council pre-read + 60-minute session | This role + `head-of-ai-governance` | Council decides on BAU posture |
| T+10mo | **Line-manager BAU brief** | Line managers | Managers digest | This role | Manager-voice note: what changes in month 12 and beyond |
| T+11mo | **Operator BAU note** | In-scope operators | Intranet + manager digest | This role | Operator-voice note: what changes for them in month 12 (usually nothing; the signal cadence persists) |
| T+12mo | **Rollout close-out memo** | Executives | Final scorecard entry | This role | Rollout-mode ends; BAU cadence confirmed |

Post-T+12mo: the rollout-mode cadence ends. The BAU cadence that persists is:

- Weekly champion sync (unchanged)
- Monthly scorecard (unchanged)
- Version-note briefings per AUP/SOP increment (unchanged)
- Quarterly council pre-read (unchanged)
- Office hours (demand-driven; may become bi-weekly or monthly in low-volume functions)
- Managers digest and operator "what we are seeing" (demand-driven; may become monthly or quarterly)
- Scripted downside templates (retained; reviewed annually)

#### Co-author surface on this plan

> Drafter: AI Enablement Lead (this role).
> Ratifier: `head-of-engineering-enablement` (L55) — primary sponsor for cadence scope.
> Governance signer: `head-of-ai-governance` (L60) — confirms the version-note-briefing cadence and the downside-moment templates.
> Comms signer: internal communications lead (`<!-- org-specific: confirm the internal comms partner role title -->`) — confirms voice/channel discipline across audiences.
> Executive sponsor sign-off: sponsor exec — required before the T−6w moment fires.

---

### End of worked plan

## 3. Validation steps

1. **Audience map covers ≥ 6 distinct audiences** with voice, channel, and purpose. If "operators" is a single row, line managers will be messaged in operator voice and attend office hours they do not need. Separating them is the discipline.
2. **Every moment has a measurable outcome.** Grep for "awareness," "engagement," "momentum" as outcome columns — if present, rewrite. Measurable outcomes are acknowledgement rate, attendance count, question volume, scorecard-case count.
3. **Pre-launch window is six weeks, not three.** Compressing pre-launch to three weeks is the most common failure mode and produces an under-recruited champion network and an unacknowledged AUP.
4. **Launch window has a daily cadence for the first 4 days.** Daily office hours in week 1 catch the questions that will otherwise fester. If the plan is weekly from day 1, the week-2 question volume spikes.
5. **Version-note briefing surface is proven with a dry run in week 3.** If the surface does not fire until an actual AUP change lands, the first real briefing is delayed by the surface failing in production.
6. **Scripted downside moments exist** for at least three scenarios: accident, tightening revision, flat scorecard. Improvised downside messaging is where posture drift shows up.
7. **The plan has an end state.** If "rollout mode" continues indefinitely, the organization loses the ability to tell when a change initiative is over and the operator population learns to tune out.
8. **Executive and operator voices do not blend.** Executives read scorecard-voice; operators read operator-voice. A scorecard entry in operator voice is a signal the plan is for only one audience.
9. **Every moment names an owner.** "Enablement team" is not an owner. Named role + backup.
10. **`<!-- org-specific: ... -->` on regulator names, comms-partner title, BU names.** `<!-- org-specific: ... -->` on any mod-105 chapter claim.

## 4. Rubric / review checklist

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | Audience map covers ≥ 6 distinct audiences with voice + channel + purpose | 10 | Fewer than 6 or audiences without voice distinction |
| R2 | Pre-launch window is ≥ 6 weeks | 5 | Compressed to < 4 weeks |
| R3 | Launch window has daily cadence in week 1 (office hours) | 10 | Weekly or less frequent from day 1 |
| R4 | Every moment has a measurable outcome column | 15 | Awareness/engagement-style unmeasurable outcomes |
| R5 | Version-note briefing surface is dry-run in week 3 | 5 | No dry run; surface untested until live AUP change |
| R6 | Steady-state cadence integrates scorecard, sync, digest, pre-read, office hours, version notes, "what we are seeing," quarterly all-hands | 10 | Missing any of the eight BAU surfaces |
| R7 | Scripted downside moments exist for ≥ 3 scenarios with pre-authored templates | 15 | Fewer than 3, or no templates |
| R8 | Plan has an end state at T+12mo | 5 | Rollout mode continues indefinitely |
| R9 | Each moment names a specific owner (role, not team) | 10 | "Enablement team" or similar |
| R10 | Voice discipline — executives/operators/managers not blended | 10 | Scorecard-voice entry in operator channel or vice versa |
| R11 | Co-author surface names drafter, ratifier, governance signer, comms signer, sponsor | 5 | Missing any co-author surface role |
| R12 | `<!-- org-specific: ... -->` on regulator, comms partner, BU names; `<!-- org-specific: ... -->` on mod-105 chapter claims | 5 | Invented facts or unverified numbers |

**Pass threshold:** ≥ 85/100 and no R4/R7/R10 fail.

## 5. Common mistakes

- **Compressing pre-launch to three weeks.** The result is an under-recruited network, an unacknowledged AUP, and a GA week where question volume overwhelms the team. The six-week pre-launch is load-bearing.
- **Using "awareness" as an outcome.** Awareness is not measurable in a way that drives decisions. Acknowledgement rate is; attendance is; question volume is.
- **A single "operators" row.** Line managers and operators need different voices and different channels. Merging them under-serves both.
- **No dry run of the version-note briefing surface.** The surface fails in subtle ways (wrong distribution list, mangled markdown, a channel that nobody reads) and you only find out when the first real AUP change lands.
- **Improvised downside messaging.** The first accident after GA is the worst time to author a template. Pre-author three templates.
- **Rollout mode without an end state.** Fourteen months later the organization is still receiving "rollout updates" and has learned to filter them out. T+12mo closes the window.
- **Scorecard-voice in operator channels.** "In the reporting period, 94% of the eligible user population demonstrated non-zero utilization of the deployed capability" is scorecard-voice; it reads as hostile when posted in an operator channel.
- **Owner = "the team."** When something goes wrong, no one owns it. Named role + backup.
- **Inventing a regulator name or a specific comms-partner title.** Those are `<!-- org-specific: ... -->` slots.
- **Communications that describe tool features rather than operator behavior.** "The tool has a new chat-with-your-codebase feature" is not a communications moment; "starting Monday, you can ask the tool to walk you through unfamiliar code in our repos" is.

## 6. References

- **Learning material:**
  - [Exercise 03 learning file](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-105-champion-networks-and-change-management/exercises/exercise-03-rollout-communications-cadence-plan.md)
  - [mod-105 chapters (champion networks and change management)](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-105-champion-networks-and-change-management) `<!-- org-specific: confirm which mod-105 chapters cover communications cadence, downside-moment scripting, and end-of-rollout transition; link the specific chapter files here -->`
  - [mod-102 Chapter 03 — The Rollout Artifact Set](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-102-selecting-and-rolling-out-ai-tools/03-the-rollout-artifact-set.md) — the artifact set the cadence rides on.
  - [mod-103 Exercise 04 — Governance Council Pre-Read](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-103-policy-co-authoring-with-governance/exercises/exercise-04-governance-council-pre-read-authoring.md) — the council touch in the cadence.
  - [mod-106 chapters (outcome measurement and executive reporting)](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-106-outcome-measurement-and-executive-reporting) — the scorecard surface.
- **Official standards and frameworks:**
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — GOVERN (transparency and communication) surfaces the cadence evidences.
  - [NIST AI 600-1: Generative AI Profile](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf) — generative-AI-specific communication considerations referenced in the operator-voice and version-note surfaces.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — context for the accident-note template and the security-incident communication posture.
  - [MITRE ATLAS](https://atlas.mitre.org/) — adversarial technique context for the downside-moment scripting on prompt-injection and output-manipulation events.
