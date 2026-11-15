# Exercise 05 — AI Productivity Literature to Metric Choice Map — Reference Solution

> Module: `mod-106-outcome-measurement-and-executive-reporting`
> Exercise type: design / research-to-practice mapping memo
> Exercise brief: `lessons/mod-106-outcome-measurement-and-executive-reporting/exercises/exercise-05-ai-productivity-literature-to-metric-choice-map.md` (in the learning repo)

## 1. Solution overview

The enablement seat will be asked, at least once, "what does the research say about AI productivity, and are you measuring the right things against it?" The question is usually asked by a board member or a skeptical VP who has read a trade-press summary of a recent paper. The *wrong* answer is "we are using the metrics the research uses"; the *right* answer is a documented, defensible map showing which research-grade constructs the program adopted, which it adapted, and which it declined to adopt — and why.

The map is a memo, not a dashboard. Its job is **defensibility under scrutiny**, not comprehensiveness. A defensible map:

- names the literature by its real authors and sources (no invented citations);
- states clearly what claim each piece of literature actually supports (which is usually narrower than the trade-press summary);
- maps each construct to a metric in the local program (or declines the construct explicitly);
- preserves the attribution-honesty discipline from `exercise-01` and `exercise-04`;
- distinguishes **research constructs** (what a paper measures) from **organizational outcomes** (what the business cares about), and names when the two can be used as proxies and when they cannot.

The solution provides:

1. A **literature inventory** — the named bodies of work the enablement seat should be literate on, with a precise one-paragraph description of what each supports.
2. A **construct-to-metric map** — how each construct from the inventory maps to a metric (or non-metric) in the local program.
3. A **what-we-declined section** — the moves the program deliberately does not make, with the reasoning.
4. A **"how to update this memo" cadence** — the research landscape moves; the memo must be kept live.

Posture checks the solution encodes:

- **Cite real work; do not invent.** Where a specific numeric claim from a paper is referenced without the author's own confidence framing, mark it `<!-- author-to-confirm: ... -->`.
- **Research construct ≠ organizational outcome.** A map that reports "we hit the Peng-et-al number on our team" has already conflated them.
- **Absence is a choice.** The memo names which constructs the program chose not to adopt, which is often the more defensible half of the answer.
- **The memo has a version date.** The AI productivity literature in 2025–2026 is moving fast; an undated memo is a trap for the reader.

## 2. Implementation — worked answer (`ai-productivity-literature-map.md`)

The artifact below is written as the memo the enablement seat hands to the governance council pre-read for any quarterly review where the question "are we measuring the right things against the research?" is on the table.

---

### AI Productivity Literature → Program Metric Map — v1.0

**Author:** AI Enablement Lead (this role).
**Reviewers:** `head-of-ai-governance` (L60), `senior-ai-governance-architect` (L50), VP Engineering (or peer at scope of the piloted tool).
**Version:** 1.0.
**Memo date:** `<!-- author-to-confirm: confirm memo publication date -->`.
**Next review:** quarterly, or on publication of a major new piece of literature in this space.
**Scope:** developer-productivity and knowledge-work-productivity claims as they apply to the organization's current AI tool portfolio (coding assistant at GA, customer-support agent in pilot).

---

#### 2.1 Literature inventory

Each entry below names a real body of work. Each entry describes the claim the literature actually supports — not the trade-press summary. Where a specific numeric finding is referenced, the reference is to the authors' own framing.

**Entry L1 — DORA metrics (Accelerate; State of DevOps Reports).**
Source: Nicole Forsgren, Jez Humble, Gene Kim. *Accelerate: The Science of Lean Software and the Theory of Constraints, Nonlinear Management, and the Business of Software* (IT Revolution Press, 2018). Successor work: the annual State of DevOps Reports (DORA / Google). What the work supports: **four organizational-outcome metrics** for software delivery — deployment frequency, lead time for changes, change failure rate, and mean time to restore. The work's own framing: these are measures of *organizational capability*, not of individual productivity. The State of DevOps Reports have, in recent editions, added measures of software reliability and (in some editions) developer-experience signals; the AI-adjacent claims in the 2023–2024 reports are framed by the authors as *correlations with capability*, not as causal effects of AI tool adoption. `<!-- author-to-confirm: confirm the exact title and publication year of the most recent State of DevOps Report at memo date; confirm whether its AI section is positioned as correlational per the authors -->`.

**Entry L2 — SPACE framework.**
Source: Forsgren, Storey, Maddila, Zimmermann, Houck, "The SPACE of Developer Productivity: There's more to it than you think," ACM Queue, 2021. What the work supports: a framework that developer productivity is multi-dimensional and should be measured across **Satisfaction and well-being, Performance, Activity, Communication and collaboration, and Efficiency and flow** — the "SPACE" acronym. The work's own framing is explicitly that **no single dimension is sufficient** and that activity metrics in isolation (e.g., lines of code, commits) are misleading. The framework is a *lens*, not a metric set; adopters pick measures per dimension that fit their context.

**Entry L3 — GitHub Copilot developer-productivity study.**
Source: Peng, Kalliamvakou, Cihon, Demirer, "The Impact of AI on Developer Productivity: Evidence from GitHub Copilot," Microsoft/GitHub, 2023 (preprint, arXiv:2302.06590). What the work supports: in a controlled experiment where developers wrote an HTTP server in JavaScript, those with access to Copilot completed the task faster than those without, with the authors reporting a **specific median task-completion speedup for that task** (`<!-- author-to-confirm: confirm the exact median speedup percentage reported by the authors and its confidence interval -->`). The authors' own framing is explicit: the result is for **one task, one language, one developer population**, and does not generalize to "developer productivity" as an organizational outcome. The paper is a point measurement, not a general productivity claim.

**Entry L4 — Microsoft knowledge-worker productivity with generative AI (Copilot for Microsoft 365 studies).**
Source: Microsoft Research and partner studies on knowledge-worker tasks (e.g., writing, summarization, meeting-prep) with generative-AI assistance; several preprints and Harvard-Microsoft collaborations published 2023–2024. What the work supports: on specific knowledge-work tasks tested in a controlled or quasi-controlled setting, assisted workers completed tasks faster and (in some studies) produced output rated at comparable or higher quality by blind reviewers. The authors' own framing varies by study but consistently bounds the claim to task-level, population-level, and context-level findings. `<!-- author-to-confirm: name the specific Microsoft/Harvard study and its exact task-level findings most relevant to the organization's customer-support-agent use case; preserve author framing -->`.

**Entry L5 — Dell'Acqua et al. "Navigating the Jagged Technological Frontier."**
Source: Dell'Acqua, McFowland, Mollick, Lifshitz-Assaf, Kellogg, Rajendran, Krayer, Candelon, Lakhani, 2023 (Harvard Business School working paper). What the work supports: in a controlled experiment with consultants performing consulting-style tasks with and without GPT-4 access, performance on tasks *inside* the model's capability frontier improved, and performance on tasks *outside* that frontier degraded when consultants used the AI unreflectively. The authors' own framing is explicit about the **"jagged frontier"** — the gain is task-dependent, and the degradation case is real. `<!-- author-to-confirm: confirm the specific effect sizes reported and the tasks classified inside / outside the frontier -->`.

**Entry L6 — Noy and Zhang "Experimental evidence on the productivity effects of generative AI."**
Source: Noy, Zhang, "Experimental evidence on the productivity effects of generative artificial intelligence," *Science* 381, 187–192 (2023). What the work supports: in a controlled experiment on mid-level professional writing tasks, assisted participants completed tasks faster and their output was rated higher in quality; the effect was larger for lower-ability participants, narrowing the ability gap in output quality. The authors' own framing: the task set is specific (mid-level writing), the population is specific, and the equity-narrowing effect is specific to this experimental context. `<!-- author-to-confirm: confirm the exact effect sizes and the task set specification -->`.

**Entry L7 — RCT and real-world evaluations of coding assistants (customer-support, call-center).**
Source: Brynjolfsson, Li, Raymond, "Generative AI at Work," NBER Working Paper 31161 (2023). What the work supports: on live call-center customer-support tasks, access to a generative-AI-based assistant was associated with a productivity increase, with the largest effect on less-experienced workers. The authors' own framing bounds the claim to the specific tool, deployment context, and worker population; the paper is cautious about generalizing to non-customer-support knowledge work. `<!-- author-to-confirm: confirm exact effect sizes and the worker-tenure distribution of the effect -->`.

The inventory is not exhaustive. The seven entries above are the ones the enablement seat should be literate on because they are the ones a board member or skeptical VP is most likely to have read a summary of, and because each supports a different claim shape that the program map responds to differently.

---

#### 2.2 Construct-to-metric map

The table below maps each literature construct to the program's current metric choice. The three columns name the construct, how the program handles it, and why. The memo is the defensible answer to "are you measuring what the research measures?" — the answer is explicit, and sometimes no.

| # | Literature construct | Program handling | Why |
|---|---|---|---|
| M1 | **DORA — deployment frequency** (L1) | **Not** on the AI-program scorecard. Tracked at the platform / SDLC level by the platform-engineering team. | Deployment frequency is an organization-wide capability measure. Assigning it as an AI-program outcome would overclaim the AI tool's causal contribution. The program references the platform team's measurement where relevant in the quarterly review (`exercise-03`, §3 attribution-honesty paragraph). |
| M2 | **DORA — lead time for changes** (L1) | **Adopted as a program outcome.** Specifically: median change-review cycle time on AI-assisted PRs, with baseline and non-AI-assisted comparison window (per `exercise-01`). | Lead time attaches to a workflow (code review) that exists without the tool, has a measurable baseline, and is the dimension the coding-assistant pilot was chartered to move. This is the closest research construct to a defensible program outcome. |
| M3 | **DORA — change failure rate** (L1) | **Adopted as a non-regression floor.** Specifically: post-merge defect rate on AI-assisted PRs vs. baseline. | Change failure rate is the paired quality signal that prevents "faster but worse" from reading as a success. Non-regression floor per `exercise-01` Type 2. |
| M4 | **DORA — time to restore service** (L1) | **Not on the AI-program scorecard.** | Time to restore is a platform / SRE measure; the AI program's incident impact on restoration is captured in `mod-109` after-actions, not in the outcome row. |
| M5 | **SPACE — Satisfaction** (L2) | **Adopted as a leading indicator.** Specifically: pilot-user NPS or satisfaction survey, labeled "leading — not a success metric" per `exercise-01`. | Satisfaction correlates with sustained adoption and is a legitimate signal, but the research itself frames it as a dimension, not a success measure. The program keeps it in §5 of the weekly scorecard. |
| M6 | **SPACE — Performance** (L2) | **Adopted.** Mapped to M2 (lead time) and a sampled quality-rating secondary outcome. | SPACE-Performance is the dimension that most directly maps to outcome metrics as `exercise-01` defines them. |
| M7 | **SPACE — Activity** (L2) | **Adopted *only* as leading indicator; never as outcome.** Activation, suggestion-acceptance rate, DAU/WAU — all in §5. | SPACE's own framing is explicit: activity in isolation is misleading. The program takes that framing seriously and refuses to let activity move the §3 outcome rows. |
| M8 | **SPACE — Communication and collaboration** (L2) | **Not measured at the program level.** Deferred. | This dimension is harder to measure defensibly and the program's current charter does not claim movement here. The quarterly review may add a measure if a specific use case (e.g., PR review quality via sampled reviewer comments) is chartered. The memo states the deferral to prevent the dimension from creeping in via a composite later. |
| M9 | **SPACE — Efficiency and flow** (L2) | **Not measured at the program level.** Deferred, with a note. | Flow measurement typically relies on self-report instruments that are expensive to run at scale; the program notes the deferral and the condition that would trigger adoption (a chartered research question, not a routine scorecard field). |
| M10 | **Peng et al. task speedup** (L3) | **Not used as a program claim.** Referenced in the attribution-honesty paragraph as prior evidence that a coding-assistant *can* produce task speedups in a controlled setting, which is one input among several that justified chartering the pilot. | The research is a point measurement for one task; adopting it as a program-level ROI number is overclaiming. The memo states this explicitly so the board does not see "Peng et al. reported X%" on an ROI slide. |
| M11 | **Microsoft / Harvard knowledge-worker studies** (L4) | **Used as evidence base for the customer-support-agent pilot charter**, not as an outcome target. | Same posture as M10. The pilot is chartered to test whether the published effects reproduce in the organization's context. "The pilot replicates the Microsoft study" is not a claim the memo lets the program make. |
| M12 | **Dell'Acqua et al. jagged frontier** (L5) | **Used in the training curriculum (`mod-104`) and the use-policy's approved-uses list (`mod-103/exercise-01`)**, not as a scorecard metric. | The jagged-frontier finding motivates the policy's insistence on operator review of outputs and the training's focus on judgment. It does not translate into a routine metric; it translates into a control. The memo makes this distinction because a reader may expect "jagged frontier" to appear as a dashboard field. |
| M13 | **Noy and Zhang mid-level writing speedup and quality** (L6) | **Used as evidence base for the drafting-tool evaluation**, not as an outcome target. | Same posture as M10 and M11. The equity-narrowing finding from the paper is noted in the training curriculum's framing of who benefits from early access. |
| M14 | **Brynjolfsson et al. call-center productivity** (L7) | **Used as evidence base for the customer-support-agent pilot charter, specifically for the choice of less-experienced-cohort-first pilot cohort.** | The paper's finding that the largest effect was on less-experienced workers informed the pilot cohort selection. The program does not claim the paper's effect sizes; it states that the cohort selection was informed by the finding. |

---

#### 2.3 What we declined to adopt

The map's defensibility often turns on what the program chose *not* to do. The entries below are explicit decisions, each with the reasoning.

- **Lines of code produced, or any variant.** Declined on the SPACE Activity reasoning (L2 / M7). Lines of code produced is the canonical misleading activity metric and would make the program instantly indefensible.
- **"Suggestion-acceptance rate" as a success metric.** Declined. Acceptance rate is in §5 of the scorecard as a leading indicator (M7). Making it an outcome rewards acceptance for its own sake and invites gaming.
- **A composite "AI productivity index."** Declined on the composite-dodge anti-pattern from `exercise-01`. Composites hide which dimension moved; the exec cannot interpret the headline. The program publishes the sub-metrics and refuses to compute the composite.
- **Headline claims derived from a single paper.** Declined. The memo uses literature as *evidence for charter decisions and policy controls*, not as *values to publish on a scorecard*. Any slide in a quarterly review (`exercise-03`) that says "we are delivering the Peng/Brynjolfsson/Noy finding" misreads the research.
- **A per-engineer productivity-rank list.** Declined. The DORA framing (L1) and the SPACE framing (L2) both reject individual-level productivity measurement as methodologically unsound and as organizationally corrosive. The program's measurement is at the workflow and cohort level, never at the engineer level.
- **"AI-assisted vs. non-AI-assisted" as a strong causal claim.** Declined. The program's sampling plan compares AI-assisted PRs against non-AI-assisted PRs for *trend direction*, not for causal attribution. The attribution-limit line in every scorecard (`exercise-02`, §9) carries this bound forward.

---

#### 2.4 How this memo is updated

- **Quarterly review.** This memo is re-read and re-dated at the start of each quarterly review cycle (`exercise-03`), with a one-paragraph change-note listing any literature added, any construct whose program handling changed, and any newly declined move.
- **On publication of a material new paper.** When a paper is published that is likely to be read by a board member or skeptical VP, the memo is updated to add an inventory entry, even if the program handling does not change. The purpose is defensibility; leaving a well-known paper off the inventory reads as not having read it.
- **Version discipline.** Memo-level changes bump the version (v1.0 → v1.1 for an inventory add; v1.0 → v2.0 for a change in program handling). Change-notes are carried in a short changelog at the memo's foot.

### End of worked memo

## 3. Validation steps

A reviewer should be able to confirm, from the learner's artifact:

1. **At least five literature entries.** Named with real authors and sources. Trade-press-only citations do not count.
2. **Each literature entry carries an authors'-own-framing line.** Not just "the paper says 55% speedup"; "the authors frame the finding as task-specific, population-specific."
3. **Numeric claims from the literature are marked `<!-- author-to-confirm: ... -->` where the exact figure is not available to the author at write time.** No invented effect sizes.
4. **A construct-to-metric map of at least ten rows.** Each row shows handling (adopted, adapted, not adopted, deferred) with reasoning.
5. **A what-we-declined section with at least four entries.** Each declined move is explicit, not implied.
6. **The map reflects the metric framework from `exercise-01`.** Leading indicators are labeled as such; outcomes attach to workflows; non-regression floors are present.
7. **The map carries the attribution-honesty discipline.** No program-level claim of a specific research effect size.
8. **The memo is dated and versioned.** Undated memos fail.
9. **The update cadence is named.** The memo's maintenance plan is part of its credibility.
10. **The memo is self-contained.** A board member who has not read this module should be able to read the memo and understand the program's position on the research.

## 4. Rubric / review checklist

Scored out of 100. Pass threshold: ≥ 80 and no R1/R3/R5/R7 fail.

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | ≥ 5 literature entries, each with real author(s) and source | 15 | Invented citations; or trade-press-only references. |
| R2 | Each entry carries an authors'-own-framing line | 10 | Trade-press summary presented as the claim. |
| R3 | Numeric claims marked `<!-- author-to-confirm: ... -->` where exact figure unavailable | 10 | Invented effect sizes. |
| R4 | Construct-to-metric map ≥ 10 rows with handling + reasoning | 15 | Fewer than 10 rows; or reasoning absent. |
| R5 | What-we-declined section ≥ 4 entries with reasoning | 15 | Fewer than 4; or declines without reasoning. |
| R6 | Map labels align with `exercise-01` (outcome / non-regression / leading / governance) | 10 | Leading indicators presented as outcomes. |
| R7 | No program-level claim of a specific research effect size | 10 | "We are delivering the X study's Y% speedup." |
| R8 | Dated and versioned | 5 | No date or version. |
| R9 | Update cadence named | 5 | No maintenance plan. |
| R10 | Memo is self-contained for a board-member reader | 5 | Requires reading the module to interpret. |

## 5. Common mistakes

- **Citing a trade-press summary as the research.** The quickest way to be caught out by a board member who has actually read the paper.
- **Adopting a paper's effect size as a program target.** Peng et al. reported a specific task-level speedup; the program is not that task, that language, or that developer population. The paper is evidence for a charter decision, not a scorecard value.
- **No "declined" section.** The memo without this section reads as credulous. The declined section is the memo's spine.
- **Conflating SPACE dimensions with metric categories.** SPACE is a framework for *thinking about what to measure*; `exercise-01` is a framework for *typing the metrics you have chosen*. They are complementary but not interchangeable. The map keeps them distinct.
- **Composite indices.** Papers sometimes report composites; the program should not. If a paper's composite is referenced, decompose it and map each sub-dimension.
- **Per-engineer rankings.** A career-ender in this role. The literature explicitly rejects this move; the memo must reject it too.
- **Undated memos.** A memo without a date is a memo that cannot be trusted in a fast-moving research space. Date the memo and name the next review.
- **Overclaiming the Dell'Acqua "jagged frontier" framing as a metric.** The jagged-frontier finding motivates a *control*, not a *dashboard field*. The memo names the control (operator review of outputs) and declines to make it a metric.
- **Treating the inventory as exhaustive.** New papers will land between memo versions. The memo names its own incompleteness.
- **Writing in academic voice.** The memo is for a board member. Shorten the inventory entries; keep the plain-language framing. "The authors report a speedup on one task" is better than "The authors conduct a controlled experiment with N participants randomized into treatment and control conditions."

## 6. References

- **Named literature cited in the inventory (verify exact titles and publication years at memo update time):**
  - [L1] Nicole Forsgren, Jez Humble, Gene Kim, *Accelerate* (IT Revolution, 2018). Annual State of DevOps Reports (DORA / Google) — `<!-- author-to-confirm: confirm current edition at memo date and whether the AI section is positioned as correlational per the authors -->`.
  - [L2] Forsgren, Storey, Maddila, Zimmermann, Houck, "The SPACE of Developer Productivity," ACM Queue, 2021 — <https://queue.acm.org/detail.cfm?id=3454124>.
  - [L3] Peng, Kalliamvakou, Cihon, Demirer, "The Impact of AI on Developer Productivity: Evidence from GitHub Copilot," 2023 — arXiv:2302.06590. `<!-- author-to-confirm: verify the final arXiv version or peer-reviewed publication the authors reference -->`.
  - [L4] Microsoft Research and partner studies on knowledge-worker tasks with Copilot for Microsoft 365, 2023–2024 — `<!-- author-to-confirm: name the specific study and its DOI relevant to the organization's customer-support-agent use case -->`.
  - [L5] Dell'Acqua, McFowland, Mollick, Lifshitz-Assaf, Kellogg, Rajendran, Krayer, Candelon, Lakhani, "Navigating the Jagged Technological Frontier," Harvard Business School Working Paper, 2023 — `<!-- author-to-confirm: confirm final working-paper number and DOI -->`.
  - [L6] Noy, Zhang, "Experimental evidence on the productivity effects of generative artificial intelligence," *Science* 381, 187–192 (2023) — <https://www.science.org/doi/10.1126/science.adh2586>.
  - [L7] Brynjolfsson, Li, Raymond, "Generative AI at Work," NBER Working Paper 31161, 2023 — <https://www.nber.org/papers/w31161>.
- **Official standards and frameworks:**
  - [NIST AI Risk Management Framework (AI RMF 1.0)](https://www.nist.gov/itl/ai-risk-management-framework) — the MEASURE function's emphasis on documented measurement methodology, uncertainty, and context motivates the authors'-own-framing discipline.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — background for the memo's position that per-engineer rankings are corrosive and expose the organization to additional misuse surface.
  - [MITRE ATLAS](https://atlas.mitre.org/) — background for the memo's position that activity metrics in isolation are misleading, including against adversarial manipulation of usage signals.
- **Local context (same repo):**
  - `modules/mod-106-outcome-measurement-and-executive-reporting/exercise-01-outcome-vs-usage-metric-framework/SOLUTION.md` — the metric framework the construct-to-metric map labels against.
  - `modules/mod-106-outcome-measurement-and-executive-reporting/exercise-02-the-weekly-executive-scorecard/SOLUTION.md` — the scorecard whose rows implement the map's adopted measures.
  - `modules/mod-106-outcome-measurement-and-executive-reporting/exercise-03-quarterly-board-ready-review-outline/SOLUTION.md` — the surface where the memo is referenced in response to "are you measuring the right things?"
  - `modules/mod-106-outcome-measurement-and-executive-reporting/exercise-06-roi-numerator-and-denominator-defence/SOLUTION.md` — the memo's declined-moves section is a direct input to ROI defence.
  - `modules/mod-104-training-programs-and-ai-literacy-curriculum/README.md` — the curriculum the Dell'Acqua "jagged frontier" construct feeds.
  - `modules/mod-105-champion-networks-and-change-management/README.md` — the equity-narrowing finding from Noy & Zhang informs cohort-selection framing here.
