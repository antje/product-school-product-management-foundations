# GTM Strategy & Success Dashboard

Module 6 · Deliverable 6. Scenario: RouteLogic Velocity. Launch: B1 One-Click Compliance Checklist. Owner: Antje Barth (PM). Weeks count from the start of the pilot.

## Go-to-market summary

| Field | Value |
|---|---|
| Feature | B1 One-Click Compliance Checklist |
| Goal | Engagement |
| Launch tier | M, targeted |
| Channels | Owned only: in-app on the route row, CS lead email to managers, largest-account meeting |
| Launch moment | Week 5, only if the pilot ships |

B1 launches to fleet coordinators who already use RouteLogic every day. So the goal is engagement: get them to log compliance in RouteLogic on the day they assign routes. The tier is M. Everyone this launch has to reach already works in RouteLogic or talks to our account team. Three owned channels cover them: a note on the route row, an email to each account's ops manager, and a meeting with our largest account.

The pilot is a release, not a launch. Announcing B1 during the A/B test would contaminate the control arm. The launch comes at general availability in week 5, and only if the day-14 read says ship. If the pilot doesn't ship, there is no launch. Go-to-market can amplify a result the pilot has proven, but it can't create one.

The scariest assumption is that every account can use the same 12 checks. The PRD built B1 on one 12-item list and kept a checklist per account (S5) as a should-have. Three pilot accounts can hide a mismatch. General availability can't. So in week 1, before the build locks, the CS lead checks the 3 pilot accounts' checklists against B1's 12 items. By the end of week 3, the CS lead asks every other account whether its checklist matches. Accounts that match go first.

What the launch must not disrupt: the compliance records managers rely on. They rate Compliance 3.9 and Reporting 4.5 today, and the guardrails below watch both.

## Success dashboard

| KPI | Baseline | Target | Measurement window |
|---|---|---|---|
| Compliance-step completion (feature level, adoption): share of a coordinator's workdays with compliance logged, base coordinators who open RouteLogic that day | 48% | 60% or more pooled, and in at least two thirds of switched-on accounts | Four full weeks after each account's switch-on |
| First-week activation (time to first key action) | New, no baseline | 85% or more of coordinators who assign routes submit a first B1 log | First 7 days after each account's switch-on |
| Median compliance logging time, B1 open to submit | 14.6 min | 3:00 or less, and no slower than the pilot's median | Weekly, from the PRD's event logging (M6) |
| Full daily workflow completion, through handoff (product level) | 31% | 39% | End of week 12 |
| Record accuracy: records corrected or flagged in audit, as a share of submitted logs (guardrail) | Each account's previous 4 weeks | No more than 2 points higher | Weekly |
| Fail rate: share of checks marked Fail (guardrail) | Each account's pre-launch rate | At least half of the pre-launch rate | Weekly |
| Manager Compliance CSAT (guardrail) | 3.9 | 3.9 or higher | End of week 12 |
| Error rate: blocked opens and compliance support tickets | No baseline. First data request: blocked opens in the pilot | Set after the first wave | Weekly |
| Largest account renewal (business level) | Trialing a leaner rival | Renews | Its decision date, still unknown |

Where the targets come from:

- **60%** is the pilot's target: half of the 23 points lost between route assignment (71%) and compliance (48%). Pooling it, with at least two thirds of accounts clearing it, follows the pilot's rule of 2 of 3 accounts. One small account can't block the launch alone.
- **85%** is arithmetic. 85% of the 71% who assign routes is 60%, so below 85% activation the completion target is out of reach. It is a floor, not a forecast.
- **3:00** is the benchmark and the PRD's E1 eval.
- **39%** assumes 65% of coordinators who log compliance still finish the handoff, as today (31 of 48). B3 ships in weeks 5 to 8 and moves this number too, so it reads B1 and B3 together, not B1 alone.
- **The guardrail boundaries** are the ones from the experiment. At general availability they are read against each account's own pre-launch rate, because there is no control arm.
- **The renewal** also depends on bugs B1 doesn't touch, such as late route changes (BUG-2044) and crashes on long routes (BUG-2031). A loss there doesn't prove B1 failed, and a renewal doesn't prove it worked.

## Responses

### Get your prior work ready

**The feature you're launching, from your M4 PRD, one feature, not a list**

B1 One-Click Compliance Checklist. One screen, opened in one tap from the route the coordinator just assigned. Six header fields come pre-filled from RouteLogic and can't be edited. Each of the 12 checks starts blank. A Pass takes one tap, every Fail needs a reason, and the log submits once.

**What your M5 experiment told you, shipped / iterating, the evidence behind the launch**

Nothing yet. VEL-01 runs in pilot weeks 3 and 4, and its read is fixed at day 14. This plan is written ahead of that read, because a GTM plan runs in parallel with the build. It goes ahead only on a ship. That means completion up 12 points or more at p < 0.05 with both guardrails held. The lift must also show in at least 2 of the 3 accounts, and the week-2 lift must be at least half of week 1. On iterate, investigate or kill, there is no launch. B1 stays behind the flag at the pilot accounts, and this plan waits for the next read.

**Your persona, pull your M2 persona, this anchors your audience**

A fleet coordinator, the dispatcher in our research, who assigns routes, logs compliance checks and hands off shifts every day. Module 2 started with the driver. The Module 3 data moved the persona to the coordinator, because that is where the workflow breaks. 71% finish route assignment, but only 48% log compliance, which takes 14.6 minutes against a 3-minute benchmark.

### Set your goal, then your audience

**Primary GTM goal, awareness · engagement · conversion, pick one**

Engagement.

**Why this goal? what makes this the right goal for this feature right now**

B1 lives inside a product coordinators already open every day, so there is no one to make aware. Conversion fits the account at risk, since our largest account is deciding during its trial. But a renewal is a lagging result, and it also depends on the sync and crash bugs outside B1. Logging compliance in RouteLogic is the behavior B1 directly controls, and it is the metric the pilot tests. Retention stays on the dashboard as the business-level signal.

**Target audience, the specific segment your goal implies, be precise**

Primary: coordinators at switched-on accounts who assign routes in RouteLogic but don't go on to log compliance there. Today that is about a third of the coordinators who assign routes (71% assign, 48% log). They are in the product at the moment B1 appears, right after assigning a route.

Secondary: each account's ops manager and compliance contact. Most managers don't work in the dispatch flow. Only 34% of them use the Live Dispatch Board. But they rely on the compliance records and approve changes to how they are made. In this product the user isn't the buyer, so the buyer has to hear what changed before the user sees it. Switch-on is the default. A manager or compliance contact can ask to delay, and the account moves to a later wave.

Also reached: the decision-makers at our largest account. The aim there is to remove slow compliance logging as a reason to switch. That is risk removal, not a launch KPI, so the goal stays engagement.

### Size your launch

**Launch tier, S (minimal) · M (targeted) · L (multi-channel) · XL (full GTM)**

M, targeted.

**Justification, reach + revenue impact + what silence would risk**

Reach: every coordinator at every account, switched on in weekly waves from week 5 to week 8. Accounts that ask to delay, or whose checklist doesn't match, switch on later. The change sits in one step of one workflow. Revenue impact: indirect, but high stakes. Four of five churned accounts cite complexity, and our largest account is trialing a leaner rival.

What silence would risk: little for adoption, a lot for trust. Coordinators would find the button, because it sits on the route row they already use. But managers and compliance contacts would see their compliance flow change without warning. And the largest account would decide without hearing that the slowest step in the workflow is fixed.

So S is too small. L is too big: earned and paid channels reach people outside RouteLogic, and everyone this launch needs is already inside it.

**Is this a launch or a release? does it need go-to-market, or can it just ship?**

Both, in sequence. In the pilot, B1 is a release behind a feature flag, with no go-to-market. The isolation check rules out demos of B1, and telling coordinators about it would contaminate the control arm. At general availability it becomes a launch. It changes how compliance records are made at every account, and the people who rely on those records should hear it from us first.

### Choose your top three channels and plan assets

**Channel 1, owned / earned / paid, and why it reaches your audience**

Owned · in-app, on the route row. The "Log compliance" button, plus a one-time note the first time a coordinator assigns a route after switch-on: "Log compliance for this route here. Driver, vehicle and route are already filled in. Each Pass is one tap, and a Fail asks for a reason." It reaches coordinators at the step where the workflow breaks today. It doesn't reach managers, who mostly work elsewhere in the product.

**Channel 2, owned / earned / paid, and why**

Owned · email from the CS lead to each account's ops manager and compliance contact, one week before that account's switch-on. Pilot accounts get theirs on the first day of week 5 with the result, because they already know B1. It covers what changes, what doesn't, and the pilot result with both guardrails. It also asks the manager to confirm that RouteLogic replaces their current logging method from switch-on. In-app would miss these people. They own the records and approve changes to how they are made.

**Channel 3, owned / earned / paid, and why**

Owned · a meeting with our largest account during its trial, led by its account manager with the CS lead. It's a live walkthrough of B1 with the pilot results. A renewal decision doesn't turn on a mass email. It depends on the account team's relationship with the customer, and AI can't do that part.

The meeting is in week 5. If the account's decision date comes first, it moves to the end of week 4 and uses the ship read. If its checklist doesn't match B1's 12 items, the meeting says so and doesn't promise a date. I take a checklist for that account (S5) to the roadmap re-score at the week-4 read-out. The meeting is done when it's held before the decision date and the CS lead has logged the objections within 2 working days.

Within one working day of a ship decision, the CS lead asks the best-performing pilot account's ops manager for a call with the largest account. No customer is asked to vouch for B1 before it ships. That call is the earned version of this channel. A peer saying it works carries more weight than we do.

I rejected paid channels. They buy reach beyond our base, and everyone this launch needs is already in it.

**Enablement & assets, what Sales / CS / Support need, plus the assets to build (one-pager, demo, etc.)**

I write the enablement brief. It goes to the CS lead, Support, the account team and the compliance owner by the end of week 4. No customer hears about B1 before them.

- **What it is:** a one-screen compliance checklist for fleet coordinators. It lets them log compliance right after assigning a route, built to cut logging from 14.6 minutes to about 3. Customer-facing copy quotes the pilot's measured median time, not the target.
- **How it works:**
  - Opens in one tap from an assigned route.
  - Pre-fills six header fields from the route record, locked against edits.
  - Starts all 12 checks blank and records each Pass in one tap.
  - Asks for a reason on every Fail.
  - Blocks submit until every check has an answer, and keeps one record per route and shift.
- **Common objections:**
  - "Why is there no 'mark all as pass'?" A pass nobody checked is a guessed record, and 12 taps still fit inside 3 minutes (PRD decision D1).
  - "The driver or vehicle is wrong." Fix it in route assignment. The checklist copies the route record and can't be edited.
  - "Is this still compliant?" The checklist items and the record format are unchanged, and the compliance owner signs off on both before launch.
  - "I submitted a wrong answer. How do I fix it?" Through the audit correction process used today. B1 doesn't change the record format, so the correction path stays the same.
  - "Can I save a draft, or use it on my phone?" Not in this version. Saving a draft is a should-have (S3), and the mobile dashboard (B4) is cut.
- **What's changing:** only the compliance step. **What's not:** route assignment, the dispatch board, shift handoff, the daily report, the driver app, the checklist items and the record format.

Assets to build:

| Asset | Builder | Ready by |
|---|---|---|
| One-pager for ops managers: the pilot result, what changes, and the guardrail results | CS lead | Signed off by end of week 4 with the result left blank. The compliance owner approves the numbers within one working day of the read. |
| Support FAQ for the three blocks: no driver or vehicle on the route, route already logged this shift, answers lost on leaving mid-checklist | Support lead | End of week 4 |
| In-app note | Designer | End of week 4 |
| 2-minute recorded walkthrough for accounts that don't get a live session | CS lead | End of week 4 |
| Launch tracker: owners, a decisions log and the risks below | Antje Barth (PM) | End of week 2 |

The tracker watches four risks, each with an owner:

- Checklists may differ from B1's 12 items (CS lead).
- Routes missing a driver or vehicle block the checklist, so dispatch data quality matters (pilot engineer).
- One CS lead has limited capacity (Antje Barth).
- Corrections after submit go through the audit correction path (compliance owner).

The PRD blocks a second record per route and shift, but doesn't define how to correct a submitted one. In this version, corrections go through the existing audit correction process. The record-accuracy guardrail counts those corrections, so Support sends every correction request there.

### Make it executable

**Ownership, named owner per key activity, individual, not department**

The scenario names only me, so the other owners are roles. Each role is one person.

- **Antje Barth (PM):** this plan, the enablement brief, the launch tracker and the wave plan by the end of week 4. Also delay approvals, the day-14 go/no-go, the weekly metric read, the all-Pass log review and the post-launch decision.
- **CS lead:** the pilot accounts' checklist check in week 1. The checklist-match check for every other account, contact confirmation and the list of accounts that raised complexity, all by the end of week 3. Also delay requests, the manager emails, live sessions, the one-pager, the walkthrough recording, the peer-call ask and the objections log.
- **Compliance owner:** sign-off on every customer-facing sentence about compliance by the end of week 4, and the weekly count of audit corrections for the record-accuracy guardrail.
- **Designer:** the in-app note.
- **Support lead:** the FAQ, and routing every correction request to the audit correction process.
- **One of the two pilot engineers, named at kickoff:** the flag ramp per account and the weekly query of all-Pass logs. Also the monitoring dashboard, built on the PRD's event logging (M6) and ready by the end of week 4.
- **The largest account's account manager:** the renewal meeting.

The scenario doesn't name the Support lead or the account manager, so I'm assuming both roles exist.

**Budget & resource gaps, what costs extra, and any asset you can't currently build**

There's no media spend, because every channel is owned. The cost is people's time, and three gaps follow from it.

1. One CS lead can't run live sessions at every account. Live sessions go to the largest account and to accounts that have raised complexity with us. The rest get the recorded walkthrough. If time runs short, live sessions drop to the largest account only.
2. The designer is on B3 in weeks 5 to 8. The walkthrough is a screen recording the CS lead narrates, not a produced video.
3. There's no product marketer. An AI assistant drafts the one-pager, the email, the FAQ and the in-app note. The CS lead edits them for customers, and the compliance owner edits them for compliance.

I make two requests before the plan locks at the end of week 2. One is the CS lead's time in weeks 5 to 8. The other is one engineer for the ramp and the dashboard. If either is denied, the waves stretch out, and the week-12 decision moves with the last wave.

**Timeline, Phase 1 beta → Phase 2 launch moment → Phase 3 post-launch**

- **Phase 1 · Beta (pilot weeks 1 to 4).** B1 is built in weeks 1 and 2 and runs as a canary at the end of week 2. It is A/B tested in weeks 3 and 4. Nothing is announced. In week 1, before the build locks, the CS lead checks the 3 pilot accounts' checklists against B1's 12 items. By the end of week 3, the CS lead checks every other account's checklist and confirms its ops manager and compliance contact. By the end of week 4, the assets are drafted and signed off, but nothing is sent. Track: how often the variant arm uses B1, and whether the week-2 lift holds at least half of week 1. Go/no-go at the end of week 4, on day 14 of the test.
- **Phase 2 · Launch moment (week 5, only on a ship).** Internal teams get the brief before any customer. In week 5, the pilot accounts get the result by email on day 1, and their control coordinators switch on no earlier than day 4. New accounts follow in weekly waves from week 6 to week 8, with matching checklists first. Each wave's email goes out a week before its switch-on. A manager's delay request is due 3 working days before switch-on. Each wave switches on only after the previous wave's 7-day activation read is in. If our largest account isn't a pilot account, it joins the week-6 wave, as long as its checklist matches. Track: first-week activation in each wave.
- **Phase 3 · Post-launch adoption (weeks 6 to 12).** I read each account weekly. Track: adoption velocity, meaning how many weeks each wave takes to reach 60% completion, and the error rate. The decision comes at the end of week 12, four full weeks after the last wave.

### Define how you'll know it worked

**Success metrics, 2 to 3 metrics that match your GTM goal**

1. **Compliance-step completion, the adoption rate:** from 48% to 60% or more, four full weeks after switch-on. It is the share of a coordinator's workdays with compliance logged, among coordinators who open RouteLogic that day, as in the pilot. It is pooled across switched-on accounts and must also hold in at least two thirds of them. It's the target the pilot tested. The pilot answers whether B1 works. General availability answers whether the result carries over to other accounts.
2. **First-week activation, the time to first key action:** 85% or more of coordinators who assign routes submit a first B1 log. The window is the first 7 days after switch-on. Below that, 60% completion is out of reach.
3. **Median logging time, from B1 open to submit:** from 14.6 minutes to 3:00 or less, and no slower than the pilot's measured median. It shows whether the time saving still drives the result outside the pilot.

The guardrails are read against each account's pre-launch rate. Corrected or flagged records, as a share of submitted logs, rise by no more than 2 points over the account's previous 4 weeks. The Fail rate stays at least half of its pre-launch rate. Manager Compliance CSAT stays at 3.9 or higher.

**Bad signal to watch for, e.g. high reach, zero signups = message-market mismatch**

- **Coordinators open B1 but don't submit.** This is the engagement bad signal: people reach the feature but not the first key action. The diagnostic is opens without a submit, from the event logging. The threshold is a wave below 85% first-week activation. Then the CS lead and the pilot engineer pull the block reasons within 3 working days, and the next wave waits until the cause is known. Check the three known blocks first, then checklist items that don't match the account's own list. Fix the data or the checklist, not the messaging.
- **Completion rises but the Fail rate collapses.** Coordinators are tapping Pass to clear the blocked submit. The threshold is the guardrail: an account's Fail rate below half its pre-launch rate in any week. I review its all-Pass logs submitted in under 20 seconds within 2 working days, as in the pilot. If confirmed, that account pauses: its flag turns off, coordinators go back to the old flow, and the CS lead tells its manager the same day.
- **Completion holds at pilot accounts but stalls in later waves.** The pilot result didn't carry over. Compare checklist match, and live session against recording, before blaming the product.
- **A compliance contact escalates,** meaning any written concern to CS, Support or the account team, logged the same day. It shows a trust problem weeks before CSAT would. That account's switch-on pauses until the compliance owner has answered.

**Most likely post-launch decision, double-down · iterate · pivot · deprioritize, and what would trigger it**

Iterate. B1 was designed on one 12-item list, and the PRD named the real item count as its main open assumption. The trigger: the later waves, whose checklists differ from B1's, stall below 60% while the matching accounts clear it. The one variable to change is the audience. B1 stays on where it fits, and the remaining waves pause until S5 ships a checklist per account.

Double-down if pooled completion holds at 60% or more for four full weeks, in at least two thirds of switched-on accounts, with the guardrails held. Then B1 stays on everywhere, and B3 launches to the same audience through the same channels. Deprioritize if completion at the new accounts slides back toward 48% within four weeks of switch-on. That would mean the pilot result didn't carry over, and the roadmap gets re-scored.
