# Exercise 02 — ROI Projection with Confidence Bands — Reference Solution

> Module: `mod-107-budget-roi-and-build-vs-buy-at-org-scope`
> Exercise type: design / worked example
> Exercise brief: [`lessons/mod-107-budget-roi-and-build-vs-buy-at-org-scope/exercises/exercise-02-roi-projection-with-confidence-bands.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-107-budget-roi-and-build-vs-buy-at-org-scope/exercises/exercise-02-roi-projection-with-confidence-bands.md) (in the learning repo)

## 1. Solution overview

The deliverable is an **ROI projection with explicit confidence bands** for the AI enablement program described by the Exercise 01 cost model. The model produces three scenarios — **pessimistic (P10)**, **expected (P50)**, and **optimistic (P90)** — with each scenario built from the same assumption graph but different ranges on the three to six assumptions the projection is most sensitive to. The output is what the AI Enablement Lead walks into the budget-renewal or program-review conversation with, and the structure is specifically designed to survive the executive's first follow-up question ("what if adoption is slower than you think?").

Posture checks this solution encodes:

- **One cost side, three benefit sides.** Cost is pinned by Exercise 01 and is not re-estimated inside the ROI model; Benefits are projected under three scenarios.
- **Benefits categories are named explicitly** (time-savings, quality-uplift, risk-reduction, revenue-adjacent) and each category carries a **realization-curve shape** — benefits do not land on day 1.
- **Every point estimate is bracketed by a range**, and the range is tied to a named driver (adoption rate, time-savings per task, task frequency, value-per-hour-saved). An ROI number without a stated range is a number the executive will discount to zero.
- **Confidence bands are not symmetric.** Downside risk (pessimistic) is almost always larger than upside (optimistic), because delivery can fail in more ways than it can over-perform. The model carries that asymmetry.
- **Sensitivity analysis is a required output**, not a stretch goal. The one-page view the executive needs to see shows which assumptions move the ROI the most.
- **A break-even date is named for each scenario**, not just a 12-month ROI percentage. The break-even date is the number the executive will internalize.
- **Risk-reduction benefits are modeled with extra discipline.** Quantifying avoided-incident cost is the easiest place to inflate the model; the solution uses **expected-loss math** (probability × impact) sourced from publicly-grounded ranges, not point estimates.

## 2. Implementation — worked answer

### 2.1 Scenario envelope (carried from Exercise 01)

- Organization: ~2,000 knowledge workers across three business units; addressable population 1,400.
- Target reached operators in FY<YYYY>: 1,250.
- FY<YYYY> total annualized cost of the enablement program (fully-loaded, including indirect labor and risk reserve): **~1.66M USD** (from Exercise 01 grand total).
- Horizon: three-year view. ROI is reported at 12, 24, and 36 months.
- Currency: USD. <!-- org-specific: confirm whether Finance wants a constant-currency or inflation-adjusted view; this model uses constant-currency and marks the inflation assumption as org-specific. -->

### 2.2 The model — `enablement-roi-projection.md`

```
Enablement ROI projection — FY<YYYY> → FY<YYYY+2>
Author:        AI Enablement Lead
Finance owner: <!-- org-specific: name the Finance partner -->
Cost basis:    Exercise 01 cost model, snapshot <!-- org-specific: date -->
Horizon:       36 months, reported at 12 / 24 / 36
```

#### Step 1 — Benefit categories and their drivers

| Category | What is being measured | Primary driver(s) | Realization curve shape |
|---|---|---|---|
| **B1. Time-savings (operator productivity)** | Hours per operator per week returned by AI-assisted workflow, converted at a fully-loaded hourly rate | Reached operators × hours saved/operator/week × 50 weeks × hourly rate × realization factor | S-curve; low in Q1 (training in flight), ramping through Q2–Q3, plateau by Q4 |
| **B2. Quality uplift (reduced rework)** | Hours of rework avoided, converted at a fully-loaded hourly rate | Reached operators × rework-reduction %/operator × baseline rework hours × hourly rate | Lags B1 by ~1 quarter (quality signal shows up after volume signal) |
| **B3. Risk reduction (avoided incidents)** | Expected-loss reduction from the policy, intake, and training posture | Baseline incident frequency × impact × posture-driven reduction factor | Step-function improvement at the quarter after policy ratification |
| **B4. Revenue-adjacent (optional)** | Incremental revenue or margin where enablement enables a priced capability (e.g., faster proposal turnaround) | Priced-capability-specific, named per BU | Deal-cycle-length dependent; omitted from the default worked example because quantification is `<!-- org-specific: ... -->` without BU-specific data |

#### Step 2 — Assumption table, with ranges

| Assumption ID | Description | Pessimistic (P10) | Expected (P50) | Optimistic (P90) | Source / tag |
|---|---|---|---|---|---|
| A1 | **Realized reach**: fraction of addressable population (1,400) who complete training and have a credentialed tool account by month 12 | 50% (700 operators) | 70% (980) | 85% (1,190) | mod-106 scorecard reach target informs the P50; P10 reflects a slower-than-planned training cadence `<!-- org-specific -->` |
| A2 | **Adoption depth**: fraction of reached operators who use the tool on a weekly cadence or better | 40% | 65% | 80% | mod-104 fluency-growth curves inform the P50 `<!-- org-specific -->` |
| A3 | **Time saved per deeply-adopted operator per week** (hours) | 0.5 | 2.0 | 4.0 | Literature on knowledge-worker productivity from AI assistants spans roughly this range; specific point estimates are vendor-marketing claims and are not used `<!-- org-specific: cite a source the learner's Finance function will accept; a vendor white paper is not sufficient -->` |
| A4 | **Fully-loaded hourly rate** of an in-scope operator (USD/hour) | 85 | 110 | 135 | Blended across the three BUs `<!-- org-specific: confirm the Finance-owned blended rate -->` |
| A5 | **Rework-reduction factor** on the baseline rework-hour budget | 5% | 15% | 25% | From the BU-owned rework telemetry that will exist by month 9 `<!-- org-specific -->` |
| A6 | **Baseline rework hours per operator per year** | 20 | 60 | 120 | `<!-- org-specific: confirm against the BU-owned quality-ops numbers; omit the category entirely if the signal is unavailable -->` |
| A7 | **Avoided-incident expected-loss reduction** (USD/year, org-wide) | 50,000 | 250,000 | 750,000 | Built from the expected-loss cell below, not a free-standing estimate |
| A8 | **Inflation / rate escalation** | +1%/yr | constant currency | +4%/yr | Constant-currency baseline; alternates marked `<!-- org-specific -->` |

#### Step 3 — Expected-loss math for A7 (avoided-incident reduction)

Avoided-incident benefit is the easiest category to inflate and the most dangerous to over-claim. The solution scopes it as **expected-loss reduction**: `probability × impact × posture-driven reduction factor`, with all three terms ranged.

| Incident class (illustrative) | Baseline annual probability | Impact if it occurs (USD) | Posture-driven reduction factor | Expected-loss reduction (USD/year) |
|---|---|---|---|---|
| Policy violation surfacing externally (e.g., prohibited data pasted into an unvetted tool) | P10: 10% / P50: 25% / P90: 40% | P10: 50k / P50: 150k / P90: 500k | P10: 20% / P50: 40% / P90: 60% | P10: ~1k / P50: ~15k / P90: ~120k |
| Vendor-tool incident requiring enablement-side rollback | P10: 20% / P50: 50% / P90: 80% | P10: 20k / P50: 75k / P90: 300k | P10: 10% / P50: 25% / P90: 50% | P10: ~0.4k / P50: ~9k / P90: ~120k |
| Training / literacy gap surfaced by regulator (EU AI Act Article 4 adjacent) | P10: 2% / P50: 10% / P90: 25% | P10: 100k / P50: 500k / P90: 2,000k | P10: 25% / P50: 50% / P90: 75% | P10: ~0.5k / P50: ~25k / P90: ~375k |
| **A7 rollup** |  |  |  | **P10 ~2k / P50 ~50k / P90 ~615k** |

The rollup is **floored at 50k for P10 and capped at 750k for P90** because the per-row numbers are multiplicative and reach implausible bands at the tails. The flooring and capping is an explicit modeling choice, documented in the row and auditable.

> This section uses `owasp-ml-top-10` and `mitre-atlas` as the threat-posture frame for which incidents to carry, not as a source of probability data. No probability or impact number in this table is quoted from either source; both ranges are learner-and-Finance-ownable and are tagged `<!-- org-specific -->` for the real artifact.

#### Step 4 — Benefit totals, by scenario, at 12 months

Formulas used (per operator; summed over the realized-reach population; applied against the year-1 realization curve averaged at ~55% of steady-state):

- **B1 (time-savings)** = A1 × 1,400 × A2 × A3 × 50 weeks × A4 × 0.55 (year-1 realization factor; 1.00 from year 2)
- **B2 (quality)** = A1 × 1,400 × A2 × A5 × A6 × A4 × 0.40 (lags B1 by one quarter; year-2 realization factor 1.00)
- **B3 (risk)** = A7 × 0.75 (year-1; posture builds up through policy ratification + training; years 2 and 3 = full A7)

| Scenario | B1 (year 1) | B2 (year 1) | B3 (year 1) | Total benefit, year 1 | Cost, year 1 (Ex-01) | Net, year 1 | ROI % year 1 |
|---|---|---|---|---|---|---|---|
| **Pessimistic (P10)** | 700 × 40% × 0.5 × 50 × 85 × 0.55 ≈ **327k** | 700 × 40% × 5% × 20 × 85 × 0.40 ≈ **10k** | 50k × 0.75 ≈ **38k** | **~375k** | ~1.66M | **-1.29M** | **-78%** |
| **Expected (P50)** | 980 × 65% × 2.0 × 50 × 110 × 0.55 ≈ **3.85M** | 980 × 65% × 15% × 60 × 110 × 0.40 ≈ **252k** | 250k × 0.75 ≈ **188k** | **~4.29M** | ~1.66M | **+2.63M** | **+158%** |
| **Optimistic (P90)** | 1,190 × 80% × 4.0 × 50 × 135 × 0.55 ≈ **14.13M** | 1,190 × 80% × 25% × 120 × 135 × 0.40 ≈ **1.54M** | 750k × 0.75 ≈ **563k** | **~16.24M** | ~1.66M | **+14.58M** | **+878%** |

#### Step 5 — Three-year horizon and break-even

Year-2 and Year-3 use the full (not year-1-ramped) realization and extend the reach and adoption-depth curves modestly. Cost grows per the three-year horizon in Exercise 01 Section 5.1.

| Scenario | Cum. net @ 12 mo | Cum. net @ 24 mo | Cum. net @ 36 mo | Break-even month |
|---|---|---|---|---|
| **Pessimistic (P10)** | -1.29M | -1.9M (benefits grow, but still below cumulative cost) | -1.6M (still negative) | **Not within 36 months** at P10. The honest story. |
| **Expected (P50)** | +2.63M | +9.0M | +16.2M | **Month 6** of year 1 |
| **Optimistic (P90)** | +14.58M | +32.9M | +53.6M | **Month 2** of year 1 |

The band is **wide on purpose**. A narrower band is almost always a sign that one or more assumptions is secretly a point estimate. The width is what makes the projection credible; it is also what makes the sensitivity analysis the most load-bearing output.

### 2.3 Sensitivity analysis — `enablement-roi-sensitivity.md`

For the P50 expected scenario, a **tornado chart** is produced by flexing each assumption one at a time to its P10 and P90 while holding the others at P50. The order below is the order that matters for the executive conversation (largest-swing first):

| Assumption flexed (A1–A8) | Net year-1 (if P10) | Net year-1 (if P90) | Swing (USD) |
|---|---|---|---|
| **A3 — Hours saved per operator per week** | ~+0.5M | ~+6.0M | **~5.5M** |
| **A2 — Adoption depth** | ~+1.4M | ~+3.4M | **~2.0M** |
| **A1 — Realized reach** | ~+1.6M | ~+3.2M | **~1.6M** |
| **A4 — Fully-loaded hourly rate** | ~+1.9M | ~+3.3M | **~1.4M** |
| **A5 + A6 — Rework reduction × baseline hours (B2)** | ~+0.1M | ~+0.6M | **~0.5M** |
| **A7 — Avoided-incident reduction** | ~+0.03M | ~+0.5M | **~0.5M** |

**Headline the tornado chart surfaces:** the ROI is overwhelmingly driven by A3 (hours saved per operator per week). The next three assumptions are roughly co-equal. The two risk-adjacent categories (quality and incident reduction) are real benefits but they move the number much less than the time-savings line. That is the narrative to bring into the executive conversation.

### 2.4 Decision rationale — why confidence bands shaped this way

- **Why P10/P50/P90, not single-point.** A single-point ROI is a sales artifact. P10/P50/P90 is what Finance will accept as a planning input because it bounds the downside. The percentiles are not derived from a formal Monte Carlo; they are the explicit low / central / high points in a scenario table. For a program this new, the scenario triplet is more defensible than a simulated distribution (simulation would imply a precision the assumptions do not support).
- **Why asymmetric bands.** The pessimistic case has a longer path to failure (slow training, weak adoption, unfavorable rate, no incident reduction because no incidents happened — which is a good outcome for the org but a zero-benefit outcome for this model category) than the optimistic case has to over-performance (there is a ceiling on hours-saved per operator). The asymmetry is preserved explicitly.
- **Why a 55% year-1 realization factor on time-savings and 40% on quality.** Training, tool onboarding, and workflow change take a quarter or two to show up as productivity. Modeling full-steady-state benefits from month 1 is the single most common inflation vector and is explicitly guarded against here.
- **Why floor and cap the risk-reduction rollup.** The expected-loss math is multiplicative across three uncertain terms; the tails become implausible fast. The floor/cap is a conservative check against false precision.
- **Why the tornado is a required output.** The executive will ask "what are you most uncertain about?" The tornado answers it. Without the tornado, the ROI number is a point for the executive to compress to zero.

## 3. Validation steps

1. **Benefit categories named.** B1 (time-savings), B2 (quality), B3 (risk), and B4 (revenue-adjacent, if used). If B4 is omitted the omission is stated and tagged.
2. **Three scenarios** (P10 / P50 / P90) with the **same assumption graph** and only the assumption ranges differing.
3. **Every assumption has P10 / P50 / P90 values and a source tag.** Any assumption that is a point estimate (one column, not three) fails.
4. **Realization-curve shape documented.** The year-1 realization factor is less than 1 for at least B1 and B2.
5. **Risk-reduction (B3) is expected-loss math**, not a free-standing estimate. Probability × impact × reduction factor is visible in the model.
6. **Avoided-incident probability/impact ranges are not quoted from `owasp-ml-top-10` or `mitre-atlas`.** Those are threat-posture frames; the specific numbers must be org-owned or tagged `org-specific`.
7. **Break-even month named for each scenario.** The P10 case may have no break-even inside the horizon — if so, the model states it explicitly.
8. **Sensitivity analysis / tornado chart produced on the P50 scenario**, naming the top-swing assumption and the top-three swing cluster.
9. **Asymmetry preserved.** The downside envelope is wider than the upside envelope on at least one assumption that has a natural ceiling (hours saved per operator per week, adoption depth).
10. **Arithmetic ties** at each scenario row: B1 + B2 + B3 = total benefit; total benefit - cost = net.
11. **`org-specific` tags on all unverified point estimates.** Hourly rates, rework baselines, incident probabilities, incident impacts, inflation assumptions.
12. **No vendor marketing numbers used as assumption sources.** Grep for claims that match a vendor white-paper framing.
13. **Executive narrative line produced.** The tornado chart's "headline" is written as one or two sentences the Enablement Lead would say in the executive conversation.

## 4. Rubric / review checklist

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | Three scenarios (P10 / P50 / P90) built from one shared assumption graph | 10 | Fewer than three scenarios, or separate assumption graphs per scenario. |
| R2 | At least three benefit categories (B1, B2, B3), with B4 explicitly deferred if not used | 10 | A category omitted without explanation. |
| R3 | Every assumption carries a range and a source/tag | 15 | Any assumption as a point estimate without a range. |
| R4 | Year-1 realization factor < 1 for B1 and B2 | 10 | Full-steady-state benefits assumed from month 1. |
| R5 | B3 built with expected-loss math (p × i × reduction), with p/i/reduction all ranged | 15 | Risk-reduction stated as a free-standing dollar number. |
| R6 | Avoided-incident probabilities/impacts are not sourced from OWASP ML Top 10 or MITRE ATLAS as numeric values | 5 | Numeric probabilities attributed to a threat-posture framework. |
| R7 | Asymmetric band widths preserved where a natural ceiling exists | 5 | Symmetric bands on a bounded assumption. |
| R8 | Break-even month named for each scenario (or honest "not within horizon" for P10) | 10 | Break-even missing or only reported as a 12-month ROI percentage. |
| R9 | Tornado / one-at-a-time sensitivity analysis produced on P50, with top-swing assumption named | 10 | No sensitivity analysis. |
| R10 | Executive-narrative headline derived from the tornado | 5 | Model shipped without a narrative line. |
| R11 | `org-specific` tags on unverified point assumptions | 5 | Unmarked quoted numbers. |

**Pass threshold:** ≥ 85/100 and no R3 / R5 / R9 fail. R5 (expected-loss discipline on risk-reduction) is the hardest criterion because the pull to inflate it is strongest; R9 (sensitivity analysis) is the criterion that makes the model survive executive follow-up.

## 5. Common mistakes

- **Reporting a single-point ROI.** "This program has 180% ROI" is a sales artifact. Replace with "Expected ROI in year 1 is +158% (pessimistic −78% / optimistic +878%); break-even month is month 6 in the expected case and not inside the 36-month horizon in the pessimistic case."
- **Full-steady-state benefits from month 1.** The single biggest ROI-inflation vector. Enforce a year-1 realization factor on time-savings and quality, and document the shape.
- **Treating vendor marketing numbers as assumption sources.** Vendor-published productivity gains are self-interested; Finance treats them as discountable. Use ranges grounded in the learner's org data; tag the rest `org-specific`.
- **Pricing risk-reduction as a free-standing number.** "Saves 500k/year in avoided incidents" without probability × impact math is unaudited. Enforce the expected-loss form.
- **Attributing numeric probabilities to OWASP ML Top 10 or MITRE ATLAS.** These frameworks name threat patterns, not their frequencies in a specific org. Quoting them as sources of probability data is a factual error.
- **Symmetric bands.** If the P10 and P90 envelopes are the same width around P50, the bands are a convenience, not an assessment. Hours-saved-per-operator-per-week has a natural ceiling long before it has a natural floor; the band should reflect that.
- **Omitting the tornado.** Without the sensitivity output, the model cannot answer "what matters most and how uncertain is it?" and will be compressed to its point estimate in the executive's head.
- **Reporting only a 12-month ROI percentage.** The break-even month is the number executives remember. Report it per scenario.
- **Collapsing B1/B2/B3 into one blended benefit line.** Loses the ability to show which category is driving the number; also prevents BU-owned validation of specific benefit lines (BU owners can confirm the rework baseline but cannot confirm "total benefit").
- **Not naming the Finance partner or counterparty.** The model must be addressed to the Finance partner who will co-sign the planning view.

### 5.1 Stretch — Monte Carlo and multi-year compounding

For the mature program version of this projection, two extensions are added as separate tabs:

- **Monte Carlo (10,000 iterations)** replacing the P10/P50/P90 scenario table with a sampled distribution per assumption. The distributions used are: triangular for A1/A2/A5 (bounded), log-normal for A3/A6 (right-skewed), uniform for A4 (narrow band), and the product-of-triangulars form for A7. The output is a full distribution of year-1 net ROI with 10th / 50th / 90th and a documented tail. This upgrade is only honest once at least two quarters of actual telemetry exist to calibrate the distributions — before then, Monte Carlo is false precision on hand-picked ranges.
- **Multi-year compounding.** Years 2 and 3 are not just "same model, same reach" — reach grows (adoption spread), benefits compound (per-operator time-savings grow as fluency deepens; mod-104 fluency-growth curves), and costs grow but at a slower rate (seat-price negotiations improve; audit cycles become biennial rather than annual after certification). The three-year cumulative view is what the build-vs-buy exercise (Exercise 03) and the consolidation exercise (Exercise 05) consume.

## 6. References

- **Learning material (local):**
  - [Exercise 01 — Enablement Cost Model Drill](../exercise-01-enablement-cost-model-drill/SOLUTION.md) — the cost basis this projection is built on.
  - [mod-104 — Training Programs and AI Literacy Curriculum](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-104-training-programs-and-ai-literacy-curriculum) — fluency-growth curves and adoption-depth signals.
  - [mod-106 — Outcome Measurement and Executive Reporting](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-106-outcome-measurement-and-executive-reporting) — the scorecard reach target and executive-reporting cadence.
  - [mod-109 — AI Incident Response and Enablement-Side Rollback](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-109-ai-incident-response-and-enablement-side-rollback) — the incident-class taxonomy that frames the B3 rollup.
- **Official standards and frameworks** (used as threat-posture frames, not as sources of numeric probabilities):
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — the GOVERN function frames the posture that lowers expected loss.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — frames the incident classes carried in the B3 rollup.
  - [MITRE ATLAS](https://atlas.mitre.org/) — frames adversarial-technique context behind the incident-class scoping.
