# Exercise 05 — Rollout Artifact Set Dry Run — Solution

> Module: `mod-102-selecting-and-rolling-out-ai-tools`
> Exercise type: design / artifact inventory + dry run
> Exercise brief: `lessons/mod-102-selecting-and-rolling-out-ai-tools/exercises/exercise-05-rollout-artifact-set-dry-run.md` (in the learning repo)

## 1. Solution overview

A rollout is a set of artifacts, not an event. When something is missing from the set, the gap is filled informally — someone answers DMs, someone edits the wiki at midnight, someone invents a policy on the fly. The exercise turns the AI Enablement Lead's rollout plan into a **checkable set of artifacts**, dry-runs it, and finds the gaps *before* go-live.

This solution produces:

1. The **artifact inventory** — the full set of things that must exist, each with an owner and a status.
2. A **dry-run script** — a step-through of a hypothetical Day 1 → Week 2 that forces every artifact to be touched by a real user path.
3. **Readiness exit criteria** — the gate between "the kit is drafted" and "we can launch."

The artifact set is the thing exercises 02, 03, and 04 live inside. Exercises 01 and 06 are the inputs. Exercise-05 is the integration test.

## Implementation

Apply this solution by building the artifact inventory in section 2 with named individual owners, running the dry-run script end-to-end before go-live, and holding launch until every readiness exit criterion is a binary "yes." Validate the finished kit against section 3 and score against the rubric in section 4; section 5 lists the common failure modes the inventory-plus-dry-run shape is designed to resist.

## 2. Worked answer

### Artifact inventory

Each row is an artifact. "Present" means the artifact exists at the stated location; "Owned" means a named individual is accountable for maintaining it.

| # | Artifact | Why it must exist | Owner | Present? | Owned? |
|---|---|---|---|---|---|
| 1 | Use policy (exercise-02) | Says what is and is not allowed | AI Enablement Lead | ✅ | ✅ |
| 2 | Policy acknowledgment record | Proves users saw the policy | IT / IAM | required | required |
| 3 | Pilot charter (exercise-04) | Defines success, decisions, rollback | AI Enablement Lead | ✅ | ✅ |
| 4 | Launch comms (3 pieces: all-hands note, team-lead briefing, user-facing one-pager) | Different audiences get the right altitude | AI Enablement Lead + Comms | required | required |
| 5 | FAQ (public internal) | First-line self-serve for the predictable questions | AI Enablement Lead | required | required |
| 6 | Quickstart / how-to | Gets a user to first value without a ticket | AI Enablement Lead + Champion | required | required |
| 7 | 60-minute live kick-off / office-hours cadence | Covers the "I didn't read the doc" tail | AI Enablement Lead | required | required |
| 8 | Support path (named channel + named escalation) | So "where do I ask?" has one answer | AI Enablement Lead + IT Support | required | required |
| 9 | Exception path (form + reviewer + SLA) | Keeps shadow use from eating the policy | AI Enablement Lead | required | required |
| 10 | Incident path (secrets / personal data / abuse) | Known report path, with amnesty clause | Security + DPO | required | required |
| 11 | Metrics sheet (outcome + leading, from exercise-06) | So Week 1 is measurable | AI Enablement Lead | required | required |
| 12 | Weekly report template + schedule (exercise-03) | Executive accountability | AI Enablement Lead | required | required |
| 13 | Admin runbook (SSO, SCIM, logs, entitlements) | So IT can operate, not just install | IT / IAM | required | required |
| 14 | Rollback runbook | So turning it off is a known procedure | AI Enablement Lead + IT | required | required |
| 15 | Audit trail (prompts/completions retention + access) | Required to investigate incidents | Security + DPO | required | required |
| 16 | Vendor contact + escalation sheet | Named human to call for sev-1 | AI Enablement Lead | required | required |
| 17 | Learning content sign-posts | So new users can self-serve past Day 1 | AI Enablement Lead + L&D | required | required |
| 18 | Champion roster for the pilot cohort | Named peer per team for the "dumb question" path | AI Enablement Lead | required | required |
| 19 | Policy change log | Changes to the policy are tracked | AI Enablement Lead | required | required |
| 20 | Data-handling SOP cross-reference | Ties the policy to existing data-handling rules | DPO | required | required |

Fill in "required" with "✅" as each artifact is drafted and reviewed.

### Dry-run script

The script is run *before* go-live by the AI Enablement Lead with the Pilot Owner and the IT Support lead. Each step corresponds to a real user path and must touch at least one artifact; if a step has no artifact to touch, the inventory has a gap.

> **Day -3 — tool enters SSO/SCIM provisioning**
> Touches: #13 admin runbook, #15 audit trail. *Gap test:* if IT does not have the runbook, this step cannot be dry-run.
>
> **Day 0 — launch comms sent**
> Touches: #4 launch comms (all-hands note, team-lead briefing, user one-pager). *Gap test:* every audience in the distribution list must be addressed by one of the three pieces.
>
> **Day 0 — user clicks into the tool for the first time**
> Touches: #1 policy, #2 acknowledgment, #6 quickstart. *Gap test:* a user who reads only these three artifacts must be able to do their first useful task without pinging anyone.
>
> **Day 0 — user hits "my question is not in the quickstart"**
> Touches: #5 FAQ, #8 support path. *Gap test:* the FAQ must cover the top 10 questions a learner can anticipate (secrets, repo tiers, "can I use it on my laptop at home", how to turn it off, how to opt out, etc.).
>
> **Day 1 — user asks for an exception (e.g., `tier-restricted` repo)**
> Touches: #9 exception path. *Gap test:* the reviewer SLA is explicit. If no SLA, the exception path becomes shadow-approval by DM.
>
> **Day 1 — user pastes something they should not have**
> Touches: #10 incident path, #1 policy §5. *Gap test:* the user can find the amnesty clause and the report path without asking for either.
>
> **Day 1 — champion fields a peer question**
> Touches: #18 champion roster. *Gap test:* every pilot team has a named champion, or the roster is incomplete.
>
> **Day 3 — IT Support receives a ticket**
> Touches: #8 support path, #16 vendor escalation. *Gap test:* IT Support knows which issues escalate to the vendor vs. which stay internal.
>
> **Week 1 — first weekly report**
> Touches: #11 metrics, #12 report template. *Gap test:* the metrics sheet already has baseline rows before Week 1, not just Week 1 rows.
>
> **Week 2 — first exception review complete**
> Touches: #9 exception path, #19 policy change log. *Gap test:* if the exception required a policy clarification, the change log reflects it.
>
> **Dry-run rollback drill (any day)**
> Touches: #14 rollback runbook. *Gap test:* the drill is run once before go-live, not left as paper. The drill is a tabletop walk-through at minimum; executing against a staging tenant where possible. <!-- to-verify: confirm whether the learner's environment allows a non-production rollback drill. -->

Every "gap test" is a potential finding. Findings go into the readiness exit criteria below.

### Readiness exit criteria

The rollout cannot launch until:

- All 20 artifacts are **present** and **owned** (named individual, not team).
- The dry-run script has been executed end-to-end with no open gap tests.
- At least one rollback drill has been completed.
- The use policy acknowledgment flow is wired in (users cannot start using the tool before acknowledging).
- The weekly report is scheduled with the exec sponsor on the calendar (not just planned).
- A named champion exists for every pilot team.
- The audit log is on and its retention has been verified against the contract, not assumed.

If any one of these is a "no" on launch day, the launch is held. This is the operational version of "a plan nobody can execute is not a plan."

## 3. Validation steps

A reviewer checking a learner's submission should be able to confirm:

1. The artifact inventory has ≥ 15 rows, each with a named owner (individual).
2. Every artifact row has a one-sentence "why it must exist" — if the learner cannot say *why*, it does not belong.
3. The dry-run script walks a user path, not an internal workflow. "User does X" is the subject of each step.
4. Every dry-run step names at least one artifact it touches.
5. Each dry-run step has a stated gap test.
6. A rollback drill is explicitly included.
7. The readiness exit criteria are concrete and binary (yes/no), not aspirational.
8. The use policy acknowledgment is wired to **gate** tool use, not run as a separate training module.
9. The weekly report is scheduled (calendar), not only drafted (template).
10. The learner's artifact inventory references exercise-02, -03, -04, and -06 explicitly rather than duplicating their contents.

## 4. Rubric or review checklist

Scored out of 20. 14+ passes.

| # | Criterion | Max |
|---|---|---|
| 1 | Artifact inventory ≥ 15 rows, each with individual owner | 3 |
| 2 | "Why it must exist" present for every artifact | 2 |
| 3 | Dry-run script is user-journey shaped | 2 |
| 4 | Every dry-run step names artifacts and a gap test | 3 |
| 5 | Rollback drill included | 2 |
| 6 | Readiness exit criteria are binary | 2 |
| 7 | Policy acknowledgment gates tool use | 1 |
| 8 | Weekly report calendared, not just drafted | 1 |
| 9 | Audit log retention verified against contract (or marked to-verify) | 1 |
| 10 | Cross-references to exercise-02/-03/-04/-06 | 2 |
| 11 | At least one artifact tied to a `nist-ai-rmf` function | 1 |

## 5. Common mistakes

- **Treating comms as the rollout.** The launch email lands and the inventory stops there. The inventory must include the operational artifacts behind the comms.
- **No rollback runbook.** Hoping never to need one. This is the artifact most often missing; the dry-run drill is what forces it to exist.
- **Owner = team.** "IT owns the admin runbook." A team owns nothing unless an individual is responsible on launch day.
- **Policy without acknowledgment gating.** The policy is published but nothing prevents tool use before acknowledgment.
- **FAQ as a wall of text.** Top 10 questions, one answer each, linked from the quickstart.
- **Champion roster is aspirational.** If there is no named peer per team, the "ask a human" path collapses to the enablement lead's DMs.
- **Dry-run on paper only.** A tabletop walk-through catches most gaps; a dry-run that exercises SSO/SCIM/logging against a staging tenant catches the rest. Skip neither.
- **Exceptions are a Slack DM.** Without an exception form and SLA, policy drift is immediate.
- **Metrics sheet starts Week 1.** Baselines must exist before Week 1, or the weekly report has nothing to compare against.

## 6. References

- NIST AI Risk Management Framework (AI RMF 1.0): <https://www.nist.gov/itl/ai-risk-management-framework> — the Govern function underpins policy, acknowledgment, exception, incident, and audit artifacts; the Manage function underpins rollback, audit, and support artifacts.
- OWASP Machine Learning Security Top 10: <https://owasp.org/www-project-machine-learning-security-top-10/> — informs the incident path and the audit-trail artifact scope.
- MITRE ATLAS: <https://atlas.mitre.org/> — framing for adversary scenarios that the audit trail and incident path must support.
- Local context: companion exercises `-02` (policy), `-03` (report), `-04` (charter), `-06` (metrics). Cross-module: `mod-105-champion-networks-and-change-management` for the champion roster; `mod-109-ai-incident-response-and-enablement-side-rollback` for rollback mechanics. <!-- to-verify: confirm cross-module titles in the learner's version of the curriculum. -->
