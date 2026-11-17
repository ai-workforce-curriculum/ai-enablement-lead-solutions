## Exercise 04 — Industry-Adjusted Policy Package — Reference Solution

> Module: `mod-108-industry-and-regulatory-flavours-of-enablement`
> Exercise type: design / worked example (industry-overlay policy package)
> Exercise brief: [`lessons/mod-108-industry-and-regulatory-flavours-of-enablement/exercises/exercise-04-industry-adjusted-policy-package.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-108-industry-and-regulatory-flavours-of-enablement/exercises/exercise-04-industry-adjusted-policy-package.md) (in the learning repo)

## 1. Solution overview

The deliverable is an **industry-adjusted policy package** — the four artifacts produced in `mod-103` (AUP, data-handling SOP, intake questionnaire, governance-council pre-read) *redlined* against the regulatory and operational realities of a specific regulated industry. The point of this exercise is *not* to rewrite the policy package from scratch; the baseline is already drafted, redlined, and co-signed. The point is to produce a disciplined **overlay** that adds, scopes, or re-tiers specific sections where the industry context demands it, and to make the overlay auditable — the reviewer can see exactly what changed, why, and under which regulatory authority.

The archetype carried through this solution is a **US regional not-for-profit health system, ~10,000 employees, ~900 providers, HIPAA Covered Entity**, rolling out an **ambient-scribe** AI tool for clinician documentation and a **general-purpose AI assistant** for non-clinical staff. The archetype continues from `mod-108 exercise-02` to keep the module cohesive. <!-- org-specific: swap the archetype for the learner's actual industry; retain the overlay-and-diff shape. -->

Posture checks this solution encodes:

- **Overlays, not rewrites.** The industry-adjusted artifact is the baseline *plus a diff*. A learner who rewrites the AUP from scratch has lost the mod-103 posture (co-authored with governance, concrete over comprehensive, co-author tags) and has produced a second artifact that will drift from the first.
- **Every overlay is grounded in a named regulation, accreditation body, or clinical standard — not in "industry feel."** "Clinicians don't like this" is not a basis for an overlay; "45 CFR 164.308(a)(5) requires security awareness training for workforce members with access to ePHI, so Module 2 of the curriculum is mapped to that standard" is.
- **Overlays carry a sign-off column.** An overlay section lists which governance counterpart signs the change (Compliance / Privacy Officer / OGC / CMIO / Quality & Patient Safety). The DACI shape from `mod-108 exercise-03` governs.
- **Diff discipline.** The artifact uses explicit "ADD" / "AMEND" / "RESCOPE" / "RECLASSIFY" tags against baseline section numbers so a reviewer can walk the overlay against the baseline in one pass.
- **Conflict-with-baseline rule.** Where the overlay conflicts with the baseline (e.g., an overlay prohibition is stricter than a baseline approved use), the overlay wins **within the industry scope of the organization**; the baseline AUP's "overlay wins" rule must be stated so no reader is left guessing.
- **Evidence package is extended, not duplicated.** The baseline training-evidence duty (per `mod-108 exercise-01`) is extended to carry HIPAA workforce-training evidence (45 CFR 164.530(b)) and Security-Rule awareness-training evidence (45 CFR 164.308(a)(5)). The extension is one row, not a parallel package.
- **No invented regulatory specifics.** CFR citations, accreditation standards, and state-privacy-statute references are flagged `<!-- verify-with-sme: ... -->` where the drafter has not confirmed with Compliance / OGC; organization-specific choices (de-identification method, consent model, state(s) of operation) are flagged `<!-- org-specific: ... -->`.

## 2. Implementation — worked answer — the industry-adjusted policy package

### 2.1 Package manifest (`industry-adjusted-policy-package.md`)

```
Industry-adjusted policy package — v0.1-draft
Archetype:                 US regional health system, HIPAA Covered Entity
Baseline (per mod-103):    AUP (exercise-01), Data-handling SOP (exercise-02),
                            Intake questionnaire (exercise-03), Council pre-read (exercise-04)
Governing regulations:     HIPAA Privacy Rule (45 CFR 160, 164 Subparts A, E)
                            HIPAA Security Rule (45 CFR 164 Subpart C)
                            42 CFR Part 2 (where SUD-program records are handled)
                            Applicable state privacy / confidentiality statutes
                            <!-- org-specific: list each state of operation and its overlay -->
Accreditation context:     <!-- org-specific: Joint Commission or DNV; name the specific manual chapters
                           the AI-touching workflows intersect (IM for information management, RC for
                           record of care) -->
FDA posture:               No in-scope AI system is 510(k)-cleared SaMD in this archetype;
                           Regulatory Affairs is the routing point for any future SaMD question.
                           <!-- org-specific: confirm; if an in-scope tool IS SaMD, this package
                           is not sufficient and a separate FDA-flavour overlay is required. -->
Owners:                    AI Enablement Lead (co-author); Chief Compliance Officer (approver);
                            Office of the General Counsel (approver); HIPAA Privacy Officer (approver);
                            Chief Medical Officer or delegate (approver on clinical sections);
                            CISO delegate (approver on control-surface sections).
Effective:                 <!-- org-specific: effective date -->
Diff legend:               ADD = new section; AMEND = redlined existing section;
                            RESCOPE = narrower or broader applicability; RECLASSIFY = tier change;
                            RECITE = unchanged from baseline, carried for reader convenience.
Overlay-wins rule:         Where the industry overlay conflicts with the baseline policy within the scope
                            of this organization's industry operations, the overlay wins.
```

### 2.2 AUP overlay (against `mod-103 exercise-01` baseline)

Walk against baseline AUP Sections 1–7. Changes are explicit; silent unchanged sections are not re-drafted here.

#### Overlay to AUP Section 1 — Scope and in-scope users

**Diff tag:** AMEND

**Baseline statement (summary):** The AUP applies to the Enterprise tenant of the AI assistant across all production and sandbox environments, for all employees and contractors.

**Overlay:**

- **AMEND** — Extend "in-scope users" to explicitly include medical staff who are not employees (independent attending physicians, residents and fellows per the GME office, and credentialed allied-health professionals). Medical staff under hospital credentialing are bound by the AUP by virtue of their medical-staff bylaws attachment. <!-- verify-with-sme: confirm that the medical-staff bylaws reference the AUP and vice versa. -->
- **AMEND** — Extend "in-scope users" to explicitly include students (medical, nursing, allied-health) under academic affiliation agreements. Student acceptable-use is governed by both the AUP and the affiliation agreement.
- **ADD** — Scope of jurisdictions: the organization operates in `<!-- org-specific: list states -->`. State-privacy overlays (e.g., CA CMIA, WA My Health My Data Act where applicable) apply in addition to HIPAA. <!-- verify-with-sme: confirm applicable state-privacy statutes and their interaction with AI-tool use. -->

**Sign-off column:** Chief Compliance Officer (A), HIPAA Privacy Officer (A), OGC (A for medical-staff and affiliation-agreement cross-references), AI Enablement Lead (D — drafter).

#### Overlay to AUP Section 2 — Approved uses

**Diff tag:** AMEND / RESCOPE

**Baseline statement (summary):** The tool is approved for named operational uses — drafting, summarization, format conversion, boilerplate code generation, test drafting, reading-code explanation — with review before commit.

**Overlay:**

- **AMEND** — For the ambient-scribe system (sys-04 per `mod-108 exercise-01` inventory): approved use is *drafting* of the clinical note; the clinician remains responsible for the note content under medical-staff bylaws and for signing the note before it is finalized in the medical record. "Approved" means the clinician may use the scribe-produced draft as the starting point; it does *not* mean the clinician may sign a scribe-produced note without reading it. Signing an unread note is a documentation-integrity and medical-legal issue that sits outside this policy, but the AUP names it here to remove ambiguity.
- **AMEND** — For the general-purpose AI assistant, approved administrative uses include: drafting non-clinical communications (internal memos, policy summaries where the policy is public-facing or already shared), format conversion for non-PHI documents, and brainstorming on non-clinical operational problems.
- **RESCOPE** — De-identified clinical narrative is **not** an approved input to a general-purpose AI assistant unless the de-identification meets the HIPAA Safe Harbor standard (45 CFR 164.514(b)(2)) or an Expert Determination standard (45 CFR 164.514(b)(1)); re-identification risk from narrative data is non-trivial, and the baseline AUP's "if-in-doubt — do not use" default governs. <!-- org-specific: confirm which de-identification method the organization uses and how the SOP (Section 2.3) operationalizes it. -->
- **ADD** — Peer-reviewed literature synthesis and public-guideline summarization (e.g., summarize a public CDC clinical guideline for discussion): approved, provided the output is not pasted into the patient record without clinician authorship and review.

**Sign-off column:** Chief Compliance Officer (A), HIPAA Privacy Officer (A), Chief Medical Officer or delegate (A for clinical-use amendments), AI Enablement Lead (D).

#### Overlay to AUP Section 3 — Prohibited uses

**Diff tag:** AMEND / ADD

**Baseline statement (summary):** No customer PII in prompts; no non-public data; no model-risk-managed decision path without the governance review; no external publication without review; no employment decisions; no filter / DLP tampering.

**Overlay:**

- **AMEND** — Replace "customer PII" with "Protected Health Information (PHI) as defined in 45 CFR 160.103," enumerated with the 18 HIPAA identifiers. PHI is prohibited as an input to any AI tool that does not sit under a Business Associate Agreement (BAA) with the organization. Tools without a BAA are prohibited from receiving PHI inputs, period — including "just to test."
- **ADD** — Any audio, video, or image capture of a patient encounter is prohibited as an input to any AI tool except the organization's approved ambient-scribe system (sys-04) under its documented consent process. Personal-device recording of clinical encounters for input to a personal-account AI tool is a terminable offense.
- **ADD** — Any attempt to use the general-purpose AI assistant for clinical decision-support (diagnosis, treatment recommendation, prognosis, triage) is prohibited. The general-purpose assistant is not approved for clinical decision-making regardless of how the clinician frames the prompt. Clinical decision-support is a separate regulatory lane (potentially SaMD) and requires its own intake, review, and approval under `mod-108 exercise-03` governance rows.
- **ADD** — 42 CFR Part 2 records (substance-use-disorder treatment records from a Part 2 program) are prohibited from AI tool inputs even where the AI tool is HIPAA-compliant under a BAA, unless a Part 2-qualifying consent is in place. The interaction between Part 2 and general HIPAA is strict; the AUP names the question and routes it to the HIPAA Privacy Officer. <!-- verify-with-sme: confirm whether the organization operates a Part 2 program and the specific disclosure-consent process. -->
- **ADD** — No AI tool is approved for employment decisions in a clinical-privilege context, including credentialing decisions, peer-review determinations, and medical-staff-office disciplinary processes. Clinical privilege determinations carry due-process obligations under medical-staff bylaws and state law that AI-tool use would not satisfy.
- **AMEND** — The baseline prohibition on disabling / bypassing content filters and DLP extends to any ambient-scribe microphone-muting or consent-dialog bypass. Reconfiguration is a change-request routed through Security.

**Sign-off column:** Chief Compliance Officer (A), HIPAA Privacy Officer (A), Chief Medical Officer or delegate (A), OGC (A on medical-staff-bylaws interactions), CISO delegate (A on control-surface items), AI Enablement Lead (D).

#### Overlay to AUP Section 4 — Data classes

**Diff tag:** AMEND / RECLASSIFY

**Baseline statement (summary):** A four-tier data-classification scheme: Public / Internal / Restricted / Regulated.

**Overlay:**

- **AMEND** — Define "Regulated" explicitly to include: PHI (HIPAA), 42 CFR Part 2 SUD records, information covered by the Clinical Laboratory Improvement Amendments (CLIA) handling restrictions, information under state-law confidentiality overlays (e.g., CMIA, state mental-health statutes). <!-- verify-with-sme: confirm each state overlay. -->
- **RECLASSIFY** — Clinical photos (dermatology, wound care, ophthalmology, radiology-adjacent clinical images): reclassify from "Restricted" to "Regulated" because clinical images are PHI under the HIPAA identifiers list.
- **RECLASSIFY** — Clinician-authored notes marked "draft" in the EHR are still Regulated. "Draft" status does not change HIPAA scope.
- **ADD** — "De-identified" data: separate tier under Restricted (not Regulated) if the de-identification has been performed under Safe Harbor or Expert Determination and the method is documented. "Pseudo-anonymized" or "minimally-redacted" narrative that does not meet the Safe Harbor standard remains Regulated. The SOP (`mod-103 exercise-02` overlay, below) names the method.

**Sign-off column:** HIPAA Privacy Officer (A), Chief Compliance Officer (A), AI Enablement Lead (D).

#### Overlay to AUP Section 5 — If-in-doubt default

**Diff tag:** RECITE / AMEND

**Overlay:**

- **RECITE** — The baseline "if-in-doubt — do not use" default is unchanged and remains load-bearing.
- **AMEND** — Add a clinical corollary: "If in doubt in a clinical encounter, do not pause the clinical encounter to resolve the AI question — resolve the clinical encounter first, then resolve the AI question with the Enablement office or the Privacy Officer offline." A clinician should never divert attention from a patient to answer an AI-policy question in real time.

**Sign-off column:** Chief Medical Officer or delegate (A), AI Enablement Lead (D).

#### Overlay to AUP Section 6 — Escalation channels

**Diff tag:** AMEND / ADD

**Baseline statement (summary):** Three escalation channels — policy, accident, security.

**Overlay:**

- **AMEND** — Replace "accident" with two distinct channels: (a) **AI-tool operational accident** (wrong output used in a non-clinical process) → routes to the AI Enablement Lead's mailbox for triage per `mod-109`; (b) **Patient-safety event involving AI** (an AI-touching output contributed to or could have contributed to patient harm) → routes to the patient-safety event-reporting system that already governs clinical adverse events. A patient-safety event routed to the Enablement mailbox is a mis-route; the Enablement Lead's job is to forward it to patient-safety and preserve the context.
- **ADD** — HIPAA breach suspicion → routes to the HIPAA Privacy Officer within the organization's HIPAA breach-notification timeline (`<!-- verify-with-sme: confirm internal timeline; HIPAA's 60-day external breach-notification clock is well-known but internal triage timelines are organization-specific -->`).
- **ADD** — FDA / state-health-department inquiry about an AI tool → routes to OGC immediately; the Enablement Lead does not respond directly.

**Sign-off column:** Chief Compliance Officer (A), HIPAA Privacy Officer (A), Quality & Patient Safety (A for patient-safety channel), OGC (A for regulatory-inquiry channel), CISO delegate (A on security-incident channel), AI Enablement Lead (D).

#### Overlay to AUP Section 7 — Co-author tags and signatures

**Diff tag:** AMEND

**Overlay:**

- **AMEND** — Extend the baseline co-author tag block (drafter, redliner, security signer, privacy signer, legal signer) with: HIPAA Privacy Officer, Chief Medical Officer or delegate (clinical sections), Quality & Patient Safety (sections that touch the event-reporting flank). Each overlay section lists the extended co-author tag in its own sign-off column; the AUP as a whole carries the superset.

**Sign-off column:** All co-signers.

### 2.3 Data-handling SOP overlay (against `mod-103 exercise-02` baseline)

The SOP baseline is a step-by-step procedure for handling data classes in prompts. The overlay adds clinical-specific procedures and names the method for the Section-4 de-identification question raised in the AUP overlay.

#### Overlay to SOP Section A — Data handling by class

**Diff tag:** AMEND / ADD

- **AMEND** — "Regulated" class handling includes PHI handling steps: (1) confirm BAA status of the tool receiving the input; (2) confirm the tool is in the current AI-tools inventory and is approved for PHI handling; (3) if approved, follow the tool-specific PHI-handling procedure (e.g., ambient-scribe follows the consent-and-retention flow; general-purpose assistant with PHI-handling guardrail configuration follows its documented procedure); (4) do not apply the general-purpose assistant's handling to a PHI input outside the guardrail configuration.
- **ADD** — De-identification method: the organization uses `<!-- org-specific: choose Safe Harbor or Expert Determination and document the choice -->`. Where Safe Harbor is used, the 18 HIPAA identifiers are enumerated and the SOP names the step-by-step redaction procedure, including free-text narrative identifiers. Where Expert Determination is used, the qualified-statistician's methodology is referenced.
- **ADD** — Ambient-scribe audio handling: audio is captured per the organization's documented consent process, retained for `<!-- org-specific: retention window -->`, used only to produce the draft note, and destroyed per the documented retention schedule. Audio does not leave the BAA scope.

#### Overlay to SOP Section B — Who to call when

**Diff tag:** AMEND

- **AMEND** — Add HIPAA Privacy Officer as the authoritative call for PHI questions; add Quality & Patient Safety for patient-safety-event questions. The AI Enablement Lead is not the HIPAA Privacy Officer and is not the patient-safety-event owner.

#### Overlay to SOP Section C — What to do when it goes wrong

**Diff tag:** ADD

- **ADD** — Three incident shapes with specific first-hour actions: (a) PHI accidentally pasted into a non-BAA tool → retrieve, document, notify Privacy Officer; (b) ambient-scribe captured audio when consent had been declined → stop the tool, retrieve the audio, notify Privacy Officer and Quality & Patient Safety; (c) a scribe-produced note was signed without review and contains an error that affected care → the patient-safety event path owns the clinical response; the AI Enablement Lead owns the training and policy response per `mod-109`.

### 2.4 Intake questionnaire overlay (against `mod-103 exercise-03` baseline)

The baseline intake asks: what is the tool, what does it do, which data classes does it touch, which users, which business process, which vendor, what is the commercial posture. The overlay adds clinical-industry fields.

| New / amended field | Required? | Rationale | Routing |
|---|---|---|---|
| Is the tool a SaMD? (FDA Software as a Medical Device classification) | Yes | SaMD is a distinct regulatory lane; even the question routes to Regulatory Affairs. | Regulatory Affairs owns the answer. |
| Does the tool produce a clinical decision-support output? | Yes | CDS has specific regulatory posture (FDA CDS guidance, state-law overlays). | Regulatory Affairs + OGC. |
| Does the tool receive PHI? | Yes | Determines BAA requirement. | HIPAA Privacy Officer owns the BAA status answer. |
| Is a BAA in place? (yes / no / in-negotiation / not-applicable) | Yes | Gate for PHI handling. | HIPAA Privacy Officer + Procurement. |
| Does the tool receive 42 CFR Part 2 records? | Yes | Part 2 is a stricter overlay than HIPAA. | HIPAA Privacy Officer. |
| Does the tool receive clinical images, audio of patient encounters, or video? | Yes | Triggers additional consent and retention steps. | HIPAA Privacy Officer + Quality & Patient Safety. |
| Does the tool make an employment-related determination? (including credentialing / privileging) | Yes | AUP prohibits; intake is also the catch for proposed uses in this class. | OGC + HR Learning. |
| Does the tool interact with patients directly? | Yes | Triggers Article 50-equivalent disclosure obligations even under US framework; also triggers patient-experience and accessibility review. | Patient Experience office + OGC. |
| Which states of patient origination does the tool serve? | Yes | State-law overlays. | HIPAA Privacy Officer + OGC. |
| Does the tool integrate with the EHR? | Yes | Integration posture is non-trivial and triggers IT Security, HIM, and clinical-informatics review. | CISO delegate + CMIO + HIM. |
| Does the tool train on, retain, or share user inputs with the vendor? | Yes | Vendor BAA and DPA must address; secondary-use provisions are negotiated by Procurement + OGC. | Procurement + OGC. |

### 2.5 Council pre-read overlay (against `mod-103 exercise-04` baseline)

The baseline council pre-read is a one-page brief for the governance council covering why the decision, what is being decided, what the options are, what the Enablement Lead recommends, and what the Enablement Lead is asking the council to approve. The overlay adds mandatory clinical-governance sections.

- **ADD — Clinical-quality signal.** Any pre-read on a clinical-adjacent tool includes the clinical-quality signal (sampling rate for scribe-produced notes, review-before-sign rate, time-to-sign delta, documentation-error rate, patient-experience signal if available). Pre-reads that lack this signal for a clinical-adjacent tool are returned unread.
- **ADD — Patient-safety posture.** Named signal from the patient-safety event-reporting system for AI-touching events in the quarter (zero is an acceptable number and should be reported explicitly; absence is not).
- **ADD — Compliance posture.** The HIPAA Privacy Officer and Chief Compliance Officer each sign off that the tool / change under review is within the organization's current compliance posture, with any open items enumerated.
- **AMEND — Risk-appetite framing.** The baseline "risk / benefit" framing is amended to lead with the patient-safety and patient-trust framing; Finance signals are secondary for clinical-adjacent tools.

### 2.6 Evidence package overlay

The baseline evidence duty (per `mod-108 exercise-01` Section 2.7) is extended:

- **ADD** — HIPAA workforce-training records (45 CFR 164.530(b)) — the AI literacy curriculum is the vehicle for the AI-tool-specific portion of HIPAA workforce training; retention per the organization's HIPAA retention schedule (<!-- verify-with-sme: confirm retention period, commonly 6 years post-training per HIPAA documentation retention. -->).
- **ADD** — HIPAA Security-Rule awareness-training records (45 CFR 164.308(a)(5)) — the AI tool security-awareness content is tied to this duty and retained accordingly.
- **ADD** — BAA inventory — cross-reference from the AI tools intake inventory to the central BAA repository; the row is Null if no PHI is received.
- **ADD** — Ambient-scribe consent-adherence audit — periodic sample of encounters to confirm consent was obtained; audit owner is Quality & Patient Safety. <!-- org-specific: confirm audit frequency and sample size with Quality and Compliance. -->
- **ADD** — "Review before sign" audit for ambient-scribe notes — periodic sample; audit owner is HIM in partnership with Quality.

### 2.7 Industry-adjusted change management

- **Refresh cadence trigger (ADD):** a redline of the HIPAA Privacy Officer's guidance, a redline of the organization's HIPAA policies, a new state-privacy statute, a new FDA guidance on CDS or SaMD affecting an in-scope tool, a Joint Commission (or DNV) survey finding relevant to AI documentation, or a ambient-scribe vendor change that affects consent or retention.
- **Refresh cadence trigger (ADD):** a patient-safety event with an AI-touching contributing factor triggers a same-cycle policy refresh, not the periodic cycle.

## 3. Validation steps

1. **The overlay is a diff, not a rewrite.** Walk against the baseline AUP, SOP, intake, and council pre-read and confirm the overlay uses ADD / AMEND / RESCOPE / RECLASSIFY / RECITE tags against baseline section numbers. A standalone rewrite fails this criterion.
2. **Every overlay section carries a sign-off column** naming the specific governance counterpart(s). The AI Enablement Lead is Drafter, never Approver, on overlay rows.
3. **PHI is defined by regulation, not by colloquialism.** The AUP Section 3 overlay should explicitly define PHI by 45 CFR 160.103 and the 18-identifier list (not "patient info" or similar). <!-- verify-with-sme: confirm the enumerated-identifier list is current. -->
4. **BAA posture is a gate, not a nice-to-have.** The intake questionnaire overlay includes a BAA-status field, and the AUP Section 3 overlay prohibits PHI input to non-BAA tools. Absence of this gate is a hard fail — it is the single most important industry overlay.
5. **42 CFR Part 2 is addressed, not skipped.** If the organization operates or receives records from an SUD program, the Part 2 overlay is present; if it does not, the overlay explicitly states so. Silence on Part 2 is a fail — it is often the forgotten overlay.
6. **Clinical adverse-event routing is a distinct channel from "AI-tool operational accident."** The AUP Section 6 overlay separates them; if the overlay collapses them into one channel, clinical-safety events may be mis-routed to the Enablement mailbox.
7. **Ambient-scribe audio handling is named.** Audio capture, consent, retention, destruction, and BAA scope are explicit. Absence is a fail.
8. **Employment-decision prohibition is extended to credentialing / privileging.** This is an industry-specific extension that is easy to miss; a general "no employment decisions" overlay is insufficient without the medical-staff cross-reference.
9. **De-identification method is named, not described abstractly.** Safe Harbor vs. Expert Determination is a binary, and the overlay names the choice (even if `<!-- org-specific: ... -->`).
10. **No invented regulatory specifics.** CFR citations carry `<!-- verify-with-sme: ... -->` where the drafter has not confirmed with Compliance / OGC; state-privacy statutes carry `<!-- org-specific: ... -->`; FDA posture is routed to Regulatory Affairs, not answered by the Enablement Lead.
11. **Overlay-wins rule is stated explicitly.** Readers of the industry-adjusted artifact should not be guessing which document governs when the two conflict.
12. **The evidence-package overlay extends, not duplicates, the baseline.** A separate HIPAA-training-records tracker that does not cross-reference the baseline evidence package is a drift risk.

## 4. Rubric / review checklist

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | Overlay is a diff against named baseline sections with explicit tags (ADD / AMEND / RESCOPE / RECLASSIFY / RECITE) | 10 | Standalone rewrite with no diff discipline. |
| R2 | Each overlay section carries a sign-off column naming specific governance counterparts; Enablement is Drafter, not Approver | 10 | Enablement listed as Approver, or sign-off columns absent. |
| R3 | PHI is defined by 45 CFR 160.103 and the 18 identifiers; prohibited as input to non-BAA tools | 15 | Colloquial "patient info" definition, or missing BAA gate. |
| R4 | Ambient-scribe audio handling is explicit (capture / consent / retention / destruction / BAA scope) | 10 | Any of the four missing. |
| R5 | 42 CFR Part 2 is addressed (either applicable with Part-2-consent language, or explicitly not applicable with rationale) | 5 | Silent on Part 2. |
| R6 | Clinical-adverse-event path is distinct from AI-tool operational-accident path | 10 | Collapsed into one channel. |
| R7 | Employment-decision prohibition extends to credentialing / privileging with medical-staff-bylaws cross-reference | 5 | Generic "no employment decisions" with no bylaws cross-reference. |
| R8 | De-identification method is named (Safe Harbor / Expert Determination / org-specific choice) | 5 | Method unspecified. |
| R9 | Intake questionnaire overlay includes SaMD, CDS, BAA, Part 2, audio/video capture, EHR integration, and vendor training/retention fields | 10 | Fewer than five of the seven. |
| R10 | Council pre-read overlay includes clinical-quality signal, patient-safety posture, compliance posture, and patient-safety-first risk framing | 5 | Pre-read overlay missing clinical-quality or patient-safety signal. |
| R11 | Evidence-package overlay extends the baseline (HIPAA training, BAA inventory, consent-adherence audit, review-before-sign audit) | 10 | Standalone / duplicate evidence tracker, or missing ≥ 2 extensions. |
| R12 | `org-specific` and `verify-with-sme` markers on CFR citations, state-law overlays, retention periods, and FDA / SaMD claims | 5 | Unmarked quoted regulatory specifics. |

**Pass threshold:** ≥ 85 / 100 and no R3 / R4 / R6 / R11 fail. R3 (PHI / BAA), R4 (ambient-scribe audio), R6 (clinical-safety routing), and R11 (evidence overlay) are the discriminators between a package that will hold in a HIPAA or Joint Commission / DNV review and one that will not.

## 5. Common mistakes

- **Rewriting the baseline instead of overlaying it.** The baseline was co-signed by governance partners who will not re-sign a standalone rewrite — they will ask for a diff. A learner who rewrites loses the co-sign history and introduces a second artifact that will drift from the first.
- **Treating PHI colloquially.** "Patient information" is not a regulatory term; 45 CFR 160.103's PHI definition is. An AUP that prohibits "patient info" without the enumerated-identifier list will be redlined by the HIPAA Privacy Officer on first read.
- **Skipping the BAA gate.** Of all the overlays, the BAA gate is the single most important; it is the practical control that keeps PHI out of tools that are not legally permitted to receive it. A learner who adds "no PHI in AI tools" without the BAA exception makes the ambient-scribe deployment illegal under their own policy.
- **Collapsing clinical adverse events into the AI-tool mailbox.** The patient-safety event-reporting system is the authoritative clinical-safety channel; an AI-touching adverse event is *also* a clinical adverse event and must route through that system. Collapsing the channels mis-routes the event and loses the patient-safety-office's authority over the response.
- **Omitting 42 CFR Part 2.** Most US health systems touch Part 2 somewhere; ignoring it because the Enablement Lead's own workflow does not expose them to it is unsafe. The overlay addresses Part 2 explicitly either way.
- **Addressing ambient-scribe capture but not retention and destruction.** Consent is the obvious step; retention and destruction are what carry the long-term risk. An overlay that has consent language but no retention schedule has a slow-burning compliance exposure.
- **Confusing "de-identified" with "pseudo-anonymized."** HIPAA has a specific de-identification standard (Safe Harbor or Expert Determination); informal redaction is not the same thing and is not sufficient for the AUP's Approved-Uses column.
- **Writing the clinical overlay without CMO / Chief Nursing sign-off.** Overlays that redline clinical workflow without clinical signatures will not survive first review by the Medical Executive Committee.
- **Assuming the general-purpose AI assistant is safe for clinical decision-support "as long as the clinician verifies."** The regulatory lane for CDS (FDA, state) is distinct, and the enablement overlay prohibits use regardless of clinician intention. A learner who writes "approved for clinical decision-support with human review" has mis-scoped the tool's regulatory posture.
- **Inventing CFR subsection numbers.** Learners sometimes quote "45 CFR 164.502(j)(iv)" or similar at a level of specificity that drifts from the actual regulation. The overlay flags unverified citations with `<!-- verify-with-sme: ... -->`.
- **Missing the medical-staff-bylaws cross-reference.** Independent attending physicians, residents, and credentialed allied-health professionals are bound by the AUP via medical-staff bylaws, not via the employment agreement. Overlooking this leaves a large population out of scope on paper.

### 5.1 Stretch — overlay against a second industry

For readers in a different industry, the same overlay shape applies with different sign-off counterparts and different regulatory authorities. A one-page crosswalk:

| Overlay target | US health system (archetype) | US bank / investment-bank group | Life sciences / pharma | US federal contractor |
|---|---|---|---|---|
| Primary data-class overlay | PHI (HIPAA) | Non-public financial / customer data + MRM scope | 21 CFR Part 11 electronic records + GxP data | CUI (NIST SP 800-171 / CMMC) |
| Gate control | BAA | SR 11-7 MRM review | 21 CFR Part 11 compliance + validation | FedRAMP / CMMC + contracting-office sign-off |
| Clinical / regulated-use prohibition | Clinical decision-support without separate lane | Trading / lending / AML / sanctions path without MRM review | GxP workflow without validated system | Classified-information handling under any circumstance |
| Primary external reporter | HIPAA Privacy Officer (breach) | Chief Compliance Officer (regulatory) | VP Quality / QA (deviation) | Contracting officer (incident report) |
| Evidence duty | HIPAA workforce training (45 CFR 164.530(b)) | FFIEC/FINRA training as applicable | 21 CFR Part 11 training; GxP training | CMMC awareness training; CUI handling training |

Running the overlay against a second industry is the fastest way to internalize which overlay sections are structural (BAA / gate / sign-off column) and which are regulation-specific (PHI definition / Part 2 / 21 CFR Part 11 / CUI). The structural sections are portable; the regulation-specific sections are re-authored.

## 6. References

- **Learning material (local):**
  - [mod-103 — Policy Co-authoring with Governance](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-103-policy-co-authoring-with-governance) — the baseline AUP, SOP, intake, and council pre-read the overlay sits against.
  - [mod-108 exercise-01](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-108-industry-and-regulatory-flavours-of-enablement/exercises/exercise-01-eu-ai-act-article-4-training-content-drill.md) — the training content package and evidence-package pattern the overlay extends.
  - [mod-108 exercise-02](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-108-industry-and-regulatory-flavours-of-enablement/exercises/exercise-02-industry-posting-to-enablement-obligation-map.md) — the health-system archetype carried through from the posting map.
  - [mod-108 exercise-03](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-108-industry-and-regulatory-flavours-of-enablement/exercises/exercise-03-enablement-vs-governance-responsibility-split-in-industry.md) — the DACI that governs the sign-off columns in this overlay.
  - [mod-109 — AI Incident Response and Enablement-Side Rollback](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-109-ai-incident-response-and-enablement-side-rollback) — the incident path the SOP overlay routes to.
- **Official standards and frameworks:**
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — GOVERN / MEASURE functions underpin the overlay's governance structure.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — threat taxonomy referenced in the CISO sign-off column.
  - [MITRE ATLAS](https://atlas.mitre.org/) — adversarial-technique vocabulary for Security-partnered review.
- **US healthcare regulatory references (verify exact citation and current applicability before relying on):** HIPAA Privacy Rule (45 CFR 160, 164 Subpart E, including workforce training at 164.530(b), de-identification at 164.514), HIPAA Security Rule (45 CFR 164 Subpart C, awareness training at 164.308(a)(5)), 42 CFR Part 2 where applicable, applicable state privacy statutes (CMIA, WA My Health My Data Act, etc.), FDA CDS and SaMD guidance where in-scope. <!-- verify-with-sme: re-confirm citations and current applicability before publishing any artifact derived from this overlay. -->
