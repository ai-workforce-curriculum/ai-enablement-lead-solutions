# Exercise 05 — NIST AI RMF GOVERN → Enablement Practice Map — Reference Solution

> Learning file: [`exercise-05-nist-ai-rmf-govern-to-enablement-practice-map.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-103-policy-co-authoring-with-governance/exercises/exercise-05-nist-ai-rmf-govern-to-enablement-practice-map.md)

## 1. Solution overview

Two artifacts: a **standards mapping table** (Deliverable A, ≥ 8 rows) and a **gaps memo** (Deliverable B, one page). The deliverables are the one-page view `head-of-ai-governance` (L60) and `senior-ai-governance-architect` (L50) will ask for inside the first three months of any real role.

Posture checks the solution encodes:

- **GOVERN category family named with confidence; sub-category IDs marked `org-specific`.** The RMF 1.0 is public and the GOVERN function's six category families are public; the exact sub-category IDs (GOVERN 1.1, 2.1, etc.) should be verified by the architect, not invented.
- **ISO/IEC 42001 clause families named with confidence; Annex A IDs marked `org-specific` when quoted.** Clauses 5, 6, and 7 (especially 7.2 Competence, 7.3 Awareness, 7.5 Documented information) are the enablement surfaces per Chapter 03.
- **Evidence column is a concrete artifact per row** — not "policy documentation."
- **Owner column names the specific role** and, where control design and evidence operation are split, names both.
- **Memo surfaces enablement-practice gaps only.** No standard rewrites. No control-library redesigns. Chapter 07 is explicit.

## 2. Implementation — worked answer

### 2.1 Deliverable A — `standards-mapping-table.md`

```
Standards-mapping — enablement-side artifacts
Author:  AI Enablement Lead (this role)
Intended readers: head-of-ai-governance (L60), senior-ai-governance-architect (L50)
Scope:   NIST AI RMF 1.0 (with NIST AI 600-1 GenAI Profile) and ISO/IEC 42001:2023
```

| Artifact | Primary NIST AI RMF GOVERN category | Primary ISO/IEC 42001 clause(s) | Evidence this role produces | Owner on the standards side |
|---|---|---|---|---|
| **Acceptable-use policy** (mod-103 Chapter 04) | GOVERN — policies, processes, procedures `<!-- org-specific: confirm exact sub-category ID, likely GOVERN 1.1 and GOVERN 1.2 -->`. Also GOVERN — third-party AI risks `<!-- org-specific: confirm GOVERN 6.1 -->` where the tool is externally provided. | Clause 5 (Leadership) — AI policy that descends from top-management-ratified policy. Clause 7.4 (Communication) — operator-facing publication. Annex A control(s) `<!-- org-specific: confirm applicable A.2 / A.9 Annex A control IDs -->`. | Ratified AUP document, versioned, with signed co-author surface (`head-of-ai-governance`, counsel, CISO, DPO, this role) plus the redline log used to produce it. | Architect (`senior-ai-governance-architect`) is accountable for the control-design mapping; this role is accountable for the evidence operation — drafting, redlining, versioning, ratification tracking. |
| **Data-handling SOP** (mod-103 Chapter 05) | GOVERN — information integrity and accountability `<!-- org-specific: confirm sub-category ID -->`. GOVERN — third-party / supply-chain where the SOP references the vendor DPA `<!-- org-specific: confirm GOVERN 6.1 / 6.2 -->`. | Clause 6 (Planning — actions to address risks) and Clause 8 (Operation) — the SOP is a planning-and-operation artifact. Annex A `<!-- org-specific: confirm A.6 / A.7 controls on AI system life cycle and data for AI systems -->`. | Ratified SOP document with accident-path procedure, signed by security and privacy; incident-record log entries demonstrating the SOP is operated in practice. | Architect designs the control that the SOP evidences (life-cycle and data controls); this role operates the SOP and produces the operational-record evidence. `ai-risk-engineer` (L25) co-owns the handoff surface. |
| **Intake questionnaire** (mod-103 Chapter 06) | MAP — categorization and context (primary) `<!-- org-specific: confirm MAP 1.1 / 1.2 sub-category IDs -->`. Secondary: GOVERN — policies for third-party AI where the tool is externally provided. | Clause 6 (Planning — AI objectives and risk-classification scheme). `<!-- org-specific: confirm whether Annex A.5 impact-assessment controls apply directly -->`. | Corpus of completed submissions, with status-tag history per submission; pre-review session notes; the schema-refinement memo cadence to the architect. | Architect **designs the schema** (fields, value enumerations, classification mapping); this role **operates the runner** (submissions interface, pre-review sessions, status tracking). Chapter 06 schema-vs-runner split. |
| **Training rosters** (mod-104) | GOVERN — workforce competence `<!-- org-specific: confirm GOVERN 2.1 / 2.2 / 2.3 IDs -->`. | Clause 7.2 (Competence) — primary. Clause 7.3 (Awareness) — secondary. `<!-- org-specific: confirm Annex A control for AI workforce training if any is called out -->`. | Role-tier training completion rosters; scoring/assessment records where graded; recertification cadence log. Links to the EU AI Act Article 4 literacy-floor evidence surface where applicable (mod-101 Chapter 05). | This role is **accountable for the evidence operation**; architect is accountable for the role-tier-to-competence-objective mapping. Human-resources information system is the operator-of-record for the roster data. |
| **Champion network** (mod-105) | GOVERN — workforce awareness and information integrity `<!-- org-specific: confirm GOVERN 2 / 3 sub-category IDs -->`. | Clause 7.3 (Awareness) — primary. Clause 7.4 (Communication). `<!-- org-specific: confirm whether Annex A.8 (information for interested parties) applies -->`. | Champion-roster log; field-signal briefing cadence to the governance council; cross-BU pattern threshold evidence (three champions or two BUs, per mod-105). | This role operates the network and produces awareness-evidence; architect specifies what awareness evidence is required by the control library. Business-unit sponsors are the operators-of-record for champion nomination. |
| **Executive scorecard** (mod-106) | MEASURE — outcome-level TEVV adjacent evidence `<!-- org-specific: confirm MEASURE sub-category IDs; rollout-outcome scorecards may map here -->`. GOVERN — accountability structures (reporting cadence) where the scorecard reaches executives. | Clause 9 (Performance evaluation) — primary. Clause 5 (Leadership — reporting to top management) — secondary. `<!-- org-specific: confirm Annex A control on performance / monitoring -->`. | Monthly scorecard publication, with executive reach records (distribution list and acknowledgement); dashboard archive showing trend over time. | This role produces the scorecard; `ai-risk-engineer` (L25) and `senior-ai-governance-architect` jointly specify which measures the scorecard carries. `head-of-ai-governance` consumes and signs. |
| **Kill-switch and rollback plan** (mod-102 artifact 7 / mod-109) | MANAGE — risk-response activities `<!-- org-specific: confirm MANAGE sub-category IDs for response and recovery -->`. GOVERN — accountability for incident response `<!-- org-specific: confirm sub-category -->`. | Clause 8 (Operation) and Clause 10 (Improvement — nonconformity and corrective action). Annex A `<!-- org-specific: confirm A.6 life-cycle control and any incident-response-specific controls -->`. | Documented kill-switch procedure per tool; rollback-exercise log (if tabletop exercises have been run); incident after-action records (operated per mod-109). | Architect designs the control and incident-response taxonomy; `ai-risk-engineer` (L25) and the SOC operate the forensic response; this role operates the enablement-side rollback and user communication. Chapter 07 routing. |
| **Redline log** (mod-103 Chapter 01) | GOVERN — transparency and documented processes `<!-- org-specific: confirm GOVERN 1.4 / 1.5 sub-category IDs for document-control-type content -->`. | Clause 7.5 (Documented information) — primary. Clause 5 (Leadership — evidence of policy stewardship). `<!-- org-specific: confirm Annex A control on documented information retention -->`. | Redline log per policy, with entries per walking-redline cycle; cross-link to AUP/SOP version history; archive of signer-side redline rationales. | This role is accountable for the log operation; architect is accountable for the records-retention policy that governs the log. Counsel reviews log entries for privileged material before archiving. |
| *(Additional row — optional)* **90-day entry plan** (mod-101) | GOVERN — roles, responsibilities, lines of accountability `<!-- org-specific: confirm GOVERN 1.3 / 2.1 sub-category IDs -->`. | Clause 5 (Leadership — roles, responsibilities, authorities). Clause 7.1 (Resources). | 90-day entry-plan artifact filed at role start; checkpoint reviews at 30/60/90 days with the chain of command. | This role authors; `head-of-ai-governance` (L60) and `head-of-engineering-enablement` (L55, the chain-of-command parent) ratify. |
| *(Additional row — optional)* **Pilot charter** (mod-102 artifact 6) | MAP — context and intended-use documentation `<!-- org-specific: confirm MAP 1 sub-category IDs -->`. | Clause 6 (Planning) and Clause 8 (Operation). | Signed charter per piloted tool; pilot-evaluation record at charter close. | Architect co-authors the risk-frame of the charter; this role operates the pilot. |
| *(Additional row — optional)* **Incident after-action** (mod-109) | MANAGE — documentation, communication, and corrective action `<!-- org-specific: confirm MANAGE sub-category IDs -->`. | Clause 10 (Improvement). `<!-- org-specific: confirm Annex A control on nonconformity / corrective action -->`. | After-action document per incident; corrective-action-tracking log tying findings to AUP/SOP revisions. | `ai-risk-engineer` (L25) authors the forensic sections; this role authors the enablement-side sections (operator communication, policy impact, training gap). `head-of-ai-governance` ratifies. |

**Column-rule note.** No row in this table lists this role as the **sole** owner of a control design. The split is consistent: architect designs; this role operates and produces the evidence. Where architectural ownership is shared with `ai-risk-engineer` (L25) or counsel, both names appear.

---

### 2.2 Deliverable B — `standards-mapping-gaps-memo.md`

```
To:    head-of-ai-governance (L60)
Cc:    senior-ai-governance-architect (L50)
From:  AI Enablement Lead (this role)
Date:  <!-- org-specific: confirm memo date -->
Re:    Two places the enablement-side artifact set does not yet map cleanly to NIST AI RMF GOVERN / ISO/IEC 42001 — operating-model observations for your consideration
```

The mapping table attached surfaces two places where the enablement-side artifacts do not yet evidence a standards-side expectation cleanly. For each, I describe the gap and propose a change in **enablement practice** — not in the standard, and not in the control library. Both are for your consideration; the control-mapping consequences of either are `senior-ai-governance-architect`'s call.

**Gap 1 — No standing evidence surface for GOVERN diversity / equity / inclusion and accessibility considerations.**

NIST AI RMF GOVERN includes an explicit category on diversity, equity, inclusion, and accessibility in the AI lifecycle; ISO/IEC 42001 Clause 5 (Leadership) and `<!-- org-specific: confirm Annex A.5 impact-assessment controls -->` similarly expect documented attention to affected-stakeholder considerations. The enablement-side artifact that would normally evidence this is the intake questionnaire (via the "cohort size and reach" and "external disclosure" groupings), but the current field set surfaces cohort demographics and affected-stakeholder categories only indirectly, and no standing record keeps that signal visible beyond the single submission. The result is that an auditor who asks "how does enablement evidence DEI-and-accessibility attention across the AI estate" gets a scattered answer assembled from individual submissions.

The proposed change in enablement practice is to add a **quarterly affected-stakeholder review record**: a two-page summary the enablement seat produces each quarter rolling up cohort-and-reach data from all intake submissions and all champion-network field signal in the window, with explicit sections on accessibility signal and on populations affected but not represented in the champion network. This record would live alongside the council pre-read cadence (one quarter of pre-reads becomes a stakeholder-review pre-read). *Whether this is the right shape of evidence, and whether it maps cleanly to a GOVERN sub-category and a Clause 5 / Annex A control, is the architect's call.*

**Gap 2 — The redline log does not yet evidence transparency to operators as distinct from documentation for the audit file.**

NIST AI RMF GOVERN includes a transparency expectation (how the organization communicates AI risk-management posture internally and externally); ISO/IEC 42001 Clause 7.3 (Awareness) and Clause 7.4 (Communication) expect evidence that operators receive and understand the policies that bind them. The redline log, as currently operated, evidences the stewardship of the policy (the walking-redline cycles, the signer rationales, the version history) — but it does not evidence operator-side awareness of what changed between versions. A reader of the redline log can see that AUP v1.2 added a prohibited use on test-fixture scrubbing; they cannot see that operators were told about the change in a form they can be expected to retain.

The proposed change in enablement practice is to institute a **version-note briefing cadence** paired to every ratified policy-version increment: a short operator-facing summary (≤ 1 page, operator voice) distributed through the champion network and to all in-scope cohorts within five business days of each ratification, with an acknowledgement-tracking record kept alongside the redline log. The briefing would carry a stable structure (what changed, why, what you do differently as a result) and would become part of the Clause 7.3 awareness evidence surface. *The directional decision — whether this is the right operating-model change versus, say, routing the gap through the training-roster artifact — is your and the architect's call.*

---

These are **operating-model recommendations for governance consideration**, not decisions. I am available for a 30-minute walk-through at your convenience and would welcome either or both being redirected if the architect sees a cleaner path.

---

### End of worked artifacts

## 3. Validation steps

### For Deliverable A (`standards-mapping-table.md`)

1. **Row count.** ≥ 8 rows. The eight required artifacts are all present: AUP, data-handling SOP, intake questionnaire, training rosters, champion network, executive scorecard, kill-switch / rollback plan, redline log. Additional rows are permitted (90-day entry plan, pilot charter, incident after-action).
2. **Five columns present and populated per row:** Artifact | NIST AI RMF GOVERN category | ISO/IEC 42001 clause(s) | Evidence this role produces | Owner on the standards side.
3. **GOVERN category family named per row, not just "GOVERN."** The six category families (roles & responsibilities; policies/processes/procedures; workforce competence; third-party; information integrity; DEI) should appear, correctly paired with artifacts.
4. **Sub-category IDs quoted are either verified or marked `<!-- org-specific: ... -->`.** Invented IDs (e.g., writing "GOVERN 2.1" without verification) are a hard fail.
5. **ISO/IEC 42001 clause families named with confidence; Annex A control IDs marked `org-specific` when quoted.** Clauses 5, 6, 7 (especially 7.2, 7.3, 7.5) should appear on the appropriate rows.
6. **Evidence column is a concrete artifact per row.** Grep for "policy documentation," "procedures," "records" without further specification — vague evidence fails. The worked table uses "ratified AUP + redline log," "training completion roster per role tier," etc.
7. **Owner column is specific per role; where design and evidence operation are split, both are named.** No row lists this role as the sole owner of a control design.
8. **Carry-forward with Chapter 03.** The RMF function names (GOVERN / MAP / MEASURE / MANAGE) and the Clause 5 / 6 / 7 mapping align with Chapter 03's framing.

### For Deliverable B (`standards-mapping-gaps-memo.md`)

1. **One page.** Render Markdown; cut if it spills.
2. **Exactly two gaps.** Grep for a third.
3. **Each gap has the required 2 + 2 sentence structure:** 2 sentences describing the gap (what the standard requires, which enablement artifact normally evidences it, why the current artifact falls short) + 2 sentences proposing an enablement-practice change.
4. **Each proposed change is a change in enablement practice** — a new record kept, a revised cadence, a new section in an existing artifact, a role-based reporting split. **Not** a proposed standard rewrite. **Not** a proposed control-library redesign. This is the single hardest rubric criterion.
5. **Memo closes with one sentence explicitly framing the recommendations as "for governance consideration."**
6. **No EU AI Act article-level change proposals** (stretch-goal territory; not the main memo).
7. **`<!-- org-specific: ... -->` used wherever specific sub-category or sub-clause IDs are quoted without verification.**

Markdown lint both files.

## 4. Rubric / review checklist

### Deliverable A — mapping table

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| A1 | ≥ 8 rows, covering the eight required artifacts | 15 | Any required artifact missing. |
| A2 | Five columns present and populated per row | 10 | Any column missing or empty. |
| A3 | GOVERN category family named per row (not just "GOVERN") | 10 | Rows that say only "GOVERN" without a category family. |
| A4 | Sub-category IDs quoted are verified or marked `org-specific` | 10 | Any invented sub-category ID. |
| A5 | ISO/IEC 42001 clause family named with confidence per row; Annex A IDs marked `org-specific` when quoted | 10 | Invented Annex A control IDs. |
| A6 | "Evidence" column names a concrete artifact per row | 10 | "Policy documentation" / generic nouns. |
| A7 | "Owner" column specific; architect-designs / this-role-operates distinction made where applicable | 10 | This role listed as sole control-design owner anywhere. |
| A8 | Carry-forward with Chapter 03 vocabulary | 5 | Function names or clause mappings inconsistent with Chapter 03. |

### Deliverable B — gaps memo

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| B1 | Fits on one page | 5 | Spills. |
| B2 | Addressed to `head-of-ai-governance` with `senior-ai-governance-architect` cc (role names) | 2 | People names, or missing cc. |
| B3 | Exactly two gaps | 3 | Wrong count. |
| B4 | Each gap has 2 sentences describing gap + 2 sentences proposing enablement-practice change | 5 | Missing or malformed. |
| B5 | **Both proposed changes are in enablement practice; no standard rewrites; no control-library redesigns** | 15 | Any proposal that rewrites a standard or redesigns a control. |
| B6 | Memo closes explicitly framing recommendations as "for governance consideration" | 5 | Missing framing sentence, or content contradicts framing. |

**Pass threshold:** ≥ 85/100 and no A4 / A7 / B5 fail. B5 is the Chapter 07 discipline test; A4 and A7 together prevent the architect-drift that Chapter 07 warns about.

## 5. Common mistakes

- **Inventing GOVERN sub-category IDs or Annex A control IDs.** The RMF 1.0 and ISO/IEC 42001:2023 both publish their exact IDs; those IDs should be verified by the architect, not invented. The discipline is to name the **family** with confidence and mark the **exact ID** with `<!-- org-specific: ... -->`.
- **Listing this role as the sole owner of a control design.** Any row where "Owner on the standards side" reads only "AI Enablement Lead" is architect drift. Rewrite to name the architect's design responsibility and this role's evidence-operation responsibility.
- **Generic "Evidence" column entries.** "Policy documentation." "Procedures." "Records." None of these will stand up to an auditor's follow-up ("show me"). Rewrite as the concrete artifact the auditor would receive.
- **Proposing a standard rewrite in the memo.** "GOVERN should add a sub-category for test-fixture-level data hygiene." That is not an enablement proposal; that is an attempt to amend NIST. Chapter 07 is explicit on this drift.
- **Proposing a control-library redesign in the memo.** "The architect should move the AUP from A.2 to A.9." Not yours to propose. Rewrite as an enablement-practice change and let the architect decide whether the control mapping also shifts.
- **Choosing gaps the artifacts already evidence cleanly.** The common cold-start error: picking GOVERN policies/processes/procedures (which the AUP covers) or workforce competence (which training rosters cover) as "gaps." Gaps live in DEI / information-integrity / transparency — look there first.
- **Omitting the closing framing sentence.** The memo must explicitly frame itself as "for governance consideration." Without it, the memo reads as decisions the enablement seat is making unilaterally.
- **Using people names anywhere.** Standards partners expect role-names discipline the same way the council pre-read does.

## 6. Stretch — EU AI Act column, AIGP mapping, 15-minute briefing script, refresh-cadence column

### 6.1 EU AI Act third-standard column

Added as a sixth column to the table, with `<!-- org-specific: ... -->` on article numbers beyond the four named in the exercise's stretch prompt.

| Artifact | Primary EU AI Act article(s) |
|---|---|
| Acceptable-use policy | Article 50 (transparency to natural persons interacting with AI systems). Article 4 adjacent (deployer AI literacy) `<!-- org-specific: confirm whether Article 4 language places direct obligation on AUP content -->`. |
| Data-handling SOP | Chapter III high-risk-system obligations `<!-- org-specific: confirm applicable articles for data governance and record-keeping — likely Article 10 (data governance) and Article 12 (record-keeping) -->`. |
| Intake questionnaire | Chapter III classification obligations `<!-- org-specific: confirm Article 6 / 7 for high-risk system classification -->`. |
| Training rosters | Article 4 (AI literacy of deployers' staff). |
| Champion network | Article 4 adjacent. |
| Executive scorecard | `<!-- org-specific: confirm whether monitoring and post-market-surveillance articles (likely Article 72) touch enablement-side scorecards -->`. |
| Kill-switch / rollback | Article 73 (serious-incident reporting). Chapter III (high-risk obligations to maintain post-market monitoring). |
| Redline log | `<!-- org-specific: confirm whether technical-documentation / record-keeping articles (likely Article 11 / 18) apply to redline logs in deployer orgs -->`. |

### 6.2 IAPP AIGP body-of-knowledge mapping sketch

| Artifact | AIGP domain `<!-- org-specific: confirm current BoK domain names from the IAPP AIGP exam blueprint -->` |
|---|---|
| Acceptable-use policy | AI Governance Principles; Implementing Responsible AI Governance `<!-- org-specific -->`. |
| Data-handling SOP | Managing AI Risks (operational controls) `<!-- org-specific -->`. |
| Intake questionnaire | Understanding the AI Life Cycle (scoping and classification) `<!-- org-specific -->`. |
| Training rosters | AI Governance (workforce competence) `<!-- org-specific -->`. |
| Champion network | AI Governance (awareness) `<!-- org-specific -->`. |
| Executive scorecard | Managing AI Risks (monitoring and reporting) `<!-- org-specific -->`. |
| Kill-switch / rollback | Managing AI Risks (incident response) `<!-- org-specific -->`. |
| Redline log | AI Governance (documented processes) `<!-- org-specific -->`. |

### 6.3 15-minute bilateral briefing script with `head-of-ai-governance`

- **Lead with (3 min):** "Here is the map on one page. Two things are missing — I will get to those second." Show the table and point out that no row lists this role as a sole control-design owner. That framing invites redlines rather than approval.
- **Flag (7 min):** The two memo gaps. For each, name the gap in one sentence and the proposed enablement-practice change in one sentence. Explicitly say both are for the architect's consideration, not decisions.
- **Do not try to cover (0 min, explicitly):** The exact GOVERN sub-category IDs, the exact Annex A control IDs, the control-library mapping, or the EU AI Act article interactions. Say "those are for the architect — we have the org-specific markers in place."
- **Close (5 min):** Ask two questions: "Does the architect see this view at least once a quarter?" and "Is the operating-model pattern of split ownership (architect designs, enablement operates, `ai-risk-engineer` on incident-adjacent artifacts) consistent with how you want the certification engagement framed next spring?"

### 6.4 Refresh-cadence column (added to the main table)

| Artifact | Refresh cadence |
|---|---|
| Acceptable-use policy | Biannual; mid-cycle triggered per AUP Section 7 (regulator guidance, accident-path event, vendor DPA change, classification-scheme revision). |
| Data-handling SOP | Biannual; co-refreshed with the AUP in the same cycle. |
| Intake questionnaire (schema) | Architect-cadenced (typically annual with mid-cycle refinement memos from this role). |
| Intake submission corpus | Per-cycle (continuous). |
| Training rosters | Annual with recertification triggers; per-hire for new in-scope staff. |
| Champion network | Per-council for signal; annual roster refresh. |
| Executive scorecard | Monthly publication; annual review of measure set. |
| Kill-switch / rollback | On-trigger (tool change, vendor change, incident); tabletop exercise annual. |
| Redline log | Continuous; archive snapshot per audit window. |

## 7. References

- **Learning material (local):**
  - [Chapter 03 — NIST AI RMF GOVERN and ISO/IEC 42001 for the Enablement Seat](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-103-policy-co-authoring-with-governance/03-nist-ai-rmf-govern-and-iso-iec-42001-for-the-enablement-seat.md)
  - [Chapter 07 — What You Route Out](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-103-policy-co-authoring-with-governance/07-what-you-route-out-counsel-soc-architect.md)
  - [mod-101 Chapter 05 — EU AI Act Article 4 and the Literacy Floor](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-101-role-and-the-org-wide-enablement-operating-model/05-eu-ai-act-article-4-and-the-literacy-floor.md)
  - [mod-104 — Training Programs and AI Literacy Curriculum](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-104-training-programs-and-ai-literacy-curriculum)
  - [mod-105 — Champion Networks and Change Management](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-105-champion-networks-and-change-management)
  - [mod-106 — Outcome Measurement and Executive Reporting](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-106-outcome-measurement-and-executive-reporting)
  - [mod-109 — AI Incident Response and Enablement-Side Rollback](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-109-ai-incident-response-and-enablement-side-rollback)
- **Official standards and frameworks** (the primary sources for the table's columns):
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — RMF 1.0, including the GOVERN function and the AI RMF Playbook.
  - [NIST AI 600-1: Generative AI Profile](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf) — GenAI-specific layer on top of the RMF, relevant to all rows where the tool is generative.
  - ISO/IEC 42001:2023 — AI management system standard. `<!-- org-specific: confirm whether the organization has direct ISO access; the standard text itself is not open-access -->`.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — security-control context behind the SOP and kill-switch rows.
  - [MITRE ATLAS](https://atlas.mitre.org/) — adversarial-technique context for the kill-switch and incident after-action rows.
