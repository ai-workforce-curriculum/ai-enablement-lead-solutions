# Exercise 02 — Kill-Switch and Rollback Dry Run — Reference Solution

> Module: `mod-109-ai-incident-response-and-enablement-side-rollback`
> Exercise type: implementation / runbook with dry-run plan
> Exercise brief: [`lessons/mod-109-ai-incident-response-and-enablement-side-rollback/exercises/exercise-02-kill-switch-and-rollback-dry-run.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-109-ai-incident-response-and-enablement-side-rollback/exercises/exercise-02-kill-switch-and-rollback-dry-run.md) (in the learning repo)

## 1. Solution overview

The deliverable is a **kill-switch and rollback runbook** that the AI Enablement Lead can execute during a drill without touching production, and a **dry-run plan** that exercises every step of the runbook at least once per quarter. The runbook has two modes:

- **Kill-switch mode** — the tool is taken off the enablement-managed surface immediately. The *technical* kill-switch (the API-key revoke or vendor-side disable) is operated by the AI Risk Engineer; the *enablement-side* kill-switch is everything the Enablement Lead flips to make sure users, workflows, training, and the cost center all move with the technical disable.
- **Rollback mode** — the tool stays available but the enablement rollout state is reverted. For example, a tool currently in General Availability (GA) returns to "pilot-only" scope; a fluency course returns to its pre-amendment version; a champion-network message is retracted and re-sent.

The two modes are triggered by different incident classes (the Exercise 01 triage drill decides which) and have different reversibility profiles. The runbook treats them as distinct procedures with explicitly named decision gates between them.

Posture checks this solution encodes:

- **The Enablement Lead does not flip the technical kill-switch.** That is the AI Risk Engineer's lever (see Exercise 03 handoff contract). The Lead's lane is the *enablement-side* kill-switch: training enrollments, help-desk macros, champion-network messaging, AUP annotations, procurement commits, SSO groups within the enablement cost center.
- **Every step in the runbook is reversible, or is explicitly flagged as non-reversible with the reason.** A non-reversible step (like sending an all-staff email) is gated behind a named approver.
- **The dry run exercises every step without touching production.** `--dry-run` flags, staging environments, and read-only Slack channels are the mechanism. Success criteria for the dry run are written down and checked.
- **Cadence is quarterly minimum, monthly for a new rollout in its first quarter.** NIST AI RMF `MANAGE-4` ("regular review of incident-response capability") sets the floor; enablement-specific maturity sets the ceiling.
- **No vendor names; no vendor-specific API calls.** The runbook names generic entitlement surfaces (`IdP group`, `help-desk macro ID`, `LMS course ID`) and the learner maps them to the specific tool IDs in their org.
- **Threat framing points at OWASP ML Top 10 and MITRE ATLAS** where a trigger condition maps to an adversarial technique, so the runbook ties back to the shared vocabulary.

## 2. Implementation — the runbook

The runbook lives in the enablement-ops repo as `runbooks/kill-switch-and-rollback.md` next to a companion shell script (`scripts/enablement-kill-switch.sh`) that performs the mechanical steps that can be automated. What follows is the full runbook.

### 2.1 When to use which mode

| Trigger (from Exercise 01 triage) | Mode |
|---|---|
| Exercise 01 Decision 1 = `Hard pause` | Kill-switch mode |
| Exercise 01 Decision 1 = `Soft pause` | Neither — Exercise 01 covers this |
| AI Risk Engineer confirms output-integrity violation that crosses the AUP boundary | Kill-switch mode |
| AI Risk Engineer confirms a *content* or *behavior* regression but not an AUP-boundary crossing | Rollback mode |
| Vendor publishes a status-page incident impacting the tool's integrity | Kill-switch mode until vendor stand-down |
| Champion-network signal of broad user frustration without a security dimension | Rollback mode (revert to prior training or config) |

If the triage is ambiguous, the default is **kill-switch** — it is more reversible than its name suggests, because the enablement-side kill-switch is a stand-down, not a deletion.

### 2.2 Kill-switch mode — enablement-side runbook

Target completion: **≤ 30 minutes from the AI Risk Engineer's decision to flip the technical kill-switch.** This is the time the enablement surface has to catch up with the technical disable. Anything slower and the field experiences the outage before the enablement function explains it.

#### Pre-flight checks (always run first)

1. Confirm the technical kill-switch has been flipped (or is about to be, within 5 minutes). If it has not been flipped, stop; the enablement-side kill-switch without the technical one creates a confusing half-off state.
2. Confirm the incident has a numeric ID and an incident channel. If it does not, open one; the runbook depends on a stable incident ID for naming artifacts.
3. Confirm the AI Enablement Lead (or backup) is on the incident channel. The runbook is not a background job; it is a live process with a human at the keyboard.

#### Step K1 — Entitlement freeze (within 5 minutes)

- Freeze the IdP group(s) that grant tool entitlement on the enablement side. "Freeze" means: no new adds to the group; existing members keep their entitlement for now (the technical kill-switch has already revoked access).
- **Action:** `enablement-kill-switch.sh --freeze-idp-group <group-id> --incident <id> [--dry-run]`
- Why freeze vs. remove: removing group memberships is the AI Risk Engineer's lever (or IT's), not the Enablement Lead's. Freezing *adds* stops the adoption surface from growing during the incident.
- **Validation:** the group's audit log shows a freeze event with the incident ID.

#### Step K2 — Help-desk macro swap (within 10 minutes)

- Swap the help-desk macros that currently route users to the tool for the "tool is unavailable; here is the alternate workflow" macro.
- **Action:** `enablement-kill-switch.sh --swap-helpdesk-macros <tool-tag> --incident <id> [--dry-run]`
- The alternate workflow macro is pre-written and maintained in the enablement-ops repo as part of the rollout charter artifacts from mod-102. If no alternate exists, the macro is "the tool is unavailable; please wait for an all-staff update at `<T+hh:mm>`."
- **Validation:** the help-desk system shows the macros swapped; a test ticket raised to the help-desk returns the alternate macro.

#### Step K3 — Training enrollment freeze (within 15 minutes)

- Freeze new enrollments in all LMS courses tagged for the tool. In-flight cohorts continue unless Decision 3 of triage escalated to `Training + AUP freeze`.
- **Action:** `enablement-kill-switch.sh --freeze-lms-courses <course-tags> --incident <id> [--dry-run]`
- **Validation:** a test enrollment attempt in a dry-run LMS tenant returns a `frozen pending incident <id>` error.

#### Step K4 — Champion-network stand-down (within 20 minutes)

- Send the "stand down from encouraging use" message to the champion Slack channel. This is the message drafted in Exercise 01 Phase 1, now sent with the current status.
- **Action:** manual Slack send; not automated. Tracked as a checklist item, not a script step.
- **Validation:** the message is posted; each champion reacts with `:eyes:` to acknowledge (or pages back if they cannot stand down because of a time-sensitive demo etc.).

#### Step K5 — Procurement commit freeze (within 25 minutes)

- Flag the Procurement partner (per the mod-107 partnership contract and Exercise 03 of this module) to freeze any in-flight commits related to the tool: no seat expansions, no consumption-uplift commitments, no renewal signings. Existing commitments are not cancelled; they are paused pending incident close.
- **Action:** manual notification; not automated. Tracked via the standing cadence from the mod-107 partnership contract.
- **Validation:** Procurement acknowledges the freeze in the incident channel.

#### Step K6 — AUP annotation (within 30 minutes; conditional)

- If Exercise 01 Decision 3 escalated to `Training + AUP freeze`, annotate the AUP page for this tool with a visible "under review pending incident `<id>`" banner. The annotation does not change the AUP text; it signals to readers that the posture is in motion.
- **Action:** manual edit to the AUP wiki page; version-controlled commit.
- **Validation:** the AUP page shows the banner; the commit is visible in the governance repo.

#### Post-flight checks (always run last)

- The decision log from Exercise 01 has new entries for each of K1–K6 with timestamp, operator (role), and script invocation (if scripted).
- The incident channel has a single consolidated status message: "Enablement-side kill-switch complete: K1–K6 done, K6 skipped because `<reason>`. Next check-in at `T+hh:mm`."
- The post-incident review already scheduled in Exercise 01 Phase 3 is confirmed.

### 2.3 Rollback mode — enablement-side runbook

Target completion: **≤ 2 hours from the decision to roll back.** Rollback is slower than kill-switch because it is about restoring a *known-good* prior enablement state, not just stopping the current one.

Rollback is defined by **what state you are returning to**. The runbook requires this state to be named explicitly before any rollback step runs.

#### Pre-flight — name the target state

Before running any rollback step, write down answers to all of:

- **Rollout stage target:** e.g., "revert from `GA` to `pilot-only`, scope = original pilot population from mod-102 charter"
- **Training-content target:** e.g., "revert fluency course `enablement-tier1-fluency` to version `v1.4`"
- **AUP target:** e.g., "revert AUP section 4.2 to version `2026-09-15`"
- **Champion-network messaging target:** e.g., "retract the `2026-11-10` champion message about the new feature; re-send the prior guidance"

If any target is "I don't know" or "whatever is current", stop. A rollback with an unnamed target is a fresh change, not a rollback, and is the single most common failure mode.

#### Step R1 — Rollout stage reversion (within 60 minutes)

- Change the IdP group memberships back to the pilot-population scope. Users outside the pilot population lose entitlement; users inside keep it.
- **Action:** `enablement-kill-switch.sh --revert-idp-group <group-id> --to-cohort <cohort-id> --incident <id> [--dry-run]`
- The pilot-population cohort is the artifact from the mod-102 rollout charter; the script reads from the charter's cohort file.
- **Validation:** IdP group membership matches the pilot-population cohort list; audit log shows the revert event.

#### Step R2 — Training-content reversion (within 90 minutes)

- Revert the LMS course(s) to the named prior version. New enrollments get the prior version; in-flight cohorts are *not* moved mid-course (that confuses learners); their current version completes, and the next cohort starts on the prior version.
- **Action:** `enablement-kill-switch.sh --revert-lms-course <course-id> --to-version <version-id> --incident <id> [--dry-run]`
- **Validation:** the LMS course page shows the prior version; a test enrollment in a dry-run tenant sees the prior content.

#### Step R3 — AUP reversion (within 2 hours)

- Revert the named AUP section to the named prior version, as a proper version-controlled commit against the governance repo.
- **Action:** `git revert <commit-sha>` in the governance repo, PR, review by Legal partner, merge. The Enablement Lead opens the PR; the Legal partner approves. The revert is a two-signature commit.
- **Validation:** the AUP wiki page shows the prior version; the PR shows the two signatures.

#### Step R4 — Champion-network re-messaging (within 2 hours)

- Send the retract-and-re-send message to the champion Slack channel: "We are rolling back the `2026-11-10` guidance on the new feature. Here is the prior guidance that is current again: `<link to prior guidance>`. We will walk this at the next champion council in `<N>` days."
- **Action:** manual send; template lives in the champion-ops repo.
- **Validation:** message posted; champions acknowledge.

#### Step R5 — Scorecard annotation (within 2 hours)

- Annotate the executive scorecard (mod-106) with a rollback event marker at the relevant date, so the fluency and adoption trend lines are not read naively after the rollback.
- **Action:** add a row to the scorecard's event table.
- **Validation:** the scorecard renders the event marker.

#### Post-flight checks (always run last)

- The decision log has entries for R1–R5 with timestamps.
- The incident channel has a single consolidated status message naming each prior state the rollback restored.
- The post-incident review already scheduled is confirmed.

### 2.4 Companion script — `scripts/enablement-kill-switch.sh`

This is the mechanical operator for the runbook steps that can be scripted. It is intentionally minimal; the operations it performs are IdP group writes, help-desk macro swaps, and LMS course freezes, each gated behind a `--dry-run` flag. The script is idempotent: running it twice with the same `--incident <id>` has the same effect as running it once.

```bash
#!/usr/bin/env bash
# enablement-kill-switch.sh — enablement-side kill-switch and rollback operator
# This script is NOT the technical kill-switch. It operates the enablement surface
# (IdP groups, help-desk macros, LMS courses) only. The technical kill-switch is
# the AI Risk Engineer's lever and lives elsewhere.

set -euo pipefail

usage() {
  cat <<'USAGE'
Usage:
  enablement-kill-switch.sh --freeze-idp-group <group-id>       --incident <id> [--dry-run]
  enablement-kill-switch.sh --swap-helpdesk-macros <tool-tag>   --incident <id> [--dry-run]
  enablement-kill-switch.sh --freeze-lms-courses <course-tags>  --incident <id> [--dry-run]
  enablement-kill-switch.sh --revert-idp-group <group-id>       --to-cohort <cohort-id>  --incident <id> [--dry-run]
  enablement-kill-switch.sh --revert-lms-course <course-id>     --to-version <version-id> --incident <id> [--dry-run]

Every invocation requires --incident <id>. Every invocation writes to the enablement audit log.
--dry-run performs no write; it prints the exact write it would perform and returns 0.
USAGE
}

# --- arg parsing (minimal; production implementation uses a proper arg parser) ---
ACTION=""
INCIDENT=""
DRY_RUN="false"
# ... (parser elided; one case per --flag) ...

if [[ -z "${INCIDENT}" ]]; then
  echo "ERROR: --incident <id> is required" >&2
  exit 2
fi

# --- helpers ---
log() {
  # Writes to the enablement audit log and the incident channel.
  local msg="$1"
  local ts
  ts="$(date -u +%Y-%m-%dT%H:%M:%SZ)"
  echo "${ts} incident=${INCIDENT} action=${ACTION} ${msg}" \
    | tee -a "${ENABLEMENT_AUDIT_LOG:-/var/log/enablement/audit.log}"
}

require_approver() {
  # Non-reversible steps require a named approver in-band.
  local step="$1"
  if [[ -z "${APPROVER:-}" ]]; then
    echo "ERROR: step ${step} requires APPROVER=<role-name> in env" >&2
    exit 3
  fi
  log "approver=${APPROVER}"
}

# --- actions ---
freeze_idp_group() {
  local group="$1"
  log "freeze-idp-group group=${group}"
  if [[ "${DRY_RUN}" == "true" ]]; then
    log "dry-run: would freeze group ${group}"
    return 0
  fi
  # idp_cli freeze --group "${group}" --reason "incident ${INCIDENT}"
  :  # implementation elided; concrete IdP CLI is org-specific
}

swap_helpdesk_macros() {
  local tag="$1"
  log "swap-helpdesk-macros tag=${tag}"
  if [[ "${DRY_RUN}" == "true" ]]; then
    log "dry-run: would swap macros tagged ${tag} to the 'tool-unavailable' alternate"
    return 0
  fi
  # helpdesk_cli macros swap --from-tag "${tag}" --to-macro "tool-unavailable"
  :  # implementation elided; concrete help-desk CLI is org-specific
}

freeze_lms_courses() {
  local tags="$1"
  log "freeze-lms-courses tags=${tags}"
  if [[ "${DRY_RUN}" == "true" ]]; then
    log "dry-run: would freeze courses tagged ${tags}"
    return 0
  fi
  # lms_cli courses freeze --tags "${tags}" --reason "incident ${INCIDENT}"
  :  # implementation elided; concrete LMS CLI is org-specific
}

revert_idp_group() {
  local group="$1"
  local cohort="$2"
  require_approver "revert-idp-group"
  log "revert-idp-group group=${group} cohort=${cohort}"
  if [[ "${DRY_RUN}" == "true" ]]; then
    log "dry-run: would set group ${group} memberships to cohort ${cohort}"
    return 0
  fi
  # idp_cli group members set --group "${group}" --from-cohort-file "${cohort}"
  :  # implementation elided
}

revert_lms_course() {
  local course="$1"
  local version="$2"
  require_approver "revert-lms-course"
  log "revert-lms-course course=${course} version=${version}"
  if [[ "${DRY_RUN}" == "true" ]]; then
    log "dry-run: would revert course ${course} to version ${version}"
    return 0
  fi
  # lms_cli course revert --course "${course}" --to-version "${version}"
  :  # implementation elided
}

# dispatch — one of the actions above runs; all other args are ignored.
case "${ACTION}" in
  freeze-idp-group)    freeze_idp_group "${FLAG_ARG}" ;;
  swap-helpdesk-macros) swap_helpdesk_macros "${FLAG_ARG}" ;;
  freeze-lms-courses)  freeze_lms_courses "${FLAG_ARG}" ;;
  revert-idp-group)    revert_idp_group "${FLAG_ARG}" "${TO_COHORT}" ;;
  revert-lms-course)   revert_lms_course "${FLAG_ARG}" "${TO_VERSION}" ;;
  *) usage; exit 2 ;;
esac
```

Notes on the script:

- The concrete `idp_cli`, `helpdesk_cli`, `lms_cli` calls are elided because they are organization-specific. The learner replaces them with the actual CLI the org uses. The shape — "idempotent, incident-scoped, dry-run-capable, audit-logged, approver-gated for reverts" — is the stable part.
- The script never calls a vendor API for the AI tool itself. That is the technical kill-switch's lane.
- The `require_approver` function enforces the two-person rule on reverts: the Enablement Lead triggers the script, but the revert does not run without an `APPROVER` role named in the environment (e.g., `APPROVER=head-of-ai-governance`). Dry-run does not require an approver, because dry-run writes nothing.
- The audit log is append-only; the dry-run entries are kept so the dry-run itself leaves a record.

### 2.5 The dry-run plan

The dry run is run on the cadence below, by the AI Enablement Lead with the Program Manager as co-operator. The goal is **to exercise the full runbook in a non-production state and verify each validation point**, not to catch bugs in the script; the script's own tests should catch those.

#### Cadence

- **Monthly** for the first three months after a new tool goes GA.
- **Quarterly** once a tool has been GA for more than three months.
- **Out-of-band** within one week after any major rollout-charter change (new population added, new AUP section, new course version).
- **Out-of-band** within one week after any real incident, as the first step of the post-incident review action set.

#### Pre-run checklist

- Dry-run tenants are reachable for IdP, help-desk, and LMS (staging equivalents of each).
- A **mock incident ID** is reserved (format: `DRY-YYYY-MM-DD-<nnn>`).
- The incident channel is a dedicated `#enablement-drill` Slack channel; not the real incident channel.
- Each champion in the champion network is informed that a dry-run message may hit the channel; a tag convention (`[drill]` prefix) marks dry-run traffic unmistakably.
- The audit log is partitioned so dry-run entries are tagged `drill=true` and do not contaminate real-incident metrics.

#### Run plan — kill-switch dry-run

1. Operator (Enablement Lead) opens the runbook and the mock incident channel.
2. Operator runs each of K1–K5 with `--dry-run`, in order, within the target times.
3. For each step, the operator records (a) elapsed time, (b) whether the validation point passed, (c) any ambiguity in the runbook text itself.
4. K6 (AUP annotation) is run against a staging branch of the governance repo, not main.
5. Operator closes with a one-paragraph summary filed in the drill-log repo: steps that passed, steps that were ambiguous, steps that took longer than target.

#### Run plan — rollback dry-run

1. Operator names the target state (rollout stage, training version, AUP version, champion message) **before** any step runs. This is the critical discipline that distinguishes rollback from fresh change.
2. Operator runs each of R1–R5 with `--dry-run`, in order, within the target times.
3. R3 (AUP reversion) is simulated with a `git revert --no-commit` in the staging branch; the actual commit is not made.
4. R5 (scorecard annotation) is made against a staging copy of the scorecard, not the live one.
5. Operator closes with a one-paragraph summary including an answer to the explicit question: **did we have a known-good prior state for every dimension, or did we invent one?** Inventing one is a finding; the mod-102 rollout-charter artifacts should always name prior states.

#### Success criteria

The dry run passes if **every validation point in the runbook is reached and recorded** and if **the total run time is within the kill-switch 30-minute and rollback 2-hour targets**. A pass on only time or only validation is a partial pass; both are required.

The dry run produces a **drill log entry** that is reviewed in the next quarterly cadence meeting with Procurement and Finance (per the mod-107 partnership contract) and in the next quarterly cadence meeting with the AI Risk Engineer and SecOps (per Exercise 03 of this module).

### 2.6 Decision rationale — why this shape, not another

- **Why two modes, not one.** Collapsing kill-switch and rollback into a single "pause/revert" button is the common first-draft move; it fails because the trigger criteria and the reversibility profile are different. Kill-switch is for *integrity* or *AUP-boundary* incidents; rollback is for *regression* or *content-drift* incidents. Confusing them leads to either overshoot (a GA tool goes to zero when it should have gone to pilot-scope) or undershoot (a cross-tenant leak gets treated as a content regression).
- **Why 30-minute and 2-hour targets.** The 30-minute kill-switch target matches the time the technical kill-switch itself typically takes to propagate through vendor-side caches; the enablement surface should not lag that. The 2-hour rollback target matches the window in which the field notices "something changed" and starts filing tickets; after 2 hours, a rollback is a change event, not a recovery.
- **Why idempotent, incident-scoped scripts.** Idempotency is what makes the script safe to run in a distracted incident state ("did I already run K1?"); incident-scoping is what makes the audit log make sense months later.
- **Why `--dry-run` as a first-class flag.** A runbook that cannot be dry-run cannot be practiced; a runbook that cannot be practiced erodes within a quarter. Dry-run is the single investment that keeps the runbook honest.
- **Why `require_approver` on reverts, not on freezes.** Freezes are reversible (freezing an IdP group adds does not delete members); reverts write a specific prior state and are harder to undo (restoring membership after a revert requires knowing the exact prior membership list). The two-person rule is proportional to reversibility.
- **Why champion-network action is not scripted.** Sending a Slack message to the champion network is the one place a human's judgment on tone, timing, and context is load-bearing. Automating it saves seconds and loses credibility.
- **Why cadence is monthly for new tools, quarterly for mature tools.** New tools concentrate the risk of an unpracticed response; after three months of operational use, the runbook has usually been exercised at least once in anger and the drill can drop to quarterly.

## 3. Validation steps

1. **Two modes, explicit triggers.** The runbook carries a trigger table mapping Exercise 01 triage outcomes (and other signals) to kill-switch vs. rollback.
2. **Every step has a validation point.** Grep for "Validation:" in the runbook; every step K1–K6 and R1–R5 has one.
3. **Scripted steps are dry-runnable.** `enablement-kill-switch.sh --dry-run` exits 0 for each of the scripted actions, writes an audit-log entry, and makes no production write.
4. **Reverts require an approver; freezes do not.** `enablement-kill-switch.sh --revert-*` without `APPROVER` in env exits 3 with a clear error; `--freeze-*` runs without an approver.
5. **Rollback mode requires a named target state before any step runs.** The runbook's rollback section opens with an explicit "name the target state" pre-flight check; the dry-run plan calls this out as a finding if the target is "unknown."
6. **No vendor API is called by the Enablement Lead's script.** Grep for vendor SDKs, vendor API hostnames, or vendor product names in the script; none are present.
7. **Audit log is append-only and incident-scoped.** Every script invocation writes a timestamp, incident ID, action, and (for reverts) approver.
8. **Champion-network action is manual, not scripted.** The runbook explicitly names K4 and R4 as manual steps with a checklist entry, not a script invocation.
9. **Dry-run cadence is named** (monthly for new tools, quarterly for mature tools, out-of-band triggers listed).
10. **The runbook references the Exercise 01 triage artifact and the Exercise 03 handoff contract by name.** These are the inputs and outputs of the runbook within the module.
11. **Threat framing points to OWASP ML Top 10 and MITRE ATLAS** at the trigger table and in the rationale section.
12. **The target completion times are named and tested.** The dry-run plan records elapsed time per step and compares to the target.

## 4. Rubric / review checklist

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | Two modes (kill-switch, rollback) with explicit trigger criteria and reversibility profile | 10 | One mode only, or modes without triggers. |
| R2 | Kill-switch runbook has K1–K6 with target time per step and a validation point per step | 10 | Steps missing times or validation points. |
| R3 | Rollback runbook has R1–R5 with target time per step and a validation point per step | 10 | Steps missing times or validation points. |
| R4 | Rollback mode requires a named target state before any step runs; the four dimensions (stage, training, AUP, champion) are each named | 10 | Target state unnamed, or only one dimension named. |
| R5 | Enablement Lead does not operate the technical kill-switch; the runbook explicitly delimits scope and references Exercise 03 handoff contract | 10 | Script calls a vendor API; runbook describes technical kill-switch steps. |
| R6 | Companion script is idempotent, incident-scoped, dry-run-capable, audit-logged, and approver-gated on reverts | 10 | Missing dry-run; missing approver gate; not idempotent. |
| R7 | Dry-run plan with named cadence (monthly / quarterly / out-of-band triggers) and success criteria (both time and validation reached) | 10 | No cadence or weak success criteria. |
| R8 | Champion-network action remains manual; runbook does not automate a field-facing Slack message | 5 | Champion message automated. |
| R9 | Threat framing cites OWASP ML Top 10 and MITRE ATLAS where relevant | 5 | No framework reference. |
| R10 | Runbook names the Exercise 01 triage artifact and Exercise 03 handoff contract as inputs/outputs | 5 | No cross-references. |
| R11 | Audit log is append-only and incident-scoped; dry-run entries tagged `drill=true` | 5 | Audit discipline absent; drill traffic contaminates real-incident log. |
| R12 | No vendor product names or vendor-specific API calls in the runbook or script | 5 | Named vendor products or SDKs. |
| R13 | Target completion times (≤ 30 min kill-switch, ≤ 2 hr rollback) are stated and reconciled against the dry-run elapsed times | 5 | Times absent, or dry-run exceeds targets without a finding. |

**Pass threshold:** ≥ 85/100 and no R4 / R5 / R6 fail. R5 (scope discipline: the Enablement Lead does not operate the technical kill-switch) and R4 (rollback target state named) are the two failures that most often appear together and together they neuter the runbook.

## 5. Common mistakes

- **Running the enablement-side kill-switch without the technical one.** This creates a half-off state where the tool still works but the help-desk says it doesn't; the field distrusts the Enablement function and the next incident is harder to coordinate.
- **Rolling back without a named target state.** "Revert to how it was" is not a target; "revert IdP group to the mod-102 pilot cohort file; revert LMS course to version `v1.4`; revert AUP section 4.2 to the `2026-09-15` version" is a target. Without one, the rollback is a fresh change wearing a rollback badge.
- **Automating the champion-network message.** A machine-authored field message during an incident reads exactly like a machine-authored field message during an incident. The 45 seconds the Enablement Lead takes to write it in human voice is the credibility.
- **Skipping dry-runs because "nothing has changed."** The runbook may not change for a quarter, but the IdP, help-desk, LMS, and governance surfaces around it do. A quarterly dry-run catches the silent drift of those surfaces before an incident does.
- **Letting dry-run traffic contaminate production incident channels or audit logs.** A dry-run that posts to `#incidents` or writes to the real incident audit log creates alarm and, worse, contaminates the data the quarterly review depends on.
- **Running the script without `--incident <id>`.** Every invocation is incident-scoped. A script invocation without an incident ID is a nameless write to the enablement surface; it is also a nameless write to the audit log, which is a review finding on its own.
- **Treating `require_approver` as a nuisance.** The approver gate exists because reverts are harder to undo than freezes. The temptation to script-around it ("I'll just set `APPROVER=self` in my shell") breaks the two-person rule the governance posture rests on.
- **Not naming the Procurement commit freeze (K5).** Commits that happen during an incident ("let me just sign this expansion so the paperwork doesn't slip") are the single largest source of post-incident finger-pointing over "why did we sign this when the tool was in triage."
- **Scripting vendor-side disables.** Any step that reaches into the vendor API is the AI Risk Engineer's lane. Leaving it in the Enablement Lead's script creates an authority confusion that resolves badly when the vendor's rate-limit or access-control pushes back.
- **Treating the runbook as read-only.** Each dry run should produce at least one finding — ambiguity, drift, a step too long — and the finding should be addressed in the runbook within a sprint. A runbook that never changes is a runbook that is no longer accurate.

### 5.1 Stretch — two refinements the mature runbook adds

Once the runbook has been dry-run four or five times, two refinements earn their place:

- **Pre-run state snapshot.** Before K1 runs, the script captures a snapshot of the current IdP group membership, help-desk macro state, and LMS course state. The snapshot is attached to the incident record. Rollback-mode uses the snapshot to build the target-state description more easily; post-incident review uses it to answer "what did we actually freeze?"
- **Multi-tool kill-switch.** For an org running more than one tool in the enablement cost center, K1–K3 accept a `--tool-set <set-id>` flag that batch-applies the freeze to every tool in a named set (e.g., "all tools in the Health BU"). This matters for cases where the trigger is a shared-dependency issue (a vendor's shared embeddings service, for example) rather than a single-tool issue. The script continues to be idempotent and dry-runnable with the set flag.

## 6. References

- **Learning material (local):**
  - [mod-102 — Selecting and Rolling Out AI Tools](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-102-selecting-and-rolling-out-ai-tools) — the rollout charter that defines pilot-population cohorts and alternate-workflow help-desk macros.
  - [mod-103 — Policy Co-authoring with Governance](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-103-policy-co-authoring-with-governance) — the AUP versions that rollback mode reverts against.
  - [mod-104 — Training Programs and AI Literacy Curriculum](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-104-training-programs-and-ai-literacy-curriculum) — the LMS course versions that rollback mode reverts against.
  - [mod-105 — Champion Networks and Change Management](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-105-champion-networks-and-change-management) — the champion-network charter that governs K4 and R4.
  - [mod-106 — Outcome Measurement and Executive Reporting](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-106-outcome-measurement-and-executive-reporting) — the executive scorecard whose event-marker row R5 annotates.
  - [mod-107 — Budget, ROI, and Build vs. Buy at Org Scope](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-107-budget-roi-and-build-vs-buy-at-org-scope) — the Procurement-Finance partnership contract that governs K5.
  - [mod-109 Exercise 01 — Enablement-Side Incident Triage Drill](../exercise-01-enablement-side-incident-triage-drill/SOLUTION.md) — the trigger upstream of this runbook.
  - [mod-109 Exercise 03 — Handoff Contract with AI Risk Engineer and SecOps](../exercise-03-handoff-contract-with-ai-risk-engineer-and-secops/SOLUTION.md) — the contract that governs scope between the Enablement Lead's runbook and the AI Risk Engineer's.
- **Official standards and frameworks:**
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — the `MANAGE` function (and `MANAGE-4` specifically on regular review of incident-response capability) is the frame for cadence and dry-run discipline.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — the threat vocabulary that seeds the trigger table (output-integrity, data-leakage, supply-chain classes).
  - [MITRE ATLAS](https://atlas.mitre.org/) — the adversarial-tactic vocabulary used alongside OWASP where the trigger involves a tactic rather than a vulnerability class.
