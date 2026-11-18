# Exercise 04 — Incident-to-Policy-and-Training Feedback Loop — Reference Solution

> Module: `mod-109-ai-incident-response-and-enablement-side-rollback`
> Exercise type: design / worked example (process + artifacts)
> Exercise brief: [`lessons/mod-109-ai-incident-response-and-enablement-side-rollback/exercises/exercise-04-incident-to-policy-training-feedback-loop.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-109-ai-incident-response-and-enablement-side-rollback/exercises/exercise-04-incident-to-policy-training-feedback-loop.md) (in the learning repo)

## 1. Solution overview

The deliverable is a **feedback loop** that turns the output of an AI-tool incident into concrete changes to policy (the mod-103 AUP, SOPs, intake questionnaires) and to training (the mod-104 fluency curriculum, champion-network briefings, new-hire onboarding). The loop closes the cycle between `MANAGE` and `GOVERN` in NIST AI RMF terms — if an incident cannot change the controls, the control set is theatre.

The loop has three artifacts and three cadences:

- **Post-incident findings note** — produced within 5 business days of incident close. Names the findings in a structured format a non-responder can read.
- **Policy-and-training change register** — the running log of findings-driven changes, with owner, status, and deadline per change.
- **Fluency curriculum changelog** — the version history of training materials, so that the `rollback mode` from Exercise 02 has a known-good prior state to restore.

And the three cadences:

- **Per-incident loop** — post-incident review within 5 business days, change register updated within 10.
- **Quarterly roll-up** — the Enablement Lead reviews all open change-register entries with Governance and reports to the AI governance council.
- **Annual refresh** — the AUP, fluency curriculum, and intake questionnaire are reviewed holistically, with the year's incidents as one input alongside regulatory change, tool-portfolio change, and executive-reporting trends.

Posture checks this solution encodes:

- **Every finding maps to a specific policy or training artifact to change, with an owner and a deadline.** Findings that do not route to a change are closed with a documented reason ("no action — root cause outside enablement lane"), not left open.
- **The AUP, SOPs, intake questionnaire, fluency courses, and champion briefings are all named as possible targets.** The loop does not collapse into "update the training"; some findings land in policy, some in process, some in content.
- **Policy changes go through the governance co-authoring pattern from mod-103.** Enablement does not amend the AUP unilaterally; it drafts and routes through the council.
- **Training changes follow the mod-104 versioning discipline.** Course versions are incremented, release notes are written, and the prior version is retained for rollback (Exercise 02 R2 depends on this).
- **Metrics on the loop itself.** Time-to-close per change-register entry, backlog age, and change-register-to-incident ratio are tracked and reported in the mod-106 executive scorecard. A loop you can't measure is a loop you can't trust.
- **No invented metrics, no named incidents.** Worked examples use labeled-hypothetical findings; any specific statistic would need an `<!-- org-specific: ... -->` tag.
- **Threat framing points at OWASP ML Top 10 and MITRE ATLAS** where a finding touches an adversarial-technique category, so the policy and training changes carry the same vocabulary the technical responders use.

## 2. Implementation — worked answer

### 2.1 Scope and what the loop does *not* do

The loop processes **enablement-side findings** — gaps in the AUP, SOPs, intake questionnaire, fluency curriculum, champion briefings, communication patterns, and dry-run cadence that the incident exposed. It does *not* process:

- **Technical root-cause findings** — those are the AI Risk Engineer's lane (model-config change, retrieval-config change, prompt-template change). They go into the Risk Engineering backlog, not this loop.
- **Security-control findings** — those are SecOps' lane (containment tool, evidence-pipeline, external-notice runbook). They go into the SecOps backlog.
- **Vendor-side findings** — those are routed through the Procurement / Legal path from the mod-107 partnership contract, not through enablement policy.

The loop *intersects* with these other backlogs at two points: (a) the post-incident review is a single meeting attended by all three lanes, so findings are identified together; (b) the quarterly roll-up reports on cross-lane findings jointly to the governance council. But each lane owns its own backlog and its own closure discipline.

### 2.2 The three artifacts

#### Artifact 1 — `post-incident-findings-note.md`

Produced within 5 business days of incident close. Convened by the AI Enablement Lead; attended by the three lane leads (per the Exercise 03 contract) plus the Legal and Comms observers. The template:

```markdown
# Post-incident findings — Incident <id>

## 1. Incident summary (one paragraph, for a non-responder reader)
- What happened, in plain language: <one paragraph>
- Final classification (OWASP ML Top 10 and MITRE ATLAS): <e.g., ML09 Output Integrity; MITRE ATLAS Exfiltration>
- Timeline high-level: first signal at <T+00:00>; technical kill-switch at <T+hh:mm>; incident closed at <T+hh:mm>; total elapsed <hh:mm>

## 2. What worked
- <2–5 bullets; this is not filler; it is the signal that tells next-incident
  responders what patterns to preserve>

## 3. Findings (structured)
Each finding has: an ID, a one-sentence statement, a category, an evidence
reference (link to the triage record, decision log, or technical findings note),
and a proposed owner. Categories: POLICY | SOP | INTAKE | TRAINING | CHAMPION |
COMMS | DRY-RUN | OTHER.

| ID | Finding (one sentence) | Category | Evidence | Proposed owner | Proposed deadline |
|---|---|---|---|---|---|
| F1 | AUP section 4.2 does not name the behavior that triggered the incident | POLICY | triage §4.3 | AI Enablement Lead + Legal partner | <deadline> |
| F2 | The Tier-1 fluency course did not include guidance on the prompt pattern that produced the symptom | TRAINING | technical findings §3 | Training designer | <deadline> |
| ... | ... | ... | ... | ... | ... |

## 4. Non-actions (explicit closures)
Any potential finding discussed but *not* taken as an action, with the reason.
This is the discipline that prevents the backlog from drifting.

- <NF1: discussed, not taken because <reason>>
- ...

## 5. Lane-handoffs (findings for other backlogs)
Findings that belong to the AI Risk Engineering or SecOps backlog, with the
handoff receipt confirmation.

- <lane: AI Risk Engineering; finding: ...; handed off to: <role>; receipt confirmed: Y/N>

## 6. Attendees and sign-off
- AI Enablement Lead: <role>
- AI Risk Engineer lead: <role>
- SecOps lead: <role>
- Legal observer: <role>
- Comms observer: <role>
- Governance council delegate (if present): <role>
```

Discipline notes on the findings note:

- **Each finding is one sentence.** The temptation is to write a paragraph; a paragraph's finding is actually several findings disguised as one. Split them.
- **Evidence references are mandatory.** A finding without an evidence anchor to the incident record is an opinion, not a finding, and does not go into the change register.
- **Non-actions are first-class citizens.** Discussing a potential finding and explicitly closing it is a stronger artifact than a long list of open items. The non-actions document decisions that would otherwise re-litigate.

#### Artifact 2 — `policy-and-training-change-register.md`

The running register of all findings-driven changes across incidents. One row per change; columns:

| Change ID | Source finding | Category | Target artifact | Owner (role) | Status | Opened | Due | Closed | Closing commit / version |
|---|---|---|---|---|---|---|---|---|---|
| C-2026-11-01 | 2026-11-17 Incident F1 | POLICY | AUP §4.2 | AI Enablement Lead | Open | 2026-11-20 | 2026-12-15 | — | — |
| C-2026-11-02 | 2026-11-17 Incident F2 | TRAINING | Course `enablement-tier1-fluency` v1.5 → v1.6 | Training designer | In review | 2026-11-20 | 2026-12-01 | — | Draft at `<link>` |
| ... | ... | ... | ... | ... | ... | ... | ... | ... | ... |

Discipline notes on the register:

- **Status values are bounded**: `Open`, `In review`, `Blocked`, `Closed`, `Rejected` (for findings that were taken into the register but later closed without action, with a reason written in the register).
- **Target artifact is named concretely.** "AUP" is not acceptable; "AUP §4.2" is. "Training" is not acceptable; "Course `enablement-tier1-fluency` v1.5 → v1.6" is.
- **Owner is a role, not an individual.** Same discipline as the Exercise 03 contract.
- **Closing commit / version is populated on close.** A `Closed` row without a commit reference is an incomplete closure.
- **The register is append-only.** Rows are not deleted; a rejected change is a `Rejected` row with the reason, preserved for audit.

#### Artifact 3 — `fluency-curriculum-changelog.md`

A `CHANGELOG.md`-shaped file in the curriculum repo, following semantic versioning for training content. Each course has its own changelog; new versions are published with release notes.

```markdown
# Changelog — Course: `enablement-tier1-fluency`

## v1.6 — 2026-12-01
### Added
- Section 3.4: "When the tool returns something that looks like other-tenant data —
  what to do" (from Incident 2026-11-17-001 finding F2; change register C-2026-11-02).

### Changed
- Section 3.1 example prompt replaced with a generic one; prior example pattern
  was proximate to the Incident 2026-11-17-001 symptom (change register C-2026-11-03).

### Note
- Prior version `v1.5` retained in the curriculum repo for rollback compatibility
  (Exercise 02 rollback mode R2 depends on this retention).

## v1.5 — 2026-10-15
### Added
- ...
```

Discipline notes on the changelog:

- **Every change links back to a change-register entry.** This is what makes the loop auditable: an auditor can walk from a changelog entry back to the register entry back to the finding back to the incident.
- **Prior versions are retained.** This is the dependency Exercise 02 R2 names; deleting prior versions breaks the rollback.
- **Version increments follow semver-shaped rules adapted for content**: `minor` for additive content; `patch` for clarifications or typo fixes; `major` for pedagogical restructures or AUP-linked changes that the learner must re-attest to.
- **Major version bumps trigger a re-attestation flow** (per mod-104 — learners who completed `v1.x` receive a `v2.0` re-attestation module, typically 10–15 minutes).

### 2.3 The three cadences

#### Cadence 1 — Per-incident loop

| Step | Owner | Target time |
|---|---|---|
| Post-incident review convened | AI Enablement Lead | Within 5 business days of incident close |
| Findings note filed | AI Enablement Lead | End of the review meeting |
| Change-register entries opened | AI Enablement Lead | Within 10 business days of incident close |
| First status update on each open entry | Entry owner | Within 15 business days |
| Entry closed or escalated for timeline slip | Entry owner | By the entry's due date |

The 5 / 10 / 15-day cadence is the enablement-side discipline; AI Risk Engineering and SecOps keep their own cadences on their own backlogs. The three backlogs are not merged.

#### Cadence 2 — Quarterly roll-up

| Step | Owner | Target time |
|---|---|---|
| Register review with Governance | AI Enablement Lead + Head of AI Governance | Last business week of the quarter |
| Backlog-age report to the AI governance council | AI Enablement Lead | First business week of the following quarter |
| Metrics published to the mod-106 executive scorecard | Enablement operations analyst | First business week of the following quarter |

The quarterly roll-up is where **patterns across incidents** are visible — three incidents in a quarter all producing a champion-network messaging finding points at a champion-network capability gap, not three individual communication errors. These patterns justify larger changes (new champion track, AUP structural refactor) that the per-incident loop cannot reach.

#### Cadence 3 — Annual refresh

| Step | Owner | Target time |
|---|---|---|
| Full AUP review | AI Enablement Lead + Legal partner + Governance | Annual, aligned with the fiscal planning cycle |
| Full fluency curriculum review | AI Enablement Lead + Training designer + L&D partner | Annual |
| Full intake questionnaire review | AI Enablement Lead + Procurement + Security intake partner | Annual |
| Consolidated annual report | AI Enablement Lead | Within 30 days of annual review close |

The annual refresh uses the year's incident-driven findings as one input; it also uses regulatory change, tool-portfolio change, and executive-reporting trends. An AUP that is only reactive to incidents misses the structural changes a year of regulatory and portfolio shift requires.

### 2.4 Worked examples — three findings end-to-end

Three fabricated findings, each traced through the full loop, illustrate how the loop operates in practice. These are **labeled-hypothetical** and do not depend on any specific incident.

#### Worked example A — POLICY finding

- **Incident symptom (abbreviated):** The AUP did not explicitly prohibit uploading a certain class of regulated data to the Tier-1 assistant. A user did upload it; the AUP review treats this as a user-error incident but the Legal partner flags the AUP gap.
- **Finding:** `F-A: The AUP §4.2 prohibited-data list is ambiguous about regulated data class <X>.`
- **Category:** POLICY
- **Target artifact:** AUP §4.2.
- **Owner:** AI Enablement Lead + Legal partner.
- **Change register entry:** `C-YYYY-MM-A1`, status `Open`, due 30 days from open.
- **Change path:** Enablement Lead drafts an amendment to §4.2; routes to Legal for review; routes to the governance council co-authoring pattern from mod-103; council approves; AUP wiki page updated with versioned commit; comms to the general population via the champion network and an all-staff note.
- **Training implication:** the fluency course `enablement-tier1-fluency` requires a `minor` version bump to reflect the new prohibited-data clarity (new change register entry `C-YYYY-MM-A2`, category TRAINING, target Course `enablement-tier1-fluency` v1.6 → v1.7).
- **Closure:** both change-register entries closed with commit references; AUP wiki page shows the new version; LMS course page shows v1.7.

#### Worked example B — INTAKE finding

- **Incident symptom (abbreviated):** The intake questionnaire did not ask a question that would have surfaced the risk the incident eventually realized (e.g., "Does this tool have retrieval over any customer-tenant-isolated data store?"). The question is retroactively obvious.
- **Finding:** `F-B: The intake questionnaire does not ask about customer-tenant isolation in retrieval configuration.`
- **Category:** INTAKE
- **Target artifact:** intake questionnaire from mod-102.
- **Owner:** AI Enablement Lead + Security intake partner.
- **Change register entry:** `C-YYYY-MM-B1`, status `Open`, due 21 days.
- **Change path:** Enablement Lead and Security intake partner draft the new question and its decision-tree branches; existing in-flight intakes are flagged for supplementary review against the new question; the next intake uses the new version.
- **Training implication:** the Procurement AI-sourcing lead and the Security intake partner need a 20-minute briefing on the new question and its decision tree — not a full fluency-course change, but a champion / partner-briefing update (new change register entry `C-YYYY-MM-B2`, category CHAMPION).
- **Closure:** questionnaire repo shows the new version; existing in-flight intakes are supplemented or paused; the partner briefing is delivered.

#### Worked example C — DRY-RUN finding

- **Incident symptom (abbreviated):** During the incident, the Exercise 02 runbook's `K2` step (help-desk macro swap) took 25 minutes instead of the 10-minute target. Root cause: the swap required a help-desk admin who was in another meeting; the runbook did not name the admin role, so paging was slow.
- **Finding:** `F-C: The kill-switch runbook K2 step does not name the help-desk admin role to page; the 10-minute target was missed because of paging delay.`
- **Category:** DRY-RUN
- **Target artifact:** the Exercise 02 runbook K2 step.
- **Owner:** AI Enablement Lead.
- **Change register entry:** `C-YYYY-MM-C1`, status `Open`, due 14 days.
- **Change path:** Enablement Lead amends the runbook to name the help-desk admin role and adds the paging path; next dry run exercises the amended step; dry-run log confirms the 10-minute target is met.
- **Training implication:** none in the fluency curriculum. The amendment is to internal operational documentation. (A finding that routes to DRY-RUN is often operational, not learner-facing.)
- **Closure:** runbook repo shows the amendment; next dry-run log shows the step within target; change-register entry closed.

### 2.5 Metrics the loop reports to the executive scorecard

These metrics go into the mod-106 scorecard under the "control effectiveness" family. They answer "is the loop closing?" and surface drift before it becomes a governance finding.

| Metric | Definition | Target | Published |
|---|---|---|---|
| **Findings-to-change ratio** | # change-register entries / # findings in post-incident notes | ≥ 60% (the rest closed as non-actions with reason) | Quarterly |
| **Change-register median time to close** | median days from `Opened` to `Closed`, excluding `Rejected` | ≤ 30 days for POLICY; ≤ 21 days for TRAINING; ≤ 14 days for DRY-RUN | Quarterly |
| **Change-register backlog age (p90)** | 90th percentile of days-open across currently-open entries | ≤ 60 days | Monthly |
| **Changes-per-incident** | median change-register entries opened per incident | watch for trend; too few suggests loop is not closing, too many suggests triage is too loose | Quarterly |
| **Repeat-category rate** | fraction of quarter's incidents whose findings include a category seen in the same quarter | watch for trend; a rising repeat rate in one category is a capability signal | Quarterly |

Metrics *not* in the loop (held out deliberately):

- **"Number of incidents"** alone is not a loop metric; incident count is visible on the executive scorecard but does not measure the loop. A quarter with zero incidents and an open-backlog of 20 old entries is a loop failure; a quarter with five incidents and a closing-backlog is a loop success.
- **"Policy word count" or "course minute count"** — vanity metrics. The loop does not reward growth of the artifacts; it rewards targeted change.

### 2.6 Decision rationale — why this shape, not another

- **Why three artifacts, not one.** A single "incident retro" document collapses three distinct things: a readable account of what happened (the findings note), an operational tracker of what's being changed (the register), and a versioned artifact history (the changelog). Each has a different reader and a different cadence; separating them makes each one useful to its reader.
- **Why findings are one sentence.** A multi-paragraph "finding" usually hides three or four findings; splitting them makes each one routable and track-able.
- **Why non-actions are a first-class artifact.** The post-incident review almost always surfaces things that *could* be changed but shouldn't be (topic churn would create training fatigue; the finding is actually outside enablement's lane). Writing those down prevents re-litigation and documents the judgment.
- **Why the register is append-only and `Rejected` is its own status.** A register that silently drops rejected items loses the audit trail that the quarterly review depends on. `Rejected` with a reason is a decision with a record.
- **Why training changes follow semver-shaped versioning.** The rollback mode from Exercise 02 depends on prior-version retention; without versioning discipline, the rollback has nothing to roll back to.
- **Why the per-incident cadence is 5 / 10 / 15 days.** Shorter (within the week) is unrealistic — the lane leads are still working the incident and the technical findings note is rarely ready. Longer (a month) loses the context; by the time the review happens, the responders have forgotten the detail that makes the findings specific.
- **Why the quarterly roll-up and the annual refresh exist alongside the per-incident loop.** Per-incident responses miss patterns across incidents (quarterly finds them) and miss structural change drivers like regulatory shift (annual catches them). A loop with only one cadence either misses patterns or over-indexes on single incidents.
- **Why the loop sits inside the enablement function, not the governance function.** Governance owns approval of policy changes (via the mod-103 co-authoring pattern); it does not own authorship. Enablement is the function that sees the field consequences of the AUP, SOPs, and training; it is the right author. Governance is a strong partner in review but should not be running the loop, or the loop drifts into a compliance exercise disconnected from field reality.
- **Why fabricated worked examples.** Any real-world example would either (a) need a primary-source citation to anchor the specifics, or (b) risk accuracy by paraphrasing from memory. Fabricated-but-labeled examples let the loop shape be concrete without pretending to primary-source status.

## 3. Validation steps

1. **Three artifacts exist** (findings note, change register, fluency curriculum changelog) with the structures shown.
2. **Findings-note template has seven sections** (summary, what worked, findings table, non-actions, lane-handoffs, attendees, sign-off).
3. **Each finding in the table is one sentence** and has an evidence reference. Grep for findings with no "evidence" column populated.
4. **Change-register columns are present** (Change ID, Source finding, Category, Target artifact, Owner, Status, Opened, Due, Closed, Closing commit / version).
5. **Status values are bounded** to `Open / In review / Blocked / Closed / Rejected`; any other value fails validation.
6. **Target artifact is named concretely** (section number, course and version). Grep for target-artifact cells that contain only the family name ("AUP", "Training").
7. **Owners are role names**, not individual names. Grep.
8. **Rejected entries carry a reason** in the register, not just the Rejected status.
9. **Fluency changelog follows a versioning convention** and retains prior versions in the curriculum repo. A deleted prior version fails validation because it breaks Exercise 02 R2.
10. **Per-incident cadence is 5 / 10 / 15 days**, stated explicitly in the loop documentation.
11. **Quarterly roll-up and annual refresh are named** with owners and target weeks.
12. **The five loop metrics are defined** with their numerator and denominator; the metrics explicitly excluded (incident count, policy word count) are named.
13. **The loop references OWASP ML Top 10 and MITRE ATLAS** in the findings-note template's classification section.
14. **The loop references dependent modules** (mod-103 governance co-authoring, mod-104 training, mod-102 intake, mod-105 champion, mod-106 scorecard) by module ID.
15. **Non-actions are present in the worked example** and explicitly tracked in the register process (not collapsed into "just don't write it down").
16. **Worked examples are labeled-hypothetical**, not tied to a real incident or vendor product.

## 4. Rubric / review checklist

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | Three artifacts defined (findings note, change register, fluency curriculum changelog) with templates | 10 | Fewer than three; or templates missing structure. |
| R2 | Three cadences defined (per-incident 5/10/15, quarterly, annual) with owners and target windows | 10 | Fewer than three cadences; or missing owners. |
| R3 | Findings are one-sentence, have evidence references, and route to a bounded set of categories (POLICY / SOP / INTAKE / TRAINING / CHAMPION / COMMS / DRY-RUN / OTHER) | 10 | Multi-paragraph findings; no evidence; unbounded categories. |
| R4 | Non-actions are a first-class artifact; the findings-note template reserves a section for them | 10 | Non-actions collapsed into "don't write"; or no section for them. |
| R5 | Change register is append-only, with `Open / In review / Blocked / Closed / Rejected` status set and role-name owners | 10 | Register is editable; status set unbounded; owners by name. |
| R6 | Target artifact in the register is named concretely (section number, course and version) | 10 | Target named only by family. |
| R7 | Fluency curriculum changelog uses a versioning convention, links each entry to a change-register entry, and retains prior versions | 10 | No versioning; no cross-link; prior versions deleted. |
| R8 | Five loop metrics defined with numerator / denominator and reporting cadence; excluded metrics explicitly named | 10 | Metrics missing; vanity metrics (word count) not excluded. |
| R9 | Loop scope explicitly excludes technical root-cause, security-control, and vendor-side findings (which route to other backlogs) | 5 | Loop absorbs other-lane findings. |
| R10 | Governance co-authoring pattern (mod-103) is named as the approval path for POLICY-category changes | 5 | Enablement amends AUP unilaterally; no governance partner. |
| R11 | OWASP ML Top 10 and MITRE ATLAS referenced in the findings-note classification; the vocabulary is consistent with Exercise 01 and Exercise 03 | 5 | No framework reference. |
| R12 | Worked examples are labeled-hypothetical and route through the full loop (finding → register → changelog / commit) | 5 | No worked examples; or examples tied to real incidents or vendor products. |

**Pass threshold:** ≥ 85/100 and no R4 / R5 / R7 fail. R4 (non-actions) is the discipline that keeps the loop honest; R5 and R7 (register and changelog append-only / versioned) are the discipline that make it auditable.

## 5. Common mistakes

- **Collapsing findings into the change register without writing a findings note.** The findings note is for the next-incident reader; the register is for the loop operator. Skipping the note loses the readable account and the non-actions discipline.
- **Writing multi-paragraph findings.** A paragraph hides multiple findings; each needs its own routing, owner, and deadline. Split.
- **Dropping rejected findings silently.** A `Rejected` entry with a reason is an audit record of a decision made; a silently-dropped finding is a decision made and un-recorded. The latter is also, over time, the raw material for "we never surface findings in this category," which is a loop failure.
- **Letting the register sit without owners or deadlines.** An entry without an owner-role and a due date is an entry that will age indefinitely. A monthly backlog-age (p90) report surfaces these; fixing them is harder than opening them correctly in the first place.
- **Amending the AUP without the governance co-authoring pattern.** Enablement does not own the AUP; mod-103 does. Unilateral amendments produce an AUP the governance council does not back and that Legal has not reviewed — one of the fastest ways to lose council trust.
- **Not versioning training content.** Rollback (Exercise 02 R2) depends on prior-version retention; a changelog that deletes prior versions breaks the rollback path and is a direct audit finding in a mature program.
- **Over-indexing on training.** The temptation after every incident is "add a module." A loop that routes every finding to TRAINING creates learner fatigue and does not address the structural (POLICY, SOP, INTAKE, DRY-RUN) causes that are often the real driver.
- **Treating the quarterly roll-up as optional.** Per-incident loops miss patterns; three similar champion-messaging findings in one quarter is a capability signal, not three individual errors. Skipping the roll-up loses this.
- **Reporting incident count to the executive as the control-effectiveness metric.** Incident count is not a loop metric; a quarter of zero incidents with an aging backlog is a loop failure the count does not show.
- **Letting the annual refresh become a formatting exercise.** The annual AUP review that only re-formats and does not consider the year's incident findings alongside regulatory and portfolio change is a governance-theatre artifact.
- **Merging the three lane backlogs.** Enablement, AI Risk Engineering, and SecOps each own their own loop. Merging them produces an artifact nobody owns and a cadence nobody keeps.
- **Including real vendor names or real incident identifiers in worked examples.** Fabricated-but-labeled examples let the loop shape be concrete without false precision; real identifiers in training artifacts have a tendency to escape context.

### 5.1 Stretch — connecting the loop to hiring and onboarding

Once the loop is mature, two extensions earn their place:

- **New-hire onboarding diff.** Every quarter, the changes to the AUP, SOP set, and fluency curriculum are summarized into a "what changed this quarter" one-pager that becomes part of new-hire onboarding — so a new hire in Q2 starts with the version of the controls that reflects Q1's incidents, not the version that was current when the program was designed. The one-pager is a 10-minute read and lives in the onboarding repo.
- **Hiring-rubric feedback.** Repeat-category findings over the year (e.g., "we repeatedly find INTAKE gaps in categories X and Y") are a signal to the hiring rubric for the Security intake partner and the Procurement AI-sourcing lead; the hiring team receives an annual note from the Enablement Lead with the categories the role must screen for. This is a soft connection and lives at the discretion of the Head of Enablement.

## 6. References

- **Learning material (local):**
  - [mod-101 — Role and Org-wide Enablement Operating Model](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-101-role-and-the-org-wide-enablement-operating-model) — the operating-model vocabulary used in the escalation paths.
  - [mod-102 — Selecting and Rolling Out AI Tools](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-102-selecting-and-rolling-out-ai-tools) — the intake questionnaire whose INTAKE-category findings amend.
  - [mod-103 — Policy Co-authoring with Governance](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-103-policy-co-authoring-with-governance) — the AUP and the governance co-authoring pattern that POLICY-category changes travel through.
  - [mod-104 — Training Programs and AI Literacy Curriculum](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-104-training-programs-and-ai-literacy-curriculum) — the fluency curriculum whose TRAINING-category findings version.
  - [mod-105 — Champion Networks and Change Management](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-105-champion-networks-and-change-management) — the champion-network charter whose CHAMPION-category findings refine.
  - [mod-106 — Outcome Measurement and Executive Reporting](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-106-outcome-measurement-and-executive-reporting) — the executive scorecard the loop metrics publish to.
  - [mod-109 Exercise 01 — Enablement-Side Incident Triage Drill](../exercise-01-enablement-side-incident-triage-drill/SOLUTION.md) — the triage record and decision log are evidence inputs for the loop.
  - [mod-109 Exercise 02 — Kill-Switch and Rollback Dry Run](../exercise-02-kill-switch-and-rollback-dry-run/SOLUTION.md) — the runbook whose DRY-RUN-category findings amend; the rollback mode depends on the curriculum changelog's prior-version retention.
  - [mod-109 Exercise 03 — Handoff Contract with AI Risk Engineer and SecOps](../exercise-03-handoff-contract-with-ai-risk-engineer-and-secops/SOLUTION.md) — the post-incident review attendance and lane-handoff discipline come from this contract.
- **Official standards and frameworks:**
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — the `MANAGE-4` function (post-incident review and continual improvement) and the `GOVERN` function (policy change discipline) are the frame for this loop.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — the vocabulary used in the findings-note classification section.
  - [MITRE ATLAS](https://atlas.mitre.org/) — the adversarial-tactic vocabulary used alongside OWASP where a finding touches an adversarial-technique category.
