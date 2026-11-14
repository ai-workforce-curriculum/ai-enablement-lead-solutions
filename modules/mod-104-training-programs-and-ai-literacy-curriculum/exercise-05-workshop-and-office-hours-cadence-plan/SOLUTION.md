# Exercise 05 — Workshop and Office-Hours Cadence Plan — Reference Solution

> Module: `mod-104-training-programs-and-ai-literacy-curriculum`
> Exercise type: design artifact
> Learning file: [`exercise-05-workshop-and-office-hours-cadence-plan.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-104-training-programs-and-ai-literacy-curriculum/exercises/exercise-05-workshop-and-office-hours-cadence-plan.md)

## 1. Solution overview

The cadence plan is the **calendar** behind everything the module ships. The curriculum (`exercise-02`) says what people learn. The playbook (`exercise-03`) says how each function should use the tool. The coaching design (`exercise-04`) says what a 1:1 looks like. The cadence plan says **when** each of those happens, at what frequency, through which channels, and how the rhythm supports the fluency targets from `exercise-01`.

The deliverable is a 12-month cadence spanning four kinds of live touchpoint: **workshops**, **office hours**, **coaching slots**, and **refreshers**. Each is sized against the segment headcount and target fluency ramp.

Archetype: same ~3,000-person US bank. Cadence is built against the +90d / +180d / +365d ramp from `exercise-01`.

Posture checks:

- **Cadence is the scaffolding of behavior change, not a marketing drumbeat.** The calendar exists because fluency does not grow from a single e-learning; it grows from recurring low-stakes contact.
- **Shorter, more frequent beats longer, less frequent.** 30-minute office hours twice a week beat a 2-hour quarterly roadshow. The exercise explicitly resists "big event" thinking.
- **Workshops are the exception, not the backbone.** One workshop per quarter per segment, max. Office hours and coaching carry the weight.
- **Refreshers are tied to AUP revisions and incidents, not the calendar alone.** Policy drift and field incidents trigger mid-cycle refreshers; a strict quarterly refresher cadence over-trains and under-responds.
- **Attendance ≠ success.** The cadence plan carries measurement from `exercise-06`; it reports changed behavior, not seats filled.

## Implementation

Apply this solution by walking section 2 through the 12-month cadence phase-by-phase — pre-GA, T+0 to T+90, T+90 to T+180, T+180 to T+365 — with the four touchpoint types (workshop, office hours, coaching, refresher) sized against the segment headcounts from `exercise-01`. Validate against section 3, score with the rubric in section 4, use section 5 to flag calendar-bloat and workshop-first failures, and treat section 6 as the regional / champion-handoff variant for larger operations footprints.

## 2. Worked answer — `workshop-and-office-hours-cadence.md`

### Cadence plan — v0.1 (coding-assistant rollout, 3,000-person US bank)

**Scope window:** 12 months from GA (T+0). Pre-GA has its own compressed cadence covered in the GA-launch section.
**Owner:** this role (AI Enablement Lead) jointly with L&D (per `exercise-07`).
**Co-sign:** `head-of-ai-governance`, `head-of-learning-and-development`.
**Segments:** S1–S6 as defined in `exercise-01`.

---

### Four touchpoint types

1. **Workshops** — scheduled, 60–90 minutes, named topic, interactive. Maximum one per quarter per segment.
2. **Office hours** — recurring, 30 minutes, drop-in, Q&A plus a short worked example. The backbone.
3. **Coaching slots** — 45-minute 1:1s following the `exercise-04` design, bookable in-week.
4. **Refreshers** — short live touchpoints (10–15 minutes) injected into existing standing meetings (e.g., all-hands, segment staff meetings) when a specific trigger fires.

The four types form a ladder: refreshers are the lowest-stakes, workshops the highest. An employee experiencing a gap should be able to find the right rung without this role scheduling a new one.

---

### Pre-GA cadence (T-30 days to T+0)

This window is where fluency is seeded for the segments that go live at T+0.

| Week | Touchpoint | Audience | Duration | Facilitator |
|---|---|---|---|---|
| T-30 | Workshop 1 — "What this tool is and why we bought it" | S1 engineers (early-access cohort) | 60 min | This role + exec sponsor |
| T-28 | Office hours | S1 early-access | 30 min twice | This role |
| T-21 | Workshop 2 — "Writing prompts for your workflow" | S1 engineers | 90 min | This role + champion |
| T-21 | Workshop 1 repeat | S2 analytics early-access | 60 min | This role |
| T-14 | Office hours | S1, S2 | 30 min x 2 | This role |
| T-14 | Workshop 1 adapted | S4 product/BA | 60 min | This role |
| T-7 | Dry-run coaching sessions | 5 S1 + 5 S4 volunteers | 45 min each | This role |
| T-3 | Refresher — "Day-of-GA expectations" | All segments | 10 min inside existing all-hands / staff meetings | Local manager + champion |
| T-0 | GA | — | — | — |

Pre-GA S5 (operations/retail/customer-facing) does **not** take live touchpoints. S5 goes live after S1/S2/S4 are stable, with a staggered 30-day ramp starting T+30. See T+0 to T+90 below.

---

### T+0 to T+90 (ramp phase)

Fluency target map says S1/S2/S4 reach +90d targets in this window. S5 begins its ramp; S6 is in exec-report-reading mode.

**Office hours cadence**

| Audience | Frequency | Slot | Duration |
|---|---|---|---|
| S1 Engineers/SRE | 2x/week | Tue 10:30, Thu 15:00 | 30 min |
| S2 Data/analytics/MRM | 1x/week | Wed 11:00 | 30 min |
| S3 RCLA | 1x/week | Thu 11:00 | 30 min (Q&A leaning) |
| S4 Product/program/BA | 1x/week | Tue 14:00 | 30 min |
| S5 Operations/retail (begins T+30) | 1x/week | Wed 13:30 | 20 min, rotating regional |
| S6 Executives | not scheduled | — | — (served by exec rollout report cadence from `mod-102 exercise-03`) |

All office-hours slots are **drop-in** and scheduled as recurring events; no booking required. Each ends with the next slot and `#ai-enablement-help` channel announced.

**Coaching slots**

- 10 slots/week reserved for S1/S2/S4; 2 slots/week reserved for S3; S5 does not yet take coaching.
- Booked through a simple form (segment, function, two prompts, goal). Follows `exercise-04`.
- Facilitator: this role for the first 60 days; champion handoff begins T+60.

**Workshops**

- One workshop at T+45: "Branch B — when you should not use the tool" for S3 and S4.
- One workshop at T+60: "Reading AI output for silently wrong code" for S1.

**Refreshers**

- T+30: 10-minute refresher injected into the S5 staff meeting ("Day-one for your segment — the three things to remember").
- T+60: 10-minute refresher across all segments ("First 60-day check-in — one case we saw and one rule that was easy to miss"). Content comes from the aggregated `#ai-enablement-help` signal and the accident log.

---

### T+90 to T+180 (consolidation phase)

Fluency map says all segments reach their +180d targets in this window.

**Office hours cadence**

- S1 reduces to 1x/week; S2, S3, S4 hold at 1x/week; S5 scales to the full regional rotation (one slot per region per week).

**Coaching slots**

- 8 slots/week; champion-led from T+90 for S4 and S3; this role remains the backstop.

**Workshops**

- One workshop at T+120: segment-specific; topic chosen from the field-signal rollup in the previous quarter, not pre-planned.
- One workshop at T+150: "Mid-cycle refresh — the three things the policy taught us" (co-delivered with `head-of-ai-governance`).

**Refreshers**

- Only on trigger. In the consolidation phase, calendar-driven refreshers over-train.

---

### T+180 to T+365 (steady state)

**Office hours cadence**

- All segments 1x/week except S1, which drops to 1x every two weeks. S5 holds at weekly per-region.

**Coaching slots**

- 5 slots/week. Champion-led; this role facilitates monthly cohort debriefs with champions.

**Workshops**

- One per segment per half-year, maximum. Topics chosen from measurement signal (`exercise-06`) and field signal.

**Refreshers**

- On trigger only. Expected triggers in a typical year: 1–3 AUP revisions, 1–2 regulator-guidance updates, 1–2 accident-path events.

---

### Mid-cycle trigger refreshers (any window)

A refresher fires when any of the following happen, independent of the calendar:

1. **AUP revision touching Section 2, 3, or 4.** Triggers a 10-minute refresher across all in-scope segments within two weeks.
2. **A Section C refusal from the playbook (`exercise-03`) fires 3+ times in a month.** Triggers a refresher focused on that refusal pattern, scoped to the function.
3. **A `mod-103 exercise-02` SOP accident-path event.** Triggers a refresher within 72 hours for the segment the accident touched, with content focused on the specific contested boundary.
4. **A regulator guidance update on generative AI in regulated financial services.** `<!-- to-verify: confirm the primary regulator whose guidance the cadence tracks — OCC / Federal Reserve / FDIC — for the target org -->`
5. **A material vendor change (tenant default, DPA, retention, region).** Triggers a refresher for S1/S2 and an exec-rollout-report update.

Each trigger refresher is logged in a short event-log table so the pattern is visible in the half-year review.

---

### Channels

- **Workshops** — Teams meetings; recorded with transcript; the deck and recording are posted to the `ai-enablement` SharePoint folder within 24 hours.
- **Office hours** — standing Teams channel with a recurring meeting link. No recording of office hours (encourages people to ask the question they would not ask on camera).
- **Coaching** — Teams 1:1s, no recording; session log (`exercise-04`) captured by the coach.
- **Refreshers** — delivered inside the receiving meeting's existing channel (all-hands, staff meeting). This role or the local manager runs them, depending on the trigger.
- **Field channel** — `#ai-enablement-help` Slack, 1-business-day response SLA, visible to all in-scope employees. The channel feeds signal to the cadence (which workshops to schedule, which refreshers to fire).

---

### Sizing — what the calendar costs

| Quarter | Workshops | Office-hour hours | Coaching hours | Refreshers | This-role hours (est.) |
|---|---|---|---|---|---|
| Pre-GA (T-30 to T+0) | 5 | 8 | 7.5 | 1 cross-org | ~55 |
| Q1 (T+0 to T+90) | 2 | 50 (over 13 wks) | ~90 | 2 scheduled + triggers | ~150 |
| Q2 (T+90 to T+180) | 2 | 48 | ~70 | triggers only | ~110 |
| Q3 (T+180 to T+270) | 1–3 | ~40 | ~50 | triggers only | ~80 |
| Q4 (T+270 to T+365) | 1–3 | ~40 | ~50 | triggers only | ~80 |

The sizing explicitly plans to reduce this role's active hours as the champion network takes load. If the hours line stays flat into Q3, the champion handoff has not worked and is the problem to solve — not the cadence. <!-- to-verify: validate champion-cohort size with `mod-105` team before committing to this hand-off slope. -->

---

### Governance of the cadence itself

- **Review cadence:** monthly standing meeting (30 min) between this role, L&D, and `head-of-ai-governance` to look at field signal and confirm the next month's calendar. Decisions logged in a shared doc versioned with the cadence plan.
- **Change control:** workshop topics past 30 days out can shift without sign-off; next-30 days require L&D co-sign; next week requires this role plus the segment champion.
- **Reporting:** cadence inputs (headcount reached, repeat questions, plant catch rate, refresher triggers) feed the executive rollout report (`mod-102 exercise-03`) and the measurement drill (`exercise-06`).

---

### End of worked cadence plan

## 3. Validation steps

1. **Four touchpoint types defined and used.** Workshops, office hours, coaching, refreshers. All four appear in the plan.
2. **Office hours are the backbone, not workshops.** Count total minutes by type; office hours should dominate.
3. **Workshops ≤ 1 per segment per quarter.** More than that reads as "we have a lot to say"; cadence beats volume.
4. **S6 (executives) has no scheduled touchpoint in this plan.** They are served by the executive rollout report cadence.
5. **S5 ramp is staggered.** S5 does not go live at T+0. Rushing S5 over-trains the Level 1 segment.
6. **Mid-cycle triggers are enumerated** and fire independently of the calendar.
7. **A sizing table exists** with estimated hours of this role per quarter, declining into Q3/Q4.
8. **Reporting hooks are named** (`mod-102 exercise-03` exec report, `exercise-06` measurement). No orphan cadence.
9. **Channels named per touchpoint.** Office hours explicitly not recorded.
10. **`<!-- to-verify: ... -->` on org specifics** (regulator identity, champion cohort size, specific slot times). Not invented.

Markdown lint before sharing.

## 4. Rubric or review checklist

Scored out of 100. ≥ 85 passes. R2, R3, R5, R7 fails are launch-gate equivalents.

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | Four touchpoint types defined | 10 | Any missing. |
| R2 | Office hours dominate by total minutes | 10 | Workshops dominate. |
| R3 | ≤ 1 workshop per segment per quarter | 10 | More scheduled. |
| R4 | Pre-GA cadence present with named workshops and dry-runs | 10 | GA assumed cold. |
| R5 | S5 ramp is staggered, not at T+0 | 10 | S5 live at GA. |
| R6 | S6 served by exec rollout report, not this cadence | 5 | S6 has scheduled coaching. |
| R7 | Mid-cycle trigger list present and enumerates ≥ 4 triggers | 10 | Triggers absent or vague. |
| R8 | Sizing table with declining this-role hours into Q3/Q4 | 10 | No sizing or flat hours. |
| R9 | Champion handoff slope explicit | 5 | Handoff absent. |
| R10 | Channels named per touchpoint; office hours not recorded | 5 | All recorded, or no channels. |
| R11 | Reporting hooks named (exec report, measurement) | 10 | Orphan cadence. |
| R12 | Governance: monthly review, change-control rules | 5 | No governance. |
| R13 | `<!-- to-verify: ... -->` on unknowns | 5 | Invented specifics (regulator, headcount). |

## 5. Common mistakes

- **Workshop-heavy cadence.** Big events feel like progress; recurring short beats actually move fluency. If the deck is bigger than one slide, it is probably a workshop and should be less frequent.
- **Recording office hours.** Reduces the question the shy employee asks. Lose the signal, lose the cadence's point.
- **S5 at T+0.** Forces 1,600 people through live training before the organization knows what to teach them. Stagger.
- **Flat champion load into Q3.** The cadence that does not plan the champion handoff reads as "this role runs the program forever" and L&D will not co-own what cannot handoff.
- **Trigger refreshers tied to the calendar.** Quarterly mandatory refreshers under-respond to the real triggers (AUP changes, accidents).
- **Exec touchpoint scheduled.** S6 fluency moves through the exec rollout report, not through office hours. Running an exec workshop signals "we have nothing better to measure."
- **No sizing.** Every cadence lacks the hours line until L&D asks for it. Have it before being asked.
- **Office hours with mandatory attendance.** Converts the cadence into training and loses the "drop-in" point.
- **Attendance reporting as success.** Seats filled is not fluency. Report the measurement from `exercise-06`.

## 6. Stretch — regional operations rollout and the champion-load target

**S5 regional rollout:**

- The bank's operations/retail footprint is distributed. A single centrally-scheduled office hour will not reach the regional staff schedule.
- Cadence design: one 20-minute regional office hour per week per region, scheduled in-region for that region's shift window. The regional champion runs it; this role joins once per quarter per region.
- `<!-- to-verify: confirm the regional structure of the target org (e.g., Northeast / Southeast / Midwest / West / Central Operations) and the local-shift slots that make a weekly office hour feasible without disrupting customer service hours. -->`

**Champion-load target (handoff plan):**

- Pre-GA: this role runs 100% of live touchpoints.
- T+30: 80% this role, 20% champions (shadowing).
- T+60: 60/40 (champions co-deliver office hours).
- T+90: 40/60 (champions lead office hours; this role backs up coaching).
- T+180: 25/75 (this role backs up only; champions and L&D own delivery).
- T+365: 15/85 (this role owns workshops with `head-of-ai-governance` and the champion program; everything else is handed off).

If the actual load does not track within ±10 points of the target by T+180, the champion network design (`mod-105`) is the thing to fix, not the cadence.

## 7. References

- **Learning material (local):**
  - [Exercise brief — `exercise-05-workshop-and-office-hours-cadence-plan.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-104-training-programs-and-ai-literacy-curriculum/exercises/exercise-05-workshop-and-office-hours-cadence-plan.md)
  - This module: `exercise-01` (segment ramp drives cadence), `exercise-02` (curriculum — workshops key off), `exercise-03` (playbook — refreshers key off), `exercise-04` (coaching — one touchpoint type), `exercise-06` (measurement — reads cadence outputs), `exercise-07` (L&D co-ownership).
  - Cross-module: `mod-102 exercise-03` (exec rollout report — serves S6), `mod-103 exercise-01/02` (AUP + SOP — trigger refreshers), `mod-105` (champion network — carries the handoff).
- **Official standards and frameworks:**
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — GOVERN function (governance of the program, including review cadence and change control) frames the monthly review and the trigger-refresher list.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — surfaces in workshop content on output trust and prompt injection.
  - [MITRE ATLAS](https://atlas.mitre.org/) — surfaces in S1/S2 workshop content on adversary techniques relevant to LLM-integrated apps.
