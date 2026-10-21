# Hypothesis & Success Metrics

Module 3 · Deliverable 3. Scenario: RouteLogic Velocity. Bet type: optimizing the existing.

## Pre-work · Hypothesis check

**Role, who you are solving for (from M2)**

A delivery driver making dozens of stops a day, often at a doorstep with one hand free.

**Goal, what this user is ultimately trying to achieve**

To confirm each stop and move on in seconds, with the rest of the route still there.

**Friction / moment of misery, the specific pain blocking their goal**

Marking a stop delivered takes three taps across three screens, at a doorstep in the rain with a package in one hand (UXR-01, BUG-2055).

**Current workaround, the external tool or manual process they rely on (M2)**

The driver texts the dispatcher instead of tapping. Drivers keep a paper manifest and a morning screenshot of the route as backup. The dispatcher runs a WhatsApp group as "the real system".

**Problem Hook, your one-sentence framing of the business crisis (M1)**

We must keep our largest account and reverse the drop in daily use across our base by making the actions drivers and dispatchers repeat all day faster inside RouteLogic than the texts, WhatsApp messages and paper they fall back on today.

**Value Proposition, the outcome your initiative promised to deliver (M1)**

For delivery drivers and their dispatchers, the frontline users among the 95% who rely on RouteLogic every day, we will make start route, mark delivered and route changes faster than the texts, WhatsApp group and paper they fall back on today, by moving the compliance and finance layers off their screens while keeping them one step away for the admins and executives who bought RouteLogic for them, because our largest account is deciding during its trial and frontline usage is already falling across the base.

## Read your data snapshots

### Snapshot 1 of 3 · Feature adoption by role

**Does the low adoption confirm your persona is burdened by tools they don’t use? Note whether the low scheduling adoption (42%) for coordinators matches your M2 moment of misery.**

Partly. Drivers carry tools they don't use: Financial Reporting reaches 3% of them, AI Predictive ETAs 11% and Shift Scheduling 15%. But their daily work clusters on three features: Live Dispatch Board (88%), Route Optimizer (72%) and Compliance Checklist (64%). The three-tap delivery sits inside that core, so the burden is less about unused tools than about how the used ones work. The coordinators' 42% scheduling adoption does not match our Module 2 misery: no research note mentions scheduling. It is a gap worth noting, not the pain we found. The surprise is compliance, the third most used feature for both frontline roles (77% of coordinators, 64% of drivers). That makes it core work, not a layer to move off their screens, which contradicts our Module 1 value proposition. These snapshots slice by role only, the behavioral lens. Tenure and account tier are not in the data, so I cannot tell whether compliance hurts new coordinators most or specific accounts most.

### Snapshot 2 of 3 · Coordinator daily dispatch workflow completion

**Does the workflow data match the manual process or hack you documented in M2? Note whether the specific drop-offs or time gaps explain why your persona avoids the digital tool.**

It explains the dispatcher's side of the Module 2 workaround, and it moves the main pain away from our persona. Coordinators, the dispatchers in our research, get through route assignment in RouteLogic: 71% finish it. Then the workflow falls apart. Only 48% log compliance checks, 31% complete the shift handoff and 18% file the daily report. Of the coordinators who assign routes, 56% never finish the handoff. That fits a WhatsApp group running the day once the routes go out (UXR-02). The largest time gap is compliance: 14.6 minutes against a 3-minute benchmark, nearly five times longer. It accounts for 11.6 of the 29.8 minutes the five steps run over benchmark. Our persona, the driver, is not in this funnel at all. That is the first pivot check: the main bottleneck sits with the coordinator at compliance, not with the driver at the doorstep.

### Snapshot 3 of 3 · Account health & CSAT by segment

**Look at the CSAT heatmap. Which specific cell most directly maps to your persona’s friction? Note how the NPS trend justifies the urgency of your M1 Problem Hook.**

Coordinators × Compliance, at 2.2 out of 5: the lowest score any role gives a feature it uses daily. The cell for our Module 2 misery, Drivers × Core Dispatch, scores 4.3, the best frontline score in the table. That is the second pivot check: our persona is satisfied where we placed the pain. A three-tap annoyance can hide inside a high cluster average, but it is not the leak behind the account crisis. The trend shows where the urgency is. Coordinator NPS fell from +18 to -12 in two years. Daily time lost to manual workarounds rose from about 9 to 31 minutes. Four of five churned accounts now cite complexity, against one of eight two years ago. Over time this is a decline, so it is a leak that needs a fix to restore lost value. The data gives two points in time, not a full cohort table, so the shape between them is unknown. Managers rate Compliance 3.9 and Reporting 4.5, so the buyer is content while the frontline struggles. That is the gap the Module 1 hook named: losing the daily user while winning the executive demo. The pivot: the persona becomes the coordinator, and the friction becomes compliance logging.

## Step 3 · Craft your hypothesis

**Qualitative evidence (from M2), quote the specific friction / moment of misery for your persona**

Dispatchers do not trust RouteLogic for the live day: "I can't trust the board" (UXR-09) and "We keep a WhatsApp group as the real system" (UXR-02). An enterprise ops manager adds: "My frontline people use maybe 5% of it and can't find that 5%" (UXR-04). Gap: no interview mentions compliance. The qualitative evidence shows coordinators leaving the tool. It does not show that compliance is the reason.

**Quantitative evidence (from M3), name the metric or data point that confirms the pain; cite the number**

Logging compliance checks takes coordinators 14.6 minutes against a 3-minute benchmark, and completion falls from 71% at route assignment to 48% at compliance. Coordinators rate Compliance 2.2 out of 5 while 77% of them use it daily. Coordinator NPS fell from +18 to -12, and four of five churned accounts cite complexity.

**Persona, role, goal, and the friction you confirmed in the reconciliation steps**

Role: a fleet coordinator, the dispatcher in our research, who assigns routes, logs compliance checks and hands off shifts every day. Goal: run the whole daily workflow inside RouteLogic. Friction: compliance logging, at 14.6 minutes against a 3-minute benchmark, the step where the workflow breaks. The driver stays at the other end of the handoff, and drivers also fill in the checklist (64% use it, CSAT 2.8).

**Problem you are solving, one sentence describing the specific friction this initiative removes**

Logging compliance checks takes coordinators nearly five times the benchmark, so most of them stop using RouteLogic for the rest of the day.

**Strategic outcome, what behaviour change do you expect, and how does it map to retention / revenue / churn?**

Coordinators finish the daily workflow in RouteLogic instead of leaving after route assignment. On the AARRR funnel this is retention of daily use, a stage the product directly controls. It cuts the complexity that four of five churned accounts cite, which is the churn risk behind our largest account's trial. The funnel we own is the coordinator's daily workflow. The manager's funnel depends on it: renewal holds only if managers keep getting complete records, and that happens only if coordinators finish the workflow inside RouteLogic. The bet is optimizing the existing: fix friction in a known workflow and measure retention and conversion, not activation.

**Primary success metric (initiative signal), the leading indicator that tells you the gap is closing**

Compliance-step completion: the share of coordinators who open RouteLogic and finish logging compliance checks in it. Baseline 48%, target 60%, a 25% relative increase. 60% recovers half of the 23 points lost between route assignment (71%) and compliance (48%). Recovering less than half would mean the fix has not removed the main barrier. Supporting signal: median compliance logging time falls from 14.6 to 7.3 minutes or less. That halves the time and still sits at 2.4 times the benchmark. The Velocity pilot made route assignment 34% faster, so halving a step with a much larger gap is an ambitious bar, not a safe one.

**Guardrail metric (product signal), the metric that must NOT drop; it protects your existing base**

Compliance quality. Managers rate Compliance 3.9 today and rely on these records for the reporting they bought (Reporting 4.5). A faster flow must not come from skipped checks. Guardrail: manager Compliance CSAT stays at 3.9 or higher, and the share of incomplete or failed compliance records does not rise. The snapshots give no baseline for incomplete records.

**Decision window, how much time or data before you scale, pivot, or kill? minimum threshold to proceed?**

First, confirm the 48% is real: check that compliance checks done on paper or another device are not simply missing from the data, the tracking-error check. Then four weeks, with at least 270 coordinators in each group (current flow and faster compliance flow). 270 per group is what it takes to tell 48% from 60% with 80% power at 5% significance. Scale if completion reaches 60% and the guardrail holds. Iterate if completion improves significantly but stays below 60%. Kill and rethink if the difference is not significant or the guardrail breaks.

## Finalized product hypothesis

**Draft your full hypothesis sentence, one to three sentences; quote the metric, name the persona, name the outcome**

> Based on dispatchers saying they "can't trust the board" and run the day in WhatsApp, and on compliance logging taking 14.6 minutes against a 3-minute benchmark while completion falls from 71% to 48% at that step, I believe that cutting compliance logging toward the benchmark for fleet coordinators will result in coordinators finishing their daily workflow inside RouteLogic, as measured by a 25% increase in compliance-step completion (48% to 60%). I will protect compliance quality (manager Compliance CSAT at 3.9 or higher, no rise in incomplete records) and will make a go/no-go decision after four weeks and at least 270 coordinators per group.

Checked against the four pitfalls:

- **Vague or broad:** it names the persona (fleet coordinators), the behavior (finishing the daily workflow in RouteLogic) and the metric (compliance-step completion).
- **Biased framing:** it states the problem to solve (compliance takes five times the benchmark), not a feature.
- **Not testable:** it has a baseline, a target and a sample size.
- **Misaligned:** it moves daily use, which is what the hook and the churned accounts are about.

## Success metrics

| Metric | Type | Target | Why it matters |
|---|---|---|---|
| Full daily workflow completion (through shift handoff), averaged over the last two weeks of the test | North-star, success signal, lagging | 31% → 39% | Proves value, not just use: coordinators keep finishing the day in RouteLogic after the novelty wears off. 39% assumes the handoff step keeps converting 65% of coordinators who log compliance, as it does today (31 of 48). |
| Compliance-step completion | Leading indicator, initiative signal | 48% → 60% (+25%) | The step where the workflow breaks, and one the build directly moves. Median logging time from 14.6 to 7.3 minutes or less supports it. |
| Manager Compliance CSAT and compliance record completeness | Guardrail, counter-metric | CSAT ≥ 3.9, and incomplete or failed records do not rise | Speed must not come from skipped checks. The buyer relies on these records. |
