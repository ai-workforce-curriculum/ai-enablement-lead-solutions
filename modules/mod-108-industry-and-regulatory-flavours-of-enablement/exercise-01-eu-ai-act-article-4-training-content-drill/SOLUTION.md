## Exercise 01 — EU AI Act Article 4 Training Content Drill — Reference Solution

> Module: `mod-108-industry-and-regulatory-flavours-of-enablement`
> Exercise type: design / worked example (training content artifact)
> Exercise brief: [`lessons/mod-108-industry-and-regulatory-flavours-of-enablement/exercises/exercise-01-eu-ai-act-article-4-training-content-drill.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-108-industry-and-regulatory-flavours-of-enablement/exercises/exercise-01-eu-ai-act-article-4-training-content-drill.md) (in the learning repo)

## 1. Solution overview

The deliverable is a **training content package the organization can point to as evidence it has taken measures to ensure a sufficient level of AI literacy of its staff and other persons dealing with the operation and use of AI systems on its behalf**, i.e., the Article 4 obligation of Regulation (EU) 2024/1689 (the EU AI Act). Article 4 became applicable on 2 February 2025 and applies to both **providers** and **deployers** of AI systems; the obligation is scoped to the organization's own staff *and* to contractors / third parties operating AI on the organization's behalf. <!-- verify-with-sme: confirm the exact national-competent-authority arrangements for Article 4 enforcement in the organization's primary member state; enforcement supervision for Article 4 is distributed across member-state authorities, and specific supervisory posture may differ. -->

The archetype carried through this solution is a **~5,000-person multinational enterprise headquartered in an EU member state** that is a **deployer** of commercial AI assistants (a general-purpose chat assistant for knowledge workers, a coding assistant for engineering, and a meeting-summary assistant). The organization is not a **provider** of AI systems in the sense of Article 3(3); it integrates vendor systems. Deployer-flavour obligations therefore dominate. <!-- org-specific: if the learner's org *is* a provider (fine-tunes, re-packages, or places AI systems on the EU market under its own trademark), add the provider-side obligations from Article 16 and treat this training content as one input among many. -->

Posture checks this solution encodes:

- **Article 4 is a "measures" obligation, not a syllabus obligation.** The regulation does not prescribe a curriculum. It says the organization must *take measures* to ensure *sufficient* literacy, *to their best extent*, *taking into account* role, context, prior training, and the populations the AI is used *on*. The training content therefore must be **auditable as a set of measures**, not just a deck. The artifact is the course plus the attendance / assessment / role-mapping evidence.
- **"Sufficient" is role-calibrated.** A warehouse worker whose shift-schedule is produced by an AI tool and an engineer who tunes the retrieval prompts need different training. The content package segments explicitly and marks which module is required of which population.
- **"Other persons dealing with the operation and use of AI systems on their behalf"** is explicit in the article text. Contractors, outsourced-ops staff, embedded consultants, and managed-service engineers are in-scope. The content package has a contractor track.
- **Training content is versioned to the AI systems it covers.** When the organization adopts a new AI system or materially changes the prompt / retrieval configuration of an existing one, the training content re-ships. The version metadata and the system inventory are part of the artifact.
- **Content ties AI literacy to the organization's existing policy stack, not to the abstract AI Act.** Staff do not need to recite the Act; they need to recognize a Restricted input, know where to escalate a suspected incident, and know when to stop. The content maps literacy objectives to the AUP, the data-handling SOP, and the incident-response path.
- **Evidence of measures is more important than form of measures.** An e-learning module + attendance log + 90-day refresher cadence counts; a one-off town hall does not. The validation steps lean on evidence shape.

## 2. Implementation — worked answer — the training content package

### 2.1 Package manifest (`article-4-training-package.md`)

```
Article 4 training content package — v0.1-draft
Organization:        <!-- org-specific: name the EU legal entity responsible for compliance -->
Primary jurisdiction: <!-- org-specific: primary member state(s); if establishment is in more than one MS, name the lead -->
Deployer / provider:  Deployer (see Section 1 of this solution; add provider track if applicable)
In-scope AI systems:  See Section 2.3 (system inventory)
Target populations:   See Section 2.4 (segment map)
Owner:                AI Enablement Lead
Co-signers:           Head of Legal/Privacy (DPO); Head of HR Learning; Works Council liaison <!-- org-specific: works-council consultation is required in several MS and advisable everywhere -->
Last redlined:        <!-- org-specific: date -->
Next refresh:         + 180 days or on material change to inventory
```

### 2.2 Literacy objectives (what "sufficient" means for this organization)

Seven objectives. Every covered population must leave the training able to do at least objectives 1–5; the Operator and Builder tracks add 6–7.

1. **Recognize an AI system when you are using one** — including when it is an embedded feature of another tool (e.g., a "summarize" button). Rationale: a staff member who does not recognize an AI system cannot apply the AUP to it.
2. **Name what class of data you may and may not put into an AI prompt or upload** — tied to the organization's data-classification scheme and the AUP's Restricted / Approved tiers.
3. **State the two most common failure modes the staff member will see in their own work** — for the general track these are hallucinated facts and confident-sounding wrong answers; for operator tracks these expand to retrieval-staleness and prompt-injection via content.
4. **State the single-sentence escalation path** for three events: (a) suspected policy breach by a colleague, (b) a wrong-and-shipped AI output, (c) a security or privacy concern about the AI tool itself.
5. **Name the organization's three governing documents** for AI use — the AUP (`mod-103 exercise-01`), the data-handling SOP (`mod-103 exercise-02`), and the incident-response path (`mod-109`). Staff must know these exist and how to find them.
6. **(Operator track)** — Explain, in one paragraph, how the organization's general-availability AI assistant works at the level of "retrieves from these sources, is grounded on these data stores, uses this model family." Depth: enough to answer a user question about where answers come from.
7. **(Builder track)** — Identify at least three of the OWASP ML Security Top 10 risks that apply to the system the builder is operating or customizing, and name the control the organization uses to mitigate each. Builders are also pointed at MITRE ATLAS as the adversarial-technique reference for threat-model conversations.

### 2.3 In-scope AI system inventory

The training content is keyed to a short, maintained inventory of in-scope systems. The inventory is versioned and lives alongside the training content so that staff can see which systems they have been trained on.

| System ID | System description | Role / purpose | Risk tier under the organization's internal classification | Covered populations |
|---|---|---|---|---|
| sys-01 | General-availability AI assistant, Tier-1 (daily) | Knowledge-work assistance, drafting, summarization | Standard | Everyone |
| sys-02 | General-availability AI assistant, Tier-2 (occasional) | Same, lower usage volume | Standard | Everyone |
| sys-03 | Code assistant for Engineering | Code generation, explanation, test drafting | Standard | Engineers, SRE |
| sys-04 | Meeting-summary assistant | Live meeting transcript + summary | Elevated — speech capture of attendees | Meeting organizers, HR, Legal |
| sys-05 | HR screening-assist for internal mobility pilots | Candidate-note summarization only (no scoring) | Elevated — HR, potential Annex III scope <!-- org-specific: confirm whether this falls under Article 6 / Annex III for employment; if yes, provider-side risk-management obligations apply and this training content is not sufficient on its own. --> | HR partners, hiring managers |
| sys-06 | Customer-facing chatbot | Customer inquiries, routing | Elevated — Article 50 transparency applies <!-- verify-with-sme: confirm Article 50 transparency obligation wording for this configuration --> | Customer-service staff, product owners |

### 2.4 Segment / population map

| Segment | Description | Example roles | Required modules | Delivery mode | Time budget |
|---|---|---|---|---|---|
| S-ALL | Everyone with system access | All staff, contractors with identity | M1, M2, M3, M4, M5 | Self-paced e-learning + manager debrief | 45 min + 15 min debrief |
| S-OPR | Operators of a specific system (daily users, trainers, support) | Enablement champions, help-desk, line managers who run AI-touching processes | S-ALL + M6-op per covered system | Self-paced + live cohort | S-ALL + 45 min per system |
| S-BLD | Builders / customizers (prompt engineers, retrieval-pipeline owners, agent builders) | Engineering, data/AI platform team | S-ALL + M7-bld | Live cohort + lab | S-ALL + 90 min |
| S-ADJ | Adjacent / specialty populations with specific obligations | HR (sys-05), customer-facing (sys-06), works-council reps | S-ALL + M8-adj specific to the system | Live cohort | S-ALL + 60 min |
| S-EXT | External / contractor / managed-service | Outsourced ops, embedded vendor engineers | S-ALL (adapted); evidence of equivalent prior training may substitute at reviewer discretion | Self-paced + attestation | 45 min or attestation |
| S-EXEC | Executive sponsors | L50+ with decision rights | M1 + a tailored M9-exec briefing | Live briefing | 30 min |

### 2.5 Module outline (what the training actually contains)

#### Module 1 — What an AI system is, in your work (10 min, all segments)

- **Objectives covered:** 1, 5.
- **Content:** definition of an AI system aligned to Article 3(1) of the AI Act (<!-- verify-with-sme: cite exact Article 3(1) wording as rendered in the published OJ text -->), rendered as three plain-language examples the audience can recognize ("the Summarize button in your email client is an AI system; the autofill in the ticketing tool is an AI system; a vendor-supplied chat window on the intranet may or may not be — here is how to tell"). A 90-second video from an executive sponsor stating *why* the organization is complying with Article 4 and *how* the commitment interacts with staff trust (AI is not here to replace you, measurement is for program health). A one-slide map of the three governing documents (AUP, SOP, incident path) and where to find them in the intranet.
- **Assessment:** three-question behavior check. "You open a vendor tool and it has a new 'Ask AI' button — before using it, which of the following do you do?" Correct answer references the AUP data-classification check, not a generic "ask my manager."

#### Module 2 — The data you can and cannot put into a prompt (12 min, all segments)

- **Objectives covered:** 2, 5.
- **Content:** the organization's data classification tiers as named in the AUP (`mod-103 exercise-01`), illustrated with realistic examples from this organization's work — not generic placeholders. Clear restated rule: Restricted data does not go into a prompt, period, in any system, including the organization's internal assistants. The "if-in-doubt — do not use" default. Where masked / synthetic data is available for development and test.
- **Assessment:** three prompt-and-input scenarios. "A customer has emailed a complaint including their account number. You want to draft a reply with the assistant. What do you paste into the prompt?" Correct answer involves removing the account number and the customer's name before pasting, or using the organization's internal tool with the PII-handling guardrail configuration.

#### Module 3 — What goes wrong (10 min, all segments)

- **Objectives covered:** 3.
- **Content:** two failure modes staff *will* encounter: (a) hallucinated / fabricated facts stated with confidence, with worked examples — a citation that does not resolve, a name that does not exist; (b) confidently wrong reasoning that passes a quick skim — a math error, a confused chronology, a mis-identified legal section. For operator and builder tracks, a brief pointer forward to Module 6/7 for retrieval staleness and prompt injection.
- **Assessment:** paired-example comparison — "Of these two AI responses, which one is the one you forward without checking? Why not the other one?" Correct answer is that neither is forwarded without checking; verification is the staff member's responsibility regardless of how confident the output reads.

#### Module 4 — The escalation path (8 min, all segments)

- **Objectives covered:** 4.
- **Content:** the three events — suspected policy breach by a colleague, wrong-and-shipped AI output, security/privacy concern about the AI tool — each mapped to a single named channel. The channels are role-name-addressed (not person-name-addressed) so the content survives staff turnover: the compliance ombuds mailbox, the shipping-owner line manager, and the security-incident intake queue. The "no-blame on first-time reporting" framing from the organization's existing speak-up program. A one-slide memory-aid.
- **Assessment:** three-event quiz with named channels.

#### Module 5 — The three governing documents and where to find them (5 min, all segments)

- **Objectives covered:** 5.
- **Content:** a live tour of the three documents on the intranet, with the version date and owner surfaced on each. The AUP, the data-handling SOP, and the incident-response path.
- **Assessment:** "Find and open the current AUP — paste the version date here." Behavior pass, not multiple choice.

#### Module 6-op — Operator deep-dive, per covered system (45 min per system, S-OPR)

- **Objectives covered:** 6, plus a deepening of 2–3 for the specific system.
- **Content:** one module per covered system (sys-01 through sys-06 as scoped). Each covers: how the system is configured in this organization's tenant; which data sources are retrieved; what the failure-mode profile looks like specifically for this system (e.g., meeting-summary attribution errors, code-assistant license-exposure); the operator's additional escalation obligations; the operator's role in seeing-and-reporting adoption and failure signals (ties into `mod-106`).
- **Assessment:** two simulated failures per system, operator must demonstrate the triage + escalation + user-communication steps.

#### Module 7-bld — Builder deep-dive (90 min, S-BLD)

- **Objectives covered:** 7, plus deepening of 2–6.
- **Content:** a threat-model session anchored to the **OWASP Machine Learning Security Top 10** and **MITRE ATLAS**. Builders walk through the organization's prompt-engineering platform, the retrieval index, and any agent they operate; identify at least three Top-10 risks that apply (prompt injection via retrieved content, input manipulation, model output integrity, etc.); and name the control the organization uses for each. ATLAS is introduced as the shared vocabulary for adversarial techniques when talking to Security. Explicit pointer to the organization's incident-response path (`mod-109`).
- **Assessment:** a threat-model artifact for the builder's own system, co-reviewed by the Security intake partner. Pass criterion is that the builder produced the artifact and the Security reviewer signed.

#### Module 8-adj — Specialty / adjacent populations (60 min, S-ADJ)

- **Objectives covered:** situational deepening for 1–5 for the system the adjacent population touches.
- **Content:** one variant for each adjacent system — HR (sys-05): the Article 6 / Annex III implications and why the organization has drawn the line at *note-summarization only*, with no scoring; customer-facing (sys-06): Article 50 transparency language and the required "you are interacting with an AI" disclosure; meeting-summary (sys-04): speech-capture consent, retention, GDPR interaction.
- **Assessment:** scenario-based — "A hiring manager asks you to run the candidate shortlist through the assistant's scoring feature — the assistant will accept the input. What is your answer?" Correct answer: the feature is out-of-scope per the AUP, with the specific rationale.

#### Module 9-exec — Executive sponsor briefing (30 min, S-EXEC)

- **Objectives covered:** 1 and a sponsor-grade orientation on the measures rationale.
- **Content:** what Article 4 requires of the organization, what measures the organization has taken, what is on the next-cycle backlog, where the current risks are, and what the sponsor is being asked to do (visibly complete the staff training, re-ship a short message on the "why," attend the annual governance council briefing). Ties directly into the executive scorecard in `mod-106`.
- **Assessment:** sponsor attestation that they completed the training, time-stamped.

### 2.6 Contractor / "other persons on their behalf" track (S-EXT)

Article 4 covers "other persons dealing with the operation and use of AI systems on their behalf." The organization must evidence training reach into this population. Three mechanisms:

1. **Direct assignment** — contractors with an organization-issued identity complete S-ALL via the same LMS as staff, with the same completion telemetry.
2. **Equivalent-prior-training attestation** — managed-service engineers and embedded vendor engineers may submit attestation of equivalent prior training by their employer; the attestation is reviewed by the AI Enablement Lead and recorded alongside the identity record. <!-- org-specific: confirm attestation wording with Legal. -->
3. **Contractual flow-through** — the MSA / DPA with every vendor that operates AI systems on the organization's behalf carries an Article-4-equivalent training clause. <!-- org-specific: confirm clause language with Legal and Procurement; ties into `mod-107` partnership contract. -->

### 2.7 Evidence package (what the organization can show on request)

This is the single most important part of the solution: the training content is the medium, but the **evidence package** is the thing the organization will be asked to produce.

| Evidence item | Form | Owner | Retention |
|---|---|---|---|
| In-scope AI system inventory (Section 2.3) | Versioned document | AI Enablement Lead + Security intake | Life of system + 3 years <!-- org-specific: confirm retention schedule --> |
| Segment / population map (Section 2.4) | Versioned document | AI Enablement Lead + HR | Life of program |
| Module versions and content archives | LMS repository | L&D partnership (per `mod-104 exercise-07`) | 6 years <!-- verify-with-sme: confirm applicable retention period under GDPR + national labour-law overlays --> |
| Completion telemetry (who / which module / when / pass) | LMS exports; linked to HRIS and to IAM for contractors | L&D + HR | 6 years <!-- verify-with-sme --> |
| Attestations (S-EXT, S-EXEC) | Signed statements, time-stamped | L&D + Legal | Same as training records |
| Contractor flow-through clause audit | Procurement record | Procurement | Contract life + statutory period |
| Change log (why a module re-shipped) | Versioned document | AI Enablement Lead | Life of program |
| Refresh cadence log (annual refresher, triggered refresher, new-system refresher) | Versioned document | AI Enablement Lead | Life of program |

### 2.8 Governance and refresh cadence

- **Baseline cadence:** S-ALL completes on hire + within 30 days of policy re-ship; refreshes every 12 months.
- **Triggered re-ship:** whenever a new AI system enters the inventory, whenever the AUP or SOP is redlined in a way that changes a Restricted / Approved tier, whenever the organization materially reconfigures a covered system (model family change, retrieval-source change, consent model change), or whenever a serious incident per `mod-109` has a human-factor root cause.
- **Internal review:** AI Enablement Lead reviews the content package quarterly; Legal/DPO reviews annually; the works council is consulted on material changes. <!-- org-specific: confirm works-council consultation steps per national labour-law overlay. -->
- **External review:** external counsel reviews annually or on demand ahead of a regulator inquiry.

## 3. Validation steps

1. **Cover every Article 4 population.** Walk through the segment map (Section 2.4) and confirm that every person with access to any system in the inventory (Section 2.3) is assigned to at least one segment and a minimum module set. No one with access is uncovered.
2. **Cover the contractor flank.** Confirm that S-EXT exists with a direct, attestation, or contractual mechanism for each contractor class the organization uses. Grep the training-package manifest for "contractor" or "other persons" — if absent, the package fails a core Article 4 obligation.
3. **Literacy objectives map back to measurable behaviors.** For each of the seven objectives, point at the assessment that measures it. If an objective exists in Section 2.2 but has no corresponding assessment in Section 2.5, it is unmeasured and the package fails.
4. **Content ties to the policy stack, not to the Act.** Modules should refer to the organization's AUP, SOP, and incident path by name and version, not to Act article numbers. If a module reads like a law-school lecture, that is a fail (the Act is the *reason*, not the *content*).
5. **System inventory is current.** Every system in Section 2.3 should have a current owner, risk tier, and covered-population list; retired systems should be marked retired and the training content archived with rationale.
6. **Evidence items exist and are owned.** Walk Section 2.7 top to bottom and confirm every evidence item has a named owner (role, not person), a form, and a retention value. Missing retention or missing owner is a fail.
7. **Refresh cadence names concrete triggers.** Section 2.8 should list specific triggers (new system, policy redline, config change, incident). "Periodic refresher" without triggers is a fail.
8. **`org-specific` markers are present where claims are not verifiable from local exercise context.** Unmarked quoted numbers (specific national transposition rules, specific retention periods, specific works-council consultation steps) are a hard fail.
9. **`verify-with-sme` markers are present where legal precision is required but not verifiable here.** The Act text, Article numbers, and MS-specific enforcement arrangements should carry `verify-with-sme` markers if the drafter has not confirmed the published OJ wording.
10. **No invented facts.** No specific vendor product names, no specific fines quoted, no specific case-law citations. The content is procedural and role-grounded; legal citations are kept to the Act article numbers and are explicitly flagged for verification.

## 4. Rubric / review checklist

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | Article 4 populations covered — staff AND contractors / "other persons on their behalf" | 15 | Contractor track absent, or no attestation / flow-through mechanism. |
| R2 | Role-calibrated segmentation (S-ALL + at least S-OPR, S-BLD, S-ADJ, S-EXT, S-EXEC) with modules keyed to segments | 10 | One-size-fits-all curriculum, or segment map absent. |
| R3 | Literacy objectives are behavioral and each has a corresponding assessment | 10 | Objectives stated but not measured, or assessments measure recall rather than behavior. |
| R4 | In-scope AI system inventory is versioned, owned, and tiered | 10 | Inventory missing, or systems listed without tier / owner. |
| R5 | Content ties to the AUP, SOP, and incident path by name and version | 10 | Content reads as a legal lecture; no pointer to the policy stack. |
| R6 | Operator (sys-specific) and Builder (threat-model) deep-dives present, with Builder track grounded in `owasp-ml-top-10` and `mitre-atlas` | 10 | No operator or builder differentiation, or builder track lacks a threat-model deliverable. |
| R7 | Adjacent-population modules address Article 50 transparency, HR / Annex III sensitivities, and meeting-capture consent at minimum | 5 | Adjacent-population obligations treated as the same as S-ALL. |
| R8 | Evidence package (Section 2.7) lists items with owner, form, and retention | 10 | Evidence package missing, or items lack owner / retention. |
| R9 | Refresh cadence names specific triggers (new system, policy redline, config change, incident) in addition to a periodic refresher | 5 | Only a time-based cadence. |
| R10 | `org-specific` / `verify-with-sme` markers present on unverifiable claims; no invented facts, no vendor product names, no specific fines or case-law quotations | 10 | Unmarked quoted legal specifics, or invented facts. |
| R11 | Links to official sources (`nist-ai-rmf`, `owasp-ml-top-10`, `mitre-atlas`) in the Builder track and governance sections | 5 | No cross-reference to the listed official standards. |

**Pass threshold:** ≥ 80 / 100 and no R1 / R3 / R4 / R8 / R10 fail. R1 (contractor coverage) and R8 (evidence package) are the most common failure modes and the discriminators between training content that *is* an Article 4 measure and training content that *looks like* an Article 4 measure.

## 5. Common mistakes

- **Teaching the Act, not the behavior.** The training content becomes a legal lecture on Article 4 definitions. Staff cannot act on it, and compliance is no better. The solution teaches the three behaviors (recognize an AI system, name the data classes, know the escalation path) and treats the Act as the rationale for the training, not the content of it.
- **Omitting contractors and "other persons on their behalf."** The text of Article 4 is explicit about this flank. A training package that only covers employees misses the majority of the risk surface in most mid-size organizations that outsource support, managed services, and embedded engineering.
- **One module for everyone.** "Sufficient" is role-calibrated by the plain text of Article 4; an undifferentiated 30-minute module treats a help-desk operator and an executive sponsor identically, which satisfies the text in form only.
- **No evidence package.** The organization has run a training but cannot answer "who completed what, when, and under what version." A regulator or auditor question on this is unanswerable; the measures are not evidenced.
- **Invented regulatory specifics.** Learners sometimes quote a fine amount, a specific enforcement date, or a particular member-state's supervisory practice. These change by jurisdiction and over time. The solution carries `verify-with-sme` markers; unmarked quotes are a hard fail.
- **Confusing provider and deployer.** Several obligations that look like deployer obligations are actually provider obligations (and vice versa for GPAI systems and high-risk systems). The archetype is explicit (deployer); a learner who mixes in provider-side obligations without naming the switch will fail the audit test.
- **Skipping the HR / Annex III flank.** HR-adjacent AI use is a common Annex III high-risk-system scope item. A training package that treats sys-05 as the same as sys-01 can create unresolved obligations the training itself is now evidence of. The solution carries sys-05 with explicit flagging and an `org-specific` marker to force a legal review.
- **Skipping Article 50 transparency.** Customer-facing chatbots are the most common place Article 50 interacts with front-line training. A customer-service module that does not teach the "you are interacting with an AI" disclosure undermines compliance even if the UI itself carries the label.
- **Conflating AI literacy training with security awareness training.** They overlap but are not the same. Security awareness covers phishing, credentials, and incident reporting. AI literacy additionally covers hallucination, prompt injection, data-class recognition in prompts, and the AI-tool-specific escalation path. The content package does not substitute for either; the two reinforce each other.
- **No refresh trigger.** Annual refreshers alone are insufficient because the AI system inventory changes between cycles. A new system or a material reconfiguration must trigger a refresher within the segment that touches it.

### 5.1 Stretch — mapping into the broader program

For the next cycle, this training content package should link into:

- **`mod-103 exercise-01` (AUP)** — the AUP's data-classification language is the authoritative source for Module 2. When the AUP is redlined, Module 2 re-ships. The AUP's "co-authored with governance" discipline (see mod-103 overview) carries through to the training content's co-sign list.
- **`mod-103 exercise-02` (Data-handling SOP)** — the SOP's step-by-step handling of masked / synthetic test data is the authoritative source for the Module 2 behaviors.
- **`mod-104 exercise-02` (Foundational curriculum)** — the Article 4 content package is a *superset* of the foundational curriculum, not a parallel track. Share modules where possible; segment only where Article 4 requires.
- **`mod-104 exercise-07` (L&D partnership contract)** — the L&D partnership owns the delivery and evidence operations.
- **`mod-105 exercise-01` (Champion network)** — champions are an obvious S-OPR cohort and act as first-line triage for Module 4 (escalation).
- **`mod-106 exercise-03` (Executive scorecard)** — training reach and completion are scorecard metrics; the evidence package feeds the scorecard directly.
- **`mod-109` (Incident response)** — Module 4 uses the incident-response path as its named channel for one of the three events.

## 6. References

- **Learning material (local):**
  - [mod-103 — Policy Co-authoring with Governance](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-103-policy-co-authoring-with-governance) — the AUP, SOP, and intake artifacts the training content is built on top of.
  - [mod-104 — Training Programs and AI Literacy Curriculum](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-104-training-programs-and-ai-literacy-curriculum) — the base curriculum discipline; this Article-4 package is a specialization.
  - [mod-105 — Champion Networks and Change Management](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-105-champion-networks-and-change-management) — champions as first-line S-OPR and escalation triage.
  - [mod-106 — Outcome Measurement and Executive Reporting](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-106-outcome-measurement-and-executive-reporting) — completion telemetry feeds the executive scorecard.
  - [mod-109 — AI Incident Response and Enablement-Side Rollback](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-109-ai-incident-response-and-enablement-side-rollback) — the escalation path that Module 4 teaches.
- **Official standards and frameworks:**
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — the MEASURE and MANAGE functions frame the operator and builder tracks; GOVERN frames the refresh cadence.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — the threat taxonomy used in Module 7-bld.
  - [MITRE ATLAS](https://atlas.mitre.org/) — the adversarial-technique vocabulary used alongside OWASP in Module 7-bld and in the Builder track's threat-model artifact.
- **Regulation (verify the published OJ text before citing):** Regulation (EU) 2024/1689 (the EU AI Act), Articles 3, 4, 50, and Annex III. <!-- verify-with-sme: confirm final article numbers and wording against the published OJ L series text; drafting-stage numbering may differ from the final publication. -->
