# Exercise 02 — Data-Handling SOP for an AI Tool — Reference Solution

> Learning file: [`exercise-02-data-handling-sop-for-an-ai-tool.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-103-policy-co-authoring-with-governance/exercises/exercise-02-data-handling-sop-for-an-ai-tool.md)

## 1. Solution overview

This SOP is artifact 2 of the rollout artifact set and is a **launch gate** — security and privacy must sign, or the tool does not go GA. The exercise is a design artifact; the worked SOP below carries the "coding assistant at a 3,000-person US bank" archetype from [Exercise 01](../exercise-01-one-page-acceptable-use-policy-drill/SOLUTION.md) forward, including the information-classification tiers (Public / Internal / Confidential / Restricted / Regulated) and the `ai-governance-analyst` escalation path.

Posture checks the solution encodes:

- **Operator voice.** The person at the keyboard whose stomach just dropped must know the next three clicks in seconds. Abstract procedural language fails here.
- **Accident-path section carries the weight.** It is the make-or-break section; it is where security and privacy will spend the most redline minutes. Five numbered steps minimum, named roles, named channels, named preservation list, and a named handoff to the SOC.
- **No SOC-side forensic language.** Chapter 07 is explicit: no log analysis, no notification-clock management, no vendor forensics in the enablement-side SOP. Those route out.
- **Reference the DPA — do not restate it.** Two sources of truth drift apart within a quarter.
- **Model-training egress vs. abuse-monitoring egress are separate sentences.** Separating them lets privacy and security redline each independently.
- **Three accident shapes named by shape.** Paste-mistake, subtly-wrong-output, tool-malfunction. Each has a different first-line response.

## 2. Implementation — worked answer (`data-handling-sop.md`)

---

### Data-Handling SOP — Coding Assistant (v0.1-draft)

**Tool:** Copilot-class coding assistant, Enterprise tenant.
**Classification scheme referenced:** `<!-- org-specific: confirm official scheme name — assumed "Information Classification Standard" with tiers Public / Internal / Confidential / Restricted / Regulated -->` (same scheme as AUP v0.1).
**Draft version:** 0.1 (enablement-side first draft).
**Status:** Pre-redline. For security and privacy walking-redline (Thursday).

---

#### 1. In-scope data classes with examples

Mapped to the bank's classification scheme (same as AUP Section 4).

| Class | Example (is in class) | Example (is not in class) | Notes |
|---|---|---|---|
| Public | README from a public open-source repo the bank mirrors. | A private fork of the same repo with internal CI config. | Fine to paste; still log at tenant level. |
| Internal | A snippet from an internal library the bank wrote for request routing. | A payment-processing adapter wired against production credential refs. | Fine to paste; review before external publication. |
| Confidential | A draft architecture diagram for next quarter's platform migration. | A finalized diagram already filed with `<!-- org-specific: confirm internal architecture review board name -->`. | Confirm with a champion before pasting; prefer summarizing in your own words. |
| Restricted | A support-case transcript with a customer name, a stack trace with a customer account ID, employment-separation memo text, draft compensation letters. | A bug report that has been scrubbed of customer identifiers and reproduces with synthetic data. | **Forbidden** as prompt input and as generated output. |
| Regulated | Any field from the bank's regulated-data inventory: SSN, DOB, account number, PAN, AML case metadata, OFAC match data. | Published regulator guidance URLs, aggregate statistics already in filings. | **Forbidden** as prompt input and as generated output. |

> **Co-author tag — Section 1**
> Drafter: AI Enablement Lead (this role).
> Redliner: `head-of-ai-governance` (L60).
> Privacy signer: Data Protection Officer — **primary**.
> Security signer: not required at class-definition level.
> IT identity: not referenced.

---

#### 2. Retention

Vendor and internal retention live on different clocks. The SOP surfaces the facts operators need; the authoritative source is the vendor DPA.

- **Vendor retention (prompts and outputs):** Per the vendor DPA for the Enterprise tenant, the vendor does not retain prompts or outputs for model training; the tenant is on the no-training path. `<!-- org-specific: confirm exact DPA clause reference, e.g., DPA §4.2 / "Customer Content Processing" -->`.
- **Vendor abuse-monitoring retention:** The vendor retains a separate abuse-monitoring log for a vendor-defined window — distinct from product telemetry, used for the vendor's platform-security review. `<!-- org-specific: confirm abuse-monitoring retention window from the DPA, typically 30 days — populate here -->`. This path exists even when training retention is disabled; operators should know the two clocks are different.
- **Internal retention (bank-side logs):** The bank's tenant-level audit log (who prompted what, when, from which device) is retained per the bank's technology-records schedule `<!-- org-specific: confirm schedule reference — likely 7 years for regulated workloads -->`. Content (prompt text, response text) is **not** captured at the bank side under the current configuration; only metadata is. If content capture becomes required, that is a tenant-reconfiguration change request routed through the CISO delegate.
- **Deletion triggers:** Tenant-level log deletion follows the records schedule above; vendor-side deletion is governed by the DPA and is not operator-initiated. User-initiated "clear chat history" removes only the client-side view; it does not delete vendor-side retention (see Section 4, step 1).

> **Co-author tag — Section 2**
> Drafter: AI Enablement Lead (this role).
> Redliner: `head-of-ai-governance` (L60).
> Privacy signer: Data Protection Officer — primary on vendor retention and DPA reference.
> Security signer: CISO delegate — primary on internal-log retention and tenant controls.
> IT identity: not referenced.

---

#### 3. Egress behavior

Each sentence below is written to be redlined independently.

- **Request routing (production path).** Prompt and completion traffic terminate at the vendor's `<!-- org-specific: confirm primary US-region endpoint and whether traffic traverses any region other than US during normal operation -->` endpoint. Traffic is TLS-encrypted on the wire; at rest at the vendor it is governed by the DPA.
- **Model-training egress.** On this tenant, prompts and completions are **not** used to train vendor models. This is distinct from abuse monitoring (next bullet).
- **Abuse-monitoring egress.** Prompts and completions are retained by the vendor for platform-security review (see Section 2). This is **not** training; it is a separate retention path with a separate access model on the vendor side.
- **Fallback-model behavior.** If the primary model is unavailable, the tool routes to `<!-- org-specific: confirm whether a fallback model is configured for this tenant and, if so, whether it traverses any additional jurisdiction or carries different retention -->`. If no fallback is configured, operators should expect request failure during primary-model outages rather than silent model substitution.
- **Cross-border crossing.** For US-origin users, request/response data remains in `<!-- org-specific: confirm US-region residency commitment in DPA -->`. Non-US users of this tenant (if any) should consult the DPO before use.

> **Co-author tag — Section 3**
> Drafter: AI Enablement Lead (this role).
> Redliner: `head-of-ai-governance` (L60).
> Security signer: CISO delegate — **primary**.
> Privacy signer: Data Protection Officer — primary on cross-border and training-vs-abuse distinction.
> IT identity: not referenced.

---

#### 4. The accident path

**Three accident shapes operators and triagers both need to pattern-match against:**

- **Paste-mistake** — a prompt contains data that is Restricted or Regulated.
- **Subtly-wrong-output** — the completion looks plausible but the engineer cannot tell whether it is correct (wrong SQL join semantics, wrong rounding, wrong regulator citation).
- **Tool-malfunction** — the tool itself returned something out-of-policy (hallucinated personal data, policy-violating code, a refused response that should have been answered).

The steps below apply to the **paste-mistake** shape primarily. Subtly-wrong-output and tool-malfunction routes are called out in the branch notes at the bottom of this section.

Operator-voice steps — read these in order, do not skip:

1. **Stop typing. Do not delete the prompt.** Clearing your chat window in the client does *not* delete what the vendor retained. Deletion destroys evidence the bank needs to measure what happened. Leave the window open exactly as it is.
2. **Capture the state in under 60 seconds.** Take a screenshot of the full prompt and output pane. Note (a) the exact timestamp; (b) the project or repo you were working in; (c) your laptop's identifier; (d) whether anything was already copied back out of the completion into another file. Paste all of this into the Slack message in step 3.
3. **Message `#ai-incident-first-line` immediately.** The first-line triager (on-call `ai-governance-analyst`) acknowledges within 15 minutes during business hours and within 60 minutes off-hours `<!-- org-specific: confirm on-call rotation hours and whether a pager is attached -->`. If you do not see an acknowledgement in that window, escalate by paging the SOC via `<!-- org-specific: confirm the bank's SOC on-call paging channel -->` and mentioning "AI data-handling accident."
4. **Preserve the evidence list.** On request from the triager, forward the screenshot and metadata from step 2, plus: the specific data class you believe you pasted (Restricted or Regulated, per Section 1), any downstream file or commit the completion touched, and any teammate who may have seen the output (channel, DM, pair-programming session). Do not post the Restricted/Regulated content itself back into Slack — describe its class, not its contents.
5. **Enablement-side next moves.** The first-line triager (a) opens a case in the `ai-governance-analyst` queue; (b) notifies `head-of-ai-governance` (L60) within one business hour if the content is Restricted or Regulated; (c) loops in the user's line manager if a training signal is indicated (not for discipline — for coaching); (d) sends the user an acknowledgement and an ETA for the next update (typical: initial read-out within 4 business hours).
6. **Handoff to security operations.** If the preserved evidence indicates the content was Restricted or Regulated, or if the completion was exfiltrated to another destination, the first-line triager formally hands the case to the SOC and to `ai-risk-engineer` (L25). From this point the forensic workstream is SOC-side (Chapter 07) — enablement convenes and transfers; it does not run forensics, does not run the regulator notification clock, does not speak with the vendor's trust team directly.

Branch notes — other accident shapes:

- **Subtly-wrong-output:** steps 1–3 still apply (do not delete, capture, message `#ai-enablement-help`). Route via the champion network (mod-105) for workflow-interview triage and feed the pattern into mod-104 prompt-coaching material. If the pattern recurs across engineers, escalate to `ai-risk-engineer` (L25).
- **Tool-malfunction:** steps 1–4 still apply. Escalate to mod-109 incident handling and to `ai-risk-engineer` (L25) for engineered-risk assessment. This is the only shape that may require a kill-switch decision; `head-of-ai-governance` owns that call.

> **Co-author tag — Section 4**
> Drafter: AI Enablement Lead (this role).
> Redliner: `head-of-ai-governance` (L60).
> Security signer: CISO delegate — **primary (co-sign)**.
> Privacy signer: Data Protection Officer — **primary (co-sign)**.
> IT identity: not referenced in this section.

---

#### 5. Access and revocation touchpoint

The bank's access and offboarding playbook is artifact 3 of the rollout artifact set and is operated by **IT identity**, not by this role. This SOP points at it; it does not re-author it.

Conditions under which SOP-side handling **requests** an access review from IT identity:

- The same user triggers the accident path twice within 90 days — training-gap signal; access-review request is consultative, not punitive.
- A single user cohort (team, function, geo) triggers the accident path three times within 90 days — cohort-level training gap, escalation to mod-105 champion coverage, and access-review request to confirm the cohort still has a documented need for the tool.
- A user tagged for offboarding by HR retains access to the tool after their end-of-employment date — standard offboarding failure; routed to IT identity for immediate revocation, with a case record opened via the first-line triager.

> **Co-author tag — Section 5**
> Drafter: AI Enablement Lead (this role).
> Redliner: `head-of-ai-governance` (L60).
> Security signer: not required (IT-identity-operated artifact).
> Privacy signer: not required (IT-identity-operated artifact).
> IT identity: **referenced** (not a signer).
> End-of-cycle ratifier: `head-of-ai-governance` (L60).

---

### End of worked SOP draft

## 3. Validation steps

1. **Page count.** Render Markdown; confirm 2–3 pages at normal body-text size. Over 3 pages typically means Section 4 was turned into a procedure manual — cut back to the five named steps plus the branch notes.
2. **Five-section order.** Data classes → retention → egress → accident path → access/revocation touchpoint.
3. **Class scheme matches Exercise 01's AUP.** Grep both files for the scheme name. The two artifacts are a pair; a mismatch is an immediate fail.
4. **Retention section distinguishes vendor vs. internal and references (not restates) the DPA.** Any paragraph that starts "the DPA states that…" and then paraphrases the DPA has restated it — rewrite as a reference with the specific clause slot named via `<!-- org-specific: ... -->`.
5. **Egress section separates model-training egress from abuse-monitoring egress.** Each gets its own sentence. Collapsing them is a Chapter 05 failure mode.
6. **Accident path is operator voice, five numbered steps minimum.** Grep for passive-voice tells ("the user should…," "it is recommended that…"). Rewrite in second person and imperative.
7. **"Do not delete the prompt"** (or a defensible alternative with a redline-log entry defending it) is in step 1.
8. **Preservation list is specific.** Prompt text, output, timestamp, user/device context. "Any relevant information" is a vague fail.
9. **Handoff to security operations is named** as the end of the enablement-side arc; `ai-risk-engineer` (L25) and the SOC are the receivers. No forensic language after that point.
10. **Three accident shapes named somewhere in Section 4** (paste-mistake, subtly-wrong-output, tool-malfunction).
11. **Section 5 is a pointer, not a re-authoring.** If it names IT-identity processes (how access reviews are conducted, what tickets look like), it has drifted; cut.
12. **Co-author tags per section, with the required signer alignment** (privacy on 1 and 2; security on 2 and 3; both on 4; IT identity referenced in 5; `head-of-ai-governance` ratifies at end of cycle).
13. **No SOC-side forensic language anywhere in the SOP.** Grep for: "chain of custody," "notification clock," "regulator notice window," "forensic image," "vendor trust team coordination." Any hit means Chapter 07 was ignored — rewrite or cut.
14. **`<!-- org-specific: ... -->` on every unknown.** Vendor retention window, DPA clause, SOC channel, records schedule, endpoint region, fallback-model config. Specific slots named per marker.

Markdown lint (`markdownlint data-handling-sop.md`).

## 4. Rubric / review checklist

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | Fits 2–3 pages at normal body-text size | 5 | Over 3 pages. |
| R2 | Five sections in required order | 10 | Any missing or reordered. |
| R3 | Data classes map to the Exercise 01 scheme; 2–3 concrete examples per class | 10 | Scheme mismatch, or examples absent / textbook-flavored. |
| R4 | Retention distinguishes vendor and internal; references (not restates) the DPA | 10 | Collapsed, or restated DPA text. |
| R5 | Egress separates model-training vs. abuse-monitoring in distinct sentences | 10 | Collapsed. |
| R6 | Accident path has ≥5 numbered operator-voice steps | 15 | Passive-voice, or fewer than 5 steps. |
| R7 | "Do not delete the prompt" (or defensible alternative with reason) present in step 1 | 5 | Missing. |
| R8 | Named role + channel + SLA for first contact | 5 | Named person, or missing channel/SLA. |
| R9 | Specific preservation list (prompt, output, timestamp, user/device context) | 5 | Vague ("any relevant information"). |
| R10 | Named handoff to the SOC and `ai-risk-engineer` (L25) | 5 | Missing handoff. |
| R11 | Three accident shapes named (paste-mistake, subtly-wrong-output, tool-malfunction) | 5 | Any missing. |
| R12 | Section 5 is a pointer to the IT-identity-operated playbook; no re-authoring | 5 | Re-authored access-review procedure. |
| R13 | Co-author tags aligned to signer discipline (privacy on 1/2; security on 2/3; both on 4; IT identity referenced in 5) | 10 | Uniform tags, or misaligned signer-section pairing. |
| R14 | No SOC-side forensic language; Chapter 07 routing discipline held | 10 | Any forensic / regulator-notification / vendor-trust-team language present. |
| R15 | `<!-- org-specific: ... -->` on every unknown, each naming the specific slot | 5 | Invented facts, or vague markers. |

**Pass threshold:** ≥ 85/100 and no R6/R10/R14 fail (those three are the security + privacy launch-gate equivalents).

## 5. Common mistakes

- **Narrating the accident path in the third person.** "The user should preserve the evidence…" is useless under pressure. Rewrite as "Do not delete the prompt. Screenshot the pane. Message `#ai-incident-first-line` now."
- **Collapsing model-training and abuse-monitoring egress into one sentence.** Operators confuse the two; privacy and security redline them separately. Give them separate sentences in Section 3.
- **Restating the DPA.** The SOP says "see DPA §X on retention" (or a `<!-- org-specific: ... -->` marker). It does not paraphrase DPA language back into the SOP; two sources of truth drift.
- **Running the forensics in the SOP.** "The CISO's team will acquire a forensic image and begin log analysis…" belongs in the SOC's runbook, not here. Chapter 07 is explicit on routing.
- **Making Section 5 a second access-review procedure.** It is a pointer. Three bullets of trigger conditions and a sentence that names IT identity as the operator is enough.
- **Writing a new data-classification scheme in Section 1.** Privacy owns the scheme; the SOP references it. If no scheme exists, name it as proposed in Exercise 01's AUP and flag it in the redline log.
- **Missing the three accident shapes.** Without them, the first-line triager has to pattern-match from scratch under pressure.
- **Uniform co-author tags.** Fails the Chapter 01 discipline test the same way it does for the AUP.

## 6. Stretch — precedence rule, triager Slack reply, retention table, evidence pack

**Precedence rule for AUP/SOP conflicts** (one paragraph):

> When the AUP's approved-use list and the SOP's data-class table appear to conflict, the SOP controls. The AUP sets permission at the use level; the SOP sets permission at the data-class level. If an approved use (for example, "explain unfamiliar code") would require pasting a Restricted or Regulated class to be executed in a particular instance, the SOP's forbidden-input rule governs and the instance is not permitted. Re-opening the AUP is the fix, not acting on the AUP against the SOP.

**3-sentence Slack message from the first-line triager** (`#ai-incident-first-line` reply to the user after step 3):

> Got your note — thanks for not clearing the pane. I've opened case AI-INC-`<!-- org-specific: confirm case ID format -->` and will ping you within four business hours with a read-out and next step. In the meantime, please do not re-prompt the tool from this session; if you need to keep working, start a fresh session in a different project and let me know you did.

**Retention-table template** (counsel and privacy populate the right-hand slots):

| Data class | Vendor retention (training path) | Vendor retention (abuse-monitoring path) | Internal retention | Deletion trigger | DPA clause reference |
|---|---|---|---|---|---|
| Public | `<!-- org-specific -->` | `<!-- org-specific -->` | Per records schedule `<!-- org-specific -->` | Standard log cycle | `<!-- org-specific: DPA §X -->` |
| Internal | `<!-- org-specific -->` | `<!-- org-specific -->` | Per records schedule `<!-- org-specific -->` | Standard log cycle | `<!-- org-specific: DPA §X -->` |
| Confidential | `<!-- org-specific -->` | `<!-- org-specific -->` | Per records schedule `<!-- org-specific -->` | Standard log cycle | `<!-- org-specific: DPA §X -->` |
| Restricted | Forbidden as input | Not applicable (prevention, not retention) | N/A | Accident-path triggered | `<!-- org-specific: DPA §X -->` |
| Regulated | Forbidden as input | Not applicable (prevention, not retention) | N/A | Accident-path triggered | `<!-- org-specific: DPA §X -->` |

**Enablement-side evidence pack handed to the SOC at step 6** (per Chapter 07):

- Screenshot and metadata bundle from step 2.
- Case record from the `ai-governance-analyst` queue, with the user's narrative and the triager's initial classification.
- Preservation list from step 4, including the data-class call and downstream-destination list.
- The exact AUP and SOP versions in force at the time of the accident (version IDs, not just file names).
- Any champion-network signal from the same cohort in the trailing 90 days that may add pattern context.
- Within a 2-business-hour SLA to the SOC, as a signed bundle (Markdown + screenshots zipped, hash recorded).

## 7. References

- **Learning material (local):**
  - [Chapter 01 — The Co-Author Posture and the Redline Log](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-103-policy-co-authoring-with-governance/01-the-co-author-posture-and-the-redline-log.md)
  - [Chapter 05 — The Data-Handling SOP](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-103-policy-co-authoring-with-governance/05-the-data-handling-sop.md)
  - [Chapter 07 — What You Route Out](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-103-policy-co-authoring-with-governance/07-what-you-route-out-counsel-soc-architect.md)
  - [mod-102 Chapter 03 — The Rollout Artifact Set](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-102-selecting-and-rolling-out-ai-tools/03-the-rollout-artifact-set.md)
  - [mod-109 — AI Incident Response and Enablement-Side Rollback](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-109-ai-incident-response-and-enablement-side-rollback)
- **Official standards and frameworks:**
  - [NIST AI RMF](https://www.nist.gov/itl/ai-risk-management-framework) — MANAGE function (incident handling), GOVERN function (procedures).
  - [NIST AI 600-1: Generative AI Profile](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf) — data-leakage and confabulation risks referenced in Sections 3 and 4.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — ML02 (data poisoning), ML06 (output integrity), relevant to the subtly-wrong-output and tool-malfunction shapes.
  - [MITRE ATLAS](https://atlas.mitre.org/) — adversary technique catalogue informing the preservation-list choices.
