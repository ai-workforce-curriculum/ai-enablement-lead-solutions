# Exercise 05 — AI-Specific Resistance Pattern Playbook — Reference Solution

> Learning file: [`exercise-05-ai-specific-resistance-pattern-playbook.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-105-champion-networks-and-change-management/exercises/exercise-05-ai-specific-resistance-pattern-playbook.md)

## 1. Solution overview

One artifact: a **resistance-pattern playbook** — a catalog of named resistance patterns that are specific to AI rollouts (not generic change-management resistance), each with a signal profile, a diagnostic, a response, and the anti-patterns to avoid. The playbook is written for champions and for the enablement seat; it is **not** a rebuttal script for pushing resistance down. The posture is explicit: resistance is a signal, not a problem to be eliminated, and some resistance patterns are correct and change the rollout.

Posture checks the solution encodes:

- **Resistance is AI-specific, not generic.** Patterns like "I don't see why we need this" exist in any rollout; patterns like "the tool hallucinated a regulation that does not exist" are AI-specific and get a dedicated playbook. This playbook covers the second class.
- **Each pattern has a legitimate reading.** Every pattern below has a version in which the operator is correct. The playbook names it; the response respects it. A playbook that treats resistance as always a misperception is a playbook that is about to miss a real risk.
- **Response is listen-first.** The first step on every pattern is a listening move — office-hours conversation, champion drill-down, or scorecard-level signal check. Response moves (reframe, policy clarification, tooling change, rollback) come after.
- **Some responses change the rollout.** Patterns 3 (tool-wrong), 5 (compensation-alignment fear), and 9 (sensitive-data drift) can all trigger a rollout change. The playbook names what the change looks like and where the authority lives.
- **The playbook is a living artifact.** Each champion sync (Exercise 02) can add a pattern; the playbook is versioned; the enablement seat owns the version increments, the champion network owns the signal.

## 2. Implementation — worked answer

### `resistance-patterns-playbook.md`

```
AI-Specific Resistance Patterns — Playbook (v0.1)
Author:   AI Enablement Lead (this role)
Audience: champions (primary), enablement seat (secondary)
Scope:    Coding-assistant rollout + G&A LLM rollout
Status:   Draft; new patterns added at weekly champion sync (Exercise 02)
```

#### How to use this playbook

- **It is a diagnostic tool, not a rebuttal script.** A champion encountering a pattern reads the diagnostic, listens, and responds per the response column. They do not read the pattern name aloud at the operator.
- **Each pattern has a "when the operator is correct" row.** Read it before the response row. If the operator is correct, the response is to escalate, not to reframe.
- **Response authority is named.** Reframe is at champion level; policy clarification is at enablement-seat level; tooling or rollout change requires governance-council surface.
- **Versioning.** This playbook is v0.1. New patterns surfaced at weekly sync become candidate entries; the enablement seat lands them in a weekly version increment.

#### The ten patterns

**Pattern 1 — "This is just marketing hype."**

- **Signal profile:** Operator declines to use the tool and dismisses pilot data as cherry-picked. Often comes from senior ICs who have survived three previous tool-of-the-month cycles.
- **Diagnostic:** The operator's prior experience is a change-management failure, not a tool failure. The rollout has to demonstrate durability past month 3, which is where previous cycles collapsed.
- **When the operator is correct:** If the pilot is < 12 weeks old and outcome signal is thin, "just hype so far" is factually accurate. Don't push back on it.
- **Response (listen-first):** Ask the operator what they would want to see at month 6 to update their view. Capture the answer; feed it into the scorecard-moment selection for that month.
- **Response (if persistent past month 6):** Share concrete field cases from champions, operator-attributed. Name the mod-106 scorecard as the surface they will see the outcome signal in.
- **Anti-patterns:** Do not list vendor stats (sounds like marketing). Do not invoke the sponsor exec (confirms the "top-down push" read). Do not treat the resistance as a training gap.
- **Response authority:** Champion + enablement seat.

**Pattern 2 — "The tool will make me replaceable / my job is going away."**

- **Signal profile:** Operator is anxious; may use the tool but under-reports usage; may avoid champion-network visibility.
- **Diagnostic:** The rollout narrative has conflated "capability" with "headcount." Often HR or Finance has made a statement — even informally — that landed as "this tool is how we reduce engineering headcount."
- **When the operator is correct:** If executive communications have cited the tool in a cost-reduction context, the operator's inference is correct. The rollout is subject to a compensation-alignment veto (Exercise 04 factor 6). The playbook escalates to the enablement seat and routes to HR.
- **Response (listen-first):** Ask what specifically they heard and where. Their source is usually a specific statement; capturing it is the input to the enablement-seat response.
- **Response (if executive communications are the source):** Escalate to the sponsor exec with a memo requesting an operator-voice re-statement. The enablement seat drafts the re-statement; sponsor exec delivers it. This is a rollout change — it changes communications.
- **Anti-patterns:** Do not promise "no one will be replaced" (not within the enablement seat's authority to promise). Do not frame it as a training opportunity ("this is a chance to grow your skills") — this is heard as corporate deflection. Do not share productivity numbers; they confirm the fear.
- **Response authority:** Champion → enablement seat → sponsor exec.

**Pattern 3 — "The tool is wrong half the time."**

- **Signal profile:** Operator can name three specific incorrect outputs. May be sampled from early-release behavior or from a workflow the tool is not well-suited to.
- **Diagnostic:** Either (a) the operator is using the tool for a workflow it is poor at (format conversion, long-context code reasoning, regulated-domain reasoning) and the fix is workflow guidance, or (b) the tool really is unsuitable for the workflow and the rollout is using the wrong tool.
- **When the operator is correct:** If the examples are from workflows the pilot charter committed the tool to supporting, the operator is right and the rollout is wrong. Escalate.
- **Response (listen-first):** Ask the operator to walk through one of the examples end-to-end. Capture the prompt, the output, and the expected output.
- **Response (if workflow-fit issue):** Add the workflow to the "where this tool is poor" section of the version-note surface. Reframe with the operator around workflows where the tool is a better fit.
- **Response (if tool-fit issue):** Escalate to pilot-review through the mod-102 pilot charter surface. This is a rollout change — the tool may need to be reconfigured, replaced, or descoped.
- **Anti-patterns:** Do not minimize ("the tool is improving every day"). Do not blame the operator's prompts ("that is a prompting skill issue"). Do not count the operator's time demonstrating errors as resistance.
- **Response authority:** Champion → enablement seat → pilot-review (if tool-fit).

**Pattern 4 — "I don't trust what happens to my data."**

- **Signal profile:** Operator is specifically concerned about prompt retention, cross-tenant training, or third-party sub-processors. Often more senior ICs; often engineers with security backgrounds.
- **Diagnostic:** The operator is reading the tool as a data-egress surface. The AUP Section 4 (data classes) and SOP (mod-103 Exercise 02) are the authoritative artifacts; if they do not answer the question clearly, the fix is in the artifacts, not the operator.
- **When the operator is correct:** If the DPA has a sub-processor clause, a cross-tenant training clause, or a retention surface the AUP does not reference, the operator has found a gap in the policy artifacts. Escalate to the redline log.
- **Response (listen-first):** Ask the operator to name the specific concern. Walk them through the AUP Section 4, the SOP, and the DPA summary. Note which part of the walk was not persuasive.
- **Response (if AUP/SOP is unclear):** File a redline-log entry; the policy artifacts get a clarification in the next walking-redline cycle.
- **Response (if DPA has a surface not covered):** Escalate to CISO delegate and counsel. This is a rollout change — the DPA may need renegotiation or a tenant-configuration change.
- **Anti-patterns:** Do not quote vendor marketing on data privacy. Do not dismiss as "paranoid." Do not promise more than the DPA actually guarantees.
- **Response authority:** Champion → enablement seat → CISO delegate / counsel (if DPA issue).

**Pattern 5 — "If I use the tool I'll be expected to be faster."**

- **Signal profile:** Operator opens the tool in secret or uses it only for low-visibility tasks. Explicit in 1:1 with their champion; silent in group settings.
- **Diagnostic:** The operator has correctly identified the compensation-alignment risk (Exercise 04 factor 6). The rollout's promise of "no performance consequence" is not credible to them.
- **When the operator is correct:** If any performance management artifact at the organization references tool-adoption, AI-fluency score, or velocity metrics tied to the tool, the operator is correct and the rollout has a veto condition. Escalate.
- **Response (listen-first):** Ask the operator what they think would happen if they adopted the tool heavily. Their specific fear is usually locatable (a manager who tracks velocity, a team norm around sprint points, a recent conversation).
- **Response (if no HR commitment is referenceable):** Flag to the enablement seat; the HR commitment from Exercise 04 needs to be surfaced to the operator's manager.
- **Response (if HR commitment is referenceable):** Walk through it with the operator. Offer office-hours attendance by their manager so the manager hears it directly.
- **Response (if executive signalling is the source):** Escalate per Pattern 2 — this is the same underlying resistance, with a different surface.
- **Anti-patterns:** Do not tell the operator the tool will make them "more productive" (confirms the fear). Do not share aggregate adoption or usage metrics with operator attribution. Do not route the concern through the operator's line manager without the operator's consent.
- **Response authority:** Champion → enablement seat → HR partner (if commitment surfacing needed).

**Pattern 6 — "My manager will stop giving me interesting work."**

- **Signal profile:** Operator uses the tool but only for the parts of their work they find tedious; actively avoids using it on work they find meaningful. May stop volunteering for stretch projects.
- **Diagnostic:** The operator has read the rollout as "the tool takes the interesting parts of the job and leaves the boring parts." This is often triggered by vendor marketing that promises to "handle the boilerplate so you can focus on the hard problems" — operators correctly recognize that the hard problems may not scale 1:1 to the time freed up by the boilerplate.
- **When the operator is correct:** If the team's work volume is bounded (fixed roadmap, limited product surface), the operator is correctly predicting that freed-up time will be re-tasked. The playbook does not promise this won't happen; it names the honest reading.
- **Response (listen-first):** Ask what they are doing with the time the tool frees up. The answer is often "I don't know yet."
- **Response:** Share operator-attributed cases from other champions where freed-up time went to meaningful work. Be honest where that has not happened — the playbook does not pretend every team will find meaningful uses for freed-up time.
- **Anti-patterns:** Do not promise the work will be more interesting ("you'll get to focus on the hard problems"). Do not treat the resistance as a growth-mindset problem. Do not pressure the operator to adopt more broadly.
- **Response authority:** Champion + enablement seat. Not a rollout change.

**Pattern 7 — "The tool is confidently wrong in ways I can't check."**

- **Signal profile:** Operator declines to use the tool for workflows that are outside their domain expertise. Specifically cites examples where the tool was confident and incorrect on a point they happened to be able to check.
- **Diagnostic:** The operator has correctly identified the asymmetric-error pattern specific to generative AI: errors in the tool's weak domains are not distinguishable in output tone from correct outputs in its strong domains. The operator's response (do not use outside domain expertise) is the correct enablement response and matches the AUP Section 2 "review before use" discipline.
- **When the operator is correct:** They almost always are. This pattern is a sign of fluency, not resistance.
- **Response (listen-first):** Ask the operator what signals they look for when they cannot check domain-wise. Capture the answer — this is training content for mod-104.
- **Response:** Reinforce. Share the operator's heuristics in the next office hours. Attribute to them (with consent).
- **Anti-patterns:** Do not suggest they "trust the tool more." Do not frame as a confidence-calibration problem (it is the opposite — they are well-calibrated). Do not tie their non-use to a performance metric.
- **Response authority:** Champion. This is a champion-amplification response, not a resistance-reduction response.

**Pattern 8 — "This is going to be a compliance nightmare."**

- **Signal profile:** Operator declines to use the tool and cites policy ambiguity. Specifically asks questions the AUP and SOP should answer but do not (clearly).
- **Diagnostic:** The policy artifacts have a gap. Either Section 2 (approved uses) is under-specified for the workflow, or Section 4 (data classes) is ambiguous for the data the operator is using.
- **When the operator is correct:** Almost always. The operator's role is to raise ambiguity; the policy's role is to answer it.
- **Response (listen-first):** Ask the specific question the operator cannot resolve against the AUP/SOP. Capture it.
- **Response:** File a redline-log entry. The question goes into the next walking-redline cycle (mod-103 Exercise 01). In the meantime, the operator gets a clarification from the `ai-governance-analyst` on-call.
- **Anti-patterns:** Do not tell the operator to "use judgment." Do not route the question upward without logging it. Do not treat the operator's refusal-to-use as the problem; the ambiguity is the problem.
- **Response authority:** Champion → enablement seat → redline log.

**Pattern 9 — "I don't want to be the one to put customer data into that thing."**

- **Signal profile:** Operator declines workflows that would involve pasting customer-adjacent data into a prompt, even when the AUP permits the workflow with masking. Often operators with prior data-breach exposure at this or a previous role.
- **Diagnostic:** The operator is risk-calibrated to the SR 11-7 / regulated-industry posture and is making the correct conservative call. AUP Section 4 already prohibits regulated-data inputs; if the operator is concerned about masked data being prohibited or re-identifiable, that is a legitimate concern.
- **When the operator is correct:** If the masking surface (test-data service, synthetic data) is weak or under-documented, the operator is identifying a real control gap. Escalate.
- **Response (listen-first):** Ask what specifically they are worried about. "Re-identification from masked data" is a different concern from "masked data accidentally being unmasked" — both are legitimate; the responses differ.
- **Response (if masking surface is weak):** File a redline-log entry; route to privacy and to the test-data service owner. This is potentially a rollout change — the tool may be descoped from customer-data-adjacent workflows until the masking surface is strengthened.
- **Response (if masking surface is strong but un-documented):** Add a version-note briefing walking through the masking surface. Offer the DPO or privacy partner as a joint office-hours guest.
- **Anti-patterns:** Do not minimize ("the masking is fine"). Do not assert the vendor has "SOC 2 certifications" as the resolution (irrelevant to re-identification risk). Do not require the operator to use customer data against their judgment.
- **Response authority:** Champion → enablement seat → DPO + test-data service owner (if control-gap).

**Pattern 10 — Silent cohort / silent function.**

- **Signal profile:** A cohort or function has very low tool access rate, very low office-hours attendance, and very low champion-signal volume — but no explicit resistance has been voiced.
- **Diagnostic:** Silence is not neutral. It usually means (a) the function is correctly applying the if-in-doubt default, (b) the function has a de facto manager-level "don't use" that is not surfacing, or (c) the champion in the function is not carrying signal.
- **When the operator is correct:** If the function's work is dominated by workflows the AUP prohibits, silence is the correct response. The playbook does not push adoption against a correctly-applied if-in-doubt default.
- **Response (listen-first):** Enablement seat initiates a listening pass — one office-hours session with the function, framed as a listening check, not an adoption push. Champion participates.
- **Response (if correct if-in-doubt application):** Scorecard the function as "correctly out-of-scope for current posture" and move on.
- **Response (if manager-level don't-use):** The posture is a de facto opt-in for that function. Surface to the enablement seat; the response is a manager-brief, not an operator-brief.
- **Response (if champion-signal gap):** Re-examine champion coverage (Exercise 01). The champion may need rotation or additional support.
- **Anti-patterns:** Do not interpret silence as consent. Do not pressure the function to adopt. Do not reach around the manager to the operators.
- **Response authority:** Enablement seat (listening pass); champion network (coverage); sponsor exec (if executive signalling is needed on the manager surface).

#### Versioning

- **v0.1** (initial draft; 10 patterns).
- **v0.x** (increments): new patterns added as surfaced at weekly sync. Each increment is announced at the sync and lands in `#ai-champions` within 24 hours.
- **Deprecation:** patterns that have not fired in ≥ 2 quarters are flagged for review; retained in an archive section rather than removed.

#### Co-author surface

> Drafter: AI Enablement Lead (this role).
> Ratifier: `head-of-engineering-enablement` (L55).
> Governance signer: `head-of-ai-governance` (L60) — confirms that patterns 2, 5 escalation paths route through the sponsor and HR as stated.
> HR signer: HR partner — confirms Pattern 5 handling.
> Privacy signer: DPO — confirms Pattern 9 masking-surface escalation path.

---

### End of worked playbook

## 3. Validation steps

1. **Patterns are AI-specific, not generic change resistance.** "People don't like change" is not a pattern; "the tool is confidently wrong in ways I can't check" is. Grep for pattern descriptions that would apply equally to a CRM rollout — rewrite or remove.
2. **Each pattern has a "when the operator is correct" row.** Playbooks that treat resistance as always misperception miss real risk. If any pattern lacks the correct-reading row, it is a draft fail.
3. **Response is listen-first.** The first response bullet on every pattern should be a listening move, not a reframe or a rebuttal. Flag any pattern where the first move is "say X to them."
4. **Response authority is named per pattern.** Who can execute each response? Champion, enablement seat, sponsor exec, governance council. Missing authority produces freelancing.
5. **Patterns 2, 5 route to sponsor and HR.** Compensation-alignment and headcount-fear resistance cannot be resolved at champion level. The escalation must be explicit.
6. **Patterns 3, 4, 9 can trigger rollout change.** Tool-fit, data-policy gap, and masking-surface gap are all escalations that may change the rollout. The playbook names this.
7. **Pattern 7 is reinforced, not reduced.** The "confidently wrong" caller is the most fluent operator in the function. If the playbook treats them as resistance to overcome, the playbook is wrong.
8. **No rebuttal scripts.** Grep for "say to the operator," "respond with," "the correct response is to tell them." If present, rewrite as listening moves.
9. **Each pattern has anti-patterns.** What to not do is at least as important as what to do. A pattern with no anti-patterns list is incomplete.
10. **`<!-- org-specific: ... -->` on DPA facts, regulator names, HR-commitment references.** `<!-- org-specific: ... -->` on any mod-105 chapter claim.

## 4. Rubric / review checklist

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | ≥ 10 patterns, each AI-specific | 15 | Fewer than 10 or generic change-resistance patterns included |
| R2 | Each pattern has signal profile, diagnostic, "when correct," response, anti-patterns, authority | 15 | Any pattern missing any of the six |
| R3 | Response is listen-first on every pattern | 10 | Rebuttal-first anywhere |
| R4 | Patterns include compensation-alignment fear (P5) and headcount fear (P2) with HR + sponsor routes | 10 | Either missing or routed only to champion |
| R5 | Patterns include tool-fit (P3), data-policy gap (P4), masking-surface gap (P9) as rollout-change triggers | 10 | Any of the three missing, or treated as perception issues |
| R6 | Pattern for "confidently-wrong-outside-domain" (P7) is reinforced, not reduced | 5 | Treated as resistance to overcome |
| R7 | Pattern for silent cohort (P10) with listening-pass response | 10 | Silence treated as consent |
| R8 | Playbook is explicitly versioned and additive from champion sync | 5 | No versioning or no update mechanism |
| R9 | Response authority named per pattern | 10 | Freelancing possible; no authority column |
| R10 | Anti-patterns on every pattern | 5 | Missing on any pattern |
| R11 | Co-author surface names drafter, ratifier, governance, HR, privacy signers | 5 | Missing HR or privacy |
| R12 | `<!-- org-specific: ... -->` on DPA, regulator, HR commitment; `<!-- org-specific: ... -->` on chapter claims | 5 | Invented or unverified facts |

**Pass threshold:** ≥ 85/100 and no R1/R3/R5/R7 fail.

## 5. Common mistakes

- **Treating resistance as a misperception to be corrected.** Every pattern has a reading where the operator is right. Playbooks that miss this miss the risk.
- **Writing rebuttal scripts.** The playbook is a diagnostic, not a script. Operators smell a script and the credibility of the surface collapses.
- **Generic change-management patterns in an AI-specific playbook.** "People don't like change" is a generic resistance pattern; it belongs in a different artifact. The AI-specific patterns are the ones in this playbook.
- **Treating the compensation-alignment fear as training.** It is a policy problem routed to HR, not a fluency gap. Patterns 2 and 5 both escalate up.
- **Treating silence as consent.** A silent function is almost never a function that has quietly adopted the tool. Pattern 10's listening pass catches this.
- **Reducing Pattern 7 (confidently-wrong-outside-domain).** The operator who notices this is the most fluent one in the room. Reinforce, don't reduce.
- **No anti-patterns.** A playbook that only names what to do leaves what to not do up to the champion's instinct. The anti-patterns list is the floor.
- **Not naming authority.** When a pattern surfaces and no one knows whose call it is, the response collapses or becomes political.
- **Treating resistance as a KPI.** "Reduce resistance incidents per quarter" is a metric that selects for suppressing signal, not addressing resistance.
- **Inventing specific DPA clauses or a specific regulator name.** `<!-- org-specific: ... -->` slots.

## 6. References

- **Learning material:**
  - [Exercise 05 learning file](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-105-champion-networks-and-change-management/exercises/exercise-05-ai-specific-resistance-pattern-playbook.md)
  - [mod-105 chapters (champion networks and change management)](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-105-champion-networks-and-change-management) `<!-- org-specific: confirm which mod-105 chapters cover resistance patterns, listening posture, and rollout-change escalation; link the specific chapter files here -->`
  - [mod-103 Exercise 01 — Acceptable-Use Policy](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-103-policy-co-authoring-with-governance/exercises/exercise-01-one-page-acceptable-use-policy-drill.md) — the Section 2/4 surfaces that Patterns 4, 8, 9 route to.
  - [mod-103 Exercise 02 — Data-Handling SOP](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-103-policy-co-authoring-with-governance/exercises/exercise-02-data-handling-sop-for-an-ai-tool.md) — the masking-surface and accident-path references used in Pattern 9.
  - [mod-104 (training and literacy curriculum)](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-104-training-programs-and-ai-literacy-curriculum) — where Pattern 7's heuristics become training content.
- **Official standards and frameworks:**
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — MAP (context and categorization), MEASURE (performance evaluation surface the playbook feeds), and MANAGE (response to identified risks) functions.
  - [NIST AI 600-1: Generative AI Profile](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf) — generative-AI-specific risk context for Pattern 7 (asymmetric error outside domain) and Pattern 9 (data-handling asymmetric risk).
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — prompt-injection and output-review context for Pattern 4 and Pattern 9.
  - [MITRE ATLAS](https://atlas.mitre.org/) — adversarial-technique context for the tool-manipulation reading in Pattern 4.
