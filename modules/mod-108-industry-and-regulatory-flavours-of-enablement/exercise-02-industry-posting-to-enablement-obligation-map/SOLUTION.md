## Exercise 02 — Industry Posting to Enablement Obligation Map — Reference Solution

> Module: `mod-108-industry-and-regulatory-flavours-of-enablement`
> Exercise type: analysis / mapping artifact
> Exercise brief: [`lessons/mod-108-industry-and-regulatory-flavours-of-enablement/exercises/exercise-02-industry-posting-to-enablement-obligation-map.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-108-industry-and-regulatory-flavours-of-enablement/exercises/exercise-02-industry-posting-to-enablement-obligation-map.md) (in the learning repo)

## 1. Solution overview

The deliverable is a **mapping artifact**: take a real-world industry **posting** — a public job posting for an AI Enablement Lead (or equivalent) role at an organization in a specific regulated industry — and decompose each stated responsibility, requirement, and expectation into the concrete **enablement obligations** that follow if the role were taken. The output is a structured map the learner can read end-to-end before their first interview, use during onboarding, and consult across their first ninety days to surface the un-stated obligations the posting implied but did not spell out.

The archetype carried through this solution is a **representative, composite posting for an "AI Enablement & Adoption Lead" role at a US regional hospital network**, approximately 10,000 employees across clinical and non-clinical roles, with a stated mandate to safely roll out ambient-scribe and clinical-summarization AI tools. The composite is explicitly composite — not quoted from a specific employer — to avoid making claims about a real organization. <!-- org-specific: swap the archetype for the actual posting the learner is mapping; retain the mapping shape. -->

Posture checks this solution encodes:

- **Every line of posting text gets mapped.** The common failure mode is to map the obviously operational lines ("stand up the training program," "liaise with Legal") and skip the vague lines ("foster a culture of responsible AI"). The vague lines carry the most un-stated obligations.
- **Each obligation is tied to one or more owner-functions** — the enablement lead, but also HR, Legal, Clinical Informatics, Compliance, Security, Procurement, Finance. The mapping names who the enablement lead must partner with, not just what the enablement lead must do.
- **Obligations are scored by `evidence-of-fulfilment` form.** An obligation that cannot be evidenced cannot be managed. Each obligation is paired with the artifact that would prove it is being met.
- **Industry-specific obligations are called out explicitly.** For a US health system, HIPAA Privacy / Security Rule workforce-training duties are additive to the baseline enablement work; a ~90-day Day-One-to-Day-90 plan that ignores them is not safe.
- **The mapping names what the posting does NOT say** and is explicit about what the learner must ask in interview or onboarding to disambiguate. A silent posting is not a safe posting.
- **No specific employer names, no specific vendor names, no fabricated statistics.** The composite posting uses generic placeholders; `<!-- verify-with-sme: ... -->` and `<!-- org-specific: ... -->` markers block auto-merge where real-world variables must be filled in.

## 2. Implementation — worked answer — the mapping artifact

### 2.1 Composite industry posting (input)

The following composite posting is used as the mapping input. It is written in the voice and shape of real-world AI Enablement Lead postings from US health systems — stitched from common language patterns rather than quoted from any specific employer — so the solution can show the mapping end-to-end without misattribution. <!-- org-specific: when the learner maps a real posting, substitute the real text and keep the mapping-table shape below. -->

```
Role:           AI Enablement & Adoption Lead
Organization:   <Regional US not-for-profit health system, ~10,000 employees, ~900 providers>
Reports to:     VP, Clinical Informatics (dotted line to CISO and Chief Compliance Officer)

About the role
We are hiring an AI Enablement & Adoption Lead to drive safe, measurable adoption of
AI tools across our clinical and non-clinical workforce. You will partner with
clinicians, administrators, Compliance, Legal, Privacy, Security, and IT to translate
our AI strategy into on-the-ground behavior change. You will own the AI literacy
program for ~10,000 staff and the change-management program for the ambient-scribe
and clinical-summarization initiatives already underway. You will be the visible face
of responsible AI at our system.

What you will do
1. Build and run the system-wide AI literacy curriculum for both clinical and non-
   clinical staff, including initial onboarding and ongoing refresh training, in
   partnership with HR Learning and the Compliance office.
2. Design and operate the champion network across our hospitals and clinics,
   including nurse informaticists, resident leads, revenue-cycle leads, and
   administrative super-users.
3. Lead the clinician-facing adoption effort for our ambient-scribe deployment,
   including workflow redesign, go-live support, and ongoing coaching.
4. Co-author AI acceptable-use and data-handling policy with the Compliance office
   and Office of the General Counsel, specific to clinical workflows.
5. Build and maintain an AI tools intake and inventory, working with Privacy,
   Security, and Procurement.
6. Produce monthly program dashboards for executive leadership and the AI
   Governance Council. Translate adoption and quality signals into business
   outcomes.
7. Partner with Compliance to ensure HIPAA, 42 CFR Part 2 (where applicable), and
   state privacy obligations are reflected in our training and our usage policies.
8. Represent the system externally at industry forums, in peer convenings, and in
   vendor partnership conversations.
9. Foster a culture of responsible, patient-centric AI across the organization.

What you bring
- 7+ years leading large-scale change management, training, or adoption programs in
  healthcare or a comparable regulated industry.
- Deep comfort with HIPAA, Joint Commission accreditation context, and the
  realities of clinician workflow.
- Experience building partnerships with Compliance, Legal, Privacy, Security, and
  clinical governance committees.
- Strong written and verbal communication, including executive and board-facing.
- A degree in a relevant field; graduate-level training in informatics, public
  health, change management, or a comparable domain preferred.
- Prior experience deploying AI, machine learning, or clinical decision-support
  tools is strongly preferred.
```

### 2.2 Mapping shape

For each line of the posting (numbered as in the posting), the map carries:

- **Posting text** — the quoted line.
- **Stated obligation** — the explicit action the posting names.
- **Implied obligations** — the un-stated obligations that follow once the stated obligation is unpacked against industry context. This is the column that does the work.
- **Owner / partners** — who inside the organization owns the obligation or must be partnered with.
- **Evidence-of-fulfilment artifact** — the concrete deliverable that proves the obligation is being met.
- **Industry-specific flags** — HIPAA / Joint Commission / state-privacy / FDA-SaMD / 42 CFR Part 2 considerations that a non-healthcare enablement lead would not know to carry.
- **First-90-days order** — whether the obligation is in-scope for Day 1–30, 31–60, or 61–90.

### 2.3 The map (`posting-obligation-map.md`)

#### About-the-role framing — "Drive safe, measurable adoption of AI tools across our clinical and non-clinical workforce"

| Field | Value |
|---|---|
| Stated obligation | Operate an adoption program that is both *safe* and *measurable*, across *clinical and non-clinical* populations. |
| Implied obligations | (a) A segment map that distinguishes clinical from non-clinical operators, because the risk profile and the training burden differ; (b) a *measurement* artifact — adoption, fluency, and clinical-quality signals — that feeds the governance council; (c) a safety discipline keyed to both the policy stack and the clinical-adverse-event path (the hospital's existing event-reporting system is the authoritative channel for clinical safety, not an enablement-lead-invented mailbox). |
| Owner / partners | Enablement Lead (D). Clinical Informatics (A, dotted-line sponsor). Quality & Patient Safety (C). Compliance (I). |
| Evidence-of-fulfilment artifact | Segment map (per `mod-104 exercise-01`); monthly adoption + quality scorecard (per `mod-106 exercise-03`, clinical-flavoured). |
| Industry-specific flags | Clinical adverse events must route through the existing patient-safety event system, *not* an enablement-side channel. Mis-routing of a clinical safety event is itself a compliance issue. <!-- verify-with-sme: confirm the specific event-reporting system and Joint Commission expectations at the archetype organization. --> |
| First-90-days order | Days 1–30: inventory existing adoption signals; confirm the patient-safety reporting path is the authoritative clinical channel. |

#### About-the-role framing — "Reports to VP, Clinical Informatics (dotted line to CISO and Chief Compliance Officer)"

| Field | Value |
|---|---|
| Stated obligation | Operate under a dotted-line relationship to both Security and Compliance. |
| Implied obligations | (a) Early establishment of a working cadence with CISO and CCO offices — not "I'll meet them when there's an issue"; (b) clarity on which decisions require which signature; (c) a shared understanding of what crosses the dotted line into a hard line (e.g., an incident, a regulator inquiry, a board-visible event). |
| Owner / partners | Enablement Lead (D). VP Clinical Informatics (A). CISO office (A for security-posture decisions). Chief Compliance Officer (A for compliance-posture decisions). |
| Evidence-of-fulfilment artifact | A one-page working-arrangement note (per the `mod-107 exercise-04` partnership-contract pattern, re-scoped to Clinical Informatics / Security / Compliance) that names the three cadences, the three signatures, and the escalation triggers. |
| Industry-specific flags | In a US hospital system, the Chief Compliance Officer typically owns HIPAA compliance posture; decisions that alter PHI-handling in prompts are CCO-signed, not CISO-signed. <!-- org-specific: confirm compliance-vs-security signature ownership at the specific organization. --> |
| First-90-days order | Days 1–30. Working-arrangement note is drafted in Week 2 and signed by Week 4. |

#### Posting line 1 — "Build and run the system-wide AI literacy curriculum for both clinical and non-clinical staff..."

| Field | Value |
|---|---|
| Stated obligation | Build and operate an AI literacy curriculum, segmented by clinical / non-clinical, with onboarding and refresh components, in partnership with HR Learning and Compliance. |
| Implied obligations | (a) The curriculum must evidence the HIPAA Privacy Rule workforce training duty under 45 CFR 164.530(b) **and** the Security Rule security-awareness duty under 45 CFR 164.308(a)(5) for any training that has an AI-tool-and-PHI component; <!-- verify-with-sme: confirm exact CFR citations and how they apply to AI-tool training at the archetype organization. --> (b) if the EU AI Act Article 4 applies (e.g., if the system contracts with EU-based providers or deployers), the Article 4 obligation is additive (see `mod-108 exercise-01`); (c) clinical content must be reviewed by clinical subject-matter experts, not just L&D; (d) non-clinical content covers revenue cycle, scheduling, and administrative use cases, which have their own data-class considerations. |
| Owner / partners | Enablement Lead (D). HR Learning (A on delivery). Compliance (A on content accuracy for HIPAA and 42 CFR Part 2 flanks). Clinical Informatics (C). Chief Medical Officer or delegate (C for clinical-SME review). |
| Evidence-of-fulfilment artifact | Baseline curriculum outline (per `mod-104 exercise-02`); evidence package (per `mod-108 exercise-01` Section 2.7) with completion telemetry linked to HRIS and credentialing. |
| Industry-specific flags | Credentialed clinicians have CE / CME requirements that interact with mandatory training; a curriculum that cannot provide CE credit may have low completion. <!-- verify-with-sme: confirm whether CE/CME accreditation is in-scope for the AI literacy curriculum. --> |
| First-90-days order | Days 31–60: audit existing HR Learning catalog; align AI literacy modules to existing HIPAA-training cadence. |

#### Posting line 2 — "Design and operate the champion network across our hospitals and clinics..."

| Field | Value |
|---|---|
| Stated obligation | Stand up a champion network across named clinical and administrative populations. |
| Implied obligations | (a) Charter the network with at least three champions per in-scope BU minimum per `mod-105 exercise-01`; (b) build the two-way feedback loop per `mod-105 exercise-02`; (c) credentialed clinicians carry additional professional-conduct expectations — champion recognition frameworks need to respect clinical hierarchy and avoid incentives that might compromise clinical judgment (e.g., no gift-card incentives tied to prescribing behavior); (d) resident / trainee champions carry labor-and-education constraints — their time is covered by residency hours and cannot be allocated without program-director sign-off. |
| Owner / partners | Enablement Lead (D). Chief Nursing Officer (C, nurse-informaticist cohort). Chief Medical Officer / GME office (C, resident cohort). Revenue-cycle leadership (C). |
| Evidence-of-fulfilment artifact | Champion charter (per `mod-105 exercise-01`); recognition framework with explicit clinical-propriety guardrails. |
| Industry-specific flags | Anti-kickback / Stark Law considerations apply to any incentive that could be construed as influencing referrals or prescribing. The recognition framework is reviewed by Compliance. <!-- verify-with-sme: confirm Anti-Kickback / Stark considerations for the specific recognition scheme. --> |
| First-90-days order | Days 31–60: name initial cohort; Days 61–90: first two-way feedback-loop cycle. |

#### Posting line 3 — "Lead the clinician-facing adoption effort for our ambient-scribe deployment..."

| Field | Value |
|---|---|
| Stated obligation | Own the adoption effort for ambient-scribe: workflow redesign, go-live support, ongoing coaching. |
| Implied obligations | (a) Ambient-scribe captures audio during a clinical encounter — patient consent, retention, and PHI-handling controls apply; (b) the generated note enters the patient's medical record, which triggers EHR documentation standards, Joint Commission documentation expectations, and medical-legal retention requirements; (c) a scribe-generated note that is not reviewed by the clinician before signing is a documentation-integrity issue, not just an AI safety issue — the enablement coaching must reinforce the "review before sign" expectation; (d) workflow redesign touches billing and coding workflows, which have their own compliance posture (CPT coding, E/M documentation) that cannot be destabilized by the AI tool. |
| Owner / partners | Enablement Lead (D). Clinical Informatics (A). Chief Medical Officer (C). Chief Nursing Officer (C). Revenue-cycle / coding leadership (A, documentation-integrity). HIM (A, record integrity). Privacy officer (A, patient-consent). |
| Evidence-of-fulfilment artifact | Workflow-redesign artifact per in-scope specialty; go-live support plan; "review before sign" compliance audit sample (post-launch). |
| Industry-specific flags | Patient consent for ambient-scribe capture varies by state and by scope — some states are one-party-consent, some two-party; some systems carry a per-encounter consent process, some a patient-registration-stage consent. The enablement artifact must align to the organization's specific consent model, not invent one. <!-- verify-with-sme: confirm the organization's consent model and applicable state laws. --> |
| First-90-days order | Days 1–30: ride-along with three ambient-scribe users across specialties. Days 31–60: audit of "review before sign" rate. Days 61–90: first targeted coaching intervention based on audit. |

#### Posting line 4 — "Co-author AI acceptable-use and data-handling policy with the Compliance office and Office of the General Counsel, specific to clinical workflows."

| Field | Value |
|---|---|
| Stated obligation | Co-author AUP and data-handling SOP with Compliance and OGC, clinical-workflow-scoped. |
| Implied obligations | (a) The AUP (`mod-103 exercise-01`) must adjust its approved / prohibited uses for clinical realities — e.g., paste of de-identified patient narrative to a general-purpose LLM is prohibited (re-identification risk) even where the baseline AUP would allow it; (b) the data-handling SOP (`mod-103 exercise-02`) must address PHI, de-identification standards (HIPAA Safe Harbor / Expert Determination under 45 CFR 164.514), and the handling of audio from ambient-scribe capture; <!-- verify-with-sme: confirm which de-identification method the organization uses. --> (c) 42 CFR Part 2 obligations apply if any in-scope AI tool touches substance-use-disorder records; (d) state privacy overlays may be stricter than HIPAA. |
| Owner / partners | Enablement Lead (D, drafter). CCO (A). OGC (A). Privacy Officer (A). CISO delegate (C). |
| Evidence-of-fulfilment artifact | Industry-adjusted policy package per `mod-108 exercise-04`. |
| Industry-specific flags | HIPAA Privacy Rule, HIPAA Security Rule, 42 CFR Part 2, applicable state privacy law (e.g., CA CMIA if operating in California). The AUP enumerates each by name and version. |
| First-90-days order | Days 31–60: draft; Days 61–90: walking-redline cycles with CCO and OGC. |

#### Posting line 5 — "Build and maintain an AI tools intake and inventory, working with Privacy, Security, and Procurement."

| Field | Value |
|---|---|
| Stated obligation | Operate an intake and inventory for AI tools, partnered with three functions. |
| Implied obligations | (a) The intake questionnaire (`mod-103 exercise-03`) extends with clinical-use fields: SaMD classification question, clinical-decision-support status, patient-interaction surface, training-data provenance claims; (b) the inventory ties to the Security tool-inventory and to Finance's software cost center so there is one version of truth; (c) for tools that may be SaMD, a 510(k) / FDA posture question is in the intake — the enablement lead is not deciding SaMD status but ensuring the question is routed to Regulatory Affairs; (d) BAA (Business Associate Agreement) posture is a required intake field — tools that will touch PHI require a BAA and the inventory tracks its state. |
| Owner / partners | Enablement Lead (D). Privacy Officer (A). CISO delegate (A on security posture). Procurement (A on commercial posture). Regulatory Affairs (A on SaMD / FDA posture if applicable). |
| Evidence-of-fulfilment artifact | Intake questionnaire with clinical fields (per `mod-103 exercise-03`, industry-adjusted per `mod-108 exercise-04`); inventory record. |
| Industry-specific flags | SaMD (Software as a Medical Device) and the FDA's evolving AI/ML-based SaMD action plan. Any in-scope tool that makes a clinical determination is in a different regulatory lane than enablement; the enablement lead's job is to route, not to classify. <!-- verify-with-sme: confirm the organization's SaMD intake routing process. --> |
| First-90-days order | Days 31–60: build intake; Days 61–90: backfill inventory for existing in-scope tools. |

#### Posting line 6 — "Produce monthly program dashboards for executive leadership and the AI Governance Council."

| Field | Value |
|---|---|
| Stated obligation | Operate the executive scorecard and governance-council reporting. |
| Implied obligations | (a) The scorecard (per `mod-106 exercise-03`) must carry clinical-quality signals alongside adoption and fluency — note-quality sampling rate, time-to-sign, encounter-duration delta, patient-experience signal if available; (b) regulated-industry scorecards carry explicit confidence bands, not point estimates, to avoid overclaiming to the governance council; (c) the scorecard includes training-completion telemetry (HIPAA workforce-training evidence) and intake-pipeline health (inventory freshness). |
| Owner / partners | Enablement Lead (D). Clinical Informatics (A). Quality & Patient Safety (C). Finance (C for cost signals). |
| Evidence-of-fulfilment artifact | Executive scorecard; governance-council pre-read (per `mod-103 exercise-04`). |
| Industry-specific flags | Dashboards that mix adoption signals with clinical-quality signals must not imply causation unless the measurement design supports it. Overclaiming to a governance council in a hospital is a material credibility failure. |
| First-90-days order | Days 1–30: inventory existing signals. Days 61–90: first scorecard shipped. |

#### Posting line 7 — "Partner with Compliance to ensure HIPAA, 42 CFR Part 2 (where applicable), and state privacy obligations are reflected in our training and our usage policies."

| Field | Value |
|---|---|
| Stated obligation | Reflect HIPAA / 42 CFR Part 2 / state-privacy obligations in training and policy. |
| Implied obligations | (a) Mapping of each in-scope obligation to a specific policy section and a specific training module (an obligation-to-artifact map, keyed to the regulation); (b) a change-log that re-ships training when a regulation changes or when a policy section is redlined; (c) a `verify-with-sme` discipline: specific regulatory details the enablement lead cannot verify alone are flagged and routed to Compliance / OGC, not invented in the policy. |
| Owner / partners | Enablement Lead (D). Compliance (A). Privacy Officer (A). OGC (C). |
| Evidence-of-fulfilment artifact | Obligation-to-artifact map; training content package (per `mod-108 exercise-01`); industry-adjusted policy package (per `mod-108 exercise-04`). |
| Industry-specific flags | HIPAA Privacy Rule workforce training (45 CFR 164.530(b)); HIPAA Security Rule awareness training (45 CFR 164.308(a)(5)); 42 CFR Part 2 where the system operates an SUD program or receives records from one; state privacy law overlays. <!-- verify-with-sme: confirm applicable state privacy statutes for each state of operation. --> |
| First-90-days order | Days 31–60: build the obligation-to-artifact map with Compliance. |

#### Posting line 8 — "Represent the system externally at industry forums, in peer convenings, and in vendor partnership conversations."

| Field | Value |
|---|---|
| Stated obligation | External representation — forums, peer convenings, vendor conversations. |
| Implied obligations | (a) Public-speaking commitments require Communications / PR sign-off; (b) vendor-partnership conversations carry Procurement and Legal posture — the enablement lead does not hand-shake commercial terms or disclose non-public strategy; (c) peer convenings (e.g., CHIME, HIMSS, local health-system informatics peer groups) are legitimate information-exchange venues, but any case-study material shared is reviewed by Compliance for PHI, by Communications for brand, and by Legal for IP. |
| Owner / partners | Enablement Lead (D). Communications / PR (A for external speaking). Procurement (A for vendor partnership scoping). Legal (A for IP and disclosure). |
| Evidence-of-fulfilment artifact | External-speaking log; vendor conversation notes with Procurement cc'd. |
| Industry-specific flags | Any external case-study material that could include PHI requires formal de-identification and sign-off. Anecdotes from clinical rounds are not shareable material. <!-- verify-with-sme: confirm the organization's external-communications-approval process. --> |
| First-90-days order | Days 61–90 only; the first 60 days are inward-facing. |

#### Posting line 9 — "Foster a culture of responsible, patient-centric AI across the organization."

| Field | Value |
|---|---|
| Stated obligation | Foster a culture. |
| Implied obligations | This is the vague line that carries the most un-stated obligations. Unpacked: (a) the enablement lead is the visible owner of the "why we are doing this" narrative, including the patient-safety framing; (b) resistance patterns specific to clinical staff (clinical-judgment protection, documentation-time concerns, medical-legal exposure concerns) are addressed proactively per `mod-105 exercise-05`; (c) governance-council and board-level reporting (`mod-106`) includes a culture signal, not just a reach signal; (d) champion-network recognition (per line 2) is the main delivery mechanism; (e) critically, "patient-centric" implies specific guardrails on uses that would route clinical attention *away* from the patient — e.g., scribe tools are approved for note-drafting but not for diverting attention from the patient during the encounter. |
| Owner / partners | Enablement Lead (D). Chief Medical Officer (A). Chief Nursing Officer (A). Patient Experience office (C). |
| Evidence-of-fulfilment artifact | Culture signal on the scorecard (patient-experience pulse, clinician-trust pulse, champion-network health). Resistance-pattern playbook per `mod-105 exercise-05`. |
| Industry-specific flags | Clinician-judgment protection is a non-negotiable framing in US clinical culture; any artifact that reads as "the AI decides" undermines adoption. |
| First-90-days order | Culture signal appears on the scorecard by Day 90 at the earliest; the Day 1–30 action is listening tours with three clinical service lines and two non-clinical functions. |

#### "What you bring" — qualifications flag block

| Field | Value |
|---|---|
| Stated obligation | The role expects healthcare (or comparable regulated-industry) change-management background and comfort with HIPAA and clinician workflow. |
| Implied obligations | (a) An enablement lead new to healthcare should plan the Day-1-to-Day-30 as *immersion* — ride-alongs, shadow shifts, service-line listening — before producing any artifact; (b) HIPAA Privacy Officer and Security Officer are often distinct roles with distinct reporting lines, and the lead's working map must disambiguate; (c) Joint Commission is the dominant accreditation body in US hospitals but is not a regulator in the HIPAA sense; accreditation-cycle posture is different from regulatory posture and both must be respected. <!-- verify-with-sme: confirm the organization's accreditation posture (e.g., Joint Commission vs DNV). --> |
| Owner / partners | Enablement Lead (D). Chief Compliance Officer (C for onboarding immersion). |
| Evidence-of-fulfilment artifact | 90-day plan with named ride-alongs and listening-tour targets. |
| Industry-specific flags | The lead who is healthcare-new cannot skip clinical immersion; the lead who is enablement-new cannot skip the policy immersion. The posting language implies both. |
| First-90-days order | Days 1–30 immersion is non-optional. |

### 2.4 What the posting does NOT say (ask-list for interview / onboarding)

The map is only half-done without the ask-list. The composite posting is silent on a number of load-bearing items; a safe enablement lead confirms them before accepting or in Week 1.

1. **Who signs the AUP and the data-handling SOP** — Compliance only, OGC only, or both, plus any medical-staff-office sign-off? The posting says "co-author with Compliance and OGC" but does not say who signs.
2. **What the clinical adverse-event reporting system is and whether an AI-touching event is routed through it today.** A missing answer is a red flag.
3. **Whether ambient-scribe deployment has a written per-encounter patient-consent process and who audits adherence.**
4. **Whether the organization is a HIPAA Covered Entity only, or also a Business Associate** (some health systems operate joint ventures that make them both). This affects BAA posture.
5. **State(s) of operation** — multi-state operation triggers overlays (CMIA in CA, HIPAA-plus state statutes in WA, TX, NY, and others). <!-- verify-with-sme --><!-- org-specific -->
6. **Scope of 42 CFR Part 2 applicability** — does the system operate SUD programs or receive records from them?
7. **FDA SaMD posture of any in-scope tool** — is anything in the inventory 510(k)-cleared? De novo? Not yet classified? A silent answer is a hint that the Regulatory Affairs partnership is immature.
8. **Executive sponsor of the AI governance council** — the posting says "AI Governance Council" exists but does not name its chair. Council effectiveness is dominated by chair identity.
9. **EHR vendor and integration posture** — ambient-scribe integration is non-trivial and the posting is silent on which EHR and which integration pattern.
10. **Training budget envelope and headcount allocation** — the posting names responsibilities but not resources. The first partnership-contract conversation with Finance (`mod-107 exercise-04` pattern) happens Week 2.

### 2.5 Day-1-to-Day-90 plan derived from the map

| Day | Theme | Key artifacts started |
|---|---|---|
| D1–D5 | Immersion: badge pickup, HIPAA mandatory training (yes, the lead takes it first), reads the current AUP and incident path, meets CCO, CISO delegate, VP Clinical Informatics. | Listening-tour schedule. |
| D6–D15 | Ride-alongs across three specialties; one revenue-cycle shadow; one administrative function shadow. | Field notebook; early segment-map hypotheses. |
| D16–D30 | Working-arrangement note with Clinical Informatics / CISO / CCO; inventory audit of existing AI tools and intake backlog; existing adoption-signal audit. | Working-arrangement note; inventory starter. |
| D31–D45 | Draft segment map; draft baseline curriculum outline; draft industry-adjusted intake questionnaire. | `mod-104 exercise-01` outputs, flavoured. |
| D46–D60 | Walk the AUP walking-redline with CCO and OGC (`mod-108 exercise-04` pattern). Seat the champion network. | Industry-adjusted policy package v0.1. |
| D61–D75 | First scorecard shipped; first two-way feedback-loop cycle; "review before sign" audit for ambient-scribe. | Scorecard v1; feedback-loop output. |
| D76–D90 | First targeted coaching intervention from audit; first governance-council pre-read authored. | Coaching intervention record; council pre-read. |

## 3. Validation steps

1. **Every posting line is mapped.** Walk the map top to bottom and confirm no line is missing. Vague lines (the "foster a culture of responsible AI" variant) in particular must be unpacked, not skipped.
2. **Every mapping row carries all six fields.** Stated obligation, implied obligations, owner / partners, evidence-of-fulfilment artifact, industry-specific flags, first-90-days order. A row with a blank column is incomplete.
3. **Industry-specific flags are non-empty on healthcare-touching lines.** Lines 1, 3, 4, 5, 7, and 9 in particular must carry HIPAA / 42 CFR Part 2 / state-privacy / SaMD / clinician-culture flags. A line that says "no flags" on an obviously healthcare-touching responsibility is a fail.
4. **Evidence-of-fulfilment artifacts are concrete and tied back to the mod-103 / mod-104 / mod-105 / mod-106 / mod-107 catalog, not invented.** A row that says "a dashboard" without naming which dashboard is a fail.
5. **The ask-list exists and is at least 10 items.** A map without an ask-list is unsafe; the vague-line problem is unresolved.
6. **The 90-day plan reflects the map, not a generic onboarding template.** The 90-day plan should cite specific rows of the map (e.g., line 3 → Day 1–30 ride-alongs) so the plan is traceable to the posting.
7. **`org-specific` and `verify-with-sme` markers are present** where specific state laws, specific accreditation bodies, specific vendor names, or specific consent models would otherwise have been invented. Unmarked specifics are a hard fail.
8. **No real employer names, no fabricated statistics.** The composite is explicitly composite; a learner who mapped a real posting should still redact employer identifiers when the artifact lives in a shared repo.
9. **DACI-style owner notation is used consistently** (D / A / C / I), and no row has two Ds on the same obligation.
10. **Explicit cross-references to the other mod-108 exercises** — Exercise 01 for training content, Exercise 03 for enablement-vs-governance split, Exercise 04 for industry-adjusted policy, Exercise 05 for industry-adjusted training — so the map feeds the rest of the module.

## 4. Rubric / review checklist

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | Every posting line mapped, including vague "culture" and "represent externally" lines | 15 | Any line unmapped, or vague lines mapped only to stated obligation. |
| R2 | Each row carries all six fields (stated, implied, owner, evidence, industry flag, 90-day order) | 10 | Any field blank. |
| R3 | Implied-obligations column goes beyond the stated — it is the column that does the work | 15 | Implied column simply restates the stated obligation. |
| R4 | Industry-specific flags on every healthcare-touching line (HIPAA / 42 CFR Part 2 / state / SaMD) | 15 | Flags absent or generic (e.g., "privacy applies"). |
| R5 | Evidence-of-fulfilment artifacts cited back to specific `mod-103` / `mod-104` / `mod-105` / `mod-106` / `mod-107` exercises | 10 | Artifacts named generically ("a training module") without module reference. |
| R6 | Ask-list present with ≥ 10 items, each addressing a specific silence in the posting | 10 | Ask-list missing or generic (e.g., "ask about budget"). |
| R7 | 90-day plan is derived from the map and cites rows | 5 | Generic onboarding plan not tied to the map. |
| R8 | `org-specific` / `verify-with-sme` markers on specific state laws, vendor names, consent models, SaMD classifications | 10 | Unmarked specifics invented. |
| R9 | No real employer names, no fabricated statistics | 5 | Specific employers named, or specific stats quoted. |
| R10 | Explicit cross-references to Exercises 01, 03, 04, 05 of this module | 5 | No cross-reference; the map is orphaned. |

**Pass threshold:** ≥ 80 / 100 and no R1 / R3 / R4 fail. R3 (implied obligations) is the discriminator between a map that is actually useful and a transcription of the posting.

## 5. Common mistakes

- **Mapping only the obvious lines.** Lines 1, 2, 4, 5, 6, 7 are concrete; lines 3, 8, 9 and the "about-the-role" framing carry most of the industry-specific risk. Skipping the vague lines produces a map that looks complete but leaves the hardest obligations unnamed.
- **Mapping stated-to-stated.** The implied-obligations column is where the work lives. "Co-author AUP with Compliance" → "co-author AUP with Compliance" is not a map; "co-author AUP with Compliance → the AUP must address HIPAA Privacy Rule workforce training (45 CFR 164.530(b)), de-identification standards under 45 CFR 164.514, and ambient-scribe audio capture consent" is a map.
- **Inventing regulatory specifics.** Learners sometimes state a specific state law provision, a specific CFR subsection, or a specific FDA guidance section that they have not verified. The map carries `verify-with-sme` on anything not directly confirmable and routes the confirmation to Compliance / OGC.
- **Mis-routing clinical safety events.** Clinical adverse events have an existing reporting system; the enablement lead does not invent a parallel channel. Learners sometimes build an "AI incident mailbox" that competes with the patient-safety event system — an audit finding waiting to happen.
- **Confusing HIPAA Privacy Officer and HIPAA Security Officer.** They are distinct roles under 45 CFR 164.530(a) and 164.308(a)(2) respectively; in many health systems they report to different executives. A map that treats them as one is a fail on realism.
- **Skipping the ask-list.** The posting is the input, not the specification. A map that acts as if the posting is complete is unsafe; the ask-list is the artifact that says "here is what I need to know before I commit."
- **Assuming the enablement lead classifies SaMD.** FDA SaMD classification is a Regulatory Affairs decision. The enablement lead's job is to make sure the intake routes the question, not to answer it. A learner who includes "classify SaMD status" in the enablement lead's responsibilities has mis-scoped the role.
- **Assuming the clinical and non-clinical tracks share a single curriculum.** They share the baseline (per `mod-104 exercise-02`) but diverge on PHI handling, consent, documentation-integrity, and the clinical-judgment framing. A single-track curriculum fails on both sides.
- **Treating "represent externally" as a benign line.** External representation carries Communications / PR, Procurement, and Legal posture. Learners who treat it as "go to conferences" miss the compliance surface.
- **Running the 90-day plan without immersion.** The posting language ("deep comfort with HIPAA," "realities of clinician workflow") implies clinical immersion is non-negotiable. A 90-day plan that opens with artifact production rather than listening is a cultural misfire.

### 5.1 Stretch — second-industry re-run

The same mapping shape applies to postings in other regulated industries. The high-leverage differences by industry:

- **US financial services / depository institution** — Posting lines that touch AUP / policy carry SR 11-7 model-risk-management overlay (any AI tool that feeds credit, lending, AML, or sanctions decisions); lines that touch training carry FFIEC and FINRA (if a broker-dealer is in the entity structure) overlays; lines that touch external representation carry Reg FD considerations for public companies.
- **Life sciences / pharma** — Posting lines that touch any system involved in clinical research, drug development, or product-quality workflows carry 21 CFR Part 11 (electronic records / electronic signatures) and GxP overlays; adverse-event reporting is a distinct regulated channel.
- **US federal contractor / defense industrial base** — Posting lines that touch data handling carry CUI / NIST SP 800-171 / CMMC overlays; external representation is limited by FAR / DFARS clauses; AI tool intake carries FedRAMP-equivalent scrutiny.
- **EU multinational** — Every line additionally carries EU AI Act Article 4 (see `mod-108 exercise-01`) and GDPR (especially Article 35 DPIA for high-risk processing) overlays, plus national works-council consultation steps.

Running the same map against a second-industry posting is the fastest way to see what is baseline enablement and what is industry-flavour.

## 6. References

- **Learning material (local):**
  - [mod-103 — Policy Co-authoring with Governance](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-103-policy-co-authoring-with-governance) — AUP, SOP, intake artifacts the map points at.
  - [mod-104 — Training Programs and AI Literacy Curriculum](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-104-training-programs-and-ai-literacy-curriculum) — segment map, baseline curriculum, L&D partnership.
  - [mod-105 — Champion Networks and Change Management](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-105-champion-networks-and-change-management) — champion charter, feedback loop, resistance patterns.
  - [mod-106 — Outcome Measurement and Executive Reporting](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-106-outcome-measurement-and-executive-reporting) — scorecard shape.
  - [mod-107 — Budget, ROI, Build-vs-Buy at Org Scope](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-107-budget-roi-and-build-vs-buy-at-org-scope) — partnership contract pattern used for the dotted-line working-arrangement note.
  - [mod-108 — Industry and Regulatory Flavours of Enablement](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-108-industry-and-regulatory-flavours-of-enablement) — Exercises 01, 03, 04, 05 are cross-referenced in the map.
- **Official standards and frameworks:**
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — GOVERN / MEASURE functions used for the scorecard and governance-council obligations.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — threat taxonomy referenced in the operator / builder training obligations.
  - [MITRE ATLAS](https://atlas.mitre.org/) — adversarial-technique vocabulary for Security-partnered threat-model conversations.
- **US healthcare regulatory references (verify exact citation and applicability before relying on):** HIPAA Privacy Rule (45 CFR Part 164 Subpart E, workforce training at 164.530(b)), HIPAA Security Rule (45 CFR Part 164 Subpart C, awareness training at 164.308(a)(5)), 42 CFR Part 2 where applicable, applicable state privacy statutes (CMIA, etc.). <!-- verify-with-sme: re-confirm citations and current applicability before publishing any artifact derived from this map. -->
