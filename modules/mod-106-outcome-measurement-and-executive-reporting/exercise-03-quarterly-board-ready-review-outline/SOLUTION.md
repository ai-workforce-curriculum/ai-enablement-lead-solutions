# Exercise 03 — Quarterly Board-Ready Review Outline — Reference Solution

> Module: `mod-106-outcome-measurement-and-executive-reporting`
> Exercise type: design / outline + worked example
> Exercise brief: `lessons/mod-106-outcome-measurement-and-executive-reporting/exercises/exercise-03-quarterly-board-ready-review-outline.md` (in the learning repo)

## 1. Solution overview

The quarterly board-ready review is the artifact a board (or its risk/technology committee) reads to form a view of the AI enablement program's posture across a full quarter. It is **not** a scaled-up weekly scorecard; it answers a different set of questions in a different voice, for a different reader with a different attention budget.

Board readers are not operators. They:

- read the artifact once, in a packet, before a scheduled meeting;
- expect prose and one or two tables, not weekly deltas;
- want clear direction decisions, not status;
- carry fiduciary responsibility for enterprise-level risk, which shapes what they ask about (material incidents, regulatory exposure, concentration risk, ROI defence).

The solution provides:

1. A reusable **eight-section outline** (the shape).
2. A **worked example** for Q1 2026 at the running archetype organization (3,000-person US bank).
3. A **board-voice guide** — what to write differently than for the weekly scorecard.
4. A **pre-read contract** — what the artifact owes the board before the meeting so the meeting is for decisions, not status.

The outline consumes trends from four quarters of weekly scorecards (`exercise-02`), the attribution-honesty frame from the ROI defence (`exercise-06`), and the anti-pattern list from the metric framework (`exercise-01`). It is designed to pair with 20–30 minutes of board discussion time and no more than 8 slides if presented visually.

Posture checks the solution encodes:

- **Board voice, not operator voice.** The weekly scorecard says "activation is 68%." The board review says "adoption is on plan; sustained usage continues to be the leading indicator we watch, not the outcome we claim."
- **A direction decision is named in §1.** The board exists to direct; if the artifact does not name the direction decision it is requesting, the meeting will drift into status.
- **Material incidents are named explicitly.** Not aggregated into an incident count, named — with date, scope, resolution, and whether the recurrence control is in place. Board-level readers are held to a materiality standard; the artifact meets them where they read.
- **Attribution honesty is paragraph-length, not a line.** The board reader has more time than a weekly scorecard reader and asks harder questions about causation. The quarterly version earns space.
- **Regulatory exposure gets its own section.** An AI program at a regulated enterprise has standing regulator interest; the board expects to see it tracked.
- **ROI claims are bounded.** The quarterly review does not state "we saved $X"; it points to the ROI defence memo (`exercise-06`) and states the bound of what can and cannot be claimed this quarter.

## 2. Implementation — worked answer

### 2.1 The outline (`quarterly-review-outline.md`)

```markdown
AI Enablement Quarterly Review — Qn YYYY
Prepared for: Board Risk & Technology Committee (or whichever body is the
              standing recipient of AI-program reviews)
Prepared by:  AI Enablement Lead (this role), reviewed by
              head-of-ai-governance (L60), countersigned by CTO as sponsor
Date:         YYYY-MM-DD, distributed [N] business days before the meeting
Length:       [X] pages; [Y] slides if presented
```

#### §1. Executive summary (≤ ¾ page)

- One-paragraph statement of program posture at quarter close.
- Named **direction decision** the board is being asked to make at this meeting (or *no direction decision this quarter — informational review*).
- The one or two things the board should remember if they only read this section.

#### §2. Portfolio at quarter close (≤ ½ page + table)

| Tool | Stage at Q open | Stage at Q close | Change during Q | Posture at Q close |
|---|---|---|---|---|
| ... | ... | ... | ... | ... |

- One short paragraph naming any tool that changed stage (new pilot opened, pilot graduated to GA, tool retired) and why.
- A sentence on concentration risk — which single tool failing would hurt most, and the current mitigation.

#### §3. Outcomes against plan (≤ 1 page)

- For each primary outcome in the quarter, a short paragraph: name of outcome, trajectory across the four quarterly scorecard snapshots, where we landed vs. plan, what moved it (what we did, what was outside our control).
- At least one non-regression floor explicitly checked.
- **Attribution-honesty paragraph** — specific to this quarter: what we claim this program did, what we claim merely coincided with the program, and what the evidence supports each claim against.

#### §4. Governance posture over the quarter (≤ ½ page)

- Open high-severity findings at quarter close, by tool.
- Exceptions outstanding past SLA at quarter close.
- Policy changes ratified this quarter, with a one-sentence rationale each.
- Training compliance at role-tier level, if the program carries an EU AI Act Article 4 literacy-floor obligation or an equivalent `<!-- author-to-confirm: confirm whether the organization's jurisdiction imposes an operator-literacy obligation and name it -->`.

#### §5. Material incidents and near-misses (≤ ½ page)

- Named incidents this quarter, each with: date, tool, scope of impact (users affected, data classes touched, external reporting trigger if any), status at quarter close, recurrence-control status.
- Named material near-misses — the ones a board member would want to have seen even though no declaration occurred.
- Aggregate near-miss count across the quarter, with the volume-of-amnesty-reports observation if the program runs that channel.

#### §6. Regulatory and external exposure (≤ ½ page)

- Guidance updates from the program's primary regulator(s) during the quarter, with the one-line impact on the enablement surface.
- Any external reporting event (regulator disclosure, customer notification, vendor DPA renegotiation triggered by regulatory change).
- Third-party dependency changes — vendor DPA amendments, model-tier changes, pricing changes with ROI implications, deprecation announcements.

#### §7. ROI frame (≤ ⅓ page, pointer-heavy)

- Program spend this quarter at FinOps level — point to the FinOps roll-up (`mod-107`), do not re-derive.
- Current ROI claim shape: *what we can defend* vs. *what we cannot*, pointing to the ROI defence memo (`exercise-06`).
- The one or two assumptions in the ROI frame that would most change the number if revised.

#### §8. Direction decisions and risks for next quarter (≤ ½ page)

- The direction decision(s) from §1, re-stated with the options the board is being asked to choose among and the recommendation.
- 3–5 named risks for the next quarter, each with: owner, current mitigation, the condition that would escalate it to a board-level event.
- Items the program would like the board to formally note for the audit record (non-decisional).

---

### 2.2 Worked example — Q1 2026 (running archetype)

The archetype is the 3,000-person US bank used throughout this module and `mod-103`. The program at Q1 2026 close runs one tool at GA (coding assistant, in GA since Q3 2025), one active pilot (customer-support agent, in pilot since Q1 2026 start), and one stage-gated evaluation (a drafting tool, eval phase, no production exposure).

```markdown
AI Enablement Quarterly Review — Q1 2026
Prepared for: Board Risk & Technology Committee
Prepared by:  AI Enablement Lead (this role), reviewed by
              head-of-ai-governance (L60), countersigned by CTO as sponsor
Date:         2026-04-10, distributed 5 business days before the Board Risk &
              Technology Committee meeting on 2026-04-17
Length:       4 pages
```

**§1. Executive summary**

The AI enablement program closed Q1 2026 with the coding-assistant tool running at GA in a steady posture, a customer-support-agent pilot paused in Week 4 pending an output-handling finding (`SEC-AI-00117`), and a drafting-tool evaluation in a controlled no-production-exposure stage. The program had **one material near-miss** this quarter (coding assistant, data-handling self-report under amnesty; no customer data involved; recurrence control in place) and **no declared incidents**. Trajectory against the program-level outcome commitments is on plan for the coding assistant and pre-baseline for the two newer tools.

The board is being asked at this meeting to **direct whether the customer-support-agent pilot should resume on a 14-day timeline (recommendation) or be re-scoped as a bounded re-evaluation**. Both options are defensible; the choice turns on the board's appetite for continuing the pilot with a vendor-side open finding.

If the board only reads one thing in this packet: the program has credible early movement on the coding-assistant outcome (see §3), but the pilot pause in §5 is the signal to watch.

**§2. Portfolio at quarter close**

| Tool | Stage Q open | Stage Q close | Change during Q | Posture at Q close |
|---|---|---|---|---|
| Coding assistant | GA | GA | No stage change | Green |
| Customer-support agent | Not yet contracted | Pilot W4 (paused) | New pilot opened Q1; paused Week 4 | Amber |
| Drafting tool | Not evaluated | Evaluation (controlled) | New evaluation opened Q1 | Green — no production exposure |

**Concentration risk.** The coding-assistant program concentrates on a single vendor's generally-available tier; a vendor outage or a material regulatory finding against the vendor would create a short-term capability gap. The current mitigation is `<!-- author-to-confirm: confirm whether the program runs a secondary-supplier dry-contract per mod-107 build-vs-buy patterns -->` and the kill-switch exercise cadence per `mod-109`.

**§3. Outcomes against plan**

**Primary outcome — median change-review cycle time on AI-assisted PRs (coding assistant).**
The outcome moved from `<!-- author-to-confirm: baseline value from pre-GA window -->` at GA start (Q3 2025) to `<!-- author-to-confirm: Q1 close value -->` at Q1 2026 close, tracking on the charter's plan curve. The movement is within the window we expected to see; the plan does not yet rule out that the headline-feature coding assistant was tracking a broader SDLC improvement from an unrelated platform change in Q4 2025 (see attribution-honesty paragraph).

**Non-regression floor — post-merge defect rate.**
Post-merge defect rate on AI-assisted PRs is `<!-- author-to-confirm: current rate -->` against the baseline floor of `<!-- author-to-confirm: baseline rate -->`. The floor is not breached.

**Secondary outcome — reviewer-rated code quality (sample).**
Mean quality rating on the Q1 sample is `<!-- author-to-confirm: Q1 mean -->` against the baseline mean of `<!-- author-to-confirm: baseline mean -->`. The sample size (`<!-- author-to-confirm: n for Q1 -->`) is large enough to see trend but not to claim statistical significance.

**Customer-support-agent pilot:** pre-baseline by plan; no outcome rows yet.

**Attribution-honesty paragraph.**
The quarter-on-quarter movement in change-review cycle time *coincides with* coding-assistant GA. The plan does **not** include a controlled comparison with teams that did not adopt the tool, and so does not support the claim that the tool caused the movement. A Q4 2025 platform change to the CI system (`<!-- author-to-confirm: confirm Q4 2025 CI platform change name -->`) is a credible co-contributor. What we can defend is: the outcome moved during the coding-assistant window; the non-regression floor is intact; reviewer-rated quality has not moved in a direction that would complicate the usage story. What we cannot defend is a per-engineer-hour productivity claim. See §7 and the ROI defence memo (`exercise-06`).

**§4. Governance posture over the quarter**

- Open high-severity findings at quarter close: **1** (`SEC-AI-00117`, customer-support-agent output-handling). All other findings opened in-quarter closed in-quarter.
- Exceptions outstanding past SLA at quarter close: **0**.
- Policy changes ratified this quarter: **2**.
  - Revised data-handling SOP for the coding assistant (v1.3), adding masked-data obligations to the test-fixture path (per `mod-103/exercise-02`).
  - Revised intake questionnaire schema (v2.1), adding stakeholder-reach fields (per `mod-103/exercise-03`).
- Training compliance at role-tier level: `<!-- author-to-confirm: confirm current role-tier completion rates from mod-104 rosters; note whether EU AI Act Article 4 literacy-floor obligation applies -->`.

**§5. Material incidents and near-misses**

- **No declared incidents this quarter.**
- **One material near-miss, 2026-02-14, coding assistant.** A pilot engineer self-reported under amnesty that a test fixture containing names that resembled real customer names was pasted into a prompt. The fixture was confirmed synthetic. No customer data was involved and no external notification was triggered. The recurrence control was already in place (masked-data obligation added by SOP v1.3 three days prior). The near-miss is material to the board because it is the first validated test of the amnesty channel and it worked.
- **Aggregate amnesty-channel near-miss volume:** `<!-- author-to-confirm: Q1 count from amnesty log -->`. The volume is consistent with a healthy amnesty channel per the literature norms we reference in `mod-105`, which the program reads as a positive signal.

**§6. Regulatory and external exposure**

- Primary regulator for this program: `<!-- author-to-confirm: confirm the organization's primary prudential regulator in its jurisdiction — likely OCC, Federal Reserve, or FDIC for a US national bank; EBA/ECB for Eurozone; FCA/PRA for UK -->`.
- Guidance updates during Q1 2026: `<!-- author-to-confirm: name any regulator guidance update on generative AI in regulated financial services published during Q1 2026 and its one-line impact -->`.
- External reporting events this quarter: none.
- Third-party dependency changes: coding-assistant vendor renegotiated the DPA mid-quarter (`<!-- author-to-confirm: confirm DPA amendment date and nature -->`); counsel reviewed and approved; no material change to the program's data-handling posture.

**§7. ROI frame**

Program spend Q1 2026: see the FinOps roll-up per `mod-107`. The program's current ROI claim shape, defended in detail in `exercise-06`, is: **spend is real and measured**; **productivity movement is observed in the primary outcome**; **a per-engineer-hour productivity-gain-to-dollar translation is not currently defended** because the plan does not support the causal claim. The single assumption in the ROI frame that would most change the number if revised is the implicit human-rate used to value engineer time; the memo lists two credible alternative choices and how the frame would change under each.

**§8. Direction decisions and risks for next quarter**

- **Direction decision — customer-support-agent pilot.** Options: (a) resume pilot with vendor-side open finding closed on vendor's stated timeline (recommendation; current vendor ETA `<!-- author-to-confirm: vendor-stated ETA -->`); (b) re-scope as a bounded re-evaluation with no live customer traffic until vendor delivers; (c) terminate the pilot. Recommendation (a) with a tripwire: if the vendor ETA slips by more than two weeks, automatically escalate to option (b).
- **Risks for next quarter:**
  - *Risk — coding-assistant exception trend.* Exceptions approved against the policy's approved-uses list are trending up; owner is `head-of-ai-governance` (L60); mitigation is the Q2 policy-review cycle; escalates to a board-level event if the trend continues through the review window.
  - *Risk — vendor concentration on the coding assistant.* Mitigation: the secondary-supplier readiness exercise is scheduled for Q2 per `mod-107`.
  - *Risk — regulator guidance drift on generative AI in regulated services.* Mitigation: counsel's regulator-tracking cadence per `mod-108`; escalates if the regulator issues a guidance update that would require a program-wide policy redline.
- **For the board to note (non-decisional):** the amnesty channel's first validated use in §5 is treated as evidence that the policy's self-report posture (per `mod-103/exercise-01`) is operating as intended.

---

### 2.3 Board-voice guide

Return to these rules when drafting any paragraph in this artifact.

- **Prose, not bullets, in §1 and §3.** Bullets read as operational. Board readers read prose.
- **Named decisions, not "we recommend."** The board exists to decide. Phrase the ask as a direction decision with options, not as a management recommendation for acknowledgement.
- **Cite the memo, don't re-derive.** For ROI, for incident detail, for governance detail — the board packet is not where those are built; it is where they are referenced.
- **Attribution-honesty before ROI.** The order matters. The board reads the honesty frame first, in §3, so that by the time they read §7 they already understand the claim boundary.
- **One quarter at a time.** Resist the urge to project forward three quarters. Project forward one quarter in §8; year-horizon projection belongs in the annual review, not this one.
- **Never remove a paragraph that was present last quarter.** If a section has nothing in it, write "no change this quarter" or "no events this quarter." A disappeared section reads as suppressed signal.
- **No vendor marketing voice.** Grep the draft for "transformative," "cutting-edge," "AI-powered." All three fail the board-voice test.

### 2.4 Pre-read contract

What the artifact owes the board before the meeting so the meeting is for decisions, not status:

1. **Distributed ≥ 5 business days before the meeting.** Shorter and the readers will skim.
2. **One author is named, countersigned by CTO.** Shared authorship reads as diffused accountability.
3. **Length no more than 6 pages.** Longer and the readers will not reach §8.
4. **All named decisions in §1 are also in §8 with options and recommendation.** The exec summary points; the decision section asks.
5. **Any claim that an incident is "resolved" names the recurrence control and its status.** A resolved-with-no-control note is the single red flag a board member will catch.
6. **All numeric claims are either measured or `<!-- author-to-confirm: ... -->`.** Invented numbers that reach the board become minuted positions and are extremely expensive to walk back.

## 3. Validation steps

A reviewer should be able to answer **yes** to all of:

1. Is the artifact 4–6 pages at normal body-text size?
2. Does §1 state posture, name the direction decision (or declare the review informational), and name the one-thing-to-remember?
3. Does §2 cover every in-scope tool and name the concentration risk?
4. Does §3 include an attribution-honesty paragraph that names what the program can and cannot defend this quarter?
5. Is at least one non-regression floor explicitly checked in §3?
6. Does §4 list open findings, SLA-exception backlog, ratified policy changes, and training compliance?
7. Does §5 name material incidents and near-misses (not just aggregate counts)?
8. Does §6 name the primary regulator and any Q-local guidance updates (or mark them `<!-- author-to-confirm: ... -->`)?
9. Does §7 point to the ROI defence memo rather than re-derive ROI?
10. Does §8 restate the §1 direction decision with options and a recommendation, and name 3–5 risks for next quarter with owner + mitigation + escalation-condition?
11. Is the pre-read contract met (distribution lead time, author countersignature, length, no invented numbers)?
12. Is the writing in board voice (prose in §1/§3, no vendor marketing language)?

## 4. Rubric / review checklist

Scored out of 100. Pass threshold: ≥ 80 and no R2/R4/R7/R10 fail.

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | 4–6 pages at normal rendering | 5 | Exceeds 6 pages. |
| R2 | §1 posture + direction decision + one-thing-to-remember | 15 | Any of the three missing. |
| R3 | §2 portfolio table with concentration-risk note | 5 | Missing concentration risk. |
| R4 | §3 attribution-honesty paragraph present and specific | 15 | Missing or generic. |
| R5 | §3 non-regression floor explicitly checked | 5 | Floor absent. |
| R6 | §4 covers findings, SLA, policy, training | 10 | Any of the four classes missing. |
| R7 | §5 names incidents and near-misses (not just aggregate) | 10 | Aggregate-only incident reporting. |
| R8 | §6 names regulator and tracks guidance | 5 | Regulator unnamed. |
| R9 | §7 points to ROI defence memo; does not re-derive | 5 | ROI re-derived in the board packet. |
| R10 | §8 restates decision with options + 3–5 risks with escalation-condition | 10 | Missing options; or risks without escalation-condition. |
| R11 | Pre-read contract met (lead time, length, signatures, no invented numbers) | 10 | Lead time short, invented numbers, or missing CTO countersignature. |
| R12 | Board voice (prose in §1/§3; no marketing language) | 5 | Vendor-marketing voice or operational bullets in §1. |

## 5. Common mistakes

- **Scaling up the weekly scorecard.** The weekly is operator-facing; the quarterly is director-facing. Copy-pasting the weekly structure into the quarterly reads as operational and is missing §5, §6, and §8.
- **Missing the direction decision.** A quarterly review with no direction decision becomes a status update. Even an informational-only review should say so explicitly in §1.
- **Aggregating incidents without naming them.** "Three incidents this quarter, all resolved" invites a specific board question with no specific answer. Name the incidents.
- **Forward-looking projections in the quarterly.** Resist. One quarter at a time.
- **Re-deriving ROI in §7.** The ROI defence memo (`exercise-06`) is a separate artifact for a reason; it carries its own attribution-honesty frame and its own review process. Point to it.
- **Attribution-honesty collapsing to "we are in early days."** The quarterly version must name the specific co-contributors and controlled-comparison absence, not the generic early-days disclaimer.
- **Removing sections that were quiet.** §4, §5, §6 should appear every quarter; a quiet quarter is "no change this quarter," not an absent section.
- **Invented regulator-guidance claims.** This is the single most expensive invention to reach a board. Specifically: naming a regulator statement that did not happen, or claiming a regulator has endorsed a practice they have not. Everything in §6 is either measured or `<!-- author-to-confirm: ... -->`.
- **Vendor-marketing voice.** "Transformative AI capability" has no place in this artifact. The board reads marketing language as management advocacy, which is the opposite of what the artifact is for.
- **Using §8 to re-ask for things the board already decided.** Decisions already taken belong in §1 as acknowledged, not re-litigated in §8.

## 6. References

- **Official standards and frameworks:**
  - [NIST AI Risk Management Framework (AI RMF 1.0)](https://www.nist.gov/itl/ai-risk-management-framework) — the GOVERN function (accountability, policies, roles and responsibilities, oversight) motivates the §4 governance structure and the §1 direction-decision expectation at the board level.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — context for the material-incident taxonomy in §5.
  - [MITRE ATLAS](https://atlas.mitre.org/) — adversary-technique context for the near-miss taxonomy in §5 and the vendor-concentration risk framing in §2.
- **Local context (same repo):**
  - `modules/mod-106-outcome-measurement-and-executive-reporting/exercise-01-outcome-vs-usage-metric-framework/SOLUTION.md` — the anti-pattern list this outline draws on for §3 and §7.
  - `modules/mod-106-outcome-measurement-and-executive-reporting/exercise-02-the-weekly-executive-scorecard/SOLUTION.md` — the weekly snapshots this quarterly aggregates.
  - `modules/mod-106-outcome-measurement-and-executive-reporting/exercise-04-metric-miss-narrative-drill/SOLUTION.md` — the narrative discipline applied in §3 when outcomes miss.
  - `modules/mod-106-outcome-measurement-and-executive-reporting/exercise-06-roi-numerator-and-denominator-defence/SOLUTION.md` — the memo §7 points to rather than re-deriving ROI.
  - `modules/mod-107-budget-roi-and-build-vs-buy-at-org-scope/README.md` — the FinOps roll-up §7 references for program spend.
  - `modules/mod-108-industry-and-regulatory-flavours-of-enablement/README.md` — the regulator-tracking cadence §6 draws on.
  - `modules/mod-109-ai-incident-response-and-enablement-side-rollback/README.md` — the incident-response taxonomy §5 reports against.
