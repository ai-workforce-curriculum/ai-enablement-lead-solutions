# Exercise 03 — Handoff Contract with AI Risk Engineer and SecOps — Reference Solution

> Module: `mod-109-ai-incident-response-and-enablement-side-rollback`
> Exercise type: design / worked example (written contract between roles)
> Exercise brief: [`lessons/mod-109-ai-incident-response-and-enablement-side-rollback/exercises/exercise-03-handoff-contract-with-ai-risk-engineer-and-secops.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-109-ai-incident-response-and-enablement-side-rollback/exercises/exercise-03-handoff-contract-with-ai-risk-engineer-and-secops.md) (in the learning repo)

## 1. Solution overview

The deliverable is a **written handoff contract** between three roles: the **AI Enablement Lead** (this role), the **AI Risk Engineer** on-call, and **SecOps** on-call. The contract names decision rights, information flows, SLAs, and escalation paths for AI-tool incidents, so that each role knows what it owns, what it hands off, and what it receives. It is a one-page agreement, signed by the three function leads, published in the governance repo, and republished whenever any of the three functions re-orgs.

Posture checks this solution encodes:

- **Three asymmetric lanes.** The Enablement Lead owns the user-population dimension (training, AUP, comms, rollout stage). The AI Risk Engineer owns the technical dimension (kill-switch, model behavior investigation, retrieval-config review, vendor technical contact). SecOps owns the security dimension (containment, chain-of-custody, evidence preservation, external contact including regulator and law-enforcement notice). Each lane has specific decisions that are *only* theirs to make; the contract names them.
- **Handoffs are written, not Slack-threaded.** The contract names the artifacts that cross boundaries (triage record, handoff memo, technical findings note, security brief) and names an SLA per artifact.
- **The contract is role-name-addressed, not person-name-addressed.** "AI Enablement Lead" and "AI Risk Engineer on-call" survive org changes; named individuals do not.
- **The contract names the incident taxonomy** so that routing decisions between the three lanes do not re-litigate per incident. The taxonomy maps to OWASP ML Top 10 and MITRE ATLAS where it crosses a technical boundary.
- **Vendor contact is scoped carefully.** The Enablement Lead does not contact the vendor; the AI Risk Engineer makes technical contact (bug reports, telemetry questions); SecOps and Legal make commercial / regulatory contact (customer notice, data-processing agreement invocation).
- **Escalation is bidirectional.** Any one role can escalate to the other two; the contract names the escalation signals and the cadence at which escalations roll up to the AI governance council.
- **Reversibility is designed in.** The contract names an off-cycle revisit trigger and an annual review cadence.

## 2. Implementation — worked answer

The contract below is the full artifact. It is organized as a one-page living document in the governance repo as `contracts/enablement-risk-secops-handoff.md`.

### 2.1 The contract — `enablement-risk-secops-handoff.md`

```
AI Enablement ↔ AI Risk Engineering ↔ SecOps — Incident Handoff Contract
Effective:        <!-- org-specific: effective date -->
Signatories:      AI Enablement Lead (this role),
                  Head of AI Risk Engineering,
                  Head of Security Operations
Next review:      Annual (next revisit: <!-- org-specific: effective-date + 12 months -->)
Scope:            All AI-tool incidents in production or GA stage of rollout.
                  Pilot-stage incidents follow the pilot-charter escalation path
                  from mod-102 and this contract applies on a best-effort basis.
```

---

#### Section 1 — Purpose

This contract names how the three on-call functions work together during an AI-tool incident so that each function moves within its own lane at the speed its lane requires, and so that the information each function needs reaches it within a predictable window. It is a working-arrangement artifact; it does not supersede the organization's corporate security-incident policy, AI governance council charter, or regulatory notice obligations. Where this contract and a corporate policy differ, the corporate policy wins and this contract is amended within 30 days.

#### Section 2 — The three lanes

Each lane owns a distinct set of decisions that are **its alone to make**. The lane owner is the single accountable party for those decisions during an incident.

| Lane | Owner (role) | Decisions it owns |
|---|---|---|
| **Enablement** | AI Enablement Lead | Rollout pause (soft / hard, in concert with AI Risk Engineer for hard); user-population communication (champion vs. general vs. external); training enrollment freeze and AUP annotation; procurement commit freeze; help-desk macro posture; champion-network messaging; LMS course version |
| **AI Risk Engineering** | AI Risk Engineer on-call | Technical kill-switch flip (API key revoke / vendor-side disable); model-behavior reproduction and investigation; retrieval-config review; prompt-and-response forensics; technical vendor contact (bug reports, telemetry questions); classification of incident against OWASP ML Top 10 and MITRE ATLAS; declaration of symptom-reproduction status |
| **SecOps** | SecOps on-call | Containment posture; chain-of-custody and evidence preservation; external contact — regulator, law-enforcement, customer notice (in concert with Legal); commercial vendor contact — DPA invocation, customer-notification request (in concert with Legal); declaration of security-incident severity and the decision to invoke the corporate security-incident policy |

Decisions that cross lanes require **concurrence**, not permission:

| Decision | Primary | Concur |
|---|---|---|
| Hard pause (kill-switch flip) | AI Risk Engineer | AI Enablement Lead |
| General-population user communication | AI Enablement Lead | SecOps (when incident has a security dimension) |
| External / regulator / customer notice | SecOps + Legal | AI Enablement Lead (for the message content) |
| Downgrade or close the incident | SecOps when security-dimension; otherwise AI Risk Engineer | AI Enablement Lead |
| Invocation of the corporate security-incident policy | SecOps | AI Enablement Lead and AI Risk Engineer are informed |

"Concurrence" means the primary names the decision in-channel; the concur role has 15 minutes to object; silence after 15 minutes is agreement. "Permission" would require an active yes; that is not the posture of this contract because 15-minute asynchronous objection is the right default for fast-moving incidents.

#### Section 3 — Incident taxonomy and routing

Incidents are classified into one of five classes at triage. Classification is a **preliminary** step by the first-responder role (usually the Enablement Lead), to be confirmed by the AI Risk Engineer within 60 minutes. The class determines the lane split.

| Class | Signal | Primary lane | Secondary lane | Taxonomy hooks |
|---|---|---|---|---|
| **A — Output-integrity violation** | Tool returns content that should not have been producible (e.g., cross-tenant data, verbatim training data, sensitive PII the tool was not configured to see) | AI Risk Engineering | SecOps (if data-exfiltration), Enablement | OWASP ML09 (Output Integrity Attack), ML06 (Supply Chain), MITRE ATLAS `Exfiltration`, `Impact` |
| **B — Behavior regression** | Tool returns substantially worse output than its baseline for an identifiable prompt class, with no security dimension | AI Risk Engineering | Enablement | OWASP ML04 (Membership Inference) is *not* this; this is quality drift, not an adversarial class |
| **C — Adversarial attack signal** | Prompt-injection, data-poisoning, model-evasion, or other adversarial technique is observed | AI Risk Engineering + SecOps | Enablement | OWASP ML01 (Input Manipulation), ML02 (Data Poisoning); MITRE ATLAS `Initial Access`, `ML Attack Staging` |
| **D — Policy or AUP violation by user** | A user has used the tool in a way the AUP prohibits (e.g., uploaded regulated data to a non-cleared tool) | SecOps + Enablement | AI Risk Engineering (if the tool's config contributed) | Not primarily an OWASP ML class; HR and legal escalation paths may apply |
| **E — Vendor-origin incident** | Vendor publishes a status-page incident or notifies the org of an issue on their side | SecOps + Enablement | AI Risk Engineering | May map to OWASP ML06 (Supply Chain) depending on the vendor's description |

Classification is written into the triage record (Exercise 01) within 30 minutes of first signal. Re-classification is logged as a new decision-log entry with the reasoning for the re-class.

#### Section 4 — Artifacts and SLAs

The following artifacts cross lane boundaries during an incident. Each artifact has an owner, an SLA from the triggering event to artifact availability, and a receiving role.

| Artifact | Owner | SLA | Receivers |
|---|---|---|---|
| **Triage record and handoff memo** (Exercise 01 artifacts) | AI Enablement Lead | Within 90 minutes of first signal | AI Risk Engineer, SecOps |
| **Technical findings note** — "did it reproduce; what is the mechanism; what is the OWASP / ATLAS class" | AI Risk Engineer | Within 2 hours of handoff memo receipt (for Class A/B/C); within 4 hours for Class D/E | AI Enablement Lead, SecOps |
| **Security brief** — "what evidence is preserved; is the corporate security-incident policy invoked; is regulator / customer notice in motion" | SecOps on-call | Within 2 hours of handoff memo receipt (if a security dimension); otherwise explicit statement that none is open | AI Enablement Lead, AI Risk Engineer |
| **Status consolidated note** (every check-in) | Rotates: whoever is lane-primary for the incident | Every 4 hours while the incident is open | All three roles; champion-network leads |
| **Post-incident review note** | AI Enablement Lead convenes; all three roles own content | Scheduled within 24 hours of first signal; held within 5 business days of incident close | All three roles; the AI governance council in an abridged form |

"Handoff memo receipt" means the memo is both written and acknowledged in the incident channel, not merely posted. Acknowledgement is a reaction emoji or a one-line "received" reply; the SLA clock starts when acknowledged, not when posted.

#### Section 5 — Communication channels and the Slack convention

A single incident channel is opened per incident, named `#inc-<id>-<class>-<short-tag>` (e.g., `#inc-2026-11-17-001-A-output-integrity`). The channel is where all three lanes work; Slack DMs are not acceptable incident-coordination surfaces because they do not preserve chain-of-custody.

| Channel | Purpose | Participants |
|---|---|---|
| `#inc-<id>-...` | Live incident coordination | All three on-calls + their backups + Legal observer + Comms observer |
| `#enablement-oncall` | Enablement-side rolling log; dry-run surface | Enablement team only |
| `#ai-risk-oncall` | AI Risk Engineering rolling log | AI Risk team only |
| `#secops-oncall` | SecOps rolling log | SecOps team only |
| `#ai-governance-council` | Governance-council visibility; incident-abridged status (not raw content) | Council members and Heads of the three functions |

Decisions, artifacts, and status consolidated notes are posted to `#inc-<id>-...`. Lane-internal discussion stays in the lane-specific channel until it produces a decision or an artifact.

#### Section 6 — Escalation

Escalation is bidirectional and asynchronous. Any one lane can escalate to the other two; the signals that trigger escalation are:

- **Lane-level escalation** (within the three lanes): "I believe this incident requires a decision outside my lane that my counterpart has not yet addressed." Expressed as a tagged request in `#inc-<id>-...`.
- **Function-head escalation**: any lane's on-call can escalate to the lane's function head (Head of AI Enablement, Head of AI Risk Engineering, Head of Security Operations) at any time, for any reason. No permission is required; the function head may redirect back.
- **Council escalation**: any function head can escalate to the AI governance council (`head-of-ai-governance`, L60 in the mod-101 operating-model vocabulary). The signals that warrant council escalation are listed below; the function head's judgment is the final test.

Signals that warrant council escalation:

- Regulator notice is in motion.
- Customer notice is in motion (external, cross-org).
- The incident involves a regulated workload (clinical, financial, legal).
- The incident has a probable public disclosure path (media, support-forum post, social media screenshot).
- The three lanes disagree on the right posture and the disagreement has not resolved in 2 hours.
- The incident requires a decision at a budget scale above the mod-107 partnership-contract threshold (`<!-- org-specific: confirm threshold -->`).

Council escalation does not pause lane work; the council convenes within 24 hours and the lanes continue to operate.

#### Section 7 — Vendor contact

Vendor contact is the single most load-bearing scoping decision in this contract, because a vendor interaction during an incident can create a customer-notice or contract-invocation surface that is hard to unwind.

| Who can contact the vendor | For what purpose |
|---|---|
| AI Enablement Lead | **Nothing** during an active incident. Vendor relationship-management continues through the normal Procurement / Enablement cadence (mod-107) outside the incident. |
| AI Risk Engineer | Technical bug report; telemetry request; configuration question; vendor status-page verification. Does not sign anything; does not request customer notice. |
| SecOps + Legal | Commercial contract invocations (DPA, SLA, customer-notification clauses); regulator-coordinated contacts; request for a vendor-side investigation. Signs vendor communications. |

No lane contacts the vendor without logging the contact in `#inc-<id>-...` with the exact words used (or a redacted summary if Legal asks). The chain-of-custody discipline from the triage record extends to vendor contact.

#### Section 8 — Service-level commitments (two-way across lanes)

Each lane commits to the following to the other two:

**Enablement commits to Risk Engineering and SecOps:**

- Triage record and handoff memo within 90 minutes of first signal.
- Preliminary incident class within 30 minutes.
- No vendor contact initiated; no AUP amendments made without Legal concurrence.
- Champion-network and user-population comms are paused or messaged within the Enablement SLAs (per Exercise 01).
- The Enablement Lead is reachable on the incident channel at all times during the incident; if unreachable, the backup is paged and the handoff is written within 30 minutes.

**AI Risk Engineering commits to Enablement and SecOps:**

- Technical findings note within 2 hours (Class A/B/C) or 4 hours (Class D/E) of handoff memo receipt.
- Reproduction status (reproduced / not reproduced / inconclusive) called out explicitly in the technical findings note.
- OWASP ML Top 10 and MITRE ATLAS classification stated explicitly; "unknown" is a valid classification but is tracked as a pending item.
- Technical kill-switch flipped within 15 minutes of a Hard pause concurrence.

**SecOps commits to Enablement and AI Risk Engineering:**

- Security brief within 2 hours of handoff memo receipt (if there is a security dimension) or explicit "no security dimension open" statement.
- Decision on whether to invoke the corporate security-incident policy within 2 hours.
- Advance notice (not permission; notice) of any external contact that would make the incident publicly discoverable.
- Chain-of-custody and evidence preservation on the incident; the triage record and handoff memo are included in the preserved set.

#### Section 9 — Off-cycle revisit triggers

This contract is revisited off-cycle if any of the following occur:

- A real incident where the lanes crossed wires (a decision that two lanes thought was theirs, or a decision that fell between lanes).
- A re-org on any of the three functions.
- A new regulatory regime (EU AI Act, state-level AI laws, sector-specific incident reporting rules) that changes the external-notice surface.
- A new tool class in GA that the current taxonomy does not cover cleanly (for example, autonomous agents with action authority — Class F candidate).
- A failed dry run of either the Exercise 02 runbook or this contract.

The off-cycle revisit produces either a contract amendment (signed by the three function heads) or a written finding that no amendment is needed; both outcomes are recorded.

### 2.2 Decision rationale — why this shape, not another

- **Why three lanes, not two.** Collapsing AI Risk Engineering and SecOps into "the technical lane" is tempting but wrong: the Risk Engineer owns *model and tool* investigation; SecOps owns *security and external* containment. Those are different muscles, different tools, and often different people. The contract makes the lane split explicit so that an incident with both a model-behavior dimension and a data-exfiltration dimension does not produce a single overloaded responder.
- **Why "concurrence" with a 15-minute asynchronous objection, not "permission".** Incident tempo rules out synchronous permission; waiting for a yes is the common failure mode that stalls a kill-switch flip for an hour. Concurrence is the lightweight pattern — the primary names the decision, the concur role has a bounded window to object. If they object, the decision is paused; if they are silent, the decision proceeds.
- **Why the Enablement Lead makes no vendor contact during an incident.** Three reasons. (1) Vendor contact during an incident is a customer-notice surface; parallel narratives (Enablement saying one thing, SecOps saying another) are hard to unwind. (2) Vendor bug reports are technical; the AI Risk Engineer has the vocabulary. (3) The vendor relationship outside the incident continues through the mod-107 partnership-contract cadence; the Enablement Lead is not shut out of the vendor relationship, just not during an incident.
- **Why five incident classes, not three.** Three (output-integrity, behavior regression, security) is a common first draft; it misses Class D (policy violation by the user, which routes through SecOps and HR, not Risk Engineering) and Class E (vendor-origin incident, which has a different information-flow shape). Both are common enough that collapsing them into one of the other three leads to routing errors.
- **Why the incident channel is named `#inc-<id>-<class>-<tag>`.** The channel name encodes the class so that anyone scrolling their Slack sidebar can distinguish a Class A from a Class D at a glance. This is a small ergonomic choice that pays back in large orgs with multiple concurrent incident channels.
- **Why the post-incident review involves all three roles but is convened by Enablement.** The review is where the lanes' interaction is examined; convening by one lane biases the agenda toward that lane's concerns. Enablement convenes because the Enablement surface is where the field's experience lands; the content is owned by all three lanes. This matches NIST AI RMF `MANAGE-4`.
- **Why vendor contact is routed through SecOps + Legal for commercial, AI Risk for technical.** This is the standard separation in a mature security program — technical bug reports do not require a Legal signoff; customer-notice and DPA invocations do. Collapsing them is the single most common commercial error during an incident.
- **Why the council escalation signals are listed explicitly.** Judgment calls on "is this council-worthy?" during an incident are hard; pre-naming the signals (regulator motion, customer motion, regulated workload, public disclosure path, three-way disagreement, budget threshold) removes the judgment call without removing the function head's final say.

## 3. Validation steps

1. **Three lanes with disjoint owned-decision sets.** The decision rights table lists each decision under exactly one owner; cross-lane decisions are in the concurrence table, not duplicated in the per-lane rows.
2. **Five incident classes with explicit taxonomy hooks.** Classes A–E are named; each maps to OWASP ML Top 10 and MITRE ATLAS where relevant; Class D's non-ML routing (HR, Legal) is explicit.
3. **Artifacts have owner, SLA, and receiver.** Every row in the artifact table has all three columns populated. SLAs are in time units (minutes or hours), not qualitative words.
4. **Vendor contact scope is clear.** The vendor-contact section names who can contact the vendor for what purpose; the Enablement Lead's "nothing during an active incident" is explicit.
5. **Role-name-addressed, not person-name-addressed.** Grep the contract for personal pronouns or named individuals; none are present.
6. **Escalation is bidirectional.** Each of the three lanes can escalate to the other two and to the council; the signals for council escalation are listed.
7. **Off-cycle revisit triggers are listed.** The revisit section names at least the five triggers (incident where lanes crossed wires; re-org; new regulatory regime; new tool class; failed dry run).
8. **Annual review cadence is named.** The contract names the annual review slot and the signatory roles.
9. **The contract references upstream and downstream artifacts.** It names the Exercise 01 triage record and handoff memo as inputs; it names the Exercise 02 runbook as a dependency; it names the Exercise 04 feedback loop as the downstream recipient of post-incident findings.
10. **No vendor product names.** Grep for vendor names, SDK names, or `.com` strings; none present.
11. **No invented regulator names or statutory references without verification.** The contract names EU AI Act, "state-level AI laws", and "sector-specific incident reporting rules" as categories; any specific statute cited would need an `org-specific` tag or a verifiable source.
12. **Signatory roles are named (AI Enablement Lead, Head of AI Risk Engineering, Head of Security Operations).** The contract is not signable without all three roles named.
13. **Three-channel Slack convention is specified.** The incident channel naming pattern, the three lane-specific channels, and the governance channel are named.

## 4. Rubric / review checklist

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | Three lanes named (Enablement, AI Risk Engineering, SecOps), each with a disjoint set of owned decisions | 10 | Lanes collapsed; cross-lane decisions appear in a lane's owned set. |
| R2 | Concurrence pattern specified with a 15-minute asynchronous objection window | 10 | Concurrence collapsed into permission (synchronous yes required). |
| R3 | Five-class incident taxonomy (A — output integrity, B — behavior regression, C — adversarial attack, D — AUP violation by user, E — vendor-origin) with OWASP ML Top 10 and MITRE ATLAS hooks | 10 | Fewer than five classes; or classes missing taxonomy hooks. |
| R4 | Artifact table with owner, SLA, and receiver per artifact (triage record, handoff memo, technical findings, security brief, status note, post-incident review) | 10 | Any artifact missing one of the columns, or SLAs qualitative. |
| R5 | Vendor contact scoped by role and purpose; Enablement Lead's "no vendor contact during active incident" is explicit | 10 | Enablement Lead empowered to contact the vendor during incidents; or the scope boundary is ambiguous. |
| R6 | Two-way SLA commitments stated per lane, including the 15-minute kill-switch flip from Hard pause concurrence | 10 | One-way SLAs (only Enablement commits; the other lanes do not); or no technical kill-switch SLA. |
| R7 | Escalation bidirectional; council escalation signals listed explicitly | 10 | Escalation only upward from Enablement; or no explicit council signals. |
| R8 | Role-name-addressed throughout; no named individuals; signatories listed as roles | 5 | Named people; no explicit signatory roles. |
| R9 | Slack channel convention specified (incident channel naming, lane-specific channels, governance channel) | 5 | No channel discipline; or incident coordination via DM accepted. |
| R10 | Off-cycle revisit triggers listed (at least five, including failed dry run of Exercise 02 runbook) | 5 | Fewer than three triggers. |
| R11 | Annual review cadence named | 5 | No cadence; or cadence defined as "ad hoc". |
| R12 | Cross-references to Exercise 01, Exercise 02, Exercise 04, and dependent modules (101 operating model, 103 AUP, 107 partnership contract) | 5 | No upstream/downstream references. |
| R13 | No vendor product names, SDK names, or `.com` strings | 5 | Any specific vendor identified. |

**Pass threshold:** ≥ 85/100 and no R1 / R5 / R6 fail. R5 (vendor contact scope) is the single most costly failure — a mis-scoped vendor contact during an incident can produce a customer-notice surface that lasts months and resists cleanup.

## 5. Common mistakes

- **Collapsing AI Risk Engineering and SecOps into one lane.** The Risk Engineer investigates the model and tool; SecOps contains the incident and handles external surfaces. Collapsing them produces an overloaded responder who does neither well.
- **Letting the Enablement Lead contact the vendor.** The temptation is real — the vendor's support rep is friendly, the Enablement Lead already has the rapport. Doing it creates a parallel narrative that complicates customer-notice and contract-invocation surfaces for the rest of the incident.
- **Making the concurrence pattern synchronous.** Requiring an active yes stalls hard-pause flips and general-population comms. 15-minute asynchronous objection is the right default.
- **Writing the contract with named individuals.** Org charts change; the contract should survive them. Role names only.
- **Routing a Class D (user AUP violation) incident through AI Risk Engineering.** Risk Engineering investigates tool behavior; a user who uploaded regulated data to a non-cleared tool is a Compliance + HR + SecOps matter. Mis-routing creates a Risk Engineer backlog and misses the Compliance notice.
- **Failing to name Class E (vendor-origin incident) as its own class.** When the vendor publishes a status-page incident, the in-house response is almost entirely coordination (SecOps + Legal + Comms); routing it through the Enablement or Risk Engineering lane as a technical investigation wastes time on investigation of something the vendor is already investigating.
- **No SLA on the technical kill-switch.** The point of the kill-switch is its speed. 15 minutes from Hard pause concurrence to flip is the defensible SLA; longer than that erodes the Enablement Lead's trust in the lever.
- **Omitting the annual review and off-cycle revisit triggers.** A contract that is never reviewed drifts out of alignment with the orgs it governs within a year.
- **Using DMs for incident coordination.** DMs do not preserve chain-of-custody and cannot be reviewed in the post-incident. The contract insists on the incident channel for all decisions.
- **Treating the Slack channel naming as cosmetic.** The channel name is the first thing a council member sees in the sidebar when an incident is live. Encoding the class into the name is a 10-second investment at channel-open and a load-bearing ergonomic later.

### 5.1 Stretch — autonomous-agent incidents (Class F candidate)

As the org's tool portfolio expands to autonomous agents with action authority (per mod-110), a sixth class is a candidate — **Class F: Autonomous-agent action incident**. The signal is that an agent took an action in the world (sent an email, closed a ticket, moved money) that the AUP did not authorize or that produced an unintended downstream effect. Routing is **SecOps + AI Risk Engineering + Enablement** co-primary, because the agent is simultaneously (a) a security-incident surface, (b) a technical-behavior surface, and (c) an AUP / policy surface.

The Class F candidate is held out of this version of the contract pending (a) sufficient autonomous-agent production footprint to calibrate the class and (b) the mod-110 commissioning charter to converge on the action-authority vocabulary. When those two preconditions are met, the off-cycle revisit trigger "a new tool class in GA that the current taxonomy does not cover cleanly" fires and the contract is amended.

## 6. References

- **Learning material (local):**
  - [mod-101 — Role and Org-wide Enablement Operating Model](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-101-role-and-the-org-wide-enablement-operating-model) — the operating-model vocabulary (L50, L60, head-of-ai-governance) used in the escalation section.
  - [mod-102 — Selecting and Rolling Out AI Tools](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-102-selecting-and-rolling-out-ai-tools) — the pilot-stage escalation path referenced in the scope note.
  - [mod-103 — Policy Co-authoring with Governance](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-103-policy-co-authoring-with-governance) — the AUP amendment path that Enablement does not travel alone.
  - [mod-107 — Budget, ROI, and Build vs. Buy at Org Scope](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-107-budget-roi-and-build-vs-buy-at-org-scope) — the Procurement-Finance partnership contract that governs vendor relationship-management outside of incidents.
  - [mod-110 — Commissioning Internal AI Tools and Custom Agents](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-110-commissioning-internal-ai-tools-and-custom-agents) — the source of the Class F candidate.
  - [mod-109 Exercise 01 — Enablement-Side Incident Triage Drill](../exercise-01-enablement-side-incident-triage-drill/SOLUTION.md) — upstream of this contract.
  - [mod-109 Exercise 02 — Kill-Switch and Rollback Dry Run](../exercise-02-kill-switch-and-rollback-dry-run/SOLUTION.md) — the runbook whose Hard-pause step triggers the technical kill-switch SLA in this contract.
  - [mod-109 Exercise 04 — Incident-to-Policy-and-Training Feedback Loop](../exercise-04-incident-to-policy-training-feedback-loop/SOLUTION.md) — downstream of this contract; it consumes the post-incident review output.
- **Official standards and frameworks:**
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — the `GOVERN` and `MANAGE` functions frame the decision-rights structure and the post-incident review discipline.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — the taxonomy hooks for Classes A, B, and C.
  - [MITRE ATLAS](https://atlas.mitre.org/) — the adversarial-tactic vocabulary used alongside OWASP where the class is adversarial-technique-shaped.
