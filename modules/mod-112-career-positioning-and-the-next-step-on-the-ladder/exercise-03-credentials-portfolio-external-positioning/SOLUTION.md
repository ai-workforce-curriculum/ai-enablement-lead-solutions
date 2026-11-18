# Exercise 03 — Credentials Portfolio External Positioning — Reference Solution

> Module: `mod-112-career-positioning-and-the-next-step-on-the-ladder`
> Exercise type: design / worked example
> Exercise brief: [`lessons/mod-112-career-positioning-and-the-next-step-on-the-ladder/exercises/exercise-03-credentials-portfolio-external-positioning.md`](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/blob/main/lessons/mod-112-career-positioning-and-the-next-step-on-the-ladder/exercises/exercise-03-credentials-portfolio-external-positioning.md) (in the learning repo)

## 1. Solution overview

The deliverable is the **external-positioning layer** of the AI Enablement Lead's credentials portfolio. It is the subset of the portfolio (from mod-111 exercise-05) that is visible to, and legible to, readers outside the current employer — hiring managers, recruiters, program committees, standards bodies, podcast hosts, future peer networks. External positioning is the part of the portfolio the Lead chooses to publish, how they package it, and the discipline for keeping it current without over-sharing.

External positioning is **not** the same as the full credentials portfolio. The full portfolio in mod-111 exercise-05 includes Family D (internal scope evidence) that is largely private; this exercise focuses on the externally-visible surface area — Families A (external credentials), B (public artifacts), C (community contributions), and the public face of Family E (relational references, e.g., LinkedIn recommendations) — organised for an external reader.

Posture checks this solution encodes:

- **External positioning is read by a cold reader.** Treat the external surface as if the reader has 90 seconds, no context, and a prior of mild skepticism. What they find in those 90 seconds is the Lead's positioning.
- **The external profile answers three questions in order:** who does this person operate as; what have they shipped; what is the next thing they could do. Profiles that lead with job title answer only the first and lose the reader on the second.
- **Framework anchoring is the fastest credibility shortcut.** A reader who recognises NIST AI RMF or ISO/IEC 42001 anchors instantly; a reader who sees only vendor certifications pattern-matches to "AI-adjacent" rather than "AI operator."
- **Patterns, not organisation-specifics.** External positioning uses pattern-level artifacts ("ran an AI governance council quarterly rhythm") not organisation-specific numbers that fail the mod-111 exercise-05 confidentiality test.
- **One canonical landing page.** The LinkedIn profile, the personal site, the GitHub/talk portfolio, the conference bios — all link to the same canonical landing page. Multiple inconsistent canonicals read as inattentive.
- **Positioning declares a next-step ambition subtly, not loudly.** Signalling "Head of AI Enablement" by the shape of the portfolio and the choice of community contributions is more effective than a banner that says "looking for Head-of role." The banner reads as job-hunting; the shape reads as readiness.
- **Freshness beats volume.** A recent long-form piece and an active community presence out-weigh a decade of lapsed credentials. Externally, staleness is read as drift.
- **External positioning respects employer loyalty.** The two-part confidentiality test from mod-111 exercise-05 is the floor; nothing published externally fails it.
- **The external profile is quarterly-reviewed.** LinkedIn bios, personal-site content, and credential currency all decay. Quarterly review catches drift; annual review misses two-thirds of the correctable items.

## 2. Implementation — worked answer (`credentials-portfolio-external-positioning.md`)

### 2.1 The external reader catalog

The external positioning is calibrated to specific reader types. Different readers skim different surfaces; a positioning plan that treats them as one reader positions for none of them.

| Reader | Where they skim | Dwell time | Dominant question |
|---|---|---|---|
| **R1. Executive recruiter** | LinkedIn profile (headline + recent activity + top 3 positions) | 60-90 sec | "Is this person at the altitude I'm sourcing for?" |
| **R2. Hiring manager at a prospective employer** | LinkedIn profile + any linked personal site or portfolio | 3-5 min | "Could this person run my program? Why them, not the ten other candidates?" |
| **R3. Hiring-committee peer** (someone at the hiring org not on the hiring loop) | Personal site, podcast appearance, long-form piece | 10-15 min | "Does this person think about this field the way we do?" |
| **R4. Conference / program committee** | Speaker bio + prior talk links + published artifacts | 5 min | "Is this person worth a slot on the program?" |
| **R5. Journalist / podcast host** | Recent published pieces + prior talk links + Twitter/X or community-forum presence | 5-10 min | "Is this person a credible source on an AI enablement story?" |
| **R6. Peer practitioner** (an AI Enablement Lead at a different org) | Community-forum presence, long-form pieces, open artifacts | varies | "Is this someone I should connect with, learn from, or refer to a role?" |
| **R7. Current / former colleague who is looking at a role** | LinkedIn profile + personal site | 2-3 min | "Does the way they talk about their work match my experience of working with them?" — this is the integrity check |

External positioning is designed to serve R1-R6 consistently; R7 is the check that keeps the Lead honest.

### 2.2 The three-answer structure

An external profile answers three questions in order. Every surface (LinkedIn, personal site, conference bio, podcast intro) is organised around them.

#### 2.2.1 Who does this person operate as? (altitude + shape of role)

- **Altitude statement.** One short line that names the operating altitude the Lead has sustained. E.g., "AI Enablement Lead for a 3,000-person regulated enterprise — standing governance council, 20+ champion network, incident-response discipline."
- **Shape of role.** The two or three dimensions of scope that calibrate altitude — organisation size, regulatory flavour, tool-stack scale, multi-region, multi-BU. These are the dimensions R1 and R2 use to decide "is this candidate at my altitude."
- **Fail-state:** "Experienced AI professional with a passion for enablement." Generic adjectives read as unanchored; they do not survive R1's 60-second skim.

#### 2.2.2 What have they shipped? (evidence at pattern level)

- **3-5 pattern-level outcomes** — governance posture stood up; tool stack consolidated at a specific scale; literacy curriculum delivered to a named floor; incident response with a specific type of rollback; CoE scorecard running at a specific cadence. Numbers where publicly OK; shapes where not.
- **1-2 named public artifacts** — long-form piece, open template, conference talk, published rubric. Linked.
- **Fail-state:** laundry-list of activities without shape; or no evidence linked externally at all (the profile says "ran governance" but nothing on the external surface confirms shape or altitude).

#### 2.2.3 What is the next thing they could do? (next step, subtle)

- **The bio sentence** — "interested in scaling AI enablement at <larger scope / adjacent domain>." Subtle enough not to read as job-hunting; specific enough to pattern-match.
- **The portfolio composition signal** — the balance of recent artifacts (Family B) and community contributions (Family C) tilts toward the ambition. A Lead aiming for Head-of-AI-Enablement at scale publishes operating artifacts; a Lead aiming for governance-adjacent roles publishes policy and standards commentary.
- **Fail-state:** banner-level "open to opportunities" messaging. Reads as transactional; narrows the funnel to recruiter outreach only. Or no signal at all — reader cannot tell what the next step is, so cannot match the Lead to an open role.

### 2.3 The external-surface map

Where each family lives externally, and what the surface owes the reader. Private-only surfaces are excluded.

| Surface | Primary audience | Required content | Update cadence |
|---|---|---|---|
| **LinkedIn headline** (120 chars) | R1, R2, R7 | Role + altitude anchor + one craft signal | Quarterly |
| **LinkedIn "about" section** | R1, R2, R7 | The three-answer structure in 2-3 short paragraphs | Quarterly |
| **LinkedIn "experience" entries** | R2, R7 | For current + prior role: altitude, shape of role, 3-5 pattern-level outcomes, link to canonical page | Quarterly |
| **LinkedIn "licenses & certifications"** | R1, R2, R4 | Current Family A credentials; stale ones archived | Quarterly |
| **LinkedIn "activity" tab** | R1, R2, R5, R6 | Evidence of recent engagement — reposts with commentary, original posts, article drops | Weekly to monthly |
| **LinkedIn "recommendations"** | R2, R7 | 5-8 recent recommendations, cross-function, one from current exec sponsor if possible | Every 24 months |
| **Personal site** (canonical) | R3, R4, R5, R6 | Scope statement, recent writing, recent talks, open artifacts, contact | Quarterly |
| **GitHub / open-artifact repo** | R6 | Published templates, rubrics, worked examples (sanitised) | On publish |
| **Speaker bio** (3 lengths: 50, 100, 200 words) | R4 | Role + 1-2 craft signals + "most recent and relevant" credential or artifact | On talk acceptance |
| **Podcast intro lines** | R5 | Role + 1 craft signal + 1-sentence hook | Per appearance |
| **Community-forum presence** | R6 | Active, substantive participation under real name | Weekly to monthly |
| **Conference-committee listings / standards-body rosters** | R6 | Name present on rosters for the groups the Lead is actually in | Annually, with roster refresh |

### 2.4 Worked example — the archetype Lead's external profile

Illustrative; the Lead replaces specifics with their own under the mod-111 exercise-05 confidentiality posture. Specifics are `<!-- org-specific: ... -->` tagged.

#### 2.4.1 LinkedIn headline (118 chars)

> AI Enablement Lead | regulated enterprise | NIST AI RMF–aligned governance | writing & speaking on CoE operating models

- *Altitude anchor:* AI Enablement Lead at regulated enterprise.
- *Framework anchor:* NIST AI RMF–aligned.
- *Craft signal:* writing & speaking on CoE operating models.
- *Next-step signal (subtle):* "writing & speaking on" tilts the reader toward thought-leadership adjacent roles; a different Lead aiming for operational scale might read "scaling an AI operating model across a multi-region regulated enterprise."

#### 2.4.2 LinkedIn "about" section (worked)

> I run an AI Enablement Center of Excellence at a 3,000-person regulated enterprise. The CoE operates a standing governance council, a champion network across every major business unit, a role-tier literacy curriculum, and an incident-response discipline that has retired AI deployments where safety or compliance required it. Our posture is anchored on the NIST AI Risk Management Framework and sector-regulatory expectations; our measurement discipline distinguishes adoption, sustained usage, and the bounded productivity claims the evidence actually supports.
>
> Over four quarters I've co-authored the organisation's acceptable-use policy with governance, led the consolidation of the AI tool stack to a bounded set, stood up the champion community of practice, and operated a quarterly board-ready review for the enterprise risk and technology committee. The work is collective; I name collaborators because the outcomes are theirs too.
>
> I'm interested in scaling an AI enablement function to a materially larger operating scope — more business units, more regions, or a sector with heavier regulatory surface. I publish patterns and templates on my personal site, speak at practitioner conferences, and contribute to <!-- org-specific: named community / standards body the Lead actually participates in -->.

Three paragraphs; three answers in order; no organisation named; no scorecard numbers; the next-step signal is one sentence, subtle, specific.

#### 2.4.3 Personal site structure (canonical landing page)

```
<Lead's name>
AI Enablement Lead — regulated enterprise
NIST AI RMF–aligned | ISO/IEC 42001 contributor | writing on CoE operating models

[one short paragraph — altitude + shape of role]

[one short paragraph — the three or four pattern-level outcomes the Lead is willing to carry publicly]

[one short paragraph — the next-step interest]

## Writing
- [most recent long-form piece]
- [second most recent]
- [prior 3-4, linked]

## Talks
- [most recent talk, with venue + date + link to deck / recording if public]
- [prior 2-3]

## Open artifacts
- [sanitised commissioning brief template]
- [sanitised governance ritual template]
- [measurement rubric / scorecard shape]

## Credentials
- [current Family A credentials, with issuer + year]
- [expired / superseded, archived]

## Elsewhere
- LinkedIn link, community-forum link, GitHub link

## Contact
- [email or form; expectations stated — "I reply to specific-context outreach; I do not reply to generic recruiter blasts"]
```

The landing page is one scroll on desktop. Everything deeper lives behind links.

#### 2.4.4 Speaker bio (worked, 100-word version)

> <!-- org-specific: Lead's name --> runs an AI Enablement Center of Excellence at a regulated enterprise, where the function operates a standing governance council, a cross-BU champion network, a role-tier literacy curriculum, and the kind of incident-response discipline that has had to rollback deployments when safety or compliance required it. Their work is anchored on the NIST AI Risk Management Framework and on measurement patterns that distinguish adoption, sustained usage, and bounded productivity claims. They write and speak on CoE operating models and the under-discussed discipline of incident response in enablement contexts.

The 50-word and 200-word variants expand or compress the same content; the three-answer structure holds.

#### 2.4.5 LinkedIn "activity" discipline

- Weekly: at least one substantive repost with 2-3 sentences of commentary (not pure link-share). Target topics: governance posture, measurement, incident response, commissioning — the craft dimensions the external positioning claims.
- Monthly: one original short-form post (200-500 words) under byline on a craft topic. Linked back to any long-form on the personal site.
- Quarterly: at least one long-form article linked from LinkedIn and from the personal site, with the author's own commentary.
- Boundaries: no specific-vendor criticism; no specific-colleague naming without consent; no current-employer scorecard numbers unless publicly disclosed; no criticism of the current employer.

#### 2.4.6 Recommendations discipline (LinkedIn)

- Target: 5-8 recommendations, kept to the past 24 months.
- Mix: at least one from a cross-function head-of peer; at least one from a direct-report or champion-equivalent; at least one from a vendor-side counterpart if appropriate.
- The current exec sponsor's recommendation is load-bearing; the Lead requests it at a natural moment (a shipped quarterly cycle, a successful policy ratification), not during a job search, and offers reciprocity.
- Stale recommendations (> 36 months) are not deleted but are supplemented with newer ones so the top three visible are current.

### 2.5 Freshness and currency discipline

Externally, staleness is read as drift. The quarterly external-positioning review checks for:

| Item | Fresh | Needs refresh | Stale |
|---|---|---|---|
| Latest long-form piece | < 6 months | 6-12 months | > 12 months |
| Latest talk | < 12 months | 12-18 months | > 18 months |
| Latest LinkedIn post with commentary | < 1 month | 1-3 months | > 3 months |
| Personal site "latest writing" section | Updated this quarter | Last quarter | 2+ quarters |
| Current Family A credentials | Within refresh schedule | Refresh in current quarter | Lapsed |
| LinkedIn recommendations in top-3 | Within 24 months | 24-36 months | > 36 months |
| Community-forum presence | Weekly or monthly posts | Dormant 1-3 months | Dormant > 3 months |
| Headline current to role | Yes | Role changed > 1 quarter ago | Role changed > 2 quarters ago |

Any "stale" item either gets refreshed in the next quarter or is archived (hidden from the external surface). A profile with three stale items reads as drift to an R1 recruiter even if the Lead is at the top of their craft.

### 2.6 Positioning calibration by next-step ambition

External positioning is calibrated to the top-two next-step ambitions from mod-112 exercise-02. The weighting of surfaces, artifact topics, and community contributions shifts with the ambition.

| Ambition | Headline anchor | Dominant artifact topics | Dominant community presence |
|---|---|---|---|
| **O1. Lateral at larger scope** (AI Enablement Lead at larger org) | "scaling an AI operating model across <larger scope>" | Operating-model patterns; multi-BU / multi-region governance; scorecard discipline | Practitioner forums; speaking at operator-oriented conferences |
| **O2. Vertical in-org** (Head of / Director of AI Enablement at current org) | "AI Enablement Lead | <altitude anchor>" — no external shift | Any; external profile is maintained but not accelerated | Any; internal network dominates |
| **O3. Vertical out-of-org** (Head of / Director of AI Enablement at a new org) | "building AI enablement functions at <altitude anchor>" | Head-of-shape pattern pieces: operating model + budget + ROI + change management + incident response | Head-of peer networks; invited talks; podcast guest appearances |
| **O4. Governance-adjacent** (Head of AI Governance / AI Risk) | "NIST AI RMF–aligned governance | ISO/IEC 42001 contributor" | Policy, controls, incident response, regulatory posture | Standards bodies (NIST, ISO working groups where accessible), model-risk forums |
| **O5. L&D / Productivity-adjacent** | "AI literacy and change management at scale" | Role-tier curricula, champion programs, change-management patterns | L&D practitioner communities, productivity-engineering forums |
| **O6. Advisor / Founder** | "patterns & templates for AI enablement teams" | Open artifacts, worked examples, pattern libraries | Founder communities, advisor networks |

The Lead picks one or two ambitions. Positioning for three is positioning for none; the artifact topics compete for attention and the reader cannot tell what the Lead actually wants.

### 2.7 Freshness vs. employer-loyalty balance

External positioning for a Lead who is **not** actively looking has to stay current without reading as a job search. The rule:

- **Freshness:** quarterly updates on the externally-visible surface (LinkedIn, personal site, speaker bio).
- **Volume:** the volume of recent activity is calibrated to the Lead's ambition. O2 (vertical in-org) uses the floor volume — enough that staleness is absent, not enough that the sponsor reads it as departure signalling. O3 and O1 use higher volume — they need an external profile that pattern-matches to "ready for a larger role" when a recruiter lands.
- **Content:** no criticism of the current employer, no specific-vendor criticism, no scorecard numbers, no incident specifics. Pattern-level content is safe.
- **Visibility:** external activity is public. The exec sponsor sees it (or can). Nothing in the external profile should surprise the sponsor if they read it tomorrow.

### 2.8 Decision rationale — why this shape, not another

- **Why the three-answer structure.** R1 (recruiter) skims for altitude in 60 seconds. R2 (hiring manager) wants "could this person run my program." R3 (hiring-committee peer) wants "does this person think like us." The three answers (who do they operate as; what have they shipped; what next) serve all three in order, in prose, in the dwell times the readers actually have.
- **Why framework anchoring in the headline.** Framework names — NIST AI RMF, ISO/IEC 42001 — are instantly readable to the exec reader; vendor certifications read as technical-fluency but not as operator altitude. The headline is a 120-character pattern-match; framework anchoring wins the first second.
- **Why patterns, not specifics, in external content.** The two-part confidentiality test (mod-111 exercise-05 §2.5.3) fails for specifics; pattern-level content passes and is still demonstrative. External credibility is built on pattern recognition, not on leaked organisation-specific metrics.
- **Why one canonical landing page.** A reader who sees three inconsistent bios across LinkedIn, Twitter/X, and a personal site pattern-matches to "inattentive." One canonical page, linked from every other surface, reads as deliberate.
- **Why the next-step signal is subtle.** Banner-level "open to opportunities" messaging narrows the funnel to recruiter outreach only and reads transactional to R3 / R4 / R6. A portfolio *shape* that tilts toward the ambition reads as readiness, not job-hunting.
- **Why freshness beats volume.** A single piece from six months ago plus an active forum presence out-signals a decade of lapsed credentials. External readers read recency as evidence of current-field engagement; older work is archived, not deleted.
- **Why the activity cadence is weekly/monthly.** Below weekly, the activity tab stales out. Above monthly, the Lead is on the content treadmill and the day-job scorecard starts to slip; that trade is net-negative.
- **Why the recommendations are ≤ 24 months old.** Older recommendations read as "this person used to be good." Fresh recommendations read as "this person is currently load-bearing."
- **Why positioning is calibrated by ambition.** An external profile optimised for O3 (vertical out-of-org) and an external profile optimised for O4 (governance-adjacent) look substantively different. A profile optimised for all ambitions reads as unfocused and pattern-matches to no specific role.
- **Why the R7 (current / former colleague) integrity check matters.** The external profile has to be defensible to the people who have actually worked with the Lead. A profile that overstates reads as self-promotion to R7, and R7 is the back-channel that gets called during reference checks and recruiter sourcing. Honest positioning compounds; inflated positioning is self-correcting in a career-damaging way.

## 3. Validation steps

1. **Reader catalog** names ≥ 6 external reader types with where they skim, dwell time, dominant question.
2. **Three-answer structure** defined for the profile (who / what shipped / what next) with fail-states per answer.
3. **External-surface map** names ≥ 8 surfaces with primary audience, required content, update cadence.
4. **Worked example** at the archetype Lead's profile: headline, about, personal site structure, speaker bio, activity discipline, recommendations discipline.
5. **Framework-anchored headline** demonstrated (NIST AI RMF / ISO/IEC 42001 / sector-regulatory).
6. **Freshness and currency discipline** names fresh / needs-refresh / stale thresholds for ≥ 6 items.
7. **Positioning calibration by ambition** shows the top ambitions from mod-112 exercise-02 with distinct headline, artifact topics, and community presence.
8. **Freshness vs. employer-loyalty balance** named — pattern-level content, no surprise to sponsor, bounded volume.
9. **Confidentiality floor** named — two-part test from mod-111 exercise-05 holds.
10. **One canonical landing page** declared and demonstrated.
11. **R7 integrity check** named — external profile is defensible to former colleagues.
12. **`org-specific` / `author-to-confirm` tags** on all organisation-dependent specifics.

## 4. Rubric / review checklist

| # | Criterion | Weight | Fail state |
|---|---|---|---|
| R1 | Reader catalog ≥ 6 types with dwell time and dominant question | 10 | Fewer reader types or missing dwell times. |
| R2 | Three-answer structure defined with fail-states | 15 | Fewer answers, or answers without fail-states. |
| R3 | External-surface map ≥ 8 surfaces with cadence | 10 | Generic surface list without cadence. |
| R4 | Worked example covers headline, about, personal site, speaker bio, activity, recommendations | 15 | One or more worked outputs missing. |
| R5 | Framework-anchored headline demonstrated | 5 | Vendor-only or unanchored headline. |
| R6 | Freshness and currency discipline with named thresholds for ≥ 6 items | 10 | No thresholds; staleness undefined. |
| R7 | Positioning calibration by ambition with ≥ 3 ambitions worked | 10 | No calibration; one-size-fits-all positioning. |
| R8 | Freshness vs. employer-loyalty balance explicit | 10 | Balance not addressed; profile reads as job search. |
| R9 | Confidentiality floor — two-part test applied | 10 | Specifics present that fail the test. |
| R10 | One canonical landing page declared | 3 | No canonical, or multiple inconsistent canonicals. |
| R11 | R7 integrity check named | 2 | No integrity check. |

**Pass threshold:** ≥ 85/100 and no R2 / R8 / R9 fail. R2 (three-answer structure) is the surface; R8 (employer-loyalty balance) prevents the profile from reading as a job search while employed; R9 (confidentiality) is the career-safety floor.

## 5. Common mistakes

- **Generic headline.** "Experienced AI professional and change leader" reads as unanchored. Specific altitude anchor + framework anchor + craft signal beats generic adjectives every time.
- **Job-title-only profile.** The profile that says "AI Enablement Lead at <Company>" and nothing else answers only "who do they operate as" and loses the reader on "what shipped" and "what next."
- **Banner-level open-to-opportunities signalling.** Narrows the funnel to recruiters and reads transactional. Subtle, shape-based signalling via artifacts and community presence is more effective and more employer-respectful.
- **Scorecard numbers in external posts.** Fails the mod-111 exercise-05 confidentiality test. Pattern-level ("retired N vendors in one cycle") is safe; specific ("retired the X vendor at Y% savings") is not.
- **Named-vendor criticism.** Even when substantively correct, it reads as unreliable future colleague. Pattern-level commentary on vendor categories is safe; specific-vendor criticism is not.
- **Named-colleague naming without consent.** Includes champions, direct reports, and cross-function peers. Consent and reciprocity are the norm; absence of consent reads as inattentive at best.
- **Stale activity tab.** A LinkedIn activity feed whose most recent entry is three months old reads as a lapsed external profile. Weekly repost-with-commentary is the floor.
- **Stale credentials.** Family A credentials from five years ago as the only credentials on display read as "this person used to be in the field." Annual refresh is the rhythm.
- **Recommendations from a prior role.** Fresh recommendations from the current role are the strongest signal; recommendations only from 5+ years ago read as "this person's current manager won't recommend them."
- **Multiple inconsistent canonicals.** A LinkedIn bio, a personal site bio, and a conference bio that disagree on the shape of the role are a pattern-match for inattention.
- **Positioning for three ambitions at once.** The external profile that is optimised for Head-of-AI-Enablement, Head-of-AI-Governance, and AI Advisor at the same time reads as unfocused. Pick one or two.
- **Content that would surprise the exec sponsor.** The external profile should not surprise the sponsor if they read it tomorrow. If any item would require a conversation to explain, hold it or run it by the sponsor first.
- **Portfolio maturity inflation.** Claiming "built the governance posture" when six people co-authored it is a reference-check failure. Honest attribution ("co-authored the governance posture; led the measurement discipline") out-signals inflation because it survives R7's integrity check and the subsequent back-channel.
- **No freshness review.** Quarterly review catches drift; absence of review lets staleness accumulate and the Lead is one recruiter skim away from reading as drifted.
- **Volume that erodes day-job performance.** External positioning is a supplement to, not a replacement for, the day-job scorecard. The mod-111 exercise-05 10%-of-working-time ceiling applies.

### 5.1 Stretch — the 90-second cold-read drill

Before any quarterly external-positioning review, the Lead runs the 90-second cold-read drill:

1. Open the LinkedIn profile in a fresh browser window (not logged in, if possible).
2. Start a 90-second timer. Read only what loads above the fold without scrolling.
3. Answer the three questions aloud: "Who does this person operate as? What have they shipped? What is the next thing they could do?"
4. If any answer is unclear, the headline and about section need work.

Then repeat with the personal site, the speaker bio, and (for conference-circuit positioning) the most recent published piece's byline paragraph. Patterns that fail across two or more surfaces are the quarter's priority fixes.

A Lead who runs this drill honestly once a quarter accumulates a cleanly-positioned external surface over 2-4 quarters. A Lead who only reads their own profile when they are already job-searching discovers the staleness at the worst possible time.

## 6. References

- **Learning material (local):**
  - [mod-103 — Policy Co-authoring with Governance](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-103-policy-co-authoring-with-governance) — the framework-anchored governance posture the headline and about section lean on.
  - [mod-104 — Training Programs and AI Literacy Curriculum](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-104-training-programs-and-ai-literacy-curriculum) — training patterns suitable for sanitised external artifacts for O5 positioning.
  - [mod-105 — Champion Networks and Change Management](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-105-champion-networks-and-change-management) — change-management patterns suitable for external artifacts.
  - [mod-106 — Outcome Measurement and Executive Reporting](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-106-outcome-measurement-and-executive-reporting) — measurement discipline the about-section references; the attribution-honesty frame the external profile mirrors.
  - [mod-107 — Budget, ROI, and Build-vs-Buy at Org Scope](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-107-budget-roi-and-build-vs-buy-at-org-scope) — consolidation and ROI patterns suitable for external long-form after sanitisation.
  - [mod-108 — Industry and Regulatory Flavours of Enablement](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-108-industry-and-regulatory-flavours-of-enablement) — sector framing that shapes R3's "do they think about this field the way we do."
  - [mod-109 — AI Incident Response and Enablement-Side Rollback](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-109-ai-incident-response-and-enablement-side-rollback) — incident-response positioning as a craft-signal the external profile can carry.
  - [mod-110 — Commissioning Internal AI Tools and Custom Agents](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-110-commissioning-internal-ai-tools-and-custom-agents) — commissioning templates suitable for open-artifact publishing.
  - [mod-111 — AI CoE Operations, Vendor Management, and Cross-Functional Leadership](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-111-ai-coe-operations-vendor-management-and-cross-functional-leadership) — Exercise 05 full credentials portfolio of which this exercise is the externally-visible layer.
  - [mod-112 — Career Positioning and the Next Step on the Ladder](https://github.com/ai-workforce-curriculum/ai-enablement-lead-learning/tree/main/lessons/mod-112-career-positioning-and-the-next-step-on-the-ladder) — the dedicated module this exercise sits inside.
  - [Exercise 01 — Exec Communication Story Outline](../exercise-01-exec-communication-story-outline/SOLUTION.md) — V6 (external interview) voice that this external profile prepares the Lead to deliver.
  - [Exercise 02 — Next Step Ladder Decision Worked Example](../exercise-02-next-step-ladder-decision-worked-example/SOLUTION.md) — the ambition selection that calibrates §2.6 positioning.
  - [Exercise 04 — Public Artifact Set Plan](../exercise-04-public-artifact-set-plan/SOLUTION.md) — the publishing schedule that feeds the "Writing" and "Talks" sections of the personal site.
- **Official standards and frameworks:**
  - [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — the framework anchor demonstrated in the headline and the about section; the governance vocabulary that R2 / R3 recognise instantly.
  - [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — threat-posture anchor relevant for O4 (governance-adjacent) external positioning.
  - [MITRE ATLAS](https://atlas.mitre.org/) — adversarial-technique anchor relevant for O4 external positioning when the Lead writes on security posture.
