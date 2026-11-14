# Exercise 01 — One-Page Acceptable-Use Policy Drill — Reference Solution

> Learning file: [`exercise-01-one-page-acceptable-use-policy-drill.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-103-policy-co-authoring-with-governance/exercises/exercise-01-one-page-acceptable-use-policy-drill.md)

## 1. Solution overview

This exercise is a **design artifact** — a 1–2 page draft AUP meant to be redlined, not approved. The worked example below carries the "coding assistant at a 3,000-person US bank" archetype through Exercises 01–04 so the AUP, SOP, intake, and council pre-read all reference the same tool, data scheme, and escalation path.

Posture checks the solution encodes:

- **Draft, not opinion.** Each section carries hooks counsel can attach obligations to, but the draft never issues a legal conclusion ("this violates GDPR"). That is the Chapter 07 drift to avoid.
- **Concrete over comprehensive.** Approved and prohibited uses are written to the "aloud at a team meeting" test. Vague AUPs feel safe to draft and fail as enforcement artifacts.
- **Co-author tags are non-uniform.** The reviewer check is that section-level ownership was actually considered. A uniform tag block is the fail state.
- **`<!-- org-specific: ... -->` on every org-specific fact we do not know.** No invention. Those markers block auto-merge and are the handoff into the walking-redline slot.

The seven-section structure is from Chapter 04; the co-author discipline is from Chapter 01; the artifact's place in the rollout set is from mod-102 Chapter 03.

## 2. Implementation — worked answer (`use-policy-draft.md`)

The artifact below is what you hand to `head-of-ai-governance` (L60) at the start of the 45-minute walking-redline slot. The accompanying 3-sentence framing email is in section 7 of this solution (Stretch).

---

### Acceptable-Use Policy — Coding Assistant (v0.1-draft)

**Tool:** Copilot-class coding assistant, Enterprise tenant. Production and sandbox.
**Organization:** `<!-- org-specific: confirm legal entity name (e.g., parent holdco vs. US national bank subsidiary) -->` — approximately 3,000 employees plus contractors, US-regulated depository institution.
**Draft version:** 0.1 (enablement-side first draft).
**Status:** Pre-redline. For reaction, not approval.

---

#### 1. Scope and in-scope users

Applies to the Enterprise tenant of the coding assistant in both the production IDE integration and the sandbox evaluation environment. In-scope populations: all employees of the bank and any contractor or consultant acting on behalf of the bank, including embedded vendor engineers who hold a bank-issued identity. Not in scope: personal developer accounts on personal devices — those are prohibited under the broader IT acceptable-use policy and are not addressed here. Jurisdictional context: all request/response traffic routes through `<!-- org-specific: confirm primary US-region vendor endpoint and any fallback region -->`.

> **Co-author tag — Section 1**
> Drafter: AI Enablement Lead (this role).
> Redliner: `head-of-ai-governance` (L60).
> Security signer: CISO delegate (identity team liaison).
> Privacy signer: Data Protection Officer.
> Legal signer: counsel (employment practice) — contractor/consultant language.

---

#### 2. Approved uses

The tool is approved for each of the following, named concretely so a line manager can read them aloud:

1. **Generate boilerplate code** in the languages the bank already supports in production (`<!-- org-specific: confirm the supported-language list from engineering standards (likely Java, Python, TypeScript, Go) -->`) from a specification the engineer wrote.
2. **Explain unfamiliar code** the engineer is reading from the bank's own repositories — for example, "what does this handler do, step by step."
3. **Write unit tests** against code the engineer has written, where the test cases are reviewed by the engineer before being committed.
4. **Draft migration or refactor plans** against code the engineer is actively modifying, with the plan reviewed by the engineer before any file is changed.
5. **Convert between well-documented formats** — for example, a pandas snippet to a PySpark snippet, or a JSON schema to a TypeScript interface, where the output is reviewed before use.

Approved uses are a floor, not a ceiling. If the use is not listed and not prohibited, the if-in-doubt default (Section 5) applies.

> **Co-author tag — Section 2**
> Drafter: AI Enablement Lead (this role).
> Redliner: `head-of-ai-governance` (L60).
> Security signer: not required (no new control surface).
> Privacy signer: not required (no data-class claim).
> Legal signer: counsel (IP practice) — "review before commit" language around generated code and license exposure.

---

#### 3. Prohibited uses

The tool is prohibited for each of the following. Each entry below is in the forbidden set because it is a contested case in a bank environment, not because it is obviously wrong.

1. **Do not paste customer PII into prompts.** Customer names, account numbers, SSN, DOB, addresses, and any `<!-- org-specific: confirm whether debit/credit card PAN appears in developer workflows at all — if yes, name explicitly -->` are forbidden inputs, including in test data or reproduction cases. Use masked or synthetic data from the bank's test-data service.
2. **Do not paste non-public financial data or trading positions** into prompts, including live rate sheets, prop desk positions, or underwriting-model parameters not yet published to regulators.
3. **Do not use the tool to generate or evaluate code that will run against production credit, lending, AML, or sanctions decisions** without the full `<!-- org-specific: confirm name of the bank's model-risk-management (MRM) review process, likely SR 11-7 aligned -->` review on the output. The tool is not approved for use inside the model-risk-managed decision path.
4. **Do not publish code generated by the tool to any external-facing output** — customer-facing applications, partner APIs, public open-source repositories, regulator-facing deliverables — without human review that is documented in the commit record.
5. **Do not use the tool for employment decisions** — hiring, promotion, termination, performance review drafting, or compensation benchmarking — regardless of whether the code or text is labeled as a "draft."
6. **Do not disable, bypass, or reconfigure** the tenant's content filters, the DLP integration, or the logging configuration. Configuration changes route through security as a change request, not through end-user settings.

> **Co-author tag — Section 3**
> Drafter: AI Enablement Lead (this role).
> Redliner: `head-of-ai-governance` (L60).
> Security signer: CISO delegate — entries 1, 2, 6.
> Privacy signer: Data Protection Officer — entry 1.
> Legal signer: counsel (regulatory practice) — entries 3, 5; counsel (employment practice) — entry 5.

---

#### 4. Data classes allowed and forbidden

Mapped to the bank's data classification scheme, `<!-- org-specific: confirm official scheme name — likely "Information Classification Standard" with tiers Public / Internal / Confidential / Restricted / Regulated -->`. For the purposes of this draft, we assume those five tiers.

| Data class | Allowed as prompt input | Allowed in generated output | Notes |
|---|---|---|---|
| Public | Yes | Yes | Published marketing, open-source references. |
| Internal | Yes | Yes | Internal technical docs, non-sensitive code from bank repos. |
| Confidential | Review required | Review required | Internal roadmaps, non-regulated business plans. Route through a champion if unsure. |
| Restricted | No | No | Customer PII, non-public financial data, employment records. |
| Regulated | No | No | Data governed by GLBA, BSA/AML, or `<!-- org-specific: confirm list of named regulations the classification scheme calls out explicitly -->`. |

If the organization's classification scheme is not named above, treat the five tiers here as the minimum classes this policy needs and flag it in the redline log for privacy to close.

> **Co-author tag — Section 4**
> Drafter: AI Enablement Lead (this role).
> Redliner: `head-of-ai-governance` (L60).
> Privacy signer: Data Protection Officer — primary.
> Security signer: CISO delegate — on tenant-enforcement claims.
> Legal signer: not required (class definitions are privacy's call).

---

#### 5. The "if-in-doubt" default

**Do not use the tool.**

The bank operates in a regulated environment where the cost of a wrong use (regulator attention, customer-data exposure, model-risk-management finding) exceeds the cost of a slower approval path. "Ask your manager" is rejected deliberately: line managers at a 3,000-person bank have not been trained to make AI judgment calls, and distributing that call across managers will produce inconsistent de facto policy.

> **Co-author tag — Section 5**
> Drafter: AI Enablement Lead (this role).
> Redliner: `head-of-ai-governance` (L60).
> Legal signer: counsel (regulatory practice) — confirms the regulated-environment framing.
> Security signer: not required.
> Privacy signer: not required.

---

#### 6. Escalation path to governance and security

- **Policy questions** ("is use X permitted?"): post in `#ai-enablement-help` (Slack). Routed to the `ai-governance-analyst` on-call. Target response within one business day. `head-of-ai-governance` (L60) is the escalation owner for contested cases.
- **Suspected data-handling accident** (wrong data pasted, suspicious output, tool behaving out-of-policy): follow the data-handling SOP accident path (Exercise 02). Do **not** delete the prompt. Contact the first-line triager via `#ai-incident-first-line` and follow the SOP from there.
- **Security incident** (credential exposure, suspected malicious output, tenant misconfiguration): escalate to the SOC via the standard IR channel (`<!-- org-specific: confirm the bank's SOC on-call channel/number -->`) and to `ai-risk-engineer` (L25).

> **Co-author tag — Section 6**
> Drafter: AI Enablement Lead (this role).
> Redliner: `head-of-ai-governance` (L60).
> Security signer: CISO delegate — primary.
> Privacy signer: Data Protection Officer — on the data-handling-accident line.
> Legal signer: not required.

---

#### 7. Review cadence

This policy is reviewed **every six months** by `head-of-ai-governance` (L60) and this role, with the first review scheduled 90 days after GA. Mid-cycle review is triggered by any of: (a) a Section 4 data-class accident-path event; (b) a regulator guidance update on generative AI in regulated financial services (`<!-- org-specific: name the primary regulator — OCC / Federal Reserve / FDIC — whose guidance this policy watches -->`); (c) a material change in the vendor's DPA, retention controls, or egress behavior; (d) a change to the bank's information classification scheme.

> **Co-author tag — Section 7**
> Drafter: AI Enablement Lead (this role).
> Redliner: `head-of-ai-governance` (L60).
> Security signer: not required at cadence level; re-entered per review.
> Privacy signer: not required at cadence level; re-entered per review.
> Legal signer: not required at cadence level; re-entered per review.

---

#### Appended note (drafter → redliner)

I expect `head-of-ai-governance` to rewrite **Section 3 (prohibited uses)** most heavily, specifically the model-risk-managed decision-path entry (3.3), because the current wording may bind the tool out of use cases the MRM team has already quietly sanctioned. I also expect Section 5 (the if-in-doubt default) to be contested — counsel may prefer "do not use" and the CIO organization may prefer "ask your manager"; the one-sentence constraint forces the choice and that choice is the walking-redline conversation.

---

### End of worked AUP draft

## 3. Validation steps

Before handing the draft into the walking-redline slot, run it against this checklist. A reviewer grading this exercise should do the same.

1. **Page count.** Render the Markdown. Confirm it fits in 1–2 pages at normal body-text size. If it spills, the usual cause is restating the data-classification scheme — cut back to naming classes and move operational detail to the SOP.
2. **Seven-section order.** Scope → approved uses → prohibited uses → data classes → if-in-doubt → escalation → review cadence. In this order. Reordering is a Chapter 04 fail.
3. **Counts.** At least five approved uses, at least five prohibited uses, each concrete. Prohibited uses touch each of the five required domains: sensitive data classes, external-facing output, high-risk decision categories (hiring/firing/credit/benefits/safety-of-life), tenant-control tampering, non-public financial/business data.
4. **One-sentence if-in-doubt default.** Not two sentences with a comma. Followed by a 2-sentence justification immediately below. "Ask your manager or governance" is the fail state.
5. **Co-author tags per section, non-uniform.** Pull the seven tag blocks side by side — if they are all identical, the uniformity test fails and the author did not think about section-level ownership.
6. **Legal hooks, not legal opinions.** Grep the draft for "violates," "unlawful," "GDPR requires" — any of these indicates the drafter drifted into legal opinion. Rewrite as hooks ("non-public financial data," "regulated under `<!-- org-specific: ... -->`") that counsel can attach obligations to.
7. **`<!-- org-specific: ... -->` on every unknown.** Specifically: legal entity name, supported-language list, SOC channel, MRM process name, regulator name, data scheme name, vendor region. Each marker should name the specific fact the partner would fill in. Generic `org-specific` with no detail is a weak marker.
8. **Appended note present.** One paragraph, 4 sentences max, naming two sections and a one-sentence reason each.

Markdown lint the file (`markdownlint use-policy-draft.md`) before sharing; the repo's `.markdownlint.jsonc` is the rule set.

## 4. Rubric / review checklist

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | Fits 1–2 pages at normal body-text size | 5 | Spills to page 3. |
| R2 | Seven sections present, in required order | 10 | Any missing or reordered. |
| R3 | ≥5 approved uses, each operator-voice concrete | 10 | Vague entries ("productivity," "general coding tasks") present. |
| R4 | ≥5 prohibited uses, covering all five required domains | 15 | Missing data-class, external-output, high-risk-decision, tenant-tamper, or non-public-financial entry. |
| R5 | Data classes map to a named classification scheme (real or clearly proposed) | 10 | No scheme named. |
| R6 | If-in-doubt default = one sentence + 2-sentence justification | 10 | Two-sentence default, or no justification. |
| R7 | Escalation path uses role names, with channel and SLA | 5 | Named people, or missing channel/SLA. |
| R8 | Review cadence names when/by whom/against what inputs | 5 | Missing trigger list. |
| R9 | Co-author tag per section, non-uniform across sections | 15 | Uniform tags across all seven sections. |
| R10 | No legal opinions; only legal hooks | 10 | Any "violates," "unlawful," "requires under GDPR"–style conclusion. |
| R11 | `<!-- org-specific: ... -->` on every unknown org fact, each with specific slot | 3 | Invented facts, or vague `org-specific` with no slot named. |
| R12 | Appended note names two sections + one-sentence reason each | 2 | Missing or more than 4 sentences. |

**Pass threshold:** ≥ 85/100 and no R4/R6/R9/R10 fail (those four are launch-gate equivalents in the real role).

## 5. Common mistakes

- **Writing the whole policy in uniform governance voice.** The AUP is operator-facing. "The institution shall not permit the use of the aforementioned tooling for unapproved purposes" is defense-document voice. Rewrite in second person or team-manager-aloud voice.
- **Listing "do not misuse the tool" and calling it a prohibited use.** That is the vague-AUP failure mode from Chapter 04. Replace with the contested cases that are the reason the policy exists.
- **Restating the data classification scheme in Section 4.** The scheme lives with privacy. Reference it by name; map which classes are in scope for this tool. Operational detail is Exercise 02's SOP, not here.
- **Issuing a legal reading.** "This use would violate GLBA" is counsel's writing. Name the data class ("non-public financial information"); let counsel attach the obligation.
- **Uniform co-author tags across all seven sections.** Review cadence does not need a legal signer. Data classes needs a privacy signer. Non-uniformity is the evidence of real co-authoring; uniformity is evidence of hand-off.
- **Two-sentence if-in-doubt default.** "Ask your manager or governance" contains no default and will be ignored. Pick one deliberately.
- **Appended note that names three or more sections.** The exercise asks for two. More is noise; it signals the drafter has not thought about which rewrites they most expect.
- **Inventing a specific vendor-DPA fact or a specific regulator name.** Those are `<!-- org-specific: ... -->` slots. Invention breaks the co-authoring posture and poisons the redline log.

## 6. Stretch — email, counsel redlines, review-cycle calendar

**3-sentence email that accompanies the draft** (to `head-of-ai-governance`, cc counsel, CISO, DPO):

> Attached is v0.1 of the coding-assistant AUP draft. I am asking for your redlines in Tuesday's 45-minute walking slot — not for approval — and I have flagged Sections 3 and 5 as the ones I expect to move the most. By the end of the slot, I need a decision on whether we lock the if-in-doubt default as "do not use the tool" or whether we are reopening that call this cycle.

**Three bullets of expected counsel redlines on Section 3:**

- Counsel tightens 3.1 to name specific regulations the PII prohibition attaches to (likely GLBA, state privacy statutes) and asks for a defined-term list.
- Counsel adds a clause to 3.3 distinguishing "code that runs against the decision" from "code that supports the decision workflow" — the MRM scope line.
- Counsel adds an audit-log retention requirement to 3.6 (tenant-control tampering) tied to the bank's `<!-- org-specific: confirm record-retention schedule -->`.

**Review-cycle calendar — 12 months:**

- **T+0 (ratification):** Day of signed policy.
- **T+90 days:** First post-launch review window. Inputs: GA-period accident-path events, champion-network field signal, any regulator guidance since launch.
- **T+180 days:** First scheduled biannual review.
- **T+365 days:** Second biannual review; annual audit snapshot captured.
- **Mid-cycle triggers (any window):** Section 4 data-class accident, regulator guidance update, vendor DPA change, classification-scheme revision.

## 7. References

- **Learning material (local):**
  - [Chapter 01 — The Co-Author Posture and the Redline Log](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-103-policy-co-authoring-with-governance/01-the-co-author-posture-and-the-redline-log.md)
  - [Chapter 04 — The One-Page Acceptable-Use Policy](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-103-policy-co-authoring-with-governance/04-the-one-page-acceptable-use-policy.md)
  - [Chapter 07 — What You Route Out](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-103-policy-co-authoring-with-governance/07-what-you-route-out-counsel-soc-architect.md)
  - [mod-102 Chapter 03 — The Rollout Artifact Set](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-102-selecting-and-rolling-out-ai-tools/03-the-rollout-artifact-set.md)
- **Official standards and frameworks** (for the hooks this policy exposes to counsel and governance):
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — GOVERN function (policies, roles & responsibilities).
  - [NIST AI 600-1: Generative AI Profile](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf) — generative-AI-specific risk considerations referenced in Sections 2 and 3.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — context for the prompt-injection and output-review concerns that shape Section 3.
  - [MITRE ATLAS](https://atlas.mitre.org/) — adversarial technique context for tenant-tamper and output-manipulation prohibitions.
