## Exercise 05 — Industry-Adjusted Training Curriculum — Reference Solution

> Module: `mod-108-industry-and-regulatory-flavours-of-enablement`
> Exercise type: design / worked example (industry-overlay training curriculum)
> Exercise brief: [`lessons/mod-108-industry-and-regulatory-flavours-of-enablement/exercises/exercise-05-industry-adjusted-training-curriculum.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-108-industry-and-regulatory-flavours-of-enablement/exercises/exercise-05-industry-adjusted-training-curriculum.md) (in the learning repo)

## 1. Solution overview

The deliverable is an **industry-adjusted training curriculum** — the baseline curriculum designed in `mod-104` (`exercise-01` segment map, `exercise-02` foundational outline, `exercise-03` role-based playbooks, `exercise-05` workshop and office-hours cadence, `exercise-06` fluency-growth measurement) *overlaid* with the specific modules, assessments, and evidence obligations imposed by a regulated industry. As with the policy overlay in `mod-108 exercise-04`, the point is not to rewrite the baseline curriculum; the point is to produce a disciplined overlay the organization's Compliance / Security / HR / Legal partners can co-sign and the organization's auditors can walk.

The archetype for this solution is a **US federal contractor / defense industrial base (DIB) organization, ~4,000 employees across the prime contract portfolio**, handling **Controlled Unclassified Information (CUI)** under DFARS 252.204-7012 and NIST SP 800-171 / CMMC obligations, with a smaller classified-contract footprint handled in a physically segregated enclave. The organization is rolling out a general-purpose AI assistant for unclassified, non-CUI work on the corporate network and a scoped code assistant in Engineering. **No AI tool is approved to receive CUI** at the time of this curriculum. <!-- org-specific: a different archetype (life sciences / 21 CFR Part 11, EU multinational / AI Act Article 4 + GDPR, US bank / SR 11-7) requires its own overlays; the shape is portable, the content is not. -->

The DIB archetype is deliberately different from the healthcare archetype in `mod-108 exercise-02` and `exercise-04` and the banking archetype in `exercise-03`. The module's teaching point is that the overlay shape is portable across industries; the regulatory content is not. Exercise 05 exercises that teaching point on a third industry.

Posture checks this solution encodes:

- **Overlay, not rewrite.** The same diff discipline as Exercise 04 — ADD / AMEND / RESCOPE / RECLASSIFY / RECITE tagged against named baseline sections, so the reviewer sees exactly what changed.
- **"No AI tool receives CUI" is the operative sentence, not "handle CUI carefully."** Several overlays (AUP training content, intake field, incident path) collapse into this single procedural posture; the curriculum spells it out in every relevant module.
- **Role-based differentiation is sharper than baseline.** Federal-contractor roles carry explicit facility-security-officer (FSO) and ITAR / export-control touchpoints that generic non-defense roles do not; the overlay segment map adds these roles.
- **Evidence and attestation are foregrounded.** NIST SP 800-171 security-awareness training and CMMC awareness-and-training practices drive specific evidence duties. The overlay carries a separate attestation flow and ties it into the organization's existing CUI-handling training.
- **Every overlay is grounded in a named regulatory authority, contract clause, or control family — not in "defense feel."** DFARS 252.204-7012, NIST SP 800-171 Rev. 2 (and the forthcoming Rev. 3 posture), CMMC 2.0 Levels, FAR 52.204-21, ITAR / EAR. Each overlay cites the authority driving it; unverified citations carry `<!-- verify-with-sme: ... -->`.
- **No classified-information handling in this curriculum.** The curriculum is explicit that classified-information training is the responsibility of the FSO and SCIF-specific training, not this curriculum; the overlay names where the line sits.
- **No specific contract numbers, no specific prime-contractor names, no specific program names.** The archetype is composite and generic markers protect against artifact leakage.

## 2. Implementation — worked answer — the industry-adjusted curriculum

### 2.1 Package manifest (`industry-adjusted-curriculum.md`)

```
Industry-adjusted curriculum — v0.1-draft
Archetype:                 US federal contractor / defense industrial base (DIB)
                            Prime and sub-tier mix; CUI + limited classified footprint (separate enclave)
Baseline (per mod-104):    Segment map (exercise-01), Foundational curriculum (exercise-02),
                            Role-based playbooks (exercise-03), Workshop/office-hours cadence (exercise-05),
                            Fluency-growth measurement (exercise-06), L&D partnership (exercise-07)
Governing regulatory /
contract authorities:      DFARS 252.204-7012 (safeguarding CDI / cyber incident reporting)
                            NIST SP 800-171 Rev. 2 (CUI protection; Rev. 3 posture pending)
                            NIST SP 800-172 (enhanced controls, where applicable)
                            CMMC 2.0 (certification expectations; level per contract portfolio)
                            FAR 52.204-21 (basic safeguarding)
                            ITAR / EAR (export-controlled technical data) where applicable
                            FedRAMP Moderate baseline for any cloud service receiving CUI
                            (relevant to AI-tool intake, not to the training itself)
                            <!-- org-specific: confirm applicable CMMC level per customer / contract -->
                            <!-- verify-with-sme: NIST SP 800-171 Rev. 3 adoption timeline and
                            interaction with CMMC — confirm with Compliance / contracting office -->
Owner:                     AI Enablement Lead (co-author)
Co-signers:                Chief Compliance Officer; Chief Information Security Officer;
                            Facility Security Officer (FSO) — for classified-adjacent segments;
                            Contracts / Contracting Office — for contract-clause flow-through;
                            Export Control Officer — where ITAR / EAR applicable;
                            HR Learning; AI Governance Council
Effective:                 <!-- org-specific: effective date -->
Diff legend:               ADD / AMEND / RESCOPE / RECLASSIFY / RECITE
Overlay-wins rule:         Where the industry overlay conflicts with the baseline curriculum within
                            the scope of this organization's CUI and contract environment, the
                            overlay wins. Classified-information training remains outside this
                            curriculum's scope and is owned by the FSO under separate program.
```

### 2.2 Segment-map overlay (against `mod-104 exercise-01` baseline)

The baseline segment map has segments S1–S6 (engineers, data/analytics, operations, knowledge workers, customer-facing, executives). The overlay adds DIB-specific segments and re-scopes existing ones.

| Segment | Status vs baseline | Description / scope | Overlay rationale |
|---|---|---|---|
| S1 Engineers | AMEND | Engineers working on unclassified, non-CUI code only; engineers working on CUI projects are in S7-CUI. | Code-assistant approval differs by CUI scope. |
| S2 Data/Analytics | AMEND | Data/analytics on unclassified, non-CUI data only; CUI data analytics is in S7-CUI. | Data-class scoping. |
| S3 Operations | RECITE | Unchanged. | — |
| S4 Knowledge workers | AMEND | Add explicit exclusion: knowledge workers who touch CUI as part of their regular duties are also in S7-CUI even if their primary segment is S4. | Dual-assignment is normal in DIB. |
| S5 Customer-facing | AMEND | "Customer" = USG customer contact. All external communication with USG customers is contract-controlled and routes through Contracts / PM. | External-communication posture differs. |
| S6 Executives | AMEND | Add export-control awareness and contract-clause flow-through responsibility awareness; any AI-tool decision with CUI implications routes through the Compliance / Contracting Office partnership. | Executive sponsor obligations differ. |
| **S7-CUI** | ADD | Any individual whose regular work involves CUI handling (as defined under the organization's CUI registry mapping to NIST SP 800-171 scope), regardless of job family. | CUI handling drives the single largest overlay. |
| **S8-FSO-adjacent** | ADD | Any individual working in or routinely entering a controlled area (SCIF or classified enclave), even where their AI-tool use is only on the unclassified corporate network. | Facility-security-officer-adjacent populations carry classified-information awareness independent of AI-tool scope; this segment ensures the curriculum does not accidentally undermine FSO training. |
| **S9-Export** | ADD | Any individual whose work touches ITAR- or EAR-controlled technical data. | AI-tool outputs may be export-controlled depending on content; the segment carries explicit training on this. |
| **S10-Ext** | ADD | Contractors, subcontractor employees under a sub-tier flow-down, and embedded vendor personnel with corporate-network identity. | Flow-down clauses (DFARS 252.204-7012 flow-down; FAR 52.204-21 flow-down) extend training obligations to sub-tier staff. |

### 2.3 Foundational curriculum overlay (against `mod-104 exercise-02` baseline)

The baseline foundational curriculum has 6 Core modules (55 min total) and 4 Core+ modules for engineers / data / prompt authors (additional 45 min). The overlay restructures as follows.

#### Core module overlay

| Baseline module | Diff tag | Overlay change |
|---|---|---|
| Module 1 — What this tool is and why we bought it (8 min) | AMEND | Add explicit statement of CUI boundary: "This tool runs in the corporate unclassified environment and is not approved for CUI inputs. If you are not sure whether your work is CUI, stop and check with your project manager and the ISSM / CUI office before using the tool for that work." Add the FSO escalation path for classified-adjacent concerns. Add the Contracting Office escalation path for contract-clause questions. |
| Module 2 — Data classes and what you can and cannot put in a prompt (12 min) | AMEND / RESCOPE | Replace the baseline 4-tier classification with the organization's 5-tier CUI-adjusted scheme: Public / Internal / Sensitive / **CUI** / Classified (out of scope for this tool). Enumerate CUI categories per the National Archives CUI Registry that are relevant to the organization's contract portfolio. State the rule in plain language: "Nothing marked CUI, nothing you would mark CUI, and nothing you are unsure about goes into this tool." Call out specifically that unmarked documents can still be CUI by content; the test is substance, not marking. |
| Module 3 — What goes wrong (10 min) | AMEND | Add two DIB-flavoured failure modes: (a) inadvertent CUI disclosure via an AI-tool prompt that includes seemingly-innocuous context (a filename, a project code, a technical specification excerpt) that in combination reveals CUI; (b) AI-generated output that re-creates technical-data content subject to export control even when inputs did not — "generated technical data" is still export-controlled if it meets the ITAR / EAR technical-data definition. |
| Module 4 — The escalation path (8 min) | AMEND | The baseline three escalation channels (policy, accident, security) extend to five: (1) Policy question → AI Enablement Lead / Compliance; (2) AI-tool operational accident (non-CUI, non-classified) → AI Enablement Lead; (3) Suspected CUI disclosure to an AI tool → ISSM / CUI office + CISO; (4) Suspected classified-information spill (rare in this curriculum's scope but named for completeness) → FSO, immediately; (5) Suspected export-control issue → Export Control Officer. The curriculum teaches the five channels by name and the one-sentence trigger that routes each. |
| Module 5 — The three governing documents and where to find them (5 min) | AMEND | Extend to five: baseline AUP, data-handling SOP, incident-response path, plus the **CUI handling policy** (organization-specific CUI SOP) and the **export-control policy**. Live tour on each. |
| Module 6 — "Everyone's AI" wrap-up (12 min) | AMEND | Add a contract-clause awareness frame: "The ability to use AI tools on this corporate network is enabled by flow-down clauses in our contracts. Staff behavior on this network has contract-clause consequences, not only employment-policy consequences." Explain, in plain language, why DFARS 252.204-7012 obligations flow down to every staff member even though most staff will never read the clause. |

#### Core+ / specialist overlay

Baseline Core+ modules (7–10) are Engineer and Data/Analytics deep-dives on prompt authoring, retrieval posture, code-assistant usage. Overlay changes:

| Baseline module | Diff tag | Overlay change |
|---|---|---|
| Module 7 — Prompt authoring deep-dive (Engineer + Data) | AMEND | Add retrieval-corpus governance: the organization's internal RAG corpora for the AI tool do NOT include CUI; staff who populate corpora must verify at corpus-authoring time; mechanical ingestion of a mixed-label SharePoint site is prohibited. |
| Module 8 — Code assistant deep-dive (Engineer) | AMEND | Code assistant is approved for unclassified, non-CUI code. Any code that is CUI (software source that implements CUI handling, software whose inputs or outputs are CUI, software identified as CTI under DFARS 252.204-7012 scope) is out of the code assistant's scope. Add the "when in doubt, keep it out" default with the specific routing: project manager + ISSM. |
| Module 9 — Retrieval / RAG for data teams | AMEND | Same as Module 7's retrieval-corpus governance, with additional attention to join-key and query-pattern leakage: a prompt that queries across datasets can reveal CUI in aggregate even if no single row is CUI. |
| Module 10 — Operator / power-user patterns | AMEND | Operator responsibilities include surfacing suspected mis-use to the AI Enablement Lead *and* to the ISSM / CUI office if CUI is suspected. |

#### Overlay-specific new modules

| New module | For segments | Length | Content |
|---|---|---|---|
| Module 11 — CUI and this AI tool (required for S7-CUI, recommended for S1 / S2 / S4 who occasionally touch CUI) | S7-CUI, S4 overlap | 20 min | CUI as a category; the organization's CUI registry; the NIST SP 800-171 practice families relevant to day-to-day behavior (Awareness, Media Protection, Communications Protection); the single-sentence rule for AI-tool use ("no AI tool receives CUI"); the mis-marking vs. mis-conduct distinction; the DFARS 252.204-7012 cyber-incident-reporting posture at 72 hours for suspected incidents affecting CDI. <!-- verify-with-sme: confirm the 72-hour reporting timeline under the current DFARS text. --> |
| Module 12 — FSO-adjacent AI use (required for S8-FSO-adjacent) | S8 | 10 min | How the corporate unclassified AI tool coexists with the classified environment; classified-information training remains the FSO's; this module names the AI-specific interactions: no classified content ever on the corporate AI tool, no AI-generated content ever brought into the SCIF without explicit FSO review, and the specific contamination-reporting path. |
| Module 13 — Export control and AI output (required for S9-Export, recommended for S1 Engineers on export-controlled programs) | S9 | 20 min | ITAR / EAR definitions of technical data; the fact that AI-generated technical data can be export-controlled by content even where inputs were not; the "deemed export" concept and its implication for any foreign-person employee or visitor; routing to the Export Control Officer for any ambiguous case. <!-- verify-with-sme: confirm current ITAR / EAR definitions and DOD / BIS guidance on AI-generated technical data; this is an active regulatory space and the content should be re-checked each refresh. --> |
| Module 14 — Contractor / sub-tier flow-down awareness (required for S10-Ext) | S10 | 15 min | How the contractor is bound by the AUP through their employer's flow-down clauses; equivalent-prior-training attestation where the contractor's employer already runs equivalent training; the specific channels the contractor uses (which are the same as employees). |

### 2.4 Role-based playbook overlay (against `mod-104 exercise-03` baseline)

Baseline role-based playbooks are one per function (Engineering, Data, Operations, Sales/Customer). Overlay changes:

- **AMEND** — Each playbook adds a "CUI boundary" section specific to the function. Engineering: which repos, which build pipelines, which environments are CUI-scoped; AI code-assistant allowed scopes are enumerated by name. Data: which datasets are CUI-scoped; AI data-assistant allowed scopes are enumerated by name. Operations: which business processes touch CUI (quality-management for export-controlled parts, logistics for export-controlled shipments) and which do not.
- **ADD** — Playbook for Program Management and Contracts: a function-specific playbook that did not exist in the baseline. Content: how AI-tool use interacts with customer deliverables, data-rights clauses, contract-performance evidence, invoicing and RMA workflows. Where any deliverable crosses the customer boundary (reports, documentation, CDRLs), the human-author discipline is non-negotiable; AI-tool use must not alter the authorship record on the deliverable.
- **ADD** — Playbook for Business Development / Capture: a function-specific playbook addressing proposal drafting. The code-assistant is not approved for use on proposal text that includes any customer-marked or CUI-marked content from a RFP that has not been released publicly. Public solicitation text may be used with the general-purpose assistant; marked solicitation attachments may not.

### 2.5 Workshop and office-hours cadence overlay (against `mod-104 exercise-05` baseline)

- **AMEND** — Workshops add a CUI-handling tabletop exercise as a standing cadence item (quarterly). The tabletop is co-facilitated by the AI Enablement Lead and the CUI office; scenarios include a seemingly-innocuous prompt that in combination with retrieval context would disclose CUI, a mis-marked document situation, and an inadvertent-ingestion case.
- **AMEND** — Office hours are segmented: unclassified / general office hours in a general conference room; CUI-adjacent office hours (if any) do not happen in the AI tool itself and route through the ISSM / CUI office rather than the Enablement office. The curriculum teaches staff the difference.
- **ADD** — Monthly "contracts-and-AI" clinic co-led with the Contracting Office. Low attendance is acceptable; the forum exists so that when a contract-clause question arises there is a known place to take it.

### 2.6 Fluency-growth measurement overlay (against `mod-104 exercise-06` baseline)

- **AMEND** — Add a CUI-awareness pulse to the baseline fluency measurement: a short, periodic behavioral check on CUI recognition that is co-designed with the CUI office and does not itself expose any CUI (hypothetical prompts, not real ones).
- **ADD** — Attestation count: separately from fluency, the curriculum tracks training-attestation completion by segment, feeding into the NIST SP 800-171 / CMMC evidence duty.
- **ADD** — Incident / suspected-disclosure rate: a signal from the ISSM / CUI office on suspected AI-tool CUI disclosures per quarter, broken out by segment. Zero is a valid reading; absence is not. A rise is a signal to re-ship training to the affected segment.

### 2.7 L&D partnership contract overlay (against `mod-104 exercise-07` baseline)

- **AMEND** — L&D co-signers extend to include Compliance (CUI office / ISSM) and the Contracting Office (for contract-clause flow-down verification). L&D does not become a CUI stakeholder; Compliance remains the authoritative owner of CUI-content accuracy, and L&D is responsible for delivery and evidence operations.
- **AMEND** — Contractor / sub-tier training SLAs are explicit: equivalent-prior-training attestation requires a 5-business-day L&D-plus-Compliance review window. Attestations older than 12 months re-trigger the training.

### 2.8 Evidence package overlay

Extends the `mod-108 exercise-01` and `exercise-04` evidence packages:

| New evidence item | Form | Owner | Retention |
|---|---|---|---|
| NIST SP 800-171 security-awareness training records — AI-tool-specific portion | LMS repository + attestation | L&D + ISSM / Compliance | Current + prior CMMC assessment cycle <!-- verify-with-sme: confirm retention per CMMC assessment process and contract clauses --> |
| DFARS 252.204-7012 flow-down evidence — contractor attestations | Procurement record + L&D attestation record | Procurement + L&D | Contract life + statutory period |
| Export-control awareness attestation (Module 13) for S9-Export | LMS attestation | L&D + Export Control Officer | Life of staff member's export-controlled program assignment |
| FSO-adjacent AI-tool training attestation (Module 12) | LMS attestation | L&D + FSO | Life of access |
| CUI-awareness pulse results (periodic) | Scorecard entries | AI Enablement Lead + Compliance | 3 years rolling |
| Suspected-disclosure / incident-correlation records | Case records cross-referenced to training completion | ISSM + AI Enablement Lead | Per organization incident-retention schedule |

### 2.9 Refresh triggers (industry-specific)

In addition to the baseline periodic cadence and the `mod-108 exercise-01` triggers:

- **NIST SP 800-171 revision** (Rev. 2 → Rev. 3 or subsequent) → review all CUI-touching modules within 60 days of the organization's adoption decision.
- **CMMC level change** for any in-scope contract → re-ship the awareness training to the affected program's staff within 30 days.
- **DFARS or FAR acquisition-regulation change** affecting CUI, cybersecurity reporting, or AI-tool use → Compliance drives a module review.
- **New ITAR or EAR guidance** affecting AI-generated technical data → Export Control Officer drives a Module 13 review.
- **Suspected AI-tool CUI disclosure** → Module 11 is re-shipped to the affected segment within the quarter, with an incident-informed scenario added to the quarterly tabletop.
- **New AI tool added to inventory (per `mod-108 exercise-01` inventory discipline)** → the segment map is reviewed for any new segment assignment; existing modules are re-shipped only if the segment mapping changes.
- **Classified-contract scope change** (new classified contract, expansion of SCIF, new FSO) → Module 12 is reviewed with the FSO.

## 3. Validation steps

1. **Overlay discipline.** Walk against baseline `mod-104` exercises 01, 02, 03, 05, 06, 07 and confirm the overlay uses explicit diff tags. A standalone rewrite fails.
2. **"No AI tool receives CUI" is the operative sentence** and appears in Module 1 (baseline-AMEND), Module 2 (baseline-AMEND), Module 11 (new), and the Engineering / Data / Program Management playbook overlays. Omission in any of these is a hard fail.
3. **Segment map adds S7-CUI, S8-FSO-adjacent, S9-Export, S10-Ext.** All four are present with named populations. A learner who only adds S7-CUI misses the FSO flank, the export-control flank, and the contractor flow-down flank.
4. **Module 11 (CUI and this AI tool) exists** with content on NIST SP 800-171, DFARS 252.204-7012 reporting posture, the CUI registry, and the single-sentence prohibition.
5. **Module 12 (FSO-adjacent) names the classified-training line.** The overlay is explicit that classified-information training remains the FSO's; this curriculum names the AI-specific interaction only. Any curriculum that attempts to teach classified-information handling is role-confused.
6. **Module 13 (export control) names ITAR / EAR, the deemed-export concept, and the "AI-generated technical data can be controlled by content" point.** A missing deemed-export point is a fail.
7. **Module 14 (contractor / sub-tier) names flow-down clauses** and provides an equivalent-prior-training attestation path. A missing contractor track is a hard fail on evidence duty under DFARS flow-down.
8. **Program Management and Business Development playbooks are present** as additions to the baseline. Omitting these is the common failure mode in a DIB environment and leaves the two functions most likely to interact with customer deliverables and solicitation content untrained.
9. **Escalation path is five channels, not three.** Baseline three + ISSM / CUI + FSO + Export Control Officer.
10. **Evidence package extends, not duplicates, the baseline.** Attestations tie back to the HRIS and to the organization's incident / CUI records.
11. **Measurement adds a CUI-awareness pulse and a suspected-disclosure-rate signal** to the baseline fluency measurement. Absence of the suspected-disclosure signal is a fail — it is the operational signal that tells the enablement function whether the training is working.
12. **No invented regulatory specifics.** DFARS, NIST SP 800-171, CMMC, ITAR, EAR, FAR citations carry `<!-- verify-with-sme: ... -->` where the drafter has not confirmed with Compliance / Contracting / Export Control. The CMMC level is `<!-- org-specific: ... -->`. Supervisory expectations are not invented.
13. **No specific contract numbers, no specific prime-contractor names, no specific program names.** The archetype is composite.
14. **Classified content is not in scope and the curriculum is explicit about that.** Any overlay that tries to teach classified-information handling has escaped the curriculum's lane.

## 4. Rubric / review checklist

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | Overlay is a diff against named baseline `mod-104` sections with explicit tags | 10 | Standalone rewrite with no diff discipline. |
| R2 | "No AI tool receives CUI" appears in Modules 1, 2, 11, and in every CUI-touching playbook | 15 | Statement missing from one or more of these. |
| R3 | Segment map adds S7-CUI, S8-FSO-adjacent, S9-Export, S10-Ext with scoped populations | 10 | Fewer than four new segments, or segments without population scope. |
| R4 | Module 11 (CUI) present with NIST SP 800-171, DFARS 252.204-7012 reporting posture, CUI registry, and the single-sentence prohibition | 10 | Module missing, or content fails to name the authorities. |
| R5 | Module 12 (FSO-adjacent) present and explicitly scoped to AI-tool-only content; classified-information training remains with the FSO | 5 | Module missing, or curriculum attempts to teach classified-information handling. |
| R6 | Module 13 (export control) present with ITAR / EAR, deemed-export, and AI-generated-technical-data points | 10 | Module missing, or deemed-export absent. |
| R7 | Module 14 (contractor / sub-tier) present with flow-down awareness and equivalent-prior-training attestation path | 10 | Module missing, or no contractor track. |
| R8 | Program Management and Business Development playbooks added | 5 | Playbooks absent; DIB-specific customer-deliverable risk left untrained. |
| R9 | Escalation path is five channels (baseline three + ISSM/CUI + FSO + Export Control) | 5 | Three-channel baseline unchanged. |
| R10 | Evidence package extends baseline with NIST SP 800-171 training records, DFARS flow-down evidence, export-control attestation, FSO-adjacent attestation, CUI-awareness pulse, and suspected-disclosure records | 10 | Fewer than four extensions. |
| R11 | Measurement adds CUI-awareness pulse and suspected-disclosure-rate signal | 5 | One or both absent. |
| R12 | Refresh triggers include NIST SP 800-171 revision, CMMC level change, DFARS / FAR change, ITAR / EAR change, suspected disclosure, new tool, classified-scope change | 5 | Only a time-based refresher. |
| R13 | `org-specific` / `verify-with-sme` markers on CMMC level, DFARS citations, NIST SP 800-171 revision posture, ITAR / EAR specifics; no fabricated contract numbers or program names | 5 | Unmarked quoted regulatory specifics, or fabricated program names. |

**Pass threshold:** ≥ 85 / 100 and no R2 / R4 / R7 fail. R2 (the "no CUI" operative sentence), R4 (Module 11 grounding), and R7 (contractor track) are the discriminators between a curriculum that holds in a CMMC assessment and one that does not.

## 5. Common mistakes

- **Curriculum rewrite instead of overlay.** The L&D partnership and the AI Governance Council co-signed the baseline curriculum; a standalone rewrite will not re-sign without a diff, and introduces a second curriculum that will drift from the first.
- **Teaching CUI as "sensitive information."** CUI is a specific regulatory category with a public registry; teaching it as "sensitive" undermines the specificity staff need when they encounter a marking question in real work. The curriculum names the CUI registry and the organization's registry mapping.
- **Mixing classified-information training into the curriculum.** The FSO's training program exists for a reason, and it is governed by distinct contract clauses and NISP rules. Learners who try to fold classified handling into Module 12 have escaped the curriculum's lane and will cause FSO sign-off to fail.
- **Omitting the contractor / sub-tier track (Module 14).** Flow-down obligations under DFARS 252.204-7012 extend training responsibility to sub-tier staff; omitting them leaves a large evidence gap under the organization's prime-contract flow-down duty.
- **Omitting Program Management and Business Development playbooks.** The two functions most likely to generate a customer-visible problem in a DIB environment are untrained if they inherit only a generic Core curriculum. The playbooks are additions to the baseline, not substitutions.
- **Treating "export control" as "international shipping."** AI-generated technical data can be export-controlled by content independent of shipping, and the deemed-export concept applies to foreign-person employees and visitors working in the United States. Omitting deemed-export in Module 13 is a common failure.
- **Confusing NIST SP 800-171 and NIST SP 800-172.** 800-171 is the general CUI control set; 800-172 is the enhanced-controls overlay for contracts that specify it. The curriculum references 800-171 as the baseline and flags 800-172 as `<!-- org-specific: applicable where contract specifies -->`.
- **Over-quoting DFARS section numbers without verification.** DFARS 252.204-7012 is the well-known CUI / cyber-incident-reporting clause; adjacent clauses (252.204-7019, 252.204-7020, 252.204-7021) are easily mis-cited. The curriculum carries citations with `<!-- verify-with-sme: ... -->` where the drafter has not confirmed with Contracting.
- **Running the CUI-awareness pulse in the AI tool itself.** Any measurement activity must not itself expose CUI. Scenarios used in the pulse are hypothetical, not real; the curriculum spells this out.
- **Scorecard that reports "zero suspected disclosures" without investigation.** A zero reading is a valid signal only if the operational feedback loop from the ISSM is actually open. If the Enablement Lead has not confirmed that the signal is observed and routed, "zero" may mean "unobserved." The curriculum teaches operators to surface, not only to comply.

### 5.1 Stretch — overlay against a second industry

For readers in a different industry, the overlay shape is portable:

| Overlay target | US federal contractor / DIB (archetype) | US health system | US bank | Life sciences / pharma |
|---|---|---|---|---|
| Primary new segment | S7-CUI, S8-FSO-adjacent, S9-Export, S10-Ext | S-CLIN, S-HIM, S-CHARGE, S-EXT | S-MRM-TOUCH, S-REG-ADJACENT, S-EXT | S-GXP, S-CLIN-TRIAL, S-COMMERCIAL-REGULATED, S-EXT |
| Primary new module | "CUI and this AI tool" (Module 11) | "PHI, de-identification, and this AI tool" | "Model-risk scope and this AI tool" | "GxP data, 21 CFR Part 11, and this AI tool" |
| Primary attestation duty | NIST SP 800-171 awareness + DFARS flow-down + export | HIPAA workforce training (45 CFR 164.530(b)) + Security Rule awareness (45 CFR 164.308(a)(5)) | FFIEC / FINRA where applicable, plus organization-specific MRM training | 21 CFR Part 11 training + GxP training |
| Primary operational signal | Suspected-disclosure rate from ISSM | Patient-safety event with AI contributing factor | Model-risk findings in AI-touching scope | Deviations in validated systems involving AI output |

Running the same overlay in the second industry is the fastest way to see what is structural (segment map extension, module 1 / 2 / N-overlay pattern, evidence package extension, measurement pulse) and what is regulation-specific (every citation changes; every attestation duty changes).

## 6. References

- **Learning material (local):**
  - [mod-104 — Training Programs and AI Literacy Curriculum](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-104-training-programs-and-ai-literacy-curriculum) — baseline curriculum the overlay sits against (exercises 01, 02, 03, 05, 06, 07).
  - [mod-105 — Champion Networks and Change Management](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-105-champion-networks-and-change-management) — champion recruitment and feedback-loop discipline the Program Management and Business Development playbooks lean on.
  - [mod-106 — Outcome Measurement and Executive Reporting](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-106-outcome-measurement-and-executive-reporting) — scorecard shape the measurement overlay extends.
  - [mod-108 exercise-01](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-108-industry-and-regulatory-flavours-of-enablement/exercises/exercise-01-eu-ai-act-article-4-training-content-drill.md) — the evidence-package pattern extended here with NIST SP 800-171 / CMMC-flavoured records.
  - [mod-108 exercise-03](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-108-industry-and-regulatory-flavours-of-enablement/exercises/exercise-03-enablement-vs-governance-responsibility-split-in-industry.md) — the DACI that governs the sign-off columns on each overlay section.
  - [mod-108 exercise-04](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-108-industry-and-regulatory-flavours-of-enablement/exercises/exercise-04-industry-adjusted-policy-package.md) — the sibling policy-overlay exercise; the curriculum overlay carries the same diff discipline.
  - [mod-109 — AI Incident Response and Enablement-Side Rollback](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-109-ai-incident-response-and-enablement-side-rollback) — the incident path taught in Module 4-AMEND.
- **Official standards and frameworks:**
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — GOVERN / MEASURE functions frame the measurement overlay.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — threat taxonomy referenced in Module 7 / 8 / 9 engineer-track content.
  - [MITRE ATLAS](https://atlas.mitre.org/) — adversarial-technique vocabulary used alongside OWASP in builder-track content and in the Security office-hours clinic.
- **US federal contractor / DIB regulatory references (verify exact citation and current applicability before relying on):** DFARS 252.204-7012 (Safeguarding Covered Defense Information and Cyber Incident Reporting); NIST SP 800-171 Rev. 2 (and Rev. 3 posture) — Protecting Controlled Unclassified Information in Nonfederal Systems and Organizations; NIST SP 800-172 — Enhanced Security Requirements for Protecting CUI; FAR 52.204-21 — Basic Safeguarding of Covered Contractor Information Systems; CMMC 2.0 model and associated DoD guidance; ITAR (22 CFR Parts 120–130) and EAR (15 CFR Parts 730–774) where applicable; FedRAMP Moderate baseline for AI-tool cloud service intake. <!-- verify-with-sme: re-confirm citations, revision levels, and current applicability with Compliance / Contracting / Export Control partners before publishing any artifact derived from this curriculum. -->
