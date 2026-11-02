# GTM Strategy & Success Dashboard

Module 6 · Deliverable 6. Scenario: RouteLogic Velocity. Launch: B1 One-Click Compliance Checklist. Owner: Antje Barth (PM). Weeks count from pilot build start, after the pre-build evidence gate clears.

**Refined on 2 November 2026.** Weekly first use is a diagnostic. The scenario mean and proposed median usability bar are separate measures. Checklist fit, enrollment and power must clear before the build.

## Go-to-market summary

| Field | Value |
|---|---|
| Feature | B1 One-Click Compliance Checklist |
| Goal | Engagement: complete daily compliance logging in RouteLogic |
| Launch tier | M, targeted |
| Channels | Owned: route-row note, CS email to managers, largest-account meeting |
| Launch moment | Week 5 planned, after a complete 14-day test and VEL-01 ship decision |

**Entry and launch policy.** VEL-01's **pre-build evidence gate** confirms the proposed mechanism, checklist fit, enrollment, baseline, power, and a feasible measurement, audit and staffing plan. The CS lead observes current work, the compliance owner confirms the 3 pilot accounts' required checks, and the PM approves the protocol. The assumed 540 eligible coordinators are not yet counted. A failed condition holds the build. Repeated days from one coordinator do not supply extra independent users.

After the weeks-1-to-2 build, the **pre-exposure implementation gate** checks working telemetry, write guards, usability and the canary. Randomization waits until these pass. A delay moves the full 14-day test and every dependent launch date. [VEL-01](../05-experimentation/experimentation-plan.md) owns both gates.

A known checklist mismatch holds any account before exposure until a checklist per account (S5) is built and validated. That applies to pilot and rollout accounts. Among eligible accounts, the unknown is whether easier entry changes daily logging and whether it lasts.

VEL-01 owns the pilot decision: at least +12 percentage points against concurrent control, a confidence interval above zero, and its quality, account and sustained-lift checks held. An inconclusive result earns no rollout. The efficacy read is fixed at day 14, but harm monitoring runs throughout. The PM orders a pause, the pilot engineer disables the affected flag, and the compliance owner investigates. Confirmed severe harm stops exposure immediately. Other boundary breaches pause affected exposure and expansion pending an audit within 2 working days.

The pilot has no launch campaign, to protect the control arm. After a ship decision, internal teams are enabled before customers. Every later wave waits for the previous wave's 7-day review: usable telemetry, guardrails held and no unresolved material block or harm report.

## Success dashboard

| KPI | Baseline | Target or decision | Window |
|---|---|---|---|
| Daily compliance-step completion, defined below | Verify the fixed-roster baseline. The scenario's 48% uses app-openers | Lock sustained target at verified baseline +12 points. Apply pooled and in at least two thirds of eligible accounts | Four full weeks after each account's switch-on |
| First-use activation and time to first log | Unmeasured | Diagnostic, with no numerical gate | First 7 days |
| Compliance logging duration, open to submit | Scenario mean 14.6 min. Median unknown | Report mean and median. Prototype hypothesis: median ≤3:00 | Weekly |
| Workflow completion through handoff | Verify the rate on the matched roster cohort. Scenario: 31% | Lock projection from the same cohort's compliance-to-handoff ratio. Scenario illustration: 39% | End of week 12 |
| Corrected or audit-flagged records, as a share of submitted logs | Account's previous 4 weeks | No more than +2 points. Breach holds expansion for review | Live harm alerts, weekly rate review |
| Fail rate, as a share of checks | Account's pre-launch rate | Below half triggers an audit and holds expansion | Live harm alerts, weekly rate review |
| Manager Compliance CSAT | 3.9 | ≥3.9 | End of week 12 |
| Blocked opens and compliance support tickets | First measured in pilot | Diagnose causes. Set a rate target after the first wave | Weekly |
| Largest account renewal | Trialing a leaner rival | Renews | Decision date still unknown |

**Definitions and derivations.** Daily completion follows VEL-01: each enrolled coordinator's fraction of scheduled workdays with all required route-shift logs submitted by shift end, using account weights fixed from eligible enrollment before assignment. Cohort, schedule and rollout weights are locked before each wave, retaining non-openers in the denominator. The 48% scenario rate uses another base, so the pre-build check must re-estimate it. Before exposure, the PM records the sustained-completion target and handoff projection below from the verified cohort. They cannot change after the results arrive.

- **60%** illustrates the scenario's 48% +12 points. The actual sustained target is the verified fixed-roster baseline +12 points, locked before exposure. Pilot shipping still depends on the controlled lift under VEL-01. The two-thirds account rule is a planning judgment to avoid hiding broad failure in a pooled rate. Confirmed harm pauses an account regardless of that rate. [Module 3](../03-analytics/hypothesis-and-metrics.md) owns the metric rationale.
- **Weekly activation has no 85% gate.** The earlier calculation mixed weekly first use with daily completion. For the same cohort and day, 60 ÷ 71 = 84.5% describes conditional completion among route assigners. It cannot set a weekly first-use threshold.
- **3:00** is the scenario benchmark and an unproven median usability bar. Subtracting it from the 14.6-minute mean would not establish a saving. Customer claims require comparable measured durations.
- **39%** illustrates 60% × (31 ÷ 48) = 38.75%, rounded. The actual projection uses the locked sustained-completion target multiplied by the verified same-cohort handoff/compliance ratio. If B3 ships too, report its timing and do not attribute this outcome to B1 alone.
- **Guardrail boundaries** are planning judgments from VEL-01. After rollout they use each account's pre-launch rate because there is no control arm. Check case mix, audit coverage and selective completion before naming a cause.
- **Renewal** also depends on late route changes and crashes on long routes (BUG-2044, BUG-2031). A renewal or loss alone cannot establish B1's effect.

## Responses

### Get your prior work ready

**The feature you're launching, from your M4 PRD, one feature, not a list**

B1 One-Click Compliance Checklist. From an assigned route, the coordinator opens one screen with six read-only header fields, answers 12 blank checks, gives reasons for Fails and submits once. The [PRD](../04-roadmap/simplified-prd.md) owns its behavior and exclusions.

**What your M5 experiment told you, shipped / iterating, the evidence behind the launch**

Nothing yet. This plan is conditional on the entry and launch policy above. A ship at the day-14 read permits launch planning to proceed. Iterate, investigate or kill does not.

**Your persona, pull your M2 persona, this anchors your audience**

A fleet coordinator who assigns routes, logs compliance and hands off shifts. Module 3 moved the persona from driver to coordinator after the workflow and satisfaction data disagreed with the interview emphasis. No interview establishes why coordinators omit compliance. The observations and experiment test that explanation.

### Set your goal, then your audience

**Primary GTM goal, awareness · engagement · conversion, pick one**

Engagement.

**Why this goal? what makes this the right goal for this feature right now**

These users already open RouteLogic. The behavior to change is finishing compliance there. Renewal remains the business signal, but sync and crash bugs outside B1 affect it too.

**Target audience, the specific segment your goal implies, be precise**

Primary: coordinators at eligible accounts, especially those who assign routes but leave compliance unfinished. The scenario gap is 23 points (71% assign, 48% log), about one third of route assigners.

Secondary: ops managers and compliance contacts who rely on the records and approve workflow changes. Only 34% of managers use the Live Dispatch Board, so in-app messaging would miss many of them. They hear from CS before switch-on and may request a delay. The largest account's decision-makers also receive a direct walkthrough.

### Size your launch

**Launch tier, S (minimal) · M (targeted) · L (multi-channel) · XL (full GTM)**

M, targeted.

**Justification, reach + revenue impact + what silence would risk**

The launch changes one step for existing accounts. Four of five churned accounts cite complexity, so the commercial stakes are real, though B1's revenue effect is unmeasured. A quiet release would leave managers unaware of a change to their compliance process. A broader paid campaign would reach people outside the audience. The three owned channels cover users, record owners and the account at risk.

**Is this a launch or a release? does it need go-to-market, or can it just ship?**

The pilot is a flagged release without a campaign. On a ship decision, the targeted launch explains the changed workflow and its measured result. That distinction keeps the A/B test isolated and prepares the people who rely on its records.

### Choose your top three channels and plan assets

**Channel 1, owned / earned / paid, and why it reaches your audience**

Owned, in-app on the route row. A one-time note appears after switch-on when a coordinator assigns a route: "Log compliance for this route here. Driver, vehicle and route are already filled in. Each Pass is one tap, and a Fail asks for a reason." It reaches users at the action, without asking them to find a new screen.

**Channel 2, owned / earned / paid, and why**

Owned, CS email to each account's ops manager and compliance contact one week before switch-on. Pilot accounts receive it on day 1 of week 5, after the result exists. It covers the result, both guardrails, changes to the workflow and how to request a delay. The manager confirms which current logging method RouteLogic will replace.

**Channel 3, owned / earned / paid, and why**

Owned, a largest-account meeting led by its account manager and CS lead. Its relationship and objections need a conversation. The result walkthrough is planned for week 5, or after the week-4 read if the decision falls between them. If the account decides earlier, meet with the evidence available and make no claim that B1 has worked. Get its revenue and decision date first. Those determine whether the sync and crash fixes need priority outside this pilot.

State any checklist mismatch without promising a date. Log objections within 2 working days. After a ship, CS asks the best-performing pilot account for a peer call within one working day. That is an earned extension of this channel. Paid reach is excluded because the audience is already in our base.

**Enablement & assets, what Sales / CS / Support need, plus the assets to build (one-pager, demo, etc.)**

I give CS, Support, the account team and compliance owner the brief by the end of week 4, before customer communication. It includes the measured result when available, the PRD flow and these answers:

- Every check starts blank. Bulk Pass and AI-suggested answers are excluded. Timed sessions must include the checking work, not only taps.
- Wrong driver or vehicle details are corrected in route assignment. A missing assignment blocks the checklist.
- The compliance owner confirms that required checks and the record format are unchanged.
- Submitted errors use the existing audit correction process and count in the accuracy guardrail.
- Draft saving and mobile use are excluded. Only compliance entry changes. Dispatch, routing, handoff and the driver app do not.

| Asset | Builder | Deadline |
|---|---|---|
| Manager one-pager: result, changes, guardrails | CS lead | Draft approved by end of week 4. Compliance owner approves result numbers within one working day of the read |
| FAQ: blocked route, duplicate log, lost answers, corrections | Support lead | End of week 4 |
| In-app note | Designer | End of week 4 |
| 2-minute recorded walkthrough | CS lead | End of week 4 |
| Launch tracker: owners, decisions, risks | Antje Barth | End of week 2 |

The tracker names four risks: checklist mismatch (CS lead), missing route data (pilot engineer), limited CS capacity (PM), and correction handling (compliance owner).

### Make it executable

**Ownership, named owner per key activity, individual, not department**

The scenario names only me. Each other role below is one person, assigned at kickoff. Support and account-manager availability are assumptions to confirm.

| Owner | Responsibility |
|---|---|
| Antje Barth, PM | Entry and day-14 decisions, brief, tracker, wave plan, weekly reads, pause orders and post-launch decision |
| CS lead | Pre-build observations and checklist checks. Later-account fit, contacts and complexity complaints by week 3. Emails, live sessions, one-pager, recording, peer call and objections log |
| Compliance owner | Pre-build fit approval, customer-facing compliance claims, harm investigation and weekly record audits |
| Designer | In-app note |
| Support lead | FAQ and routing corrections into the audit process |
| Pilot engineer, named at kickoff | Flags, rollback and telemetry. Harm alerts and audit queries ready before canary. Rollout dashboard ready by week 4 |
| Largest account's account manager | Renewal meeting before its decision date |

**Budget & resource gaps, what costs extra, and any asset you can't currently build**

There is no media spend. Before the plan locks at the end of week 2, I request CS time and one engineer for rollout and monitoring in weeks 5 to 8. If denied, the waves and final decision move.

Live sessions go to the largest account and accounts that raised complexity. Others get a CS-narrated screen recording. If capacity is tighter, only the largest account gets a live session. B3 is the designer's next candidate after the read and re-score, so the recording needs no production work. With no product marketer, an AI assistant drafts assets, CS edits for customers and the compliance owner approves compliance claims.

**Timeline, Phase 1 beta → Phase 2 launch moment → Phase 3 post-launch**

- **Before week 1:** clear the pre-build evidence gate above. This approves the feasible design and protocol, not unbuilt software.
- **Beta, weeks 1 to 4:** build and instrument in weeks 1 and 2, then clear the pre-exposure implementation gate before randomization. Test for the full 14 days, planned as weeks 3 and 4, with harm monitoring and no campaign. If implementation checks delay the start, move the read and launch dates. Check later accounts and contacts by week 3. Approve asset drafts by week 4, leaving results blank until the read.
- **Launch, weeks 5 to 8, only on a ship:** send pilot-account results on day 1 of week 5. Switch their control coordinators no earlier than day 4. Eligible new accounts follow in provisional weekly waves in weeks 6 to 8. Email one week ahead. Delay requests are due 3 working days before switch-on. Each wave requires the previous wave's 7-day review under the launch policy above.
- **Adoption, weeks 6 to 12:** read each account weekly. Decide at week 12, four full weeks after the last planned wave. Delayed waves move their decision date too.

### Define how you'll know it worked

**Success metrics, 2 to 3 metrics that match your GTM goal**

The dashboard defines three engagement measures: sustained daily completion, first use and logging duration. The controlled pilot estimates B1's effect. Rollout follows whether the behavior persists at eligible accounts. Without a control arm, post-launch changes alone cannot establish causation. Keep cohort, schedule, weighting and duration statistics consistent with the definitions above.

**Bad signal to watch for, e.g. high reach, zero signups = message-market mismatch**

- **Opened but unfinished logs:** CS and the engineer investigate missing assignments, reasons, lost answers and workflow obstacles within 3 working days. Compare eligible workdays and event counts before blaming messaging. An unresolved material block holds the next wave.
- **Fail rate below half of pre-launch:** hold expansion and audit within 2 working days. Check rubber-stamping, changed case mix, better maintenance, selective completion and audit coverage. Sub-20-second all-Pass logs prioritize review but prove nothing by themselves. Confirmed harm restores the old flow and triggers a same-day manager explanation.
- **Pilot completion holds but later accounts stall:** observe shifts, training and actual checking work. Matching item lists do not prove the whole workflow fits.
- **Written compliance concern:** log it the same day and pause that account's switch-on until the compliance owner answers. Do not wait for week-12 CSAT.

**Most likely post-launch decision, double-down · iterate · pivot · deprioritize, and what would trigger it**

Iterate if eligible accounts try B1 but completion is below the locked sustained target at the four-week read. Observe unfinished logs and handoffs. If re-entry fell but physical checking or approvals still prevent completion, revise the workflow and test again before expanding.

Double-down within eligible accounts if completion holds at or above that locked target pooled and in at least two thirds of accounts for four full weeks, with guardrails held and no unresolved harm. B3 needs its own scope and evidence. If completion returns toward the verified pre-launch rate, hold expansion and re-score the roadmap at week 12, or four weeks after the last delayed wave.
