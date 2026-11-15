# Exercise 05 — Tool Stack Consolidation Worked Example — Reference Solution

> Module: `mod-107-budget-roi-and-build-vs-buy-at-org-scope`
> Exercise type: design / worked example
> Exercise brief: [`lessons/mod-107-budget-roi-and-build-vs-buy-at-org-scope/exercises/exercise-05-tool-stack-consolidation-worked-example.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-107-budget-roi-and-build-vs-buy-at-org-scope/exercises/exercise-05-tool-stack-consolidation-worked-example.md) (in the learning repo)

## 1. Solution overview

The deliverable is a **consolidation decision pack** for a sprawling AI tool stack: an inventory, an overlap analysis, a candidate target stack, a transition plan with cutover windows, and a signed recommendation. The scenario is deliberately representative — most organizations ~18 months into an AI enablement program have picked up 10–20 tools across BUs, many with overlapping capabilities, several with soft or absent governance evidence, and a long tail of forgotten pilots that never shipped and never got cancelled. The pack is the artifact the AI Enablement Lead walks into the governance council and the CFO's planning cycle with when the ask is "we're spending how much on AI tools — what can we consolidate?"

Posture checks this solution encodes:

- **Inventory first, overlap second, target stack third, transition fourth.** Skipping any step produces a plan that dies on first contact with a BU sponsor.
- **Inventory is at the capability grain, not the product grain.** Three AI meeting-notes tools map to one capability, not three different products.
- **The consolidation ROI uses the Exercise 02 shape** — three scenarios (P10/P50/P90), explicit realization curves, risk-reduction with expected-loss math. Consolidation savings do not land on day 1; they land over 6–12 months as contracts expire and operators move.
- **Build-vs-buy per retained capability** is run with Exercise 03's matrix, not re-litigated inside this exercise.
- **Transition risk is modeled explicitly.** Operator-migration risk, incident-window risk, and signal-loss risk (losing telemetry during the cut) are named with mitigations.
- **The recommendation names the reversal condition.** Consolidation is reversible per retired tool under a documented trigger; the pack states those triggers.
- **Role-name addressing and governance posture mirror mod-103.**

## 2. Implementation — worked answer (`tool-stack-consolidation-pack.md`)

```
AI tool-stack consolidation — <YYYY-Q?> review
Author:    AI Enablement Lead
Signoffs:  head-of-ai-governance (L60), senior-ai-governance-architect (L50),
           Head of Procurement, Head of Finance, affected BU sponsors (role names)
Snapshot:  <!-- org-specific: as-of date -->
Scope:     All AI tools in the enablement cost center + BU-owned AI tools surfaced via intake
```

### 2.1 Inventory — the "actual stack today"

Format of each row: capability; vendor / product class (no product names); seats / consumption; annual cost (USD, carried from the Exercise 01 cost model); governance status (intake complete? AUP coverage? SOP coverage?); owner.

For the worked scenario (the Exercise 01 / 02 organization of ~2,000 knowledge workers), the inventory is stylized and marked `<!-- org-specific: ... -->` for cells that depend on the learner's org:

| ID | Capability | Vendor class | Seats / consumption | Annual cost (USD) | Governance status | Owner (role) |
|---|---|---|---|---|---|---|
| T01 | General-purpose AI assistant | Tier-1 vendor, enterprise SKU | 900 seats | 216,000 | Intake complete; AUP covered; SOP covered | Enablement |
| T02 | General-purpose AI assistant | Tier-1 vendor, departmental SKU | 500 seats | 60,000 | Intake complete; AUP covered; SOP covered | Enablement |
| T03 | Developer code-assistant | Tier-1 code vendor | 180 seats | 54,000 | Intake complete; AUP covered; SOP covered | Engineering BU |
| T04 | Meeting-notes assistant (production) | Vendor A | 300 seats | 54,000 `<!-- org-specific -->` | Intake complete; AUP covered; SOP covered | Sales BU |
| T05 | Meeting-notes assistant (shadow pilot) | Vendor B | 60 seats | 7,200 | **Intake missing; AUP not explicitly scoped** | Legal BU `<!-- org-specific -->` |
| T06 | Meeting-notes assistant (legacy) | Vendor C | 40 seats | 4,800 | **Intake missing; contract auto-renews** | None named (orphan) `<!-- org-specific -->` |
| T07 | Prompt-engineering platform | Shared platform vendor | API only | 120,000 | Intake complete; AUP covered; SOP covered | Enablement |
| T08 | Internal RAG platform (pilot) | In-house | — | ~250,000 `<!-- org-specific -->` | Intake complete; AUP covered; SOP in draft | Engineering + Enablement |
| T09 | HR policy assistant (production) | Vendor D (wraps T07) | 1,400 users | 30,000 | Intake complete; AUP covered; SOP covered | HR BU |
| T10 | IT self-serve assistant | Vendor D (same as T09) | ~1,000 users | 20,000 | Intake complete; AUP covered; SOP covered | IT BU |
| T11 | Knowledge-base search assistant (pilot) | Vendor E | 200 pilot users | 15,000 | **Intake complete; AUP partial; pilot charter expired** | Knowledge-Mgmt BU `<!-- org-specific -->` |
| T12 | Image-generation tool (shadow) | Vendor F | 20 users (marketing) | 9,000 | **Intake missing; AUP not scoped; SOP not drafted** | Marketing BU `<!-- org-specific -->` |
| T13 | Transcription / dictation | Legacy pre-AI vendor + AI module add-on | 100 seats | 12,000 | Intake partial (AI module not re-reviewed on activation) | Operations BU |

**Total today:** `<!-- org-specific: sum once org-specific numbers confirmed -->` ≈ **852,000 USD/year in direct tool spend**, plus ~250,000 USD in the T08 in-house platform (which has a different cost profile and is handled separately under Exercise 03 build-vs-buy).

### 2.2 Overlap analysis — collapse the inventory into capabilities

| Capability cluster | Tools in cluster today | Observed overlap |
|---|---|---|
| **General-purpose AI assistant** | T01, T02 | Two SKUs on the same vendor, same contract; already consolidated. No action. |
| **Developer code-assistant** | T03 | Single tool; no overlap. No action. |
| **Meeting-notes assistant** | T04, T05, T06 | **Three vendors on the same capability.** T04 is production; T05 is a shadow pilot by Legal that never routed through intake; T06 is an orphan on auto-renewal. |
| **Prompt-engineering platform / shared LLM API** | T07 | Single tool; serves T08, T09, T10. No action. |
| **Internal RAG platform** | T08 | Decision space is Exercise 03 (build-vs-buy). Not a consolidation question. |
| **HR + IT + knowledge-base assistants** | T09, T10, T11 | T09 and T10 share a vendor (D); T11 is a different vendor (E) covering adjacent-but-distinct ground. **Partial overlap.** |
| **Image generation** | T12 | **Shadow tool.** Governance-first problem, not a consolidation problem — but if it survives governance, it may consolidate into T07-adjacent vendor offerings. |
| **Transcription / dictation** | T13 | **Zombie AI module.** The AI capability on a pre-AI vendor was activated without intake re-review; the consolidation question is whether it should be deactivated or the vendor replaced with a consolidation into T04. |

The overlap narrative to the council: **four consolidation candidates** — meeting-notes (T04/T05/T06), HR+IT+knowledge-base (T09/T10/T11), image-generation (T12), and transcription (T13). The general-purpose and code-assistant clusters are clean; the internal RAG platform is the subject of a separate build-vs-buy exercise.

### 2.3 Target stack — the "what we want to end up with"

| Capability | Target | What changes |
|---|---|---|
| General-purpose AI assistant | T01/T02 unchanged | No change |
| Developer code-assistant | T03 unchanged | No change |
| **Meeting-notes assistant** | **Single-vendor (T04)** | Retire T05 (shadow pilot) and T06 (orphan auto-renewal). Migrate T06's 40 operators and T05's 60 operators to T04. |
| Prompt-engineering platform | T07 unchanged | No change |
| Internal RAG platform | Pending Exercise 03 build-vs-buy decision | Separate track |
| **HR + IT + knowledge-base assistants** | **T09 + T10 retained; T11 retired or absorbed** | Evaluate whether T11's knowledge-base-search capability can be served by the T07-wrapped assistant family (Vendor D). If yes, retire T11; if no, retain all three. `<!-- org-specific: requires a mod-102-style evaluation on T11 against T09/T10's capability set -->` |
| **Image generation** | **One tool, intake-complete, AUP-scoped, SOP-drafted** — not necessarily T12 | Governance-first: intake T12 immediately; either retain, replace, or retire pending the intake outcome. |
| **Transcription / dictation** | **Deactivate the AI module** on T13; route transcription needs to T04 for meeting contexts; retain T13 as the pre-AI tool for its original scope | Removes the zombie AI module without disrupting the legacy workflow. |

### 2.4 Consolidation ROI — the Exercise 02 shape applied to this scenario

**Benefits side:**

| Benefit | P10 | P50 | P90 | Timing |
|---|---|---|---|---|
| **Direct cost savings (retired contracts)** — T05 (~7,200), T06 (~4,800), T11 (~15,000 if retired), T13 AI-module (~3,000 of the 12,000 attributable to AI module `<!-- org-specific -->`) | 7,200 | 22,200 | 30,000 | Rolls in as each contract expires — spread across 3–12 months |
| **Reduced operator confusion / cognitive-load savings** — operators on two overlapping meeting-notes tools spend time deciding which to use | 0 | 20,000 | 60,000 `<!-- org-specific: thin evidence base; use only with BU-sponsor-confirmed signal -->` | Begins month 4 of the transition |
| **Reduced governance-and-intake burden** — intake, AUP, SOP, and training re-cycles are fewer when the tool count drops | 5,000 | 25,000 | 60,000 | Full benefit lands month 9 onward |
| **Risk reduction — retiring shadow and orphan tools reduces expected-loss from policy-violation-surfacing-externally and from a regulator-flagged literacy gap** (expected-loss math per Exercise 02) | 10,000 | 50,000 | 180,000 | Step-function at retirement |
| **Procurement discount leverage — consolidating onto fewer vendors creates volume-based negotiation posture on remaining contracts** | 0 | 15,000 | 50,000 `<!-- org-specific: requires procurement input on vendor concentration posture -->` | Lands at next renewal cycle |
| **Rollup (year 1, ramped)** | **~22k** | **~130k** | **~380k** |  |

**Costs side:**

| Cost | P50 (USD) |
|---|---|
| Migration labor — Enablement + Procurement + Finance + affected-BU sponsors for the cutover windows | ~40,000 |
| Training and comms — retraining operators onto the retained tool for each cluster | ~20,000 |
| Early-termination fees — T05 pilot (if applicable), T06 orphan (if cancellable) `<!-- org-specific -->` | ~10,000 |
| Signal-loss mitigation — running the retiring and retained tools in parallel for a short bridge window | ~15,000 |
| Risk reserve — two of the migrations go longer than planned | ~10,000 |
| **Year-1 cost rollup** | **~95,000** |

**Net (expected case, P50):** ~130k - ~95k = **~35k net year-1 savings**; **break-even month ~10** (P50).

But the real payoff is **year 2 forward**: once the retiring contracts are fully off, the recurring benefit lines (~90k/year direct savings + ~25k/year governance-burden + ~50k/year risk-reduction + ~15k procurement leverage ≈ ~180k/year) carry forward against a much smaller recurring migration cost (~5k/year sustaining comms). **Year-2 net ~175k; year-3 net ~190k (with renewal leverage).**

**Narrative to the council:** the year-1 case is near-break-even and should be framed honestly as such; the story is the **cumulative three-year net** (~400k) and the **governance-posture improvement** (shadow tools retired, intake coverage on all retained tools, AUP and SOP coverage on all retained tools).

### 2.5 Transition plan

| Phase | Weeks | Primary actions | Who | Reversal condition for this phase |
|---|---|---|---|---|
| **Phase 0 — Intake backfill for the uncovered tools** | Weeks 1–3 | Run intake on T05, T06, T12, T13 (AI module). This is independent of consolidation; it is governance hygiene. | Enablement + intake owners | — |
| **Phase 1 — Meeting-notes consolidation** | Weeks 4–10 | Cutover window: parallel-run T04 and the two retiring tools for 2 weeks; migrate operators; cancel T06 at next renewal; terminate T05 pilot; confirm no silent data left in retiring tools (per mod-109 kill-switch pattern). | Enablement + affected BU sponsors (Sales, Legal, orphan owner) + Procurement | Rollback if operator-satisfaction signal drops > 15% for > 2 weeks on the retained tool. |
| **Phase 2 — HR + IT + knowledge-base evaluation** | Weeks 6–14 (parallel to Phase 1) | Run mod-102-shape evaluation of T11 against the T07-wrapped assistant family's knowledge-base-search capability. If T07-family wins, retire T11 at end of charter; if not, retain. | Enablement + Knowledge-Mgmt BU + Engineering | Keep T11 if the evaluation does not clearly show feature parity on the knowledge-base-search capability. |
| **Phase 3 — Image generation governance-first** | Weeks 4–8 (parallel) | Intake T12. If intake pass → retain or replace with an intake-complete option; if intake fail → retire. | Enablement + Marketing BU + Security + Legal | Immediate retire if intake fails on data-handling or AUP coverage. |
| **Phase 4 — Transcription AI-module deactivation** | Weeks 8–12 | Deactivate the AI module on T13; route AI-shaped transcription needs to T04 for meeting contexts. | Enablement + Operations BU + Procurement (for module-pricing adjustment) | Reactivate the module if T04 does not cover the non-meeting dictation use case; retain legacy T13 workflow for its original scope regardless. |

### 2.6 Risks and mitigations

| Risk | Likelihood | Mitigation |
|---|---|---|
| Operator backlash on the retained tool in meeting-notes cluster | Medium | Parallel-run window; comms via champion network (mod-105); operator feedback loop at week 2 and week 4 of the cutover. |
| Silent data left in retiring tools (operator notes, saved summaries, embedded links) | Medium | Kill-switch audit per mod-109 pattern: documented confirmation that the retiring tools' tenants are empty and the vendors have deleted per DPA before contract close. |
| Early-termination fees higher than planned | Low-medium | Pre-confirm termination terms before announcing the consolidation; carry a reserve. |
| BU sponsor pushback on losing their preferred tool (T05 Legal, T06 orphan owner, T11 KM sponsor) | High on Legal (T05); medium on KM (T11) | 1:1 pre-brief per BU sponsor in week 2–3; co-author the cutover window with each affected BU; honor one feature-gap in the retained tool if it is BU-critical and can be delivered as a configuration. |
| Signal loss during cutover (dashboards, telemetry, usage reports) | Medium | Bridge-window telemetry: both tools emit usage signal through week-6 (a dashboard overlay); do not retire a tool without the retained tool's telemetry already operational. |
| Regulator or auditor arrives during the cutover window and asks for tool-level evidence that is mid-migration | Low-medium | Keep the inventory snapshot and the consolidation pack as auditor-facing artifacts; the pack itself is evidence of a governed consolidation. |

### 2.7 Decision rationale — why consolidate this way, not another

- **Why inventory first, overlap second, target stack third.** Most consolidation efforts invert this order and produce a target stack that reflects the Enablement Lead's preferences rather than the organization's actual capability needs. Running inventory → overlap → target protects against that by making the overlap analysis the step where the retired-tool list is proposed.
- **Why capability-grain, not product-grain.** Three meeting-notes vendors map to one capability; two assistants-of-knowledge-bases on the same vendor map to one capability; an AI module on a legacy transcription tool is a separate capability from its legacy host. The grain defines the consolidation moves.
- **Why the ROI is three-year, not one.** Year-1 of a consolidation is near-break-even by design; the retired contracts take 3–12 months to roll off. Framing year-1 ROI as the decision input will make consolidation look unattractive; year-3 cumulative is the honest view.
- **Why risk-reduction is not quantified as "insurance payout avoided."** Shadow tools raise real expected loss (per Exercise 02's expected-loss framing); the solution scopes the benefit as expected-loss reduction grounded in the same probability × impact × posture-reduction form, not as a vendor-insurance-style number.
- **Why phases have reversal conditions.** Any individual retirement can go wrong (operator satisfaction, feature gap, surprise signal loss). Naming the reversal condition per phase is what makes the consolidation reversible without re-opening the whole decision.
- **Why intake backfill is Phase 0, not Phase 1.** Governance hygiene (intake coverage on shadow tools) is independent of consolidation; running it first means the consolidation decisions are made on fully-intaked tools, not on half-governed ones.

## 3. Validation steps

1. **Inventory is at the capability grain.** Each row names the capability, the vendor class, the seats/consumption, the annual cost, the governance status, and the owner role. Pure-product inventories that don't cluster into capabilities fail.
2. **Overlap analysis names each cluster** and counts the consolidation candidates.
3. **Target stack states what changes and what does not.** No-change clusters are acknowledged explicitly (prevents the appearance of scope creep).
4. **Consolidation ROI uses the Exercise 02 shape**: three scenarios, benefits broken into categories (direct cost savings, operator-time, governance-burden, risk-reduction, procurement leverage), with a cost side.
5. **Year-1 and year-3 numbers both reported.** A year-1-only ROI fails on honest framing; a year-3-only ROI fails on near-term commitment.
6. **Each phase in the transition plan has a reversal condition** stated operationally.
7. **Risks table carries at least five risks** with mitigations.
8. **Phase 0 = intake backfill** for uncovered tools, run independently of the consolidation decisions.
9. **Silent-data-check is explicit in the risks or in the Phase 1 plan** (per mod-109 kill-switch discipline).
10. **Role-name addressing throughout.** No people names.
11. **`org-specific` tags** on specific annual costs, specific seat counts, specific termination-fee amounts.
12. **No vendor product names in the printed pack.** Vendor classes are allowed; specific product names are not.
13. **Cross-references** to Exercises 01 / 02 / 03 / 04 and to mod-102 / mod-103 / mod-105 / mod-106 / mod-109 are present.

## 4. Rubric / review checklist

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | Inventory present, at capability grain, with governance-status column | 10 | Inventory missing, product-grain only, or no governance status. |
| R2 | Overlap analysis names each cluster and the consolidation candidates | 10 | Overlap analysis missing or doesn't collapse to capabilities. |
| R3 | Target stack states what changes **and** what does not | 5 | Changes-only view (reads as scope creep). |
| R4 | ROI uses the Exercise 02 shape (P10/P50/P90, categories, cost side) | 15 | Single-point ROI, missing categories, or no cost side. |
| R5 | Year-1 and year-3 ROI both reported | 10 | Only one horizon reported. |
| R6 | Risk-reduction is expected-loss math per Exercise 02, not a free-standing estimate | 10 | Risk-reduction stated as a flat dollar number. |
| R7 | Transition plan has phased cutover with reversal conditions per phase | 10 | No phasing or no reversal conditions. |
| R8 | Phase 0 = intake backfill for uncovered tools (governance-first) | 5 | Intake backfill treated as an after-step. |
| R9 | Silent-data check named explicitly (per mod-109 kill-switch pattern) | 5 | No silent-data-check for retiring tools. |
| R10 | Risks table ≥ 5 rows with mitigations | 5 | Too few risks or no mitigations. |
| R11 | Role-name addressing; no people names | 5 | People names used. |
| R12 | `org-specific` tags on org-specific values | 5 | Unmarked quoted numbers. |
| R13 | No vendor product names in the printed pack | 5 | Vendor product names appear. |

**Pass threshold:** ≥ 85/100 and no R4 / R6 / R7 / R8 fail. R4 (Exercise 02 shape), R6 (expected-loss math on risk-reduction), R7 (phased cutover with reversal), and R8 (intake backfill first) are the discriminators between a consolidation pack and a wish list.

## 5. Common mistakes

- **Inventorying at the product grain.** "We have Vendor A, Vendor B, and Vendor C for meeting-notes" is three rows; the overlap is invisible until the row is "meeting-notes capability, three products." Cluster into capabilities before overlap analysis.
- **Year-1-only ROI.** Consolidation ROI in year 1 is near-break-even by design because retiring contracts roll off over 3–12 months. Framing year-1 as the decision input understates the benefit and risks killing a valid consolidation.
- **Over-claiming cost savings on retired contracts.** Early-termination fees and parallel-run windows eat into the apparent savings; the year-1 model should carry those costs explicitly.
- **Risk-reduction as a flat dollar number.** "Saves 100k/year by retiring shadow tools" without expected-loss math is unaudited. Apply Exercise 02's probability × impact × posture-reduction form.
- **Treating the internal RAG platform (T08 in the example) as a consolidation question.** It is a build-vs-buy question (Exercise 03), not a consolidation question. Keeping them separate protects both exercises from motivated reasoning.
- **Omitting the silent-data check.** Retiring a tool without confirming its tenants are empty is a mod-109 failure mode and a real regulatory exposure; include the check in the plan.
- **Doing consolidation before intake backfill.** Running overlap analysis on half-governed tools means half the consolidation decisions are being made on tools with unknown posture. Intake backfill is Phase 0 for a reason.
- **No reversal condition per phase.** A phased plan without reversal conditions is a sequenced plan, not a reversible one. Each phase lists the signal under which it would roll back.
- **Addressing to people names.** The pack survives signatory changes only if it addresses roles.
- **Naming specific vendor product names in the printed pack.** The pack is an internal artifact that may circulate widely; vendor product names are an unnecessary disclosure. Vendor classes are allowed; products are not.
- **Treating consolidation as a one-off exercise.** The consolidation cadence is quarterly (mod-107 → Exercise 04 quarterly tactical cadence); the pack format persists even when the number of candidate consolidations is zero in a given quarter.

### 5.1 Stretch — the "second-pass" consolidation after certification

For the mature program (post-ISO/IEC 42001 certification per mod-108), a second-pass consolidation is run on a different grain: **certification-evidence coverage**, not capability overlap. The question becomes "which tools carry audit-grade evidence (intake, AUP, SOP, DPA, training-roster mapping, incident-record), and which do not — and can we retire the uncovered tools even if they are not duplicates?" This second-pass surfaces tools the first-pass missed (because the first-pass only looked for duplication) and is run annually at the strategic-cadence meeting from Exercise 04 Section 4.

## 6. References

- **Learning material (local):**
  - [Exercise 01 — Enablement Cost Model Drill](../exercise-01-enablement-cost-model-drill/SOLUTION.md) — the cost basis for the inventory annual-cost column.
  - [Exercise 02 — ROI Projection with Confidence Bands](../exercise-02-roi-projection-with-confidence-bands/SOLUTION.md) — the shape of the consolidation ROI (three scenarios, expected-loss math).
  - [Exercise 03 — Org-Scope Build-vs-Buy Matrix](../exercise-03-org-scope-build-vs-buy-matrix/SOLUTION.md) — handles the internal RAG platform (T08) decision outside this consolidation pack.
  - [Exercise 04 — Procurement and Finance Partnership Contract](../exercise-04-procurement-and-finance-partnership-contract/SOLUTION.md) — quarterly tactical cadence consumes the consolidation shortlist.
  - [mod-102 — Selecting and Rolling Out AI Tools](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-102-selecting-and-rolling-out-ai-tools) — the intake pattern used for Phase 0 backfill.
  - [mod-103 — Policy Co-authoring with Governance](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-103-policy-co-authoring-with-governance) — role-name addressing and governance posture.
  - [mod-105 — Champion Networks and Change Management](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-105-champion-networks-and-change-management) — the comms channel for the transition plan.
  - [mod-106 — Outcome Measurement and Executive Reporting](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-106-outcome-measurement-and-executive-reporting) — the executive-scorecard reach signal that tracks reversal conditions.
  - [mod-108 — Industry and Regulatory Flavours of Enablement](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-108-industry-and-regulatory-flavours-of-enablement) — the certification posture that triggers the Section 5.1 second-pass consolidation.
  - [mod-109 — AI Incident Response and Enablement-Side Rollback](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-109-ai-incident-response-and-enablement-side-rollback) — the kill-switch and silent-data-check pattern for retiring tools.
- **Official standards and frameworks:**
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — the GOVERN function underpins the governance-status column in the inventory.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — threat posture frame for the risk-reduction category.
  - [MITRE ATLAS](https://atlas.mitre.org/) — adversarial-technique context for the risk-reduction scoping.
