# Exercise 06 — Change-Management Health Dashboard — Reference Solution

> Learning file: [`exercise-06-change-management-health-dashboard.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-105-champion-networks-and-change-management/exercises/exercise-06-change-management-health-dashboard.md)

## 1. Solution overview

Two artifacts: a **dashboard specification** (metrics, definitions, instrumentation sources, thresholds, review cadence) and a **worked month-4 snapshot** carrying the mod-103 archetype — a coding-assistant rollout at a ~3,000-person US bank — through the dashboard so the thresholds and the red/amber/green readings land on concrete signal.

The dashboard is an **enablement-seat instrument**, distinct from the mod-106 executive scorecard. The scorecard answers "is this rollout producing outcomes worth the investment"; the health dashboard answers "is the change-management surface healthy enough that the outcome signal we are reporting is trustworthy." A rollout can have strong scorecard numbers and a sick health dashboard — in which case the outcome numbers are not durable — and the health dashboard is the surface that catches this.

Posture checks the solution encodes:

- **Health, not adoption.** Adoption rate is one input; the dashboard does not report adoption as "the" health signal. A rollout at 90% adoption with a silent champion network and no field signal is in worse health than one at 40% adoption with a loud, honest network.
- **Four dimensions, not twelve metrics.** Coverage, signal, posture, and sentiment. Each has 2–4 metrics. Ten metrics is the ceiling; more produces dashboard fatigue and selective reading.
- **Every metric has a threshold.** Red / amber / green are defined numerically. A dashboard without thresholds becomes a vanity surface.
- **Every metric has a false-positive and false-negative behavior.** The dashboard names how each metric can lie. A metric with no documented failure mode cannot be read correctly under pressure.
- **The dashboard is read at a cadence, not a dashboard.** Monthly review is the point; a real-time surface invites selective-watching and over-reaction. The enablement seat publishes a monthly snapshot and files it alongside the mod-106 scorecard.

## 2. Implementation — worked answer

### 2.1 Deliverable A — `change-mgmt-health-dashboard-spec.md`

```
Change-Management Health Dashboard — Specification (v0.1)
Owner:   AI Enablement Lead (this role)
Audience: enablement seat (primary); head-of-engineering-enablement (L55) and head-of-ai-governance (L60) (review)
Cadence: Monthly snapshot; filed alongside mod-106 executive scorecard
Status:  Draft for sponsor sign-off
```

#### Four dimensions, ten metrics

```
DIMENSION 1 — COVERAGE      (is the change-management surface reaching the in-scope population?)
DIMENSION 2 — SIGNAL         (is the surface producing honest two-way signal?)
DIMENSION 3 — POSTURE        (are the artifacts and cadence operating as designed?)
DIMENSION 4 — SENTIMENT      (is the operator-side experience sustainable?)
```

#### Dimension 1 — Coverage

| # | Metric | Definition | Source | Thresholds (red / amber / green) |
|---|---|---|---|---|
| C1 | **Champion coverage of in-scope operators** | % of in-scope operators whose BU + function has an active champion in the roster | Champion roster (Exercise 01) × operator headcount roster | < 90% red / 90–95% amber / ≥ 95% green |
| C2 | **Policy-acknowledgement coverage** | % of in-scope operators who have acknowledged the current AUP version within 30 days of ratification | Version-note briefing surface (Exercise 03) acknowledgement log | < 85% red / 85–90% amber / ≥ 90% green |
| C3 | **Training-roster coverage (role-tier 1 or higher)** | % of in-scope operators who have completed role-tier 1 fluency training | mod-104 training roster | < 80% red / 80–90% amber / ≥ 90% green |

Coverage is a volume signal. It cannot replace the signal and sentiment dimensions, but low coverage is a load-bearing red: an operator who has not acknowledged the AUP is an operator who may unknowingly violate it.

#### Dimension 2 — Signal

| # | Metric | Definition | Source | Thresholds |
|---|---|---|---|---|
| S1 | **Champion signal rate** | Average reports per champion per month, over a 30-day rolling window | `field-signal-log` (Exercise 02) | < 1 or > 6 red / 1–1.5 or 4–6 amber / 1.5–4 green |
| S2 | **Cross-BU pattern escalations per quarter** | Count of patterns meeting the 3-reports-in-2-BUs-in-30-days threshold that escalate to governance council | `field-signal-log` escalation entries | 0 per quarter is red (signal is being suppressed); 1–4 is green; > 4 is amber (possible rollout-change pressure) |
| S3 | **Silent-function count** | Number of in-scope functions with < 1 champion report per month for ≥ 2 consecutive months | `field-signal-log` function-partition | > 2 red / 1–2 amber / 0 green |

Signal is the dimension that catches dishonest health. An adoption-at-ceiling rollout with zero cross-BU pattern escalations per quarter is in worse health than a 60%-adoption rollout with 3 honest escalations per quarter — the first is not surfacing problems; the second is working.

#### Dimension 3 — Posture

| # | Metric | Definition | Source | Thresholds |
|---|---|---|---|---|
| P1 | **Policy-artifact freshness** | Age in days of the current ratified AUP and SOP; longer-of-two reported | Redline log (mod-103) | > 180 days red / 90–180 days amber / ≤ 90 days green `<!-- org-specific: confirm the mod-103/mod-105 learning-content default for AUP/SOP freshness thresholds -->` |
| P2 | **Version-note briefing turnaround** | Days from AUP/SOP ratification to version-note briefing publication (target: ≤ 5 business days) | Version-note briefing surface (Exercise 03) | > 10 days red / 5–10 days amber / ≤ 5 days green |

Posture catches the cadence drifting away from the design. The most common failure mode is an AUP that has aged 180+ days without a redline cycle while the field signal has been accumulating against it.

#### Dimension 4 — Sentiment

| # | Metric | Definition | Source | Thresholds |
|---|---|---|---|---|
| T1 | **Quarterly pulse — "the policy artifacts are clear and useful"** | % of surveyed in-scope operators who agree or strongly agree. ≥ 300 respondents per quarter | Quarterly operator pulse survey | < 60% red / 60–75% amber / ≥ 75% green |
| T2 | **Quarterly pulse — "I can raise concerns and expect them to be addressed"** | % agree or strongly agree | Quarterly operator pulse survey | < 60% red / 60–75% amber / ≥ 75% green |

Sentiment is the dimension that catches dishonest signal from above. A high-coverage, high-signal-rate rollout with T2 < 60% is a rollout where the signal flowing up is not being acted on honestly; the field knows it.

#### Metric failure modes — how each metric can lie

Every metric has a documented false-positive and false-negative behavior.

| Metric | False positive (looks good, isn't) | False negative (looks bad, isn't) |
|---|---|---|
| C1 (champion coverage) | Roster includes an inactive champion. Fix: cross-reference with weekly sync attendance. | A function that has intentionally opted out of the rollout posture shows as uncovered. Fix: scope the denominator. |
| C2 (AUP ack) | Operators acknowledge without reading. Fix: cross-reference with Pattern 8 / S1 signal rate. | New operators during month-of-ratification are counted as unacknowledged for 30 days. Fix: exclude from the 30-day window. |
| C3 (training) | Completion ≠ fluency. Fix: cross-reference with the mod-104 fluency-growth measurement. | Role-tier 1 is coarse; some operators need higher. Fix: report tier-weighted coverage as a secondary. |
| S1 (signal rate) | High rate driven by one hyper-active champion. Fix: report distribution, not just mean. | Low rate for correct reasons (early rollout, small function). Fix: contextual thresholds in the first 90 days. |
| S2 (escalations) | Zero escalations because the enablement seat is suppressing. Fix: external review by `head-of-ai-governance` of the `field-signal-log`. | Zero escalations because nothing cross-BU happened. Fix: pair with S1 and S3. |
| S3 (silent functions) | Function is silent because posture is correctly opt-in. Fix: scope the denominator to opt-out and mandate posture. | Function is silent because the champion rotated and the backup is onboarding. Fix: 30-day grace after rotation. |
| P1 (freshness) | Artifact is fresh but has drifted from field signal. Fix: pair with S2 (escalation count against the artifact). | Artifact is old but the field signal is also stable. Fix: amber is appropriate; red requires signal-side evidence. |
| P2 (briefing turnaround) | Briefing was on time but not acknowledged. Fix: pair with C2. | Ratification happened on a Friday and the 5-business-day clock started Monday. Fix: define business-day correctly. |
| T1 (policy clarity pulse) | Low respondent base, biased toward satisfied operators. Fix: require ≥ 300 respondents; report respondent count. | Quarterly lag catches a now-resolved issue. Fix: pair with the most recent month's S1 trend. |
| T2 (concerns addressed pulse) | Low respondent base. Fix: same as T1. | Quarter captures a difficult month that was addressed by publication. Fix: trend over 3 quarters, not single-point. |

#### Monthly review cadence

- First business day of the month: enablement seat compiles the snapshot.
- Within 5 business days: snapshot is filed in the dashboard archive and shared with `head-of-engineering-enablement` (L55) and `head-of-ai-governance` (L60).
- Any **red** triggers:
  - A narrative note (≤ 1 page) explaining the reading, the likely cause, and the remediation.
  - A review on the next weekly champion sync.
  - A council-pre-read mention at the next quarterly cycle if the red persists ≥ 2 months.
- Any **amber** triggers:
  - A note in the snapshot explaining the reading. No standalone escalation.
- **All-green readings** are also narrated. Don't let the dashboard lose explanatory voice when the numbers are OK — reviewers lose calibration.

#### What the dashboard is not

- **Not an executive surface.** The mod-106 scorecard is the executive surface. The health dashboard is for enablement-seat review.
- **Not a champion-performance surface.** Metrics S1, S3 are about the signal, not about individual champions. A champion signal-rate column by name would convert the surface into a performance-management artifact and would destroy signal honesty.
- **Not a real-time dashboard.** Monthly cadence is the point. Daily read invites over-reaction.
- **Not comprehensive.** Change-management health is bigger than ten metrics. The four dimensions are the minimal set that catches most drift; anything beyond ten metrics is dashboard fatigue.

#### Co-author surface

> Drafter: AI Enablement Lead (this role).
> Ratifier: `head-of-engineering-enablement` (L55).
> Governance signer: `head-of-ai-governance` (L60) — confirms S2 external-review mechanism for escalation suppression.
> Analytics owner: `<!-- org-specific: confirm the analytics partner role title; typically enablement analytics or business-ops analyst -->` — owns the instrumentation and the archive surface.

---

### 2.2 Deliverable B — `month-4-snapshot.md` (worked example)

```
Change-Management Health Dashboard — Month 4 Snapshot
Reporting period: T+3mo through T+4mo (post-GA)
Compiled:         <!-- org-specific: confirm compile date -->
Reviewed:         head-of-engineering-enablement (L55), head-of-ai-governance (L60)
```

| Dim | # | Metric | Reading | Status | Note |
|---|---|---|---|---|---|
| 1 | C1 | Champion coverage | 96% | 🟢 | Platform/Infra at 100%; HR at 93% — nomination gap in HR pending close. |
| 1 | C2 | AUP acknowledgement (v1.1) | 94% | 🟢 | v1.1 ratified T+3w; 30-day ack window closed in-period. |
| 1 | C3 | Role-tier 1 training | 78% | 🔴 | Below red threshold. Main cause: Marketing and Finance behind by two cohorts. Remediation note in narrative. |
| 2 | S1 | Champion signal rate (mean) | 2.3 reports/champion/month | 🟢 | Distribution: median 2, max 7, min 0.5. One outlier at 7 — Platform/Infra champion A — not a concern. |
| 2 | S2 | Cross-BU escalations | 1 (if-in-doubt over-weighting pattern, Exercise 02 drill) | 🟢 | In expected range. Routed to council pre-read for Q+1. |
| 2 | S3 | Silent functions | 0 | 🟢 | Legal/Compliance was at borderline-silence (1 report in 30 days) in month 3; recovered in month 4 after champion rotation. |
| 3 | P1 | Policy-artifact freshness | 24 days (AUP v1.1 ratified T+3w) | 🟢 | SOP unchanged since launch (60 days); within green. |
| 3 | P2 | Version-note briefing turnaround | 3 business days | 🟢 | AUP v1.1 briefed within spec. |
| 4 | T1 | Pulse — policy clarity | 71% (321 respondents) | 🟡 | First quarterly pulse. Open-text responses cluster around Section 2 approved-use ambiguity on refactor workflows — feeds next walking-redline cycle. |
| 4 | T2 | Pulse — concerns addressed | 68% (321 respondents) | 🟡 | First quarterly pulse. Open-text responses cluster around visibility of escalation outcomes — may drive a version-note moment explicitly on "what happens after you raise something." |

#### Narrative

C3 (training-roster coverage) is **red** at 78%. This is below threshold and is the headline of the snapshot. Two causes: (a) Marketing and Finance are behind the training schedule by two cohorts, which is primarily a scheduling issue with the mod-104 cadence, not a resistance pattern; (b) a group of ~45 operators in Platform/Infra have completed role-tier 2 but were never recorded against role-tier 1 (data gap in the mod-104 roster, not a training gap). Remediation: scheduling catch-up with mod-104 to add two cohorts in the next 6 weeks; data-gap close with HRIS in the next 2 weeks. Expected back to green by month 5 snapshot.

T1 and T2 (pulse metrics) are both **amber**. This is the first quarterly pulse post-GA, so there is no trend yet; single-point reads are weak signals. The open-text response clustering is the actionable content — Section 2 ambiguity on refactor workflows will be addressed in the next walking-redline cycle (mod-103 Exercise 01 surface); the "visibility of escalation outcomes" signal will be addressed by a version-note moment published in-period on escalation handling (Exercise 03 downside-moment template applies). Monitor T1/T2 trend over the next two quarters before treating as a durable signal.

All other metrics are green. S2 (cross-BU escalations) at 1 is in the expected 1–4 range — the Exercise 02 drill surfaced the if-in-doubt over-weighting pattern and routed it to the governance-council pre-read cycle for Q+1. Signal is flowing honestly in both directions.

#### Decisions this month

- **Decision 1:** Two-cohort catch-up with mod-104 to address C3. Owner: this role + mod-104 curriculum lead. Due: T+6 weeks.
- **Decision 2:** HRIS data-gap close for Platform/Infra role-tier recording. Owner: this role + HRIS partner. Due: T+2 weeks.
- **Decision 3:** Version-note moment published in-period on escalation-outcome visibility (addresses T2). Owner: this role. Due: T+10 business days.
- **Decision 4:** Section 2 approved-use ambiguity on refactor workflows into next walking-redline cycle. Owner: this role + `head-of-ai-governance`. Due: next scheduled walking-redline.

---

### End of worked artifacts

## 3. Validation steps

1. **Four dimensions, not twelve.** Coverage, signal, posture, sentiment. If the dashboard is organized by metric rather than by dimension, reviewers will cherry-pick.
2. **Ten metrics or fewer.** Beyond ten is dashboard fatigue; readers stop reading. The ten chosen here cover the dimensions; adding more is almost always redundant.
3. **Every metric has a threshold.** Red / amber / green are numerically defined. A metric without a threshold is a vanity metric.
4. **Every metric has a documented failure mode** — one false positive and one false negative. This is the single most important check; metrics without documented failure modes are misread under pressure.
5. **S2 (escalation count) has 0 as a red.** Zero escalations in a quarter is almost always suppression, not health. If the dashboard treats 0 as green, the dashboard is suppressing.
6. **T2 (concerns addressed) is paired with T1.** T2 alone is noisy; T1+T2 together reads field honesty.
7. **The dashboard is not the executive scorecard.** The scorecard answers "is the outcome worth it"; the dashboard answers "is the signal honest." Readers who conflate them will under-read one and over-read the other.
8. **No per-champion performance columns.** Converting the dashboard into a champion-performance surface destroys signal honesty.
9. **Monthly cadence, not real-time.** The design calls for monthly; a daily dashboard invites selective watching.
10. **`<!-- org-specific: ... -->` on the analytics partner role, HRIS vendor, pulse-survey platform.** `<!-- org-specific: ... -->` on any mod-105 chapter-specific threshold claims.

## 4. Rubric / review checklist

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | Four dimensions named explicitly (coverage, signal, posture, sentiment) | 10 | Fewer than four, or dimensions renamed in a way that hides one |
| R2 | ≤ 10 metrics total, ≥ 2 per dimension | 10 | More than 10, or any dimension with < 2 metrics |
| R3 | Every metric has a definition, source, and red/amber/green threshold | 15 | Any metric missing threshold or source |
| R4 | Every metric has a documented false-positive and false-negative behavior | 15 | Missing on any metric |
| R5 | S2 (escalation count) treats 0 as red | 10 | 0 escalations shown as green |
| R6 | T1 and T2 paired; T2 not read alone | 5 | T2 reported standalone without T1 context |
| R7 | Dashboard is framed as distinct from the executive scorecard | 5 | Conflated or sold as an executive surface |
| R8 | No per-champion performance columns | 10 | Champion-name columns in the signal dimension |
| R9 | Monthly cadence; not real-time | 5 | Real-time or daily cadence specified |
| R10 | Worked snapshot has at least one red or two ambers (realistic) | 5 | All-green worked snapshot |
| R11 | Worked snapshot includes decisions block with named owners and dues | 5 | Decisions missing or no owners |
| R12 | Narrative includes how the metric could be misread | 5 | Narrative is interpretation-only, no caveats |
| R13 | `<!-- org-specific: ... -->` on analytics partner, HRIS, pulse platform; `<!-- org-specific: ... -->` on chapter-specific threshold defaults | 5 | Invented facts or thresholds without caveat |

**Pass threshold:** ≥ 85/100 and no R3/R4/R5/R8 fail.

## 5. Common mistakes

- **Reporting adoption as "the" health metric.** Adoption is one input; a 90%-adoption-with-silent-network rollout is in worse health than a 40%-adoption-with-honest-network rollout. The four-dimension view catches this.
- **Twenty metrics across the dashboard.** Dashboard fatigue sets in past ten. The discipline is pruning, not comprehensiveness.
- **No thresholds.** "Watch this metric" is not a threshold. Red/amber/green numerical cuts are the discipline.
- **No documented failure modes.** Every metric can lie. The documented false-positive and false-negative lines are what make the dashboard read correctly under pressure.
- **Zero escalations as green.** This is the single most dangerous dashboard error. Zero escalations per quarter is suppression, not health.
- **Per-champion performance columns.** The moment this is on the dashboard, champions start managing the signal upward, and the dashboard becomes a lagging political artifact.
- **Real-time dashboard.** Daily readings produce over-reaction and under-interpretation. Monthly is the cadence; snapshot discipline is the output.
- **Conflating with the executive scorecard.** They answer different questions. Keep both; label both.
- **All-green worked snapshots.** A snapshot with no red or amber is unrealistic and invites readers to assume the dashboard is cosmetic. The worked example should show at least one red and / or two ambers with the narrative handling.
- **Narrative that interprets without caveats.** "C3 is red because training is behind" without the "second cause is a HRIS data gap, not a training gap" caveat sends the remediation in the wrong direction.
- **Inventing a specific pulse-survey vendor.** `<!-- org-specific: ... -->` slot.

## 6. References

- **Learning material:**
  - [Exercise 06 learning file](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-105-champion-networks-and-change-management/exercises/exercise-06-change-management-health-dashboard.md)
  - [mod-105 chapters (champion networks and change management)](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-105-champion-networks-and-change-management) `<!-- org-specific: confirm which mod-105 chapters cover health-metric framing, signal-vs-adoption distinction, and threshold defaults; link the specific chapter files here -->`
  - [mod-106 chapters (outcome measurement and executive reporting)](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-106-outcome-measurement-and-executive-reporting) — the distinct executive-scorecard surface the dashboard pairs with.
  - [mod-104 (training and literacy curriculum)](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-104-training-programs-and-ai-literacy-curriculum) — the source for C3 and for the fluency-growth measurement referenced in the C3 failure-mode line.
  - [mod-103 Exercise 02 — Data-Handling SOP](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-103-policy-co-authoring-with-governance/exercises/exercise-02-data-handling-sop-for-an-ai-tool.md) — the SOP freshness input for P1.
- **Official standards and frameworks:**
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — MEASURE function (metrics, measurement, and performance evaluation) and GOVERN function (accountability and transparency) that the dashboard evidences.
  - [NIST AI 600-1: Generative AI Profile](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf) — generative-AI-specific measurement considerations referenced in the signal-dimension failure modes.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — context for the posture-dimension freshness threshold on policy artifacts that reference prompt-injection and output-review controls.
  - [MITRE ATLAS](https://atlas.mitre.org/) — adversarial technique context for the escalation-count failure-mode discussion.
