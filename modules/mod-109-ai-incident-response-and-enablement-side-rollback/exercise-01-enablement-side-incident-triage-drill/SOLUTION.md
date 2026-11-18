# Exercise 01 — Enablement-Side Incident Triage Drill — Reference Solution

> Module: `mod-109-ai-incident-response-and-enablement-side-rollback`
> Exercise type: design / worked example (scenario drill)
> Exercise brief: [`lessons/mod-109-ai-incident-response-and-enablement-side-rollback/exercises/exercise-01-enablement-side-incident-triage-drill.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-109-ai-incident-response-and-enablement-side-rollback/exercises/exercise-01-enablement-side-incident-triage-drill.md) (in the learning repo)

## 1. Solution overview

The deliverable is a **run-through of an enablement-side triage drill** — the first 90 minutes an AI Enablement Lead works a live AI-tool incident, from first signal to the point where the technical and security leads can take the ball. The drill produces three artifacts that must sit on disk before anyone goes to bed:

1. A completed **enablement-side triage record** for the scenario.
2. A **decision log** covering the three enablement-only decisions — rollout pause, user-population communication, and training/AUP freeze — with the reasoning preserved so the post-incident review has evidence.
3. A **handoff memo** that the AI Risk Engineer and SecOps on-call can read in two minutes to understand the enablement state they are inheriting.

Posture checks this solution encodes:

- **The Enablement Lead is not the technical incident commander and is not the security incident commander.** The Enablement Lead owns the user-population dimension of the incident: who is touching the tool right now, who was trained to use it, what workflows are mid-flight, and whether the acceptable-use posture needs to change. The triage drill is scoped to that lane.
- **Triage is time-boxed.** The 90-minute envelope keeps the drill honest. Anything that cannot be decided inside 90 minutes is explicitly escalated or explicitly deferred to the post-incident review, with the hand-off written down.
- **Every decision is captured with a timestamp, the person who made it, and the evidence that justified it** — this is the baseline NIST AI RMF `MANAGE` and `GOVERN` discipline. Decisions made and not written down are decisions that will be re-litigated in the post-mortem.
- **No invented metrics or named incidents.** The drill uses a fabricated-but-labeled scenario; any figure that would need an org-specific truth to be real is marked `<!-- org-specific: ... -->`.
- **Threat framing points at OWASP ML Top 10 and MITRE ATLAS where the scenario touches an adversarial technique**, so the technical responders see a shared vocabulary when the handoff lands.

## 2. Implementation — worked answer

### 2.1 Scenario envelope used for the worked example

> **Fabricated drill scenario. No specific product, vendor, or incident is named.**
>
> At `T+00:00` on a weekday morning, the AI Enablement Lead receives a Slack DM from a mid-level engineer in Business Unit B (BU-B) saying that the **general-availability AI assistant** returned what looks like a **snippet of another customer's data** inside a summarization response. The engineer attaches a screenshot. The tool in question is a Tier-1 enablement rollout (per the mod-102 selection charter) and is in general availability across ~900 Tier-1 seats and ~500 Tier-2 seats (per the mod-107 cost-model worked example).
>
> The engineer is not sure whether the snippet is real or hallucinated. The engineer has not reported this to Security yet. The engineer tags the Enablement Lead because the acceptable-use briefing from mod-103 named the Enablement Lead as the first contact for "something is wrong with the tool, I don't know who to tell."

This is, in OWASP ML Top 10 terms, potentially an `ML02: Data Poisoning` / `ML06: AI Supply Chain Attacks` / `ML09: Output Integrity Attack` candidate, and in MITRE ATLAS terms sits in the `Exfiltration` and `Impact` tactic columns — the Enablement Lead does not yet know which, and triage will not resolve that. The job here is to stabilize the enablement surface while the technical responders answer the "what actually happened" question.

### 2.2 The 90-minute triage drill

The drill proceeds in three phases. The time-boxing matters; drifting past 90 minutes without a written handoff is itself a failure.

#### Phase 1 — `T+00:00 → T+00:15`: contain the enablement surface

The Enablement Lead's first fifteen minutes are spent **stabilizing the enablement surface so the rest of triage can happen without the incident blast radius growing**. The Lead is not investigating root cause.

Actions, in order:

1. **`T+00:01`** — Acknowledge the reporter in writing. "I see this. I'm pulling in our AI Risk Engineer on-call and Security on-call now. Please do not reproduce this prompt. Please do not share the screenshot further until we tell you who to send it to." This preserves the chain-of-custody posture that SecOps will need and prevents a well-meaning reporter from paging the vendor directly.
2. **`T+00:03`** — Page the **AI Risk Engineer on-call** and the **SecOps on-call** via the paging channel named in the mod-103 AUP. Explicitly do **not** page the vendor's support channel; that is a SecOps / Legal decision, not an Enablement decision. The handoff-contract (Exercise 03 of this module) governs who talks to the vendor.
3. **`T+00:05`** — Open the **enablement-side incident record** (template below). This is a markdown file in the incident-tracker repo, not a slide, not a Slack thread. Anything in Slack after this point also lands in the incident record as a copy-paste block with timestamp.
4. **`T+00:08`** — Pull up the **active-session view** for the tool (from the usage dashboard that is a dependency of the mod-106 executive scorecard). Record the current session count and the top-10 teams by session volume for the last 30 minutes, so the Lead can make the "pause vs. keep live" decision in Phase 2 with evidence rather than feel.
5. **`T+00:12`** — Draft the **holding message** for the champion network (from mod-105). Do not send it yet. The holding message is "we are investigating a report about the AI assistant. Please stand down from encouraging new use for the next hour. We will update at `T+01:00` whether we are pausing, keeping live, or escalating." The champion network is the information artery that keeps the field from hearing about the incident through rumor.

At `T+00:15` the Enablement Lead has a written incident record, two paged counterparts, a current-use snapshot, and a holding message ready to send. The Lead has not made any irreversible decisions yet.

#### Phase 2 — `T+00:15 → T+01:00`: make the three enablement-only decisions

These three decisions are the decisions the Enablement Lead owns. They are not the AI Risk Engineer's or SecOps' to make; equally, they are not decisions the Lead should defer to them. The whole point of the triage drill is that these decisions get made quickly and cleanly.

##### Decision 1 — Rollout pause or keep-live?

Options on the table:

- **`Keep live`** — the tool continues to operate for all current and new sessions.
- **`Soft pause`** — the tool continues for existing sessions but the enablement function stops encouraging new sign-ups, stops onboarding sessions, stops champion-driven adoption pushes, and the help-desk macros stop pointing users to the tool as a first-line option.
- **`Hard pause`** — the enablement function asks the AI Risk Engineer to flip the **kill-switch** (per Exercise 02 of this module) and the tool is unavailable to everyone until further notice.

The Enablement Lead does not own `Hard pause` unilaterally — that is a joint decision with the AI Risk Engineer who operates the kill-switch. The Lead *does* own `Soft pause` unilaterally, because "soft pause" is a change to enablement posture, not a change to tool availability.

Criteria the worked drill uses:

| Signal | If true → | If false → |
|---|---|---|
| The reported output appears to contain data that *should not have been in the model's training or retrieval context* (not just a plausible hallucination) | lean toward `Hard pause`; the surface is exfiltrating | lean toward `Soft pause` |
| The report has been reproduced by the AI Risk Engineer or by the Lead (with the reporter's permission) | lean toward `Hard pause` | lean toward `Soft pause` |
| Current sessions include any team with a regulated workload (clinical, financial, legal) | lean toward `Hard pause` or targeted pause by population | lean toward `Soft pause` |
| The vendor has a known advisory or status-page incident for the same symptom | document and lean toward `Hard pause` | investigate further |

Decision in the worked drill: **`Soft pause`** at `T+00:30`, subject to escalation to `Hard pause` if the AI Risk Engineer reproduces the symptom by `T+01:00`. Reasoning entered in the decision log: the Lead cannot confirm from the screenshot whether the snippet is real or hallucinated; current sessions include no regulated workload; soft-pausing stops the adoption surface from growing while the technical responders investigate.

##### Decision 2 — User-population communication posture

Options on the table:

- **`No communication yet`** — no field-facing message goes out; the incident remains in the responder lane.
- **`Champion-network holding message`** — the message drafted at `T+00:12` goes out. Champions stand down; general population is not messaged.
- **`General-population message`** — a message goes to every user of the tool.
- **`External / regulator-facing message`** — anything that crosses the org boundary. This is **not** the Enablement Lead's decision alone; it is a joint decision with Legal and Comms, per the AUP.

Criteria the worked drill uses:

| Signal | Posture |
|---|---|
| Report is from one user, not reproduced, no evidence of blast radius | `Champion-network holding message` only |
| Report reproduced; blast radius plausibly includes multiple teams | `General-population message` |
| Regulated workload impacted, or the vendor has a public incident | `General-population message`, draft external / regulator-facing message for Legal review |

Decision in the worked drill: **`Champion-network holding message` at `T+00:35`**. The message goes to the champion Slack channel, not a mass-email. The general-population message is *drafted* at `T+00:40` and parked in the incident record so it can go out at `T+01:00` if the status escalates; it does not go out yet.

The posture here reflects the mod-105 champion-network pattern: the champions are the information artery to the field; messaging the general population too early creates panic and too late creates distrust. The holding message is the bridge.

##### Decision 3 — Training and AUP freeze

Options on the table:

- **`No change`** — training and AUP continue as published.
- **`Training-material freeze`** — stop new enrollments in the fluency course from mod-104 that teaches this specific tool, but let in-flight cohorts continue. New hires scheduled to onboard this week do not get the tool-specific module.
- **`Training-material and AUP freeze`** — same as above, plus the AUP for this tool is temporarily annotated as "under review pending incident `<incident-id>`" so the field knows the acceptable-use posture may change.

Criteria the worked drill uses:

| Signal | Posture |
|---|---|
| The incident is enablement-adjacent but does not change what the tool is cleared to do (e.g., degraded performance) | `No change` |
| The incident could change what the tool is cleared to do (e.g., output-integrity violation that may cross the AUP boundary) | `Training-material freeze` |
| The incident appears to cross the AUP boundary (e.g., data from outside the authorized tenant) | `Training-material and AUP freeze` |

Decision in the worked drill: **`Training-material freeze` at `T+00:45`**. The AUP is not annotated yet because the Enablement Lead does not have enough evidence to say the AUP boundary was crossed. The AUP annotation is drafted and parked; it will be applied at `T+01:00` if the AI Risk Engineer confirms the snippet contained data outside the authorized tenant.

By `T+01:00` the three decisions are made, logged, and have reversibility criteria attached ("escalate to `Hard pause` if reproduced by `T+01:00`", "send general-population message at `T+01:00` if status is not downgraded", "annotate AUP if snippet is confirmed cross-tenant").

#### Phase 3 — `T+01:00 → T+01:30`: write the handoff

By `T+01:30` the Enablement Lead's work in the drill is complete and the handoff memo is on disk. The handoff is **not** a Slack message; it is a written artifact the AI Risk Engineer and SecOps on-call can read without the Lead present and operate from. The handoff memo template is reused verbatim in Exercise 03 of this module, where the contract that governs these handoffs is written. The Lead's drill output is one instance of that contract in action.

The Lead's remaining Phase 3 actions:

1. **`T+01:05`** — Fill out the handoff memo (template below).
2. **`T+01:10`** — Send a one-line Slack message to the incident channel: "Enablement-side handoff memo at `<link>`. Current posture: soft pause, champion-network notified, training freeze in effect, AUP unchanged pending investigation. I am on-call and will be back for the `T+04:00` status check."
3. **`T+01:15`** — Update the champion-network holding message with the actual status if the incident is still open, or send the stand-down message if the incident was downgraded.
4. **`T+01:25`** — File a `post-incident review` meeting slot for the next business day (minimum 24 hours after the incident is closed; per NIST AI RMF `MANAGE-4`, the post-incident review is where improvements to the response process are identified).
5. **`T+01:30`** — Formal handoff complete. The Lead remains available for the next status check and for the three reversibility triggers above, but the enablement-side triage drill is finished.

### 2.3 Artifact templates

Below are the three artifacts the drill produces. These are the actual templates the Lead should maintain in the incident-tracker repo.

#### Artifact 1 — `enablement-side-triage-record.md`

```
# Enablement-side triage record — Incident <YYYY-MM-DD>-<nnn>

## 1. Reporter and first signal
- Reporter: <role name, not person name in this template; person name in the private incident record>
- First signal time: <T+00:00 absolute timestamp>
- Signal channel: <Slack DM / help-desk ticket / champion escalation / usage-dashboard anomaly>
- Signal content (verbatim or screenshot ref): <one line>

## 2. Tool and scope
- Tool: <internal name, e.g., "Tier-1 general-availability AI assistant">
- Rollout stage: <pilot / general availability / sunset>
- Addressable population: <N seats>
- Active sessions at T+00:10: <N>
- Top-10 teams by session volume in the last 30 minutes: <list>

## 3. Threat framing (preliminary)
- OWASP ML Top 10 candidates: <e.g., ML02, ML06, ML09>
- MITRE ATLAS tactic candidates: <e.g., Exfiltration, Impact>
- Note: this is a *preliminary* classification by the Enablement Lead to seed the AI
  Risk Engineer's investigation. Final classification is the AI Risk Engineer's.

## 4. Three enablement-only decisions
### 4.1 Rollout pause
- Decision: <Keep live / Soft pause / Hard pause>
- Time: <T+00:xx>
- Reasoning: <one paragraph; cite the signals from §2.2 above>
- Reversibility triggers: <list; e.g., "escalate to Hard pause if reproduced by T+01:00">

### 4.2 User-population communication
- Decision: <No communication yet / Champion-network holding / General population / External>
- Time: <T+00:xx>
- Message text (copy-paste): <verbatim>
- Audience: <list of channels>
- Reversibility triggers: <list>

### 4.3 Training and AUP freeze
- Decision: <No change / Training freeze / Training + AUP freeze>
- Time: <T+00:xx>
- Scope: <which course IDs, which AUP sections>
- Reversibility triggers: <list>

## 5. Handoff
- Handoff memo location: <path>
- Handoff time: <T+01:xx>
- Receivers: <AI Risk Engineer on-call, SecOps on-call, role names>
- Next Enablement check-in: <T+04:xx and T+24:xx>

## 6. Decision log (chronological, timestamped)
- T+00:01 — <action> — <who> — <evidence or reasoning>
- T+00:03 — ...
- ...
```

#### Artifact 2 — `decision-log.md` (sub-artifact of the triage record)

The decision log is **strictly chronological** and **strictly append-only**. It is not edited after the fact; corrections are entered as new entries with their own timestamp. This is the discipline the post-incident review depends on.

```
# Decision log — Incident <id>

| Time | Who (role) | Action or decision | Evidence or reasoning | Reversibility |
|---|---|---|---|---|
| T+00:01 | AI Enablement Lead | Acknowledged reporter; told reporter not to reproduce prompt | Chain-of-custody preserved for SecOps | n/a |
| T+00:03 | AI Enablement Lead | Paged AI Risk Engineer on-call and SecOps on-call | Per AUP paging chart | n/a |
| T+00:08 | AI Enablement Lead | Captured active-session snapshot | Need current-use baseline for Decision 1 | n/a |
| T+00:12 | AI Enablement Lead | Drafted champion-network holding message | Prepared for Decision 2 | n/a |
| T+00:30 | AI Enablement Lead | Decision 1: Soft pause | Report not reproduced; no regulated workload active; adoption surface stopped from growing | Escalate to Hard pause if reproduced by T+01:00 |
| T+00:35 | AI Enablement Lead | Decision 2: Champion-network holding message sent | Blast radius uncertain; avoid field panic | Send general-population message at T+01:00 if not downgraded |
| T+00:45 | AI Enablement Lead | Decision 3: Training-material freeze | AUP boundary status not yet known | Annotate AUP if snippet confirmed cross-tenant |
| T+01:05 | AI Enablement Lead | Handoff memo filed | Transition to AI Risk Engineer + SecOps lead | n/a |
```

#### Artifact 3 — `handoff-memo.md`

```
# Enablement-side handoff memo — Incident <id>

## One-paragraph read
At T+00:00 a Tier-1 operator in BU-B reported a possible cross-tenant output from
the Tier-1 general-availability AI assistant. Enablement-side triage completed by
T+01:30. Current enablement posture: soft pause (adoption stopped, existing
sessions untouched); champion-network holding message out; training freeze on the
tool-specific fluency module; AUP unchanged pending investigation. Reversibility
triggers are listed in §4 of the triage record.

## What we are handing off
- Reporter identity, screenshot reference, and preserved chain-of-custody.
- Active-session snapshot at T+00:10.
- Preliminary threat framing (OWASP ML Top 10 candidates, MITRE ATLAS tactic
  candidates), pending final classification by the AI Risk Engineer.
- The three enablement-only decisions and their reversibility triggers.

## What we are NOT doing
- We are not contacting the vendor. That is Legal's and SecOps' call.
- We are not analyzing the output for whether the snippet is real data. That is
  the AI Risk Engineer's lane.
- We are not amending the AUP yet. That waits on the AI Risk Engineer's
  confirmation of whether the AUP boundary was crossed.

## What we need from you
- A yes/no by T+01:00 on whether the symptom reproduces, so Decision 1 can hold
  or escalate.
- A yes/no by T+02:00 on whether the snippet contained cross-tenant data, so
  Decision 3 can hold or escalate to AUP annotation.
- Visibility on vendor-advisory status; we will not contact the vendor but we
  will adjust Decision 1 if the vendor publishes a status-page incident.

## Enablement on-call
- AI Enablement Lead: <role name>
- Backup: <role name>
- Next check-in: T+04:00; T+24:00 post-incident review scheduled.
```

### 2.4 Decision rationale — why this shape, not another

- **Why three decisions, not one.** The enablement lane in an incident collapses to three choices: how is the tool *available*, how is the *user population* informed, and what is the *training and policy posture*. Splitting them makes each one reversible on its own trigger; collapsing them into a single "pause the tool" button forces the Lead into an all-or-nothing posture that will usually overshoot.
- **Why 90 minutes.** Shorter than that (30-minute drill) and the decisions are made without evidence; longer than that (half-day drill) and the incident has spread past what the enablement-side triage can meaningfully bound. The 90-minute envelope is what NIST SP 800-61 calls a "triage" step rather than a "recovery" step, adapted to AI-tool blast-radius patterns.
- **Why `Soft pause` as the usual default.** The failure mode of "Keep live" is that the adoption surface keeps growing while the investigation runs; the failure mode of "Hard pause" is that every incident gets escalated to a full outage and the field stops trusting the enablement function with on/off decisions. `Soft pause` is the reversible middle move, and it is the move the Enablement Lead can make unilaterally.
- **Why the champion-network holding message, not a general-population message.** The champion network is the information artery. A general-population message at `T+00:35` creates a panic signal before the responders know whether there is anything to be panicked about. A champion-network message routes correct expectations into the field through the people the field already listens to.
- **Why `Training-material freeze` is a separate decision.** New operators coming into the tool during the incident window are the population most likely to be harmed if the AUP boundary turns out to have shifted. Freezing training enrollments is cheap, reversible, and defensive. Not freezing is the default failure mode — nobody remembers that there is a training course still auto-enrolling new hires until a week later.
- **Why `No vendor contact` by the Enablement Lead.** Vendor relationships are Procurement + Legal + SecOps. The Enablement Lead contacting the vendor during an incident creates a parallel narrative that complicates the eventual customer-notice question. The handoff contract (Exercise 03) formalizes this boundary.
- **Why decision reversibility is logged explicitly.** The post-incident review reads the decision log looking for "was this decision made with the right evidence?" — reversibility triggers are the thing that lets a defensible-at-the-time decision get undone later without re-litigating. They are also the thing that lets the Lead *not* escalate prematurely.

## 3. Validation steps

1. **Phase discipline.** The three phases (`Contain surface`, `Make three decisions`, `Write handoff`) are each time-boxed; the record shows a timestamp for the start and end of each phase.
2. **Three decisions, three reversibility triggers.** Each of the three enablement-only decisions has an explicit reversibility trigger. A decision with no trigger is a decision that will drift, and fails validation.
3. **Decision log is append-only.** The decision log entries are chronological; corrections appear as new entries with later timestamps. Any edited entry fails the chain-of-custody discipline.
4. **Handoff memo under 400 words.** The handoff memo is two minutes of reading. If it is longer than that, the AI Risk Engineer will not read it during the live incident. Grep the memo word count.
5. **No vendor contact initiated by Enablement.** Grep the decision log for "vendor" or the vendor's product name; if the Lead initiated vendor contact, the drill fails.
6. **Champion network contacted before general population.** The decision log shows the champion-network message timestamp strictly earlier than any general-population message timestamp (or shows no general-population message, which is also acceptable in this scenario).
7. **Threat framing is preliminary, not final.** The triage record names OWASP ML Top 10 and MITRE ATLAS candidates but explicitly marks the final classification as the AI Risk Engineer's lane.
8. **Scenario is not tied to a named vendor, named product, or named real-world incident.** Grep the artifacts for vendor product names, trademarked tool names, or `<vendor>.com`. The scenario is generic by design.
9. **Post-incident review is scheduled before the drill ends.** The triage record names the review slot (minimum 24 hours post-close) and lists the attendees.
10. **References back to the dependent modules are present.** The record cites mod-102 (rollout charter), mod-103 (AUP), mod-104 (training), mod-105 (champion network), mod-106 (usage dashboard), and mod-107 (cost model population) by module ID.

## 4. Rubric / review checklist

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | Scope is enablement-side only; AI Risk Engineer and SecOps lanes are explicitly named as out-of-scope | 10 | Drill blurs into technical root-cause analysis or security containment steps the Lead does not own. |
| R2 | 90-minute envelope with three timed phases (`Contain surface`, `Make three decisions`, `Write handoff`) | 10 | Phases missing, untimed, or drifting past 90 minutes without explicit escalation. |
| R3 | Decision 1 (rollout pause) decided with explicit criteria and reversibility trigger | 10 | Decision made without criteria, or without a trigger for revisiting. |
| R4 | Decision 2 (user-population communication) decided with explicit criteria and reversibility trigger; champion-network message sent before any general-population message | 10 | General-population message sent prematurely, or no criteria. |
| R5 | Decision 3 (training and AUP freeze) decided with explicit criteria and reversibility trigger | 10 | Decision collapsed into Decision 1, or no freeze considered. |
| R6 | Decision log is append-only, chronological, and includes who/what/evidence/reversibility per row | 10 | Edited entries; missing columns; untimed entries. |
| R7 | Handoff memo under ~400 words and includes `One-paragraph read`, `What we are handing off`, `What we are NOT doing`, `What we need from you` | 10 | Memo too long, or missing a required section. |
| R8 | Threat framing cites OWASP ML Top 10 candidates and MITRE ATLAS tactic candidates as *preliminary* only | 5 | Lead makes a final classification; no framework reference. |
| R9 | No vendor contact initiated by Enablement; Lead references the handoff contract (Exercise 03) | 5 | Vendor contacted directly during the drill. |
| R10 | References to dependent modules (102, 103, 104, 105, 106, 107) are present by module ID | 5 | No cross-reference to the enablement artifacts the incident actually touches. |
| R11 | Post-incident review scheduled before the drill ends | 5 | No review scheduled; NIST AI RMF `MANAGE-4` discipline missing. |
| R12 | Scenario is generic (no vendor product names, no named real-world incidents) | 5 | Specific product or incident named. |
| R13 | Artifacts are on disk as markdown in the incident-tracker repo, not Slack threads | 5 | Decisions captured only in Slack. |

**Pass threshold:** ≥ 85/100 and no R1 / R6 / R9 fail. R1 (scope discipline) is the most common failure for first-time Leads — pulling the triage into technical root-cause work is the single thing that makes the enablement-side response collapse.

## 5. Common mistakes

- **Pulling into technical root-cause analysis.** The Enablement Lead is not the AI Risk Engineer. Attempting to reproduce the symptom, chase prompt variations, or diagnose retrieval behavior is scope creep; it also burns the 90-minute envelope that was supposed to be spent on the three enablement-only decisions.
- **Contacting the vendor.** Even when it feels helpful ("the vendor's support team is right there"), vendor contact is Legal + SecOps + Procurement territory. Parallel vendor narratives produced by the Enablement Lead create customer-notice headaches later.
- **Messaging the general population immediately.** A `T+00:30` general-population message produces panic signals before the responders know anything. The champion-network holding message is the bridge; use it.
- **Collapsing the three decisions into "pause the tool."** All-or-nothing availability is the wrong instinct. Soft pause, training freeze, and communication posture are three independent levers; use the smallest one that holds.
- **Making decisions without reversibility triggers.** A "soft pause" with no trigger to escalate or stand down drifts into "soft pause forever." Every decision gets a trigger.
- **Editing the decision log.** Corrections happen as new log entries with later timestamps. Edited rows compromise the chain-of-custody posture that the post-incident review and any regulatory inquiry will depend on.
- **Failing to freeze training enrollments.** New operators coming in during the incident window are the population most likely to be harmed; forgetting to pause their fluency-course enrollments is the quiet error that only becomes obvious the following week.
- **Drafting a 1,500-word handoff memo.** If the AI Risk Engineer has to read a wall of text, they will skim it. 400 words, four sections.
- **Not scheduling the post-incident review before the drill ends.** Review slots are the hardest thing to calendar after the adrenaline fades; booking it in Phase 3 is the discipline.
- **Framing the incident as a vendor problem.** Even when it turns out to be, framing it that way during triage anchors the field on an external-blame narrative that undercuts the enablement function's credibility when the cause turns out to be a policy or training gap.

### 5.1 Stretch — second-wave scenario

For practice beyond the single-drill run, re-run the triage with the scenario envelope altered as follows:

- **The reporter is a BU executive**, not a mid-level engineer. The champion-network holding message now routes through a tighter escalation chain, and Decision 2 shifts toward a general-population message earlier because the signal that an executive is already looking means the field will see rumor otherwise.
- **The active-session view shows a regulated workload in flight** (e.g., a clinical-trial summarization task from the Health BU). Decision 1 shifts toward `Hard pause` or a *targeted* pause by population rather than a soft pause; Decision 3 shifts toward `Training + AUP freeze` because the AUP boundary is proximate.
- **The AI Risk Engineer is on PTO and the backup is 45 minutes slower to respond.** The 90-minute envelope now has to carry extra uncertainty; the reversibility triggers extend, and the Lead's default moves toward the more conservative option for each decision.

Running these three alternates is how the drill produces calibration across the Lead team, not just a single rehearsed answer.

## 6. References

- **Learning material (local):**
  - [mod-102 — Selecting and Rolling Out AI Tools](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-102-selecting-and-rolling-out-ai-tools) — the rollout charter that defined which tool is Tier-1 and what "general availability" means for pause posture.
  - [mod-103 — Policy Co-authoring with Governance](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-103-policy-co-authoring-with-governance) — the AUP that names the Enablement Lead as the first-contact role and the paging chart.
  - [mod-104 — Training Programs and AI Literacy Curriculum](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-104-training-programs-and-ai-literacy-curriculum) — the tool-specific fluency course that Decision 3 may freeze.
  - [mod-105 — Champion Networks and Change Management](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-105-champion-networks-and-change-management) — the champion-network charter that makes the holding message a credible channel.
  - [mod-106 — Outcome Measurement and Executive Reporting](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-106-outcome-measurement-and-executive-reporting) — the usage dashboard that provides the active-session snapshot.
  - [mod-107 — Budget, ROI, and Build vs. Buy at Org Scope](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-107-budget-roi-and-build-vs-buy-at-org-scope) — the seat populations and cost-model context used in the scenario envelope.
- **Official standards and frameworks:**
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — the `MANAGE` function is the frame for incident response; `MANAGE-4` is the frame for post-incident review discipline.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — the preliminary threat vocabulary the Enablement Lead uses when seeding the AI Risk Engineer's investigation (ML02, ML06, ML09 in the worked scenario).
  - [MITRE ATLAS](https://atlas.mitre.org/) — the adversarial-tactic vocabulary (`Exfiltration`, `Impact`) used for the preliminary classification.
