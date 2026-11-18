# Exercise 02 — Vendor Vetting and Certification Rubric — Reference Solution

> Module: `mod-111-ai-coe-operations-vendor-management-and-cross-functional-leadership`
> Exercise type: design / worked example
> Exercise brief: [`lessons/mod-111-ai-coe-operations-vendor-management-and-cross-functional-leadership/exercises/exercise-02-vendor-vetting-and-certification-rubric.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-111-ai-coe-operations-vendor-management-and-cross-functional-leadership/exercises/exercise-02-vendor-vetting-and-certification-rubric.md) (in the learning repo)

## 1. Solution overview

The deliverable is a **vendor vetting and certification rubric**: the scored, evidence-anchored artifact the AI CoE uses to turn a prospective (or renewing) AI vendor into one of three states — **certified for scope**, **conditionally certified**, or **not certified / do not sign**. The rubric is run as the main artifact inside the Vendor Vetting service in Exercise 01's catalog.

The certification record is a formal attestation that the CoE, alongside Security, Legal/privacy, Procurement, and Finance, has reviewed the vendor against a consistent set of criteria, that evidence was collected (not asserted), and that the vendor's certification has a **scope**, a **tier**, and an **expiry**. A vendor is never "approved forever"; a vendor is certified to a specific scope for a specific window.

Posture checks this solution encodes:

- **Certification is scoped, not blanket.** A vendor certified to assist with marketing-copy drafting is not thereby certified to touch customer PII. Scope is written down and enforced by the vendor registry row.
- **Certification is tiered.** Tier 1 (restricted-data-capable, strongest controls, fewest vendors) through Tier 3 (general-purpose, public-data-only) have different rubric thresholds and different renewal cadences. The tiers are the reason the rubric is not binary.
- **Evidence is required, not asserted.** For every criterion, the rubric names the evidence type that supports the score. A score without named evidence is a self-report.
- **Risk posture ties to `owasp-ml-top-10`, `mitre-atlas`, and `nist-ai-rmf`** by ID. The threat model is the one the governance council already uses; the rubric does not re-derive it.
- **DACI is explicit across six partner functions.** CoE, Procurement, Security, Legal/privacy, Finance, and the Business Sponsor each have a named role per decision. No single function unilaterally certifies.
- **Recertification is standing.** Tier 1 vendors re-certify annually (scope-dependent) with a 60-day pre-expiry lead time; Tier 2 at 18 months; Tier 3 at 24 months. Early recertification is triggered by events (model change, sub-processor change, incident).
- **Kill / de-certification is pre-committed.** The rubric names the conditions under which a certification is revoked rather than renewed.
- **The record is a product of the CoE.** The vendor registry is a stewarded product (per Exercise 01 Section 3), not an ad-hoc spreadsheet.

## 2. Implementation — worked answer

The pack consists of three artifacts: the rubric template (Section 2.2), the certification record template (Section 2.3), and the worked example showing the rubric applied to a representative vendor scenario (Section 2.4).

### 2.1 Tier definitions

Every certified vendor sits in exactly one tier for its certified scope. A single vendor may carry different tiers for different scopes (e.g., Tier 3 for internal productivity use; Tier 1 for a specific confidential-data workflow after additional controls are established).

| Tier | Scope posture | Example data classes | Rubric minimum score | Re-certification cadence | Example renewal lead time |
|---|---|---|---|---|---|
| **Tier 1 — Restricted** | May be used with regulated / confidential data on named workflows only | Customer PII, financial records, health records (jurisdictional), privileged legal content | ≥ 85 / 100, with no criterion in Band A below threshold | Annual | 60 days pre-expiry |
| **Tier 2 — Confidential** | May be used with internal confidential content and employee operational data; not with regulated data classes | Internal docs, non-PII operational data, synthetic test data | ≥ 70 / 100, with no criterion in Band A below threshold | 18 months | 45 days pre-expiry |
| **Tier 3 — General / Public-data-only** | May be used with public or internal-non-sensitive content only | Public marketing content, public code, openly published reference material | ≥ 55 / 100, with no criterion in Band A below threshold | 24 months | 30 days pre-expiry |
| **Conditional** | Certified for a time-boxed pilot inside a named scope with explicit additional controls | As per pilot's named scope | Rubric score below tier threshold but above Tier-3 floor; conditions named | Expires at pilot end; no automatic promotion | Pilot-end date |
| **Not certified** | Not approved for use in any scope; added to the known-rejected list with reason and re-apply window | n/a | Below any threshold, or Band A criterion unsatisfied | Re-apply window ≥ 6 months | n/a |

### 2.2 Rubric criteria

The rubric is organised in four bands — **A Governance and Risk**, **B Security and Data Handling**, **C Operational Reliability**, **D Commercial and Partnership**. Each criterion has a weight, a scoring scale (0 / 1 / 2 / 3 — see Section 2.2.5), and a named evidence type.

Band A criteria are **gating**: a score of 0 on any Band A criterion is an automatic "not certified / needs remediation", regardless of total score. This prevents a vendor with excellent commercial terms and weak governance from being waved through.

#### 2.2.1 Band A — Governance and Risk (weight: 35)

| # | Criterion | Weight | Evidence type |
|---|---|---|---|
| A1 | Model provenance and version transparency — the vendor publishes which model(s) underpin which product surface, and provides notice of material changes | 5 | Vendor documentation; change-log policy; most recent change-log excerpt |
| A2 | Threat-model alignment against `owasp-ml-top-10` — vendor can name the OWASP ML Top 10 rows it mitigates and the ones it considers out-of-scope | 5 | Written response; third-party ML security assessment if available |
| A3 | Adversarial-posture alignment against `mitre-atlas` — vendor can name the ATLAS techniques within its threat model | 5 | Written response; red-team summary; penetration test extract |
| A4 | AI Risk Management framework alignment — vendor attests to `nist-ai-rmf` (GOVERN / MAP / MEASURE / MANAGE) or an equivalent named framework (e.g., ISO/IEC 42001) | 5 | Attestation letter; framework crosswalk document |
| A5 | Training-data posture — vendor discloses whether customer data is used to train shared models; opt-out or default-off posture | 5 | DPA language; contractual commitment |
| A6 | Sub-processor list and change notice — vendor publishes sub-processors and provides N-day advance notice of changes | 3 | Sub-processor list URL; DPA notice clause |
| A7 | Human-in-the-loop controls where applicable — vendor's product affords human review gates on high-stakes outputs; no "autonomous action on customer records" by default | 3 | Product documentation; configuration evidence |
| A8 | Jurisdictional and residency posture — vendor's processing locations are declared, align with the org's residency requirements | 4 | Hosting-region documentation; contractual residency clause |

#### 2.2.2 Band B — Security and Data Handling (weight: 30)

| # | Criterion | Weight | Evidence type |
|---|---|---|---|
| B1 | Industry-recognised independent security attestation (e.g., SOC 2 Type II, ISO/IEC 27001) current within 12 months | 5 | Attestation report; current certificate |
| B2 | Encryption at rest and in transit — AES-256 at rest, TLS 1.2+ in transit, with documented key management | 3 | Security whitepaper; architecture excerpt |
| B3 | Access controls — SSO support (SAML 2.0 / OIDC), SCIM provisioning, role-based access controls, MFA enforcement | 4 | Admin documentation; config evidence |
| B4 | Audit log availability and retention — who-did-what-when logs available to the customer, with named retention | 3 | Admin documentation; sample log export |
| B5 | Data isolation — confirmed segregation of the organisation's data from other tenants; no cross-tenant inference | 4 | Architecture doc; penetration-test summary |
| B6 | Vulnerability-disclosure and incident-notification SLAs — vendor commits to notification within a named window after a confirmed incident | 4 | DPA incident clause; most recent public incident disclosure if applicable |
| B7 | Right-to-erasure and data-subject-request handling — vendor honours DSRs within a named SLA and propagates into any retrieval index | 4 | DPA clause; operational runbook |
| B8 | Prompt-injection and output-safety controls — vendor demonstrates controls against prompt injection and unsafe outputs | 3 | Security whitepaper; red-team summary |

#### 2.2.3 Band C — Operational Reliability (weight: 20)

| # | Criterion | Weight | Evidence type |
|---|---|---|---|
| C1 | Published uptime SLA with service credits | 4 | SLA document; historic uptime report |
| C2 | Status page and incident-communication history | 2 | Public status page; past 12 months of major-incident posts |
| C3 | Named enterprise support channel with response-time SLAs by severity | 3 | Support contract |
| C4 | Deprecation and change-management policy — vendor commits to a notice window on breaking changes | 3 | Change-management policy; past change notices |
| C5 | Data portability — the customer can export their data (prompts, outputs, configurations) in a documented format | 3 | Export documentation; demonstrated export |
| C6 | Observability — the customer can see usage, cost, and error signals at the account grain | 3 | Admin console / API evidence |
| C7 | Rate-limit, throttling, and capacity-plan transparency | 2 | Documentation; vendor confirmation |

#### 2.2.4 Band D — Commercial and Partnership (weight: 15)

| # | Criterion | Weight | Evidence type |
|---|---|---|---|
| D1 | DPA, MSA, and (if in scope) BAA / SCC terms signable without material unresolved issues | 4 | Signed / signable contracts; Legal/privacy sign-off memo |
| D2 | Pricing model fits the usage shape — predictable budget envelope per mod-107 Exercise 01 | 3 | Pricing proposal; cost-model reconciliation |
| D3 | Reference customers of comparable scope willing to speak to the reviewing organisation | 2 | Reference contact list |
| D4 | Roadmap transparency — vendor is willing to share near-term roadmap under NDA | 2 | Roadmap conversation notes |
| D5 | Exit and portability terms — contract supports exit without vendor-lockout tactics (data return in portable format, cooperation window) | 4 | Exit clause; portable-format commitment |

#### 2.2.5 Scoring scale (per criterion)

| Score | Meaning |
|---|---|
| 0 | Evidence absent, or evidence present but materially inconsistent with the criterion |
| 1 | Partial evidence — the vendor has some posture but with named gaps |
| 2 | Evidence present and satisfactory for Tier 2 / Tier 3 use |
| 3 | Evidence present and satisfactory for Tier 1 use |

Weighted score = Σ (criterion_score × criterion_weight / 3). Total possible = sum of weights = 100.

**Band A gating rule.** If any Band A criterion scores 0, the vendor is "not certified / needs remediation" regardless of total. Band A floor rule for Tier 1: every Band A criterion must score ≥ 2.

### 2.3 Certification record template

```
Vendor Certification Record
Record ID:                VC-<vendor-slug>-<YYYY>-<NN>
Vendor:                   <vendor legal name>
Product(s) in scope:      <specific product surfaces; not "the vendor's platform">
Certified tier:           Tier 1 / Tier 2 / Tier 3 / Conditional / Not certified
Scope boundary:           <workflows, data classes, user populations, geographies in scope>
Explicit out-of-scope:    <what the certification does NOT cover>
Effective:                <YYYY-MM-DD>
Expires:                  <YYYY-MM-DD>
Re-certification due:     <expires minus tier lead time>
Rubric total (out of 100): <score>
Rubric band detail:       <A: XX / 35, B: XX / 30, C: XX / 20, D: XX / 15>
Band A gating:            Pass / Fail-at-criterion <ID>
Conditions (if any):      <additional controls required for conditional certification>
Signatories (role names):
  AI Enablement Lead      — D on the certification record
  Procurement AI-sourcing lead — A on contracting
  Security intake partner — A on the security posture
  Legal/privacy partner   — A on the DPA / data posture
  Finance partner (per mod-107) — C on the cost envelope
  Business sponsor        — A on the business scope
  head-of-ai-governance (L60) — A on tier at Tier 1
```

The record is stored in the vendor registry — the stewarded product per Exercise 01 Section 3. The registry is the system of record. A certification that is not in the registry is not a certification.

### 2.4 Worked example — vendor certification for a generative-text SaaS

> This worked example uses a generic representative vendor scenario — a plausible generative-text SaaS. It is **not** a review of any specific real-world product. Specific vendor names and scored numbers are left as `<!-- org-specific: … -->` for the learner to fill in from their actual vetting.

#### 2.4.1 Scenario

- Requesting business unit: Marketing.
- Requested use: brand-safe marketing-copy drafting; no PII inputs; public outputs reviewed by human marketer before publication.
- Candidate tier: **Tier 3 (general / public-data-only)**, with an explicit re-apply route to Tier 2 later if the usage scope expands.
- Alternative candidates: evaluated under the mod-102 intake questionnaire; this worked example focuses on the vetting of the preferred candidate.

#### 2.4.2 Band-A scoring walk-through (abbreviated)

| # | Criterion | Score | Notes |
|---|---|---|---|
| A1 | Model provenance and version transparency | 2 | Vendor publishes model family and version; change-log for breaking changes present. Not Tier-1-grade (no explicit advance notice on silent model updates). Satisfies Tier 3. |
| A2 | `owasp-ml-top-10` alignment | 2 | Vendor response addresses LLM-adjacent rows; names structured-output guardrails and prompt-injection mitigation; no detailed row-by-row map. Satisfies Tier 3. |
| A3 | `mitre-atlas` alignment | 1 | Vendor can discuss adversarial ML at a high level; no mapped technique list. Gap documented. Satisfies Tier 3 floor but limits Tier-2 route. |
| A4 | `nist-ai-rmf` or equivalent | 2 | Vendor attests to NIST AI RMF alignment; ISO/IEC 42001 roadmap in progress. Satisfies Tier 3. |
| A5 | Training-data posture | 3 | Default-off on training with customer data; contractual commitment in DPA. Tier-1-grade. |
| A6 | Sub-processor list and change notice | 2 | Public sub-processor list; 30-day notice. Satisfies Tier 2 / 3. |
| A7 | Human-in-the-loop by default | 3 | Product does not take autonomous action on customer records; drafting workflow by design. Tier-1-grade. |
| A8 | Jurisdictional / residency | 1 | Vendor operates in-region for the org, but residency contractual commitment is weaker than ideal. Flag for the DPA redlines. Satisfies Tier 3 floor. |
| Band A weighted contribution | 25 / 35 | Band A floor: no 0; Tier 3 threshold met |

Band B, C, D would be scored in the same way with their evidence types. For brevity, the worked example assumes the vendor scores **Band B 22 / 30, Band C 14 / 20, Band D 10 / 15 → Total 71 / 100**.

#### 2.4.3 Verdict

- **Tier**: Tier 3 (general / public-data-only).
- **Scope boundary**: Marketing-copy drafting; public-data prompts and outputs only; human review before publication; no PII, no customer records, no confidential material; same-region processing per the DPA addendum.
- **Explicit out-of-scope**: customer PII, financial data, regulated content; no auto-publish integrations; no training-data contribution.
- **Expiry**: 24 months from effective date.
- **Re-certification due**: 24 months minus 30 days = effective + 23 months.
- **Conditions**: none (clean Tier-3 certification).
- **Route to Tier 2**: available at any time with re-submission that includes an upgraded residency commitment (A8), an ATLAS-technique crosswalk (A3), and a prompt-injection red-team summary (B8).

#### 2.4.4 Registry entry (abbreviated JSON)

```json
{
  "record_id": "VC-GEN-TEXT-SAAS-2026-01",
  "vendor": "<!-- org-specific: vendor legal name -->",
  "products_in_scope": ["<!-- org-specific: product surface -->"],
  "certified_tier": "Tier 3",
  "scope_boundary": "Marketing-copy drafting; public-data only; human review before publication",
  "out_of_scope": ["customer PII", "financial data", "auto-publish integrations", "training-data contribution"],
  "effective": "<!-- org-specific: YYYY-MM-DD -->",
  "expires": "<!-- org-specific: YYYY-MM-DD -->",
  "recertification_due": "<!-- org-specific: YYYY-MM-DD -->",
  "rubric_total": 71,
  "band_breakdown": {"A": 25, "B": 22, "C": 14, "D": 10},
  "band_a_gating": "pass",
  "conditions": [],
  "signatories": {
    "ai_enablement_lead": "D",
    "procurement_lead": "A",
    "security_partner": "A",
    "legal_privacy_partner": "A",
    "finance_partner": "C",
    "business_sponsor": "A",
    "head_of_ai_governance": "I"
  },
  "linked_contracts": ["<!-- org-specific: MSA, DPA, order-form references -->"],
  "linked_security_reviews": ["<!-- org-specific: Security intake record ID -->"],
  "linked_mod102_intake": "<!-- org-specific: mod-102 intake ticket ID -->",
  "notes": "Route to Tier 2 available on re-submission with upgraded residency, ATLAS crosswalk, prompt-injection red-team summary.",
  "status": "certified"
}
```

### 2.5 De-certification triggers

A certification is revoked (not simply allowed to expire) on any of:

- An AI incident per mod-109 Sev-2+ traceable to the vendor's product within the certified scope.
- A material change in the vendor's model or product that alters the basis of the rubric score (e.g., a model substitution not covered by A1 change-log policy).
- A sub-processor change that violates A6 notice commitments or introduces a sub-processor that fails the organisation's Security / Legal review.
- A security incident on the vendor's side above a severity threshold named in B6.
- A regulatory change (e.g., EU AI Act transparency obligations, sector-specific regulation) that invalidates the posture of the certification without a feasible remediation path inside the remaining window.
- The vendor fails to deliver remediation on a conditional certification by the pilot-end date.
- A consolidation decision per mod-107 Exercise 05 retires the vendor's scope from the stack.

De-certification is a Driver-A decision by the AI Enablement Lead with Approver on the governance council for Tier 1 vendors; Procurement executes contract wind-down.

### 2.6 Re-certification choreography

The CoE opens a re-certification work item at `expiry - tier_lead_time`:

| Step | Owner | Rhythm |
|---|---|---|
| Re-certification work item created in the intake queue | Enablement Operations Analyst | At `expiry - lead_time` |
| Evidence refresh request to the vendor | AI Enablement Lead | Within 5 business days |
| Security review refresh | Security intake partner | Within 10 business days of evidence receipt |
| Legal/privacy review refresh (DPA, SCC, sub-processors) | Legal/privacy partner | Within 10 business days of evidence receipt |
| Finance envelope refresh (per mod-107) | Finance partner | Within 10 business days of evidence receipt |
| Re-scored rubric and verdict memo | AI Enablement Lead | Within 5 business days of all refreshes |
| Sign on new certification record (or de-certification memo) | All signatories per Section 2.3 | Before expiry date |

If the re-certification does not complete before expiry, the certification lapses on the expiry date. The vendor's product moves to the "pending re-cert" state in the registry and is not usable for new workflows until the new record is signed. Existing in-scope usage continues *only* under an explicit grace-period memo from the AI Enablement Lead and head-of-ai-governance; grace periods are ≤ 30 days and are logged.

### 2.7 Decision rationale — why this shape, not another

- **Why tiered, not binary.** A binary "approved / not approved" rubric collapses two distinct decisions (is the vendor safe for public-data marketing content? is the vendor safe for customer PII?) into one, and in practice every edge case gets the lenient answer. Tiers force the harder question — *what is the vendor certified for?* — to be written down.
- **Why Band A is gating.** The three failure modes the CoE cannot tolerate are (a) a vendor who will not disclose when the underlying model changes, (b) a vendor who trains on customer data without opt-out, and (c) a vendor who has no coherent AI risk-management framework. These are Band A rows A1, A5, A2/A3/A4. Letting a strong commercial posture outweigh a weak A1 posture is exactly the failure Band A gating prevents.
- **Why evidence types are named per criterion.** Without named evidence, scoring devolves into "the vendor seemed credible on the call". Evidence types force the vetting conversation to produce an artifact that survives the call.
- **Why risk posture ties to OWASP ML Top 10, MITRE ATLAS, and NIST AI RMF.** Those are the official sources the governance council, Security partner, and Applied AI Engineer already use. Naming them by ID in Band A is what lets the three downstream functions converge on a shared threat model without re-negotiating it per vendor. Same discipline as mod-110 Exercise 01's commissioning brief Section 6.
- **Why DACI spans six partner functions.** The CoE cannot unilaterally certify; Procurement owns contracting; Security owns security sign-off; Legal/privacy owns the DPA; Finance owns the envelope per mod-107; the business sponsor owns the business scope. Blurring these into a single CoE signature produces certifications that unwind when any of the five other functions later discovers it was not consulted.
- **Why recertification is standing, not ad-hoc.** AI vendor posture shifts materially within 12-24 months — model substitutions, sub-processor additions, pricing model changes, roadmap pivots. Ad-hoc recert reliably misses these. Standing recert with scope-dependent cadence catches them before contract renewal.
- **Why de-certification is pre-committed.** Revoking a certification under sunk-cost pressure (budget already paid, users already trained) is near-impossible. Pre-committing the triggers at certification time is the moment to write them down. Same discipline as mod-110 Exercise 01 Section 10.
- **Why the record is stored in a registry, not a shared drive.** A shared-drive spreadsheet drifts, gets out of sync with reality, and becomes untrustworthy. The registry is a stewarded CoE product; it is the single source of truth and is referenced by the mod-102 intake questionnaire and the mod-109 incident runbook.
- **Why scope is written down, not implied.** The dominant failure mode in observed CoEs is "we certified this vendor for X and over 18 months they slid into Y without re-review". Explicit scope boundary + explicit out-of-scope is what makes scope slide detectable at the monthly operational review or the quarterly portfolio.

## 3. Validation steps

1. **Tiers defined with scope posture, data classes, minimum score, re-cert cadence, and lead time.** All five columns populated per tier.
2. **Rubric has four bands** (A Governance and Risk, B Security and Data Handling, C Operational Reliability, D Commercial and Partnership) with weights summing to 100.
3. **Band A is gating.** A rule stating "0 on any Band A → not certified regardless of total" is present.
4. **Every criterion has a weight AND a named evidence type.** A criterion without named evidence is a self-report, not a criterion.
5. **Band A names `owasp-ml-top-10`, `mitre-atlas`, and `nist-ai-rmf` by ID.** Generic "has considered risks" is insufficient.
6. **Scoring scale is 0 / 1 / 2 / 3** with a stated meaning for each score that ties to tier threshold (score 3 is Tier-1-grade).
7. **Certification record template has: record ID, vendor, products in scope, tier, scope boundary, explicit out-of-scope, effective date, expiry, re-cert due date, rubric score, band breakdown, Band A gating result, conditions, signatories (role names), linked contracts.**
8. **Signatory block names six partner functions** (CoE, Procurement, Security, Legal/privacy, Finance, Business Sponsor) each with a DACI role; Tier 1 adds head-of-ai-governance as A.
9. **Worked example is present** and demonstrates Band-A scoring at the criterion level.
10. **De-certification triggers are pre-committed** with ≥ 5 triggers including ≥ 1 outside vendor control (regulatory change, consolidation decision).
11. **Re-certification choreography** names owner and rhythm per step; grace-period posture is named with a cap.
12. **Role-name addressing throughout.** No personal names.
13. **`org-specific` tags on all unverifiable specifics** (vendor names, scored numbers in the worked example beyond illustrative Band A, effective dates, IDs).
14. **No invented specifics about real vendors.** The worked example is explicitly a generic representative scenario; no real-world vendor is scored or implied.

## 4. Rubric / review checklist

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | Tiers (3 or 4 named tiers + conditional + not certified) with scope posture and re-cert cadence | 10 | Binary rubric, or tiers without scope posture. |
| R2 | Four scoring bands (A/B/C/D) with weights summing to 100 | 10 | Bands collapsed or weights imbalanced. |
| R3 | Band A is explicitly gating | 10 | Total-score-only threshold. |
| R4 | Every criterion has a weight AND a named evidence type | 15 | Any criterion missing evidence type. |
| R5 | Band A names `owasp-ml-top-10`, `mitre-atlas`, `nist-ai-rmf` by ID | 10 | Generic risk coverage. |
| R6 | Scoring scale with per-score meaning and tier-threshold tie-in | 5 | Ambiguous scoring. |
| R7 | Certification record template has all 13 fields | 10 | Missing field(s). |
| R8 | Signatory block names six partner functions with DACI roles | 10 | Single-function signature or role-conflation. |
| R9 | Worked example present, criterion-level scoring shown | 10 | Score given without criterion-level demonstration. |
| R10 | De-certification triggers pre-committed with ≥ 5 incl. ≥ 1 outside vendor control | 5 | Fewer or all vendor-controlled. |
| R11 | Re-certification choreography with owner + rhythm per step; grace-period cap | 5 | Ad-hoc re-cert or no grace cap. |

**Pass threshold:** ≥ 85/100 and no R3 / R4 / R5 / R8 fail. R3 (Band-A gating), R4 (evidence per criterion), R5 (official sources named), and R8 (multi-function DACI) are the four discriminators between a rubric the organisation can defend to Procurement, Security, and Legal and a rubric that looks good in a deck but produces unanchored certifications.

## 5. Common mistakes

- **Binary approved / not approved rubric.** This forces every vendor to the lenient answer. Tier the rubric so the harder question — *for what scope?* — is written down.
- **Scoring without named evidence.** "Vendor is strong on security" is a self-report. Named evidence (SOC 2 Type II report, DPA clause excerpt, admin console screenshot) is what makes scoring auditable.
- **Total-score threshold without Band-A gating.** A vendor with excellent commercial terms and weak training-data posture scores above threshold on total but should not be certified. Band A gating prevents this.
- **Certification without a scope boundary.** The dominant failure mode: "we certified them for X" then users route Y through the same vendor. Scope boundary + explicit out-of-scope is what makes scope slide detectable.
- **Single-function signature.** The CoE cannot unilaterally certify; Procurement, Security, Legal, Finance, and the business sponsor each own a facet. Blurring produces certifications that unwind when any of the other functions later surfaces an objection.
- **Ad-hoc re-certification.** AI vendors evolve materially within 12-24 months; ad-hoc misses model substitutions, sub-processor additions, and pricing shifts. Standing re-cert with tier-dependent cadence catches these.
- **De-certification only on incident.** Regulatory change, consolidation, and sub-processor drift are equally valid triggers. The pre-committed trigger list must include ≥ 1 outside vendor control.
- **Vendor-registry drift from reality.** A spreadsheet in a shared drive goes stale. The registry is a stewarded product with a quarterly audit cycle (per Exercise 01 Section 3).
- **Scoring the vendor by sales-call impression.** The rubric is anchored to evidence, not rapport. If the vendor's sales team is excellent and the vendor's security documentation is thin, the rubric should reflect the documentation.
- **Scoping certifications to "the vendor's platform".** A vendor often has multiple product surfaces with different data postures and different risk profiles. Scope the certification to specific product surfaces, not the vendor as a company.

### 5.1 Stretch — portfolio-level vendor view

For a mature program, the registry supports a portfolio-level view at the quarterly strategic review (per Exercise 03): vendors by tier, vendors by business unit, vendors by data class, vendors approaching re-certification, vendors with conditional terms, vendors in de-certification. The portfolio view is what feeds the mod-107 Exercise 05 consolidation decision (concentrated redundancy in Tier 3 general-productivity vendors is a classic consolidation signal). A single-vendor record without a portfolio view risks optimising each certification while the stack as a whole fragments.

## 6. References

- **Learning material (local):**
  - [mod-102 — Selecting and Rolling Out AI Tools](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-102-selecting-and-rolling-out-ai-tools) — the intake questionnaire that routes a request into the Vendor Vetting service.
  - [mod-103 — Policy Co-authoring with Governance](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-103-policy-co-authoring-with-governance) — the AUP that the certification scope must be consistent with.
  - [mod-106 — Outcome Measurement and Executive Reporting](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-106-outcome-measurement-and-executive-reporting) — the scorecard rows for vendor stack health and certification currency.
  - [mod-107 — Budget, ROI, and Build-vs-Buy at Org Scope](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-107-budget-roi-and-build-vs-buy-at-org-scope) — Finance envelope (Exercise 01), Procurement and Finance partnership (Exercise 04), and consolidation patterns (Exercise 05) consumed by the vetting.
  - [mod-108 — Industry and Regulatory Flavours of Enablement](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-108-industry-and-regulatory-flavours-of-enablement) — sector-specific posture (healthcare, finance, public sector) that modifies tier thresholds and Band A evidence expectations.
  - [mod-109 — AI Incident Response and Enablement-Side Rollback](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-109-ai-incident-response-and-enablement-side-rollback) — the Sev-2+ definition that is a de-certification trigger.
  - [Exercise 01 — CoE Service Catalog and Intake Cadence](../exercise-01-coe-service-catalog-and-intake-cadence/SOLUTION.md) — the Vendor Vetting service row runs this rubric; the vendor registry is listed as a CoE product in Section 3 of the catalog.
  - [Exercise 03 — Quarterly Operating Ritual Plan](../exercise-03-quarterly-operating-ritual-plan/SOLUTION.md) — the vendor-portfolio review is a standing agenda item at the quarterly strategic review.
- **Official standards and frameworks:**
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — Band A criterion A2 is scoped against this list by ID.
  - [MITRE ATLAS](https://atlas.mitre.org/) — Band A criterion A3 maps vendor posture against adversarial-technique context.
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — Band A criterion A4 is scoped against GOVERN / MAP / MEASURE / MANAGE; underpins the standing re-certification discipline.
