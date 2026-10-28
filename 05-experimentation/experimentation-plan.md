# Experimentation Plan

Module 5 · Deliverable 5. Scenario: RouteLogic Velocity. Experiment: VEL-01 One-Click Compliance Checklist. Owner: Antje Barth (PM). Sign-off: the CS lead and the compliance owner.

## Overview

This is an A/B test of the One-Click Compliance Checklist (B1) inside the 4-week pilot. B1 takes the first two weeks to build. The test runs for the last 14 days, two full weekly dispatch cycles, with one fixed read at the end.

**Why it matters.** Our largest account is trialing a leaner rival, coordinator NPS fell from +18 to -12, and four of five churned accounts cite complexity. Compliance logging is the step where coordinators leave RouteLogic. This test decides whether B1 rolls out to every account.

**Why this method.** The question is whether one change moves one metric, so the experiment type is an A/B test. A pilot of about 540 coordinators sits below the usual 1,000-user guide for A/B tests. Measuring each coordinator's daily rate gives about ten observations per person instead of one. The stakes are high, so the test combines three methods:

- **Canary:** at the end of week 2, the CS lead and two coordinators use B1 for two days to confirm it is stable.
- **Feature flag:** the flag controls who sees B1 and allows instant rollback.
- **Phased rollout:** if B1 ships, it goes to one account, then all three, then general availability.

A multivariate test would need about ten times the traffic. A fake door would only measure interest, and demand for a faster form is not in doubt.

**Instrumentation.** The M6 events from the PRD (checklist opened, item answered, submitted, time taken) are the experiment tags. The two engineers build them with B1 in weeks 1 and 2, and they must work in the canary before randomization starts.

## What you're testing

| Element | Detail |
|---|---|
| Hypothesis under test | B1 gets fleet coordinators to finish compliance logging in RouteLogic, lifting daily compliance-step completion from 48% to 60%. |
| Experiment design (A/B, etc.) | A/B test, 50/50 by coordinator within each of the 3 pilot accounts, exposed through a feature flag tied to the login. |
| Primary metric | Daily compliance-step completion, per coordinator, averaged per arm. |
| Guardrail metric | Record accuracy, and the Fail rate as a check against rubber-stamping. |
| Decision rule (ship / kill / pivot) | Ship at +12 points or more with p < 0.05 and both guardrails held. Iterate, investigate or kill otherwise. Read fixed at day 14. |

## Parameters

| Parameter | Decision |
|---|---|
| Feature under test | B1 One-Click Compliance Checklist, as specified in the Simplified PRD |
| Persona | Fleet coordinator who assigns routes, logs compliance checks and hands off shifts every day |
| Expected outcome | Coordinators finish compliance logging in RouteLogic on the day they assign routes |
| Primary success metric | Daily compliance-step completion, per coordinator, averaged per arm |
| Baseline rate | 48% |
| Guardrail metric | Record accuracy: records corrected or flagged in the compliance audit |
| Guardrail boundary | No more than 2 points above control |
| Second guardrail | Fail rate: share of checks marked Fail, not below half of control |
| Minimum Detectable Effect | +12 percentage points (48% to 60%) |
| Sample size per arm | 270 coordinators (540 in total) |
| Traffic split | 50/50 by coordinator, within each of the 3 pilot accounts |
| Test duration | 14 days, pilot weeks 3 and 4 |
| Significance threshold | p < 0.05, two-sided |

## Get your documents ready

**From M3, your hypothesis sentence**

Based on dispatchers who "can't trust the board" and 14.6-minute compliance logs, I believe faster compliance logging will get fleet coordinators to finish their day in RouteLogic. It will show as a 25% increase in compliance-step completion, from 48% to 60%.

**From M3, your primary success metric & guardrail metric**

Primary: compliance-step completion, 48% to 60%. Guardrail: record accuracy holds and the Fail rate does not collapse, with manager Compliance CSAT at 3.9 or higher.

**From M4, the feature you scoped in your PRD this is what you're testing**

B1 One-Click Compliance Checklist. It is one screen, opened in one tap from the assigned route, with six read-only pre-filled fields. Each check takes one tap, every Fail needs a reason, and submit stays blocked until every check has an answer.

## Define your experiment parameters

**Feature under test, pull from your M4 PRD**

B1 One-Click Compliance Checklist, as specified in the Simplified PRD. We test the package. The decision is whether to ship B1 as a whole, so the lift is not attributed to any single part.

**Persona, pull your M2 persona**

A fleet coordinator, the dispatcher in our research, who assigns routes, logs compliance checks and hands off shifts every day.

**Expected outcome, the behaviour change you expect, from your M3 hypothesis**

Coordinators finish compliance logging in RouteLogic on the same day they assign routes, instead of leaving the tool for WhatsApp and paper.

**Primary success metric, the one number that defines success, from M3**

Daily compliance-step completion: the share of a coordinator's workdays on which they finish logging compliance checks in RouteLogic. It is computed per coordinator and averaged per arm. The base is coordinators who open RouteLogic that day, the same base as the M3 funnel. All randomized coordinators are analyzed, whether or not they use the checklist.

**Baseline rate, today's rate of your primary metric, from your M3 data**

48%. Among coordinators who finish route assignment, it is already about 68% (48 of 71), so the 60% target means about 85% of route assigners.

**Guardrail metric & boundary, what must not break, and how far it can move before you investigate**

Two guardrails, each against the control arm in the same weeks:

- **Record accuracy:** measured as the share of records later corrected or flagged in the compliance audit, including wrong pre-filled drivers or vehicles. Boundary: no more than 2 points above control.
- **Fail rate:** the share of checks marked Fail. More Fails can mean more honest logging. A collapse means coordinators are tapping Pass to clear the blocked submit. Boundary: not below half of the control rate. All-Pass records submitted in under 20 seconds are reviewed as the diagnostic.

Manager Compliance CSAT, which must stay at 3.9 or higher, is tracked across the whole pilot. It cannot be split by arm, because managers see records from both.

**Minimum Detectable Effect (MDE), the smallest improvement worth shipping, your floor**

+12 percentage points, from 48% to 60%. That recovers half of the 23 points lost between route assignment (71%) and compliance (48%). A smaller lift would not remove the main barrier.

**Sample size per arm, use the calculator in the builder, baseline + MDE**

270 coordinators per arm, 540 in total, from the standard two-proportion formula: baseline 48%, MDE 12 points, 80% power, 5% significance. This assumes the 3 pilot accounts have 540 active coordinators. If they have fewer, running longer does not help, because it adds no coordinators. Power then comes from the per-coordinator daily rate, from adjusting for each coordinator's pre-pilot logging rate (CUPED), and from analyzing by account.

**Traffic split & test duration, 50/50 standard · cover ≥ 2 weekly cycles**

50/50 by coordinator, randomized within each account so the accounts balance. An even split is a real choice here, not a default. The coordinator population is small, and any other split would leave one arm too small to read. 14 days, pilot weeks 3 and 4, which covers two full weekly dispatch cycles.

**Significance threshold, p < 0.05 is standard, explain any deviation**

p < 0.05, two-sided, with no deviation. There is one primary metric, so no multiple-comparison correction is needed. The guardrails are checks against harm, not extra chances to win.

## Define your control and variant

**Control (A), the current experience, reference your M2 moment of misery and M3 funnel/workflow data**

Today's compliance step. Coordinators log checks across several screens and re-type driver, vehicle and route details. It takes 14.6 minutes against a 3-minute benchmark. 71% finish route assignment, but only 48% log compliance, and the rest of the day runs in a WhatsApp group and on paper.

**Variant (B), your single change, copy the relevant screens & functional requirements from your M4 PRD**

The B1 checklist from the PRD:

- **Screen 1, Today's Routes:** each assigned route has a "Log compliance" button. Routes without a driver or vehicle show "Assign a driver and vehicle before logging compliance".
- **Screen 2, Compliance Checklist:** a read-only "From RouteLogic" card with six fields, then 12 checks that start blank with one tap each. A Fail opens a reason list, and "Other" needs a note. Submit stays blocked until every check has an answer.
- **Screen 3, Compliance Logged:** passes, fails and time taken, with failed checks listed first.
- **Rules:** FR1 to FR7, including one record per route per shift and events logged for every step.

**Isolation check, what has NOT changed?**

Identical in both arms:

- route assignment and the optimizer
- the dispatch board
- the shift handoff and daily report steps
- the driver app and its notifications
- the checklist items and the compliance record format
- the app version

The CS lead's onboarding uses the same general compliance script for both arms, before randomization, and never demos B1. The flag follows the login, not the device, so a control coordinator on a shared depot screen still sees control. Crossovers are logged.

## Formalize your hypothesis & shipping criteria

**Your hypothesis (filled in)**

I believe that B1, the One-Click Compliance Checklist, for fleet coordinators will result in more compliance logged in RouteLogic, as measured by a +12-point change in daily compliance-step completion within 14 days. We will protect record accuracy and the Fail rate throughout the test.

**Your shipping criteria (filled in)**

We will **ship** if daily compliance-step completion improves by 12 points or more at p < 0.05 after 14 days. Neither guardrail may reach its boundary. The lift must point the same way in at least 2 of the 3 accounts. And the week-2 lift must be at least half of week 1.

We will **iterate** if the direction is positive but the lift is below 12 points. The next step is a sharper variant or more accounts, not a rollout.

We will **investigate** if completion clears the bar but a guardrail breaks, or the accounts disagree. We find out who was harmed before any decision.

We will **kill** if completion shows no improvement or moves down. We also kill if record accuracy is breached by more than twice its boundary, whatever the primary result.

The read date is fixed at the end of day 14, which is the end of pilot week 4. No results are reviewed before then. Once the test is live, targeting, the variant and the metrics do not change. No other Velocity change ships to the pilot accounts during the test. A sample-ratio check runs at launch and at the read, and a split far from 50/50 makes the test invalid. The read covers all five questions: significance, lift against the MDE, the confidence interval, both guardrails, and the segments. The segments are account, shift (day or night) and coordinator tenure, since new coordinators struggle most with the current menus. A confidence interval that crosses zero means iterate, however good the midpoint looks. Median time to submit is reported alongside. It does not gate the decision, but it shows whether the time saving was the mechanism. Every outcome, including a kill, is logged with its rationale in the team's experiment library. A clean result ships on day 14 without reopening the debate.

**Hardest parameter to define, and did it change your hypothesis? quick debrief**

The guardrail. My first guardrail, "no rise in incomplete or failed records", had a flaw. In the variant, incomplete records cannot happen because submit is blocked, so that guardrail could never fail. And more Fails can mean coordinators finally log honestly. The real risk of a faster form is rubber-stamping. So the hypothesis now protects record accuracy and the Fail rate instead. The sample size was the second hardest. A B2B pilot has coordinators, not millions of users, and 540 active coordinators is an assumption.
