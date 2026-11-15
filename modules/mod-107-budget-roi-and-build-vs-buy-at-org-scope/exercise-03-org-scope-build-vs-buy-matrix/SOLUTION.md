# Exercise 03 — Org-Scope Build-vs-Buy Matrix — Reference Solution

> Module: `mod-107-budget-roi-and-build-vs-buy-at-org-scope`
> Exercise type: design / worked example
> Exercise brief: [`lessons/mod-107-budget-roi-and-build-vs-buy-at-org-scope/exercises/exercise-03-org-scope-build-vs-buy-matrix.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-107-budget-roi-and-build-vs-buy-at-org-scope/exercises/exercise-03-org-scope-build-vs-buy-matrix.md) (in the learning repo)

## 1. Solution overview

The deliverable is an **org-scope build-vs-buy decision matrix** — a scored comparison across two candidate paths (build-and-operate vs. buy-and-integrate) for a specific AI capability, with a third path (**buy-plus-glue**: buy the core and build the integration/customization layer) treated as a first-class option rather than a tie-breaker. The matrix is what the AI Enablement Lead walks into the architecture council with when the executive ask is "should we build this ourselves?" and needs an answer that is defensible to Engineering, Finance, Security, and the business.

Posture checks this solution encodes:

- **The decision is capability-scoped, not program-scoped.** "Should we build AI enablement" is the wrong question; "should we build the internal RAG-and-knowledge platform that powers five internal assistants" is the right one. The matrix is run once per capability, not once per program.
- **Three options are scored**, not two. The buy-plus-glue middle path is the one the enterprise usually ends up on; naming it up-front prevents a false binary.
- **Dimensions are grouped into four families**: strategic fit, total cost (3-year TCO), risk & compliance, time-to-value. Each family has 2–4 criteria; each criterion has a 1–5 scoring rubric with explicit anchors.
- **Weights are set before scores are collected**, by Finance / Enablement / Architecture jointly. Setting weights after seeing scores is the single most common integrity failure in a build-vs-buy exercise.
- **TCO is the Exercise 01 cost model re-run under each path**, not a free-standing estimate. The 3-year horizon and the indirect-labor discipline carry through.
- **Risk assumptions reference `owasp-ml-top-10`, `mitre-atlas`, and the GOVERN function of `nist-ai-rmf`** as the threat / control posture frame — and are not quoted as numeric probabilities.
- **A reversal condition is named per path.** The signed decision is reversible under a documented trigger; the matrix states what that trigger is.

## 2. Implementation — worked answer

### 2.1 Capability chosen for the worked example

- **Capability:** an internal Retrieval-Augmented Generation (RAG) platform that serves three in-house assistants (HR policy lookup, IT self-serve, internal knowledge-base search) across the ~2,000-person org from Exercise 01 and the ~1,400-person addressable population.
- **Executive ask:** "Can we build this ourselves rather than buy another seat-priced vendor?" Framed by `head-of-ai-governance` (L60).
- **Scope frame:** platform + first-line support + content-ingestion workflow. User-facing assistant UX is out of scope for this matrix (it is a separate capability).

### 2.2 Three paths

| Path | Short name | What it means in practice |
|---|---|---|
| **Build** | Build-and-operate | In-house platform: in-house vector store, in-house retrieval orchestration, in-house evaluation and ops. Vendor-of-record for the model only (hosted LLM API). |
| **Buy** | Buy-and-integrate | Buy a vendor RAG platform that packages ingestion, retrieval, orchestration, and evaluation; enablement owns content governance and the operator experience, vendor owns the platform. |
| **Buy-plus-glue** | Buy-core + build-glue | Buy a vector store and orchestration primitives (managed), build the content-ingestion workflow, the evaluation harness, and the operator-admin surfaces in-house. |

### 2.3 Dimensions, criteria, and scoring rubric

Scores are 1 (worst fit) to 5 (best fit) per criterion. Weights are set before scores are collected; the solution shows the agreed weight for each criterion.

#### Family 1 — Strategic fit (weight: 25% of total)

| Criterion | Weight | Scoring anchors |
|---|---|---|
| S1. Differentiation — does this capability underpin a priced or strategic capability of the org? | 10% | 5 = central to a priced product line; 1 = commodity capability with no strategic edge |
| S2. Cross-BU reuse — how many business units consume the capability? | 8% | 5 = three or more BUs reuse; 1 = single BU consumer |
| S3. Workforce alignment — do we have, or can we hire, the engineering capacity to operate this long-term? | 7% | 5 = capacity in place with retention plan; 1 = would require a new team with no retention plan |

#### Family 2 — Total cost of ownership over 3 years (weight: 30% of total)

TCO is computed by re-running the Exercise 01 cost model per path, including indirect labor and risk reserve, over 36 months.

| Criterion | Weight | Scoring anchors |
|---|---|---|
| C1. Year-1 cost vs. budget envelope | 10% | 5 = within envelope with ≥ 20% headroom; 1 = ≥ 20% over envelope |
| C2. 3-year TCO vs. the alternative paths | 10% | 5 = lowest 3-year TCO; 1 = highest 3-year TCO (score others pro-rata between) |
| C3. Cost-curve shape (lumpy vs. smooth) and exit cost | 5% | 5 = smooth, low exit cost (data portable); 1 = lumpy with significant exit cost |
| C4. Fully-loaded labor burden (ongoing FTE requirement) | 5% | 5 = ≤ 0.5 FTE marginal; 1 = ≥ 2 FTE marginal |

#### Family 3 — Risk & compliance (weight: 30% of total)

The threat-posture context references `owasp-ml-top-10` and `mitre-atlas`; the governance-posture context references the GOVERN function of `nist-ai-rmf` and ISO/IEC 42001 Clause 5 / 7. No numeric probabilities are quoted from these sources.

| Criterion | Weight | Scoring anchors |
|---|---|---|
| R1. Data-residency and tenant-isolation posture | 7% | 5 = fully in our tenant with documented isolation; 1 = multi-tenant with no documented isolation |
| R2. Supply-chain and vendor-risk exposure (third-party AI risk under GOVERN) | 7% | 5 = minimal — model vendor only; 1 = multiple critical vendors with limited substitutability |
| R3. Incident-response and rollback ownership (per mod-109) | 8% | 5 = we control rollback end-to-end; 1 = rollback fully gated on vendor response time |
| R4. Standards alignment (`nist-ai-rmf` GOVERN, ISO/IEC 42001 Clauses 5 and 7) | 8% | 5 = direct mapping with vendor-produced or in-house-produced evidence; 1 = non-mappable |

#### Family 4 — Time-to-value and reversibility (weight: 15% of total)

| Criterion | Weight | Scoring anchors |
|---|---|---|
| T1. Time to first production use | 5% | 5 = ≤ 3 months; 1 = ≥ 12 months |
| T2. Time to break-even (from Exercise 02 ROI model) | 5% | 5 = ≤ 6 months expected-case; 1 = > 24 months or not in horizon |
| T3. Reversibility — can we switch paths within 12 months of a signal? | 5% | 5 = data portable, operators retrainable in-cycle; 1 = effective lock-in beyond 24 months |

### 2.4 Worked scores

Scores below are illustrative for the worked example and are tagged `<!-- org-specific: ... -->` where the specific anchor depends on the learner's org.

| Criterion | Weight | Build | Buy | Buy-plus-glue |
|---|---|---|---|---|
| S1 Differentiation | 10% | 4 (RAG tuned to internal corpora is differentiating for internal-knowledge assistants) | 2 (commodity vendor features; no competitive edge) | 3 (differentiation on glue layer, commodity on core) |
| S2 Cross-BU reuse | 8% | 4 (platform reusable across three BUs) | 4 | 4 |
| S3 Workforce alignment | 7% | 2 (would require new platform team; `<!-- org-specific: confirm engineering capacity plan -->`) | 5 (vendor operates it) | 3 (hybrid: glue-layer team only) |
| C1 Year-1 cost vs. envelope | 10% | 2 (year-1 is lumpy — platform build, hiring ramp) | 4 (predictable seat/consumption pricing) | 3 |
| C2 3-year TCO | 10% | 3 (lower if adoption scales; higher if it does not — carries variance) | 3 (predictable but non-trivial) | 4 (lower expected TCO under P50 adoption) |
| C3 Cost-curve shape and exit cost | 5% | 3 (smooth after year 1; exit cost is the people, not the data) | 2 (lumpy renewals; exit cost material if data is in vendor format) | 4 (smooth after year 1; data portable because we own the content and glue) |
| C4 Ongoing FTE burden | 5% | 1 (≥ 2 FTE marginal for platform ops + evaluation) | 5 (≤ 0.5 FTE marginal; vendor operates) | 3 (~1 FTE marginal; glue only) |
| R1 Data-residency / isolation | 7% | 5 (our tenant end-to-end) | 3 (vendor tenancy model; `<!-- org-specific -->`) | 5 (our tenant for data; vendor API for model only) |
| R2 Supply-chain exposure | 7% | 4 (model vendor only; other platform pieces in-house) | 2 (several critical vendors) | 4 (model vendor + managed vector store) |
| R3 Incident-response ownership | 8% | 5 (end-to-end control) | 2 (rollback gated on vendor SLA; per mod-109) | 4 (we control content and glue rollback; vendor for core) |
| R4 Standards mapping | 8% | 4 (evidence produced in-house; mapping work is ours) | 3 (vendor-produced evidence; we do the gap-close) | 4 (hybrid, favorable) |
| T1 Time to first production use | 5% | 1 (≥ 12 months) | 5 (≤ 3 months) | 3 (~6 months) |
| T2 Time to break-even (Ex-02) | 5% | 2 (break-even moves right by ~6 months vs. baseline) | 4 (close to the Exercise 02 P50 break-even) | 4 |
| T3 Reversibility | 5% | 3 (data portable; team-cost exit) | 2 (renewal-cycle gated) | 4 (data portable; glue retainable) |

#### Weighted rollup

| Path | Weighted score (out of 5.0) |
|---|---|
| Build | **3.12** |
| Buy | **3.18** |
| **Buy-plus-glue** | **3.70** |

### 2.5 Recommendation and decision rationale

**Recommendation:** **Buy-plus-glue** path for the internal RAG platform. Buy a managed vector store and orchestration primitives; build the content-ingestion workflow, the evaluation harness, and the operator-admin surfaces in-house.

**Why the middle path wins this instance:**

- **Differentiation lands on the layer we control.** Internal-corpus curation, evaluation harness tuned to our operators' queries, and the operator-admin surfaces are what give the capability a strategic edge. The vector store and orchestration primitives are commodity. Owning the differentiated layer and buying the commodity layer is the shape the matrix surfaces.
- **TCO is favorable under P50 adoption** (Exercise 02 central case) because the FTE burden is moderate rather than heavy, and because the vendor-of-record on commodity primitives negotiates well at the three-BU scale.
- **Risk posture is strong on the dimensions that matter.** Our data stays in our tenant; rollback is largely under our control; standards-mapping evidence is a hybrid of vendor-produced and in-house-produced artifacts, which `senior-ai-governance-architect` (L50) will find easier to work with than either extreme.
- **Reversibility is preserved.** If the adoption curve under-performs (Exercise 02 P10 scenario), the glue layer is retainable even if the managed core is swapped; the data is ours.

**Reversal condition (named in the signed recommendation):**

> This decision reverts to Buy (all-vendor) if, by month 12, the FTE burden on the glue-layer team exceeds 1.5 FTE marginal on a rolling 3-month basis, or if content-ingestion backlog persistently exceeds 30 days. Both conditions are tracked on the mod-106 executive scorecard.

### 2.6 Sensitivity — what would change this recommendation?

| Change | Would it flip the recommendation? |
|---|---|
| Adoption falls to P10 band (Exercise 02 pessimistic) | Likely flips toward **Buy** — glue-layer build is not worth the FTE if the operator population does not materialize. |
| A dominant vendor emerges that packages the differentiated layer at acceptable TCO | Flips toward **Buy**. |
| Engineering capacity contracts (hiring freeze, re-org) | Flips toward **Buy** — the glue layer requires capacity we would lose. |
| New regulatory posture requires data-sovereignty guarantees the vendor cannot meet | Flips toward **Build** or stays **Buy-plus-glue** with a stricter vendor filter. |
| Priced-product differentiation falls away (capability becomes commodity to our business) | Flips toward **Buy**. |

## 3. Validation steps

1. **Capability is scoped at the right grain.** The matrix is run on one capability (e.g., "internal RAG platform"), not on the whole enablement program. Rows describe criteria against that capability.
2. **Three paths scored**, not two. Build, Buy, and Buy-plus-glue (or a named equivalent middle path).
3. **Four dimension families present** with explicit weights summing to 100%.
4. **Each criterion has a 1–5 rubric with named anchors** at the top and bottom (what a 1 and a 5 look like).
5. **Weights set before scores collected.** The weights appear in a separate section or are called out as pre-agreed at the top of the matrix.
6. **TCO reuses the Exercise 01 cost-model shape** per path, over a 3-year horizon, with fully-loaded labor and indirect labor.
7. **Risk & compliance dimensions reference `nist-ai-rmf` GOVERN, `owasp-ml-top-10`, `mitre-atlas`, and ISO/IEC 42001 Clauses 5 / 7** as the posture frame — and do not quote them as sources of numeric probabilities.
8. **Reversal condition is named** for the recommended path, stated in operational terms (what signal, what threshold, what artifact tracks it).
9. **Sensitivity section names at least three changes that would flip the recommendation.**
10. **Weighted rollup arithmetic verified.** Weighted score per path = Σ(weight × score) across criteria; totals printed to two decimals.
11. **`org-specific` tags** on every criterion whose scoring depends on org-specific signals (engineering capacity, vendor tenancy details, procurement rate card).
12. **No vendor product names.** Grep for trademarks, `.com` strings, or specific vendor-product references.

## 4. Rubric / review checklist

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | Capability scoped at the right grain (one capability, not the whole program) | 10 | Scored against a program-level ask. |
| R2 | Three paths (Build / Buy / Buy-plus-glue), not two | 10 | Binary Build-or-Buy framing. |
| R3 | Four dimension families with explicit weights summing to 100% | 10 | Missing family or weights not summing to 100%. |
| R4 | Each criterion has a 1–5 rubric with named 1 and 5 anchors | 10 | Un-anchored or free-text scores. |
| R5 | Weights set before scores collected, and this is explicit | 5 | Weights appear to be set after scores. |
| R6 | TCO lines re-use Exercise 01 cost-model shape (fully-loaded labor + indirect labor + risk reserve) across 3 years | 15 | TCO is a free-standing estimate or misses indirect labor. |
| R7 | Risk & compliance dimensions reference GOVERN / OWASP ML Top 10 / MITRE ATLAS / ISO 42001 as frames, not as numeric sources | 10 | Numeric probabilities attributed to a threat-posture framework. |
| R8 | Reversal condition named operationally | 10 | No reversal condition, or vague ("re-evaluate periodically"). |
| R9 | Sensitivity: ≥ 3 changes that would flip the recommendation | 5 | No sensitivity analysis. |
| R10 | Weighted-score arithmetic verified | 5 | Rollup off-by-arithmetic. |
| R11 | `org-specific` tags on org-specific anchors | 5 | Unmarked claims. |
| R12 | No vendor product names | 5 | Vendor product names appear. |

**Pass threshold:** ≥ 85/100 and no R2 / R6 / R8 fail. R6 (TCO re-uses the cost model) and R8 (reversal condition) are the two criteria that turn the matrix from a scoring exercise into a decision artifact.

## 5. Common mistakes

- **Framing as a binary.** Build-vs-Buy is a false binary at enterprise scale. The middle path (buy-plus-glue, or a managed-core + in-house-glue variant) is usually the right answer and is omitted most often.
- **Setting weights after scores.** Finance, Architecture, and the business-unit sponsor should set weights before the scoring session; otherwise the exercise degenerates into motivated reasoning.
- **Collapsing TCO to a single year.** 3-year TCO is what matters for the decision; 1-year TCO systematically favors Buy (which amortizes commercially) over Build (which requires upfront investment).
- **Forgetting indirect labor in TCO.** The Exercise 01 failure mode compounds here: Build looks artificially cheap because the FTE burden is under-counted, or Buy looks artificially cheap because the enablement team's integration time is under-counted.
- **Quoting vendor rate-card prices as the Buy TCO.** Same failure mode as Exercise 01: list price is not contract price. Use the rate card as a planning placeholder tagged `org-specific`.
- **Scoring risk with numeric probabilities attributed to OWASP ML Top 10 or MITRE ATLAS.** These are posture frames, not probability tables. Use them to scope which risks matter; set the scoring with org-owned signals.
- **Omitting the reversal condition.** A build-vs-buy decision that cannot be reversed is a bet, not a decision. The recommendation names the signal that would trigger reversal and the artifact that tracks it.
- **Omitting the sensitivity section.** The council will ask "what would change your mind?" The sensitivity section is the answer. Without it, the recommendation does not survive first contact with the room.
- **Scoring against a program-wide capability.** "AI enablement" is too big to score; "internal RAG platform" is the right grain. Run the matrix once per capability; capabilities like priced-product-facing AI, internal-knowledge platforms, developer-assistant tooling, and training-content pipelines each get their own.
- **Using people names.** The matrix is addressed to role-names (`head-of-ai-governance`, `senior-ai-governance-architect`), not people, consistent with mod-103 governance posture.

### 5.1 Stretch — Two-capability comparison

The full exercise is extended by running the matrix on a **second capability** and surfacing which path wins for each — demonstrating that different capabilities in the same organization legitimately land in different paths.

| Capability | Likely recommended path (illustrative, `<!-- org-specific -->`) | Why |
|---|---|---|
| Internal RAG platform (worked example) | Buy-plus-glue | Differentiation is in the content-and-glue layer; commodity vector store is cheap to buy. |
| Developer code-assistant (adjacent) | Buy | Commodity vendor landscape; no priced-product differentiation; FTE burden of Build is prohibitive. |
| Priced-product-facing customer-service assistant | Build or Buy-plus-glue | High differentiation, high data-sovereignty bar, direct revenue implications. |
| Policy-and-training content pipeline | Buy | Commodity LMS-adjacent capability; FTE burden of Build is unjustified for a non-differentiating capability. |

Running the matrix on multiple capabilities also surfaces that the *same vendor* may land on different sides for different capabilities — reinforcing the Exercise 05 consolidation discussion.

## 6. References

- **Learning material (local):**
  - [Exercise 01 — Enablement Cost Model Drill](../exercise-01-enablement-cost-model-drill/SOLUTION.md) — TCO per path is built with the same shape.
  - [Exercise 02 — ROI Projection with Confidence Bands](../exercise-02-roi-projection-with-confidence-bands/SOLUTION.md) — the break-even and adoption-sensitivity input to the T2 and sensitivity sections.
  - [mod-102 — Selecting and Rolling Out AI Tools](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-102-selecting-and-rolling-out-ai-tools) — the three-stage selection pattern that feeds the "what we would actually buy" column.
  - [mod-103 — Policy Co-authoring with Governance](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-103-policy-co-authoring-with-governance) — the GOVERN mapping behind the R4 criterion and the role-name posture.
  - [mod-109 — AI Incident Response and Enablement-Side Rollback](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-109-ai-incident-response-and-enablement-side-rollback) — the rollback-ownership shape in R3.
- **Official standards and frameworks** (used as posture frames, not numeric sources):
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — GOVERN function frames R2, R3, R4.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — threat posture behind the risk-family weighting.
  - [MITRE ATLAS](https://atlas.mitre.org/) — adversarial-technique context for risk scoring.
