# Exercise 02 — Co-Author the Use Policy with Governance — Solution

> Module: `mod-102-selecting-and-rolling-out-ai-tools`
> Exercise type: design / co-authoring drill
> Exercise brief: `lessons/mod-102-selecting-and-rolling-out-ai-tools/exercises/exercise-02-co-author-the-use-policy-with-governance.md` (in the learning repo)

## 1. Solution overview

The exercise is not a policy-writing exercise, it is a **co-authoring** exercise. The point is that an AI Enablement Lead does not author an acceptable-use policy alone, nor hand it to Legal to author alone. The failure mode in both directions is a policy that (a) no employee can actually follow, or (b) has no operational owner when it is broken.

This solution produces three things:

1. A **one-page use policy** for one specific AI tool (an AI coding assistant, used as the running example).
2. A **co-authoring trail** — who said what, what changed, and why — so the policy is defensible and the editing history itself is a training artifact.
3. A **handoff map** that says, for each clause, who owns enforcement and who owns the exception path.

The policy is the output. The co-authoring trail and handoff map are what distinguishes this from a "write a policy" assignment. This exercise also pairs directly with `mod-103-policy-co-authoring-with-governance/exercise-01-one-page-acceptable-use-policy-drill`, which generalizes the pattern across tools; the mod-102 version is scoped to a single tool being rolled out. *(To verify: confirm the cross-module reference in the learner's version of the curriculum.)*

## Implementation

Apply this solution by convening the governance co-authors named in section 2, co-drafting the one-page policy with the trail captured in parallel, producing the handoff map, and gating publication on the sign-off set in §7 of the policy. Validate the finished artifact against section 3 and score against the rubric in section 4; section 5 lists the common failure modes the co-authoring shape is designed to resist.

## 2. Worked answer

### Context

- Tool being rolled out: an AI coding assistant (IDE integrated).
- Audience: ~400 engineers across product, platform, and data.
- Governance stakeholders brought in as co-authors:
  - **Legal** — contractual obligations, IP, third-party code licensing.
  - **Security** — secret handling, prompt injection, exfiltration risk.
  - **Privacy / DPO** — personal data in prompts; EU vs US routing.
  - **Engineering leadership** — practical enforceability and fit with existing SDLC.
  - **People/HR** — disciplinary pathway when the policy is broken.
  - **AI Enablement Lead** — convenes, holds the pen, publishes the final.

### The one-page use policy

> **AI Coding Assistant — Acceptable Use Policy (v1.0)**
>
> This policy covers use of the **[Tool Name]** AI coding assistant inside the company's development environments. It is a living document. Questions go to `#ai-enablement`. Exceptions go to the AI Enablement Lead and are logged.
>
> **In scope**
> - Any use of the tool during work time, on company devices, or against company repositories.
>
> **Out of scope**
> - Personal use on personal devices against personal repositories. That is covered by the general employee handbook, not this policy.
>
> **1. Where you may use it**
> - In company repositories tagged `tier-standard` or `tier-internal`.
> - Not in repositories tagged `tier-restricted` or `tier-regulated` without a written exception.
>
> **2. What you must not paste into prompts**
> - Secrets, keys, tokens, credentials, or `.env` contents.
> - Customer personal data, including names, emails, identifiers tied to real people.
> - Code that is not ours to share (e.g., third-party code under a license that forbids redistribution).
>
> **3. What you must do with its output**
> - Review every suggestion before accepting. You are the author of code you commit, whether or not the tool wrote it.
> - Do not accept suggestions wholesale into security-sensitive paths (auth, crypto, access control, payment) without a second-pair review.
> - If a suggestion appears to reproduce substantial copyrighted text verbatim, discard it and flag it in `#ai-enablement`.
>
> **4. What the company does with your data**
> - The tool is contracted with training-on-tenant-data **off**. The contract and DPA are linked in the policy footer.
> - Prompts and completions are logged for audit for [N] days. <!-- to-verify: insert the retention period from the learner's actual contract, do not invent one. -->
> - Logs are accessible only to Security and, on named incident, to Legal.
>
> **5. If something goes wrong**
> - If you suspect you leaked a secret: revoke it immediately, then tell Security in `#sec-incident`. You will not be disciplined for a good-faith self-report.
> - If you suspect you leaked customer personal data: tell the DPO at `[DPO contact]` within one working day.
> - If you are unsure whether something counts: ask in `#ai-enablement` before you paste.
>
> **6. Enforcement**
> - First-time, good-faith policy breaches are a coaching conversation with the AI Enablement Lead.
> - Repeat or egregious breaches escalate per the standard employee conduct process.
>
> **7. How this policy changes**
> - Changes require sign-off from Legal, Security, DPO, and Engineering leadership.
> - The current version is `v1.0`. The change log is in the policy's source file.
>
> *Signed:* AI Enablement Lead · VP Engineering · General Counsel · CISO · DPO · VP People — [date]

### The co-authoring trail (excerpt)

The trail is kept as an append-only doc. Each row is a substantive change with named author and rationale. It is the training artifact that shows how the clauses got negotiated.

| # | Clause touched | Change | Driven by | Rationale |
|---|---|---|---|---|
| 1 | §2 "What you must not paste" | Added explicit `.env` reference | Security | Pattern observed in prior incident-free near-misses; concrete examples outperform abstract categories. <!-- to-verify: cite the internal near-miss log if the learner has one; otherwise state the clause is defensive and not incident-driven. --> |
| 2 | §3 second-pair review | Scoped to auth/crypto/access-control/payment paths only | Engineering | A blanket rule was unenforceable; a scoped rule is enforceable at PR review time. |
| 3 | §5 self-report amnesty | Added "will not be disciplined for good-faith self-report" | People/HR + Legal | Without amnesty, nobody reports and the policy fails open. |
| 4 | §4 retention | Marked retention period as to-verify pending contract check | AI Enablement Lead | Refused to invent a number the contract may not support. |
| 5 | §1 repository tiering | Pinned to existing `tier-*` labels already used by Security | Security | Avoids creating a parallel classification scheme. |
| 6 | §6 enforcement | Moved from "disciplinary action" to "coaching first" | People/HR | Enablement intent, not punitive. First-contact violations are a signal that the policy or training is unclear. |

### The handoff map

| Clause | Enforcement owner | Exception owner | Auditable evidence |
|---|---|---|---|
| §1 scope / repo tiers | Security (tier labels) | AI Enablement Lead | Repo metadata |
| §2 prompt hygiene | Engineering manager chain | AI Enablement Lead | Prompt logs (Security access only) |
| §3 review responsibility | Engineering (PR process) | VP Engineering | PR review records |
| §4 data handling | DPO | DPO + Legal | Contract + DPA + log retention config |
| §5 incident reporting | Security (secrets) / DPO (personal data) | n/a — report path, not exception | Incident tickets |
| §6 enforcement | People/HR | People/HR | HR case record |
| §7 change control | AI Enablement Lead | Governance Council | Policy change log |

The handoff map is the piece that makes the policy *operational* instead of *aspirational*: every clause has a human whose job it is to catch when it is broken, and a human whose job it is to say "yes this time" without rewriting the policy.

## 3. Validation steps

A reviewer should be able to confirm, reading only the learner's artifacts:

1. The policy fits on one page at a readable font size. Overflow is a design failure.
2. Every clause either states a rule or states a report path. Advisory prose that does neither is cut.
3. The policy names the tool, not "AI" in general.
4. There is a scope clause **and** an out-of-scope clause.
5. Every "you must not" has a corresponding "if you did, here is what to do" (amnesty / self-report).
6. The co-authoring trail has at least one entry per governance stakeholder, i.e. each stakeholder visibly touched the policy.
7. The handoff map covers every section; no clause is orphaned.
8. Retention, contractual, and DPIA-adjacent claims are either grounded in the actual contract or marked `<!-- to-verify: ... -->`.
9. The policy has a version number and a change-control clause. "v1.0 draft, update ad hoc" is a fail.

## 4. Rubric or review checklist

Scored out of 20. 14+ passes; below 10 is a rework.

| # | Criterion | Max |
|---|---|---|
| 1 | One-page policy fits on one page | 1 |
| 2 | Scope and out-of-scope clauses both present | 2 |
| 3 | Prompt-content prohibitions are specific (names examples, not categories only) | 2 |
| 4 | Output-handling clauses scope the "second-pair review" to named sensitive paths | 2 |
| 5 | Self-report / amnesty clause present | 2 |
| 6 | Enforcement clause is coaching-first, not punitive-first | 1 |
| 7 | Retention / contract claims either cite the contract or are marked to-verify | 2 |
| 8 | Change control clause names the sign-off set | 1 |
| 9 | Co-authoring trail has entries from each listed stakeholder | 3 |
| 10 | Handoff map covers every clause | 3 |
| 11 | Clear mapping to at least one `nist-ai-rmf` Govern outcome | 1 |

## 5. Common mistakes

- **Writing it alone.** Any artifact that shows a single author is failing the co-authoring purpose.
- **Policy-as-wishlist.** Clauses like "use AI responsibly" are unenforceable and should be cut.
- **No amnesty path.** Omitting §5 produces a policy that punishes the behavior it needs (self-reporting), and incidents stay hidden.
- **No exception path.** A policy with no written exception path *will* get broken informally. Formalize the path.
- **Policy ≠ tool docs.** Resist the urge to list keyboard shortcuts or vendor features in the policy; link to the tool docs instead.
- **Inventing retention periods and contract terms.** This is the most common `<!-- to-verify: ... -->` miss. The policy is only as credible as its contract.
- **Confusing this with a general AI policy.** This is a **per-tool** policy. A top-level company AI policy is a different artifact — see `mod-103-policy-co-authoring-with-governance`.

## 6. References

- NIST AI Risk Management Framework (AI RMF 1.0): <https://www.nist.gov/itl/ai-risk-management-framework> — specifically the Govern function, whose outcomes include policies, procedures, and accountability structures tied to AI use.
- OWASP Machine Learning Security Top 10: <https://owasp.org/www-project-machine-learning-security-top-10/> — informs the "do not paste secrets / do not accept suggestions wholesale into security-sensitive paths" clauses.
- MITRE ATLAS: <https://atlas.mitre.org/> — for threat framing when extending the policy to LLM-integrated tools with external connectors.
- Local context: `mod-103-policy-co-authoring-with-governance/exercise-01-one-page-acceptable-use-policy-drill` (general AUP) and `mod-102.../exercise-05-rollout-artifact-set-dry-run` (where this policy lives inside the rollout kit).
